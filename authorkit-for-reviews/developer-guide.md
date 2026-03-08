# Developer Guide

This guide covers hooks, filters, and functions available to developers who want to customize or extend the AuthorKit Reviews module. Use these tools to integrate reviews with custom themes, add functionality, or modify default behavior.

## Core Functions

Access review data programmatically using these functions:

**Get Reviews for a Book**:
```php
$reviews = authorkit_get_reviews( $book_id, $args );
```
Parameters:
- `$book_id` (int): The book post ID
- `$args` (array): Optional query arguments (status, limit, offset, orderby)

Returns an array of review objects.

**Get Average Rating**:
```php
$average = authorkit_get_average_rating( $book_id );
```
Returns a float between 0 and 5.

**Get Review Count**:
```php
$count = authorkit_get_review_count( $book_id, $status = 'approved' );
```
Returns the total number of reviews for a book.

**Check Review Limit**:
```php
$can_accept = authorkit_can_accept_review( $book_id );
```
Returns boolean indicating whether the book can accept more reviews (considers free tier 3-review limit).

**Submit a Review Programmatically**:
```php
$review_id = authorkit_submit_review( array(
    'book_id' => 123,
    'reviewer_name' => 'John Doe',
    'reviewer_email' => 'john@example.com',
    'rating' => 5,
    'review_text' => 'Excellent book!',
    'verified' => false,
    'status' => 'pending'
) );
```

## Action Hooks

Perform custom actions at specific points in the review lifecycle:

**Before Review Submission**:
```php
do_action( 'authorkit_before_review_submit', $review_data );
```
Fires before a review is saved to the database. Use for validation or logging.

**After Review Submission**:
```php
do_action( 'authorkit_after_review_submit', $review_id, $review_data );
```
Fires after a review is successfully saved. Use for notifications or integrations.

**Review Status Changed**:
```php
do_action( 'authorkit_review_status_changed', $review_id, $old_status, $new_status );
```
Fires when a review is approved, rejected, or status is modified.

**Review Deleted**:
```php
do_action( 'authorkit_review_deleted', $review_id, $review_data );
```
Fires before a review is permanently deleted.

**Before Review Display**:
```php
do_action( 'authorkit_before_reviews_display', $book_id );
```
Fires before the review section renders on the frontend.

**After Review Display**:
```php
do_action( 'authorkit_after_reviews_display', $book_id );
```
Fires after the review section renders.

## Filter Hooks

Modify review data and behavior using filters:

**Filter Review Data Before Save**:
```php
add_filter( 'authorkit_review_data_before_save', function( $review_data ) {
    // Modify review data
    $review_data['review_text'] = sanitize_text_field( $review_data['review_text'] );
    return $review_data;
} );
```

**Filter Average Rating Display**:
```php
add_filter( 'authorkit_average_rating_display', function( $average, $book_id ) {
    // Round to nearest 0.5
    return round( $average * 2 ) / 2;
}, 10, 2 );
```

**Filter Review Query Arguments**:
```php
add_filter( 'authorkit_review_query_args', function( $args, $book_id ) {
    // Modify query parameters
    $args['limit'] = 20;
    return $args;
}, 10, 2 );
```

**Filter Review Submission Form Fields**:
```php
add_filter( 'authorkit_review_form_fields', function( $fields ) {
    // Add custom field
    $fields['custom_field'] = array(
        'type' => 'text',
        'label' => 'Custom Field',
        'required' => false
    );
    return $fields;
} );
```

**Filter Spam Detection**:
```php
add_filter( 'authorkit_is_review_spam', function( $is_spam, $review_data ) {
    // Add custom spam detection logic
    if ( strpos( $review_data['review_text'], 'banned-word' ) !== false ) {
        return true;
    }
    return $is_spam;
}, 10, 2 );
```

**Filter Email Notification Recipients**:
```php
add_filter( 'authorkit_review_notification_recipients', function( $recipients, $review_id ) {
    // Add additional recipients based on book category
    $recipients[] = 'editor@example.com';
    return $recipients;
}, 10, 2 );
```

**Filter Review Display HTML**:
```php
add_filter( 'authorkit_review_html', function( $html, $review, $book_id ) {
    // Modify review card HTML
    return $html;
}, 10, 3 );
```

## Template Override System

Override default review templates by copying them to your theme:

**Default Template Location**:
```
/wp-content/plugins/authorkit/modules/reviews/templates/
```

**Theme Override Location**:
```
/wp-content/themes/your-theme/authorkit/reviews/
```

**Available Templates**:
- `reviews-section.php` - Main review section wrapper
- `review-card.php` - Individual review display
- `review-form.php` - Submission form
- `rating-summary.php` - Average rating display
- `rating-stars.php` - Star display component

Copy any template to your theme's override location and modify as needed.

## Custom Review Types

Register custom review metadata:

```php
add_action( 'authorkit_reviews_init', function() {
    authorkit_register_review_meta( 'purchase_source', array(
        'type' => 'string',
        'default' => '',
        'sanitize_callback' => 'sanitize_text_field'
    ) );
} );
```

Access custom metadata:
```php
$source = authorkit_get_review_meta( $review_id, 'purchase_source' );
authorkit_update_review_meta( $review_id, 'purchase_source', 'Amazon' );
```

## Schema Markup Customization

Modify structured data for SEO:

```php
add_filter( 'authorkit_review_schema', function( $schema, $review, $book_id ) {
    // Add custom schema properties
    $schema['customProperty'] = 'value';
    return $schema;
}, 10, 3 );
```

## JavaScript Events

Listen for frontend events:

```javascript
// Review submitted successfully
document.addEventListener('authorkit.review.submitted', function(e) {
    console.log('Review submitted:', e.detail.reviewData);
});

// Review form validation failed
document.addEventListener('authorkit.review.validation_failed', function(e) {
    console.log('Validation errors:', e.detail.errors);
});

// Star rating changed
document.addEventListener('authorkit.rating.changed', function(e) {
    console.log('New rating:', e.detail.rating);
});
```

## Database Schema

Review data is stored in a custom table `{$wpdb->prefix}authorkit_reviews`:

**Table Structure**:
- `id` - Primary key
- `book_id` - Foreign key to posts table
- `reviewer_name` - Reviewer's display name
- `reviewer_email` - Reviewer's email (not publicly displayed)
- `rating` - Integer 1-5
- `review_text` - The written review
- `status` - pending|approved|rejected
- `verified` - Boolean for verified purchase
- `created_at` - Submission timestamp
- `updated_at` - Last modification timestamp

Query directly if needed:
```php
global $wpdb;
$table = $wpdb->prefix . 'authorkit_reviews';
$results = $wpdb->get_results( "SELECT * FROM {$table} WHERE book_id = 123" );
```

## Best Practices

**Performance**: Use `authorkit_get_reviews()` with appropriate limits rather than querying all reviews at once.

**Caching**: Review counts and averages are cached. Clear cache after programmatic updates:
```php
authorkit_clear_review_cache( $book_id );
```

**Security**: Always sanitize and validate data when using hooks. The module sanitizes input, but custom code should follow WordPress security standards.

**Compatibility**: Test customizations with updates, as internal APIs may change between versions.

---

**Navigation:**
- Previous: [Settings](settings.md)
- [Overview](overview.md)
- [Review Management](review-management.md)

**Last Updated:** March 7, 2026
