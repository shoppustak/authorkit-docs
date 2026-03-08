# Developer Reference

Extend AuthorKit with custom code using hooks, filters, and APIs. This reference covers the most commonly used developer features.

## Action Hooks

### Core Hooks

```php
// After AuthorKit Core initializes
do_action( 'authorkit_init' );

// Before module loads
do_action( 'authorkit_before_module_load', $module_name );

// After module loads
do_action( 'authorkit_after_module_load', $module_name );

// Before settings save
do_action( 'authorkit_before_settings_save', $settings );

// After settings save
do_action( 'authorkit_after_settings_save', $settings );
```

### Book Hooks

```php
// After book published
do_action( 'authorkit_book_published', $post_id );

// Before book deleted
do_action( 'authorkit_before_book_delete', $post_id );

// After book meta saved
do_action( 'authorkit_book_meta_saved', $post_id, $meta_data );

// Before bookshelf sync
do_action( 'authorkit_before_bookshelf_sync', $post_id, $book_data );

// After bookshelf sync
do_action( 'authorkit_after_bookshelf_sync', $post_id, $response );
```

### Review Hooks

```php
// After review submitted
do_action( 'authorkit_review_submitted', $review_id, $book_id );

// Review status changed
do_action( 'authorkit_review_status_changed', $review_id, $old_status, $new_status );

// Review approved
do_action( 'authorkit_review_approved', $review_id );

// Review rejected
do_action( 'authorkit_review_rejected', $review_id );
```

## Filter Hooks

### Core Filters

```php
// Modify plugin capabilities
$caps = apply_filters( 'authorkit_capabilities', $caps, $tier );

// Modify cache duration (in seconds)
$duration = apply_filters( 'authorkit_cache_duration', 43200 );

// Modify API endpoints
$endpoints = apply_filters( 'authorkit_api_endpoints', $endpoints );

// Modify template path
$path = apply_filters( 'authorkit_template_path', $path, $template_name );
```

### Book Filters

```php
// Modify book query args
$args = apply_filters( 'authorkit_book_query_args', $args );

// Modify book data before save
$data = apply_filters( 'authorkit_book_data', $data, $post_id );

// Modify book permalink
$permalink = apply_filters( 'authorkit_book_permalink', $permalink, $post_id );

// Modify book meta fields
$fields = apply_filters( 'authorkit_book_meta_fields', $fields );

// Modify buy links
$links = apply_filters( 'authorkit_buy_links', $links, $post_id );
```

### Review Filters

```php
// Modify review query args
$args = apply_filters( 'authorkit_review_query_args', $args, $book_id );

// Modify review data before save
$data = apply_filters( 'authorkit_review_data', $data, $review_id );

// Modify rating calculation
$rating = apply_filters( 'authorkit_average_rating', $rating, $book_id );

// Modify review display HTML
$html = apply_filters( 'authorkit_review_html', $html, $review_id );
```

## Helper Functions

### Book Functions

```php
// Get book by ID
$book = authorkit_get_book( $post_id );

// Get all books
$books = authorkit_get_books( $args = [] );

// Get book meta
$value = authorkit_get_book_meta( $post_id, $meta_key, $single = true );

// Update book meta
authorkit_update_book_meta( $post_id, $meta_key, $value );

// Get book buy links
$links = authorkit_get_buy_links( $post_id );

// Check if book is published
$is_published = authorkit_is_book_published( $post_id );

// Get book cover URL
$url = authorkit_get_book_cover( $post_id, $size = 'medium' );
```

### Review Functions

```php
// Get reviews for book
$reviews = authorkit_get_reviews( $book_id, $args = [] );

// Get review count
$count = authorkit_get_review_count( $book_id );

// Get average rating
$rating = authorkit_get_average_rating( $book_id );

// Submit review
$review_id = authorkit_submit_review( $data );

// Approve review
authorkit_approve_review( $review_id );

// Reject review
authorkit_reject_review( $review_id );
```

### License Functions

```php
// Get current tier
$tier = authorkit_get_tier(); // 'free' or 'pro'

// Check if Pro
if ( authorkit_is_pro() ) {
    // Pro-only code
}

// Check capability
if ( authorkit_can( 'unlimited_books' ) ) {
    // User has this capability
}

// Get license status
$status = authorkit_get_license_status();
```

## REST API

### Authentication

```php
// Add API key to request headers
$args = [
    'headers' => [
        'X-AuthorKit-Key' => 'your-api-key'
    ]
];
```

### Endpoints

**List Books:**
```
GET /wp-json/authorkit/v1/books
```

**Get Single Book:**
```
GET /wp-json/authorkit/v1/book/{id}
```

**List Reviews:**
```
GET /wp-json/authorkit/v1/reviews?book_id={id}
```

**Get Stats:**
```
GET /wp-json/authorkit/v1/stats
```

### Example Request

```php
$response = wp_remote_get( 'https://yoursite.com/wp-json/authorkit/v1/books' );
$books = json_decode( wp_remote_retrieve_body( $response ) );
```

## Custom Templates

### Template Hierarchy

AuthorKit searches for templates in this order:

1. `wp-content/themes/your-theme/authorkit/template-name.php`
2. `wp-content/themes/your-theme/template-name.php`
3. `wp-content/plugins/authorkit/templates/template-name.php`

### Available Templates

**Books:**
- `single-book.php` - Single book display
- `archive-book.php` - Book archive/list
- `book-card.php` - Book grid item
- `book-meta.php` - Book meta information

**Reviews:**
- `review-form.php` - Review submission form
- `review-list.php` - Reviews list
- `review-single.php` - Single review display

### Template Override Example

```php
// In your theme: authorkit/single-book.php
<?php
// Get book data
$book_id = get_the_ID();
$title = get_the_title();
$cover = authorkit_get_book_cover( $book_id );
$rating = authorkit_get_average_rating( $book_id );
?>

<div class="my-custom-book-layout">
    <img src="<?php echo esc_url( $cover ); ?>" alt="<?php echo esc_attr( $title ); ?>">
    <h1><?php echo esc_html( $title ); ?></h1>
    <div class="rating"><?php echo esc_html( $rating ); ?> stars</div>
    <?php the_content(); ?>
</div>
```

## WP-CLI Commands

### Cache Management

```bash
# Clear all AuthorKit caches
wp authorkit cache clear

# Clear specific cache
wp authorkit cache clear --type=books

# Get cache statistics
wp authorkit cache stats
```

### Database Commands

```bash
# Optimize database
wp authorkit optimize-database

# Count books
wp authorkit count books

# Count reviews
wp authorkit count reviews
```

### License Commands

```bash
# Activate license
wp authorkit license activate AK-XXXX-XXXX-XXXX

# Deactivate license
wp authorkit license deactivate

# Check license status
wp authorkit license status
```

## Code Examples

### Add Custom Book Meta Field

```php
// Add custom field
add_filter( 'authorkit_book_meta_fields', 'my_custom_book_field' );
function my_custom_book_field( $fields ) {
    $fields['custom_field'] = [
        'label' => 'Custom Field',
        'type'  => 'text',
        'desc'  => 'My custom field description'
    ];
    return $fields;
}
```

### Modify Book Query

```php
// Show only published books
add_filter( 'authorkit_book_query_args', 'my_published_books_only' );
function my_published_books_only( $args ) {
    $args['meta_query'][] = [
        'key'   => '_authorkit_status',
        'value' => 'published'
    ];
    return $args;
}
```

### Send Email on Review Submission

```php
// Email notification on review
add_action( 'authorkit_review_submitted', 'my_review_notification', 10, 2 );
function my_review_notification( $review_id, $book_id ) {
    $book_title = get_the_title( $book_id );
    $reviewer = get_post_meta( $review_id, '_authorkit_reviewer_name', true );

    wp_mail(
        get_option( 'admin_email' ),
        'New Review for ' . $book_title,
        'New review by ' . $reviewer
    );
}
```

### Custom Buy Button

```php
// Add custom buy link
add_filter( 'authorkit_buy_links', 'my_custom_buy_link', 10, 2 );
function my_custom_buy_link( $links, $post_id ) {
    $links['custom_store'] = [
        'label' => 'Buy from My Store',
        'url'   => 'https://mystore.com/book/' . get_post_field( 'post_name', $post_id ),
        'icon'  => 'dashicons-cart'
    ];
    return $links;
}
```

### Conditional Pro Features

```php
// Show Pro-only content
if ( authorkit_is_pro() ) {
    echo '<div class="pro-feature">This is a Pro feature</div>';
} else {
    echo '<a href="https://authorkit.pro">Upgrade to Pro</a>';
}
```

## Debugging

### Enable Debug Mode

```php
// In wp-config.php
define( 'AUTHORKIT_DEBUG', true );
```

### Debug Log Location

```
/wp-content/debug.log
```

### Common Debug Checks

```php
// Check if module loaded
if ( function_exists( 'authorkit_get_books' ) ) {
    // Books module is active
}

// Check tier
$tier = authorkit_get_tier();
error_log( 'Current tier: ' . $tier );

// Check capabilities
$can_unlimited = authorkit_can( 'unlimited_books' );
error_log( 'Can unlimited books: ' . ( $can_unlimited ? 'yes' : 'no' ) );
```

## Performance Best Practices

### Use Caching

```php
// Cache expensive queries
$cache_key = 'my_custom_book_query';
$books = get_transient( $cache_key );

if ( false === $books ) {
    $books = authorkit_get_books( $args );
    set_transient( $cache_key, $books, 12 * HOUR_IN_SECONDS );
}
```

### Conditional Loading

```php
// Only load on book pages
if ( is_singular( 'authorkit_book' ) ) {
    wp_enqueue_script( 'my-book-script' );
}
```

### Optimize Queries

```php
// Use specific fields
$args = [
    'posts_per_page' => 10,
    'fields' => 'ids', // Only get IDs
    'no_found_rows' => true, // Skip pagination count
];
```

## Security Best Practices

### Sanitize Input

```php
// Sanitize text
$safe_text = sanitize_text_field( $_POST['field'] );

// Sanitize email
$safe_email = sanitize_email( $_POST['email'] );

// Sanitize URL
$safe_url = esc_url_raw( $_POST['url'] );
```

### Escape Output

```php
// Escape HTML
echo esc_html( $user_input );

// Escape attributes
echo '<div data-id="' . esc_attr( $id ) . '">';

// Escape URLs
echo '<a href="' . esc_url( $url ) . '">';
```

### Verify Nonces

```php
// Create nonce
wp_nonce_field( 'my_action', 'my_nonce' );

// Verify nonce
if ( ! wp_verify_nonce( $_POST['my_nonce'], 'my_action' ) ) {
    wp_die( 'Security check failed' );
}
```

### Check Capabilities

```php
// Check user can edit books
if ( ! current_user_can( 'edit_authorkit_books' ) ) {
    wp_die( 'Insufficient permissions' );
}
```

## Support

**Documentation:** [docs.authorkit.pro](https://docs.authorkit.pro)
**Community:** [WordPress.org Forums](https://wordpress.org/support/plugin/authorkit/)
**Pro Support:** support@authorkit.pro
**GitHub:** [github.com/shoppustak/authorkit](https://github.com/shoppustak/authorkit)

---

**Last Updated:** March 7, 2026
**Applies to:** AuthorKit Core 1.0.0+
