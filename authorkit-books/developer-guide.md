# Developer Guide

## Introduction

This guide covers hooks, filters, and functions available for developers who want to extend or customize the AuthorKit Books module. All examples assume basic knowledge of WordPress development and PHP.

## Custom Post Type

Books are registered as a custom post type with the slug `authorkit_book`.

### Post Type Registration

```php
// Access the post type object
$book_post_type = get_post_type_object('authorkit_book');
```

## Hooks & Actions

### Book Save Actions

**authorkit_books_save_post**
Fires after a book is saved, before metadata is updated.

```php
add_action('authorkit_books_save_post', function($post_id, $post, $update) {
    // Custom logic after book save
    error_log("Book {$post_id} was saved");
}, 10, 3);
```

**authorkit_books_after_save_meta**
Fires after all book metadata has been saved.

```php
add_action('authorkit_books_after_save_meta', function($post_id, $meta_data) {
    // Custom logic after metadata save
    // $meta_data contains all saved book fields
}, 10, 2);
```

### Display Actions

**authorkit_books_before_single_book**
Fires before single book content is rendered.

```php
add_action('authorkit_books_before_single_book', function($book_id) {
    echo '<div class="custom-book-header">Featured Book</div>';
});
```

**authorkit_books_after_single_book**
Fires after single book content is rendered.

```php
add_action('authorkit_books_after_single_book', function($book_id) {
    echo '<div class="custom-cta">Buy Now</div>';
});
```

## Filters

### Metadata Filters

**authorkit_books_meta_fields**
Filter the array of registered meta fields.

```php
add_filter('authorkit_books_meta_fields', function($fields) {
    $fields['custom_field'] = array(
        'label' => 'Custom Field',
        'type' => 'text',
        'sanitize_callback' => 'sanitize_text_field'
    );
    return $fields;
});
```

**authorkit_books_get_meta**
Filter book metadata before it's returned.

```php
add_filter('authorkit_books_get_meta', function($meta_value, $post_id, $meta_key) {
    // Modify meta value before returning
    if ($meta_key === 'book_price') {
        return '$' . number_format($meta_value, 2);
    }
    return $meta_value;
}, 10, 3);
```

### Display Filters

**authorkit_books_single_template**
Filter the template path for single book display.

```php
add_filter('authorkit_books_single_template', function($template, $book_id) {
    // Use custom template for specific books
    if (has_term('fantasy', 'book_category', $book_id)) {
        return get_stylesheet_directory() . '/templates/fantasy-book.php';
    }
    return $template;
}, 10, 2);
```

**authorkit_books_archive_template**
Filter the template path for book archive display.

```php
add_filter('authorkit_books_archive_template', function($template) {
    return get_stylesheet_directory() . '/templates/books-grid.php';
});
```

**authorkit_books_shortcode_output**
Filter shortcode HTML output before rendering.

```php
add_filter('authorkit_books_shortcode_output', function($output, $atts, $shortcode) {
    // Wrap shortcode output in custom container
    return '<div class="custom-books-wrapper">' . $output . '</div>';
}, 10, 3);
```

### Query Filters

**authorkit_books_query_args**
Filter WP_Query arguments for book queries.

```php
add_filter('authorkit_books_query_args', function($args, $context) {
    // Modify default query arguments
    if ($context === 'shortcode') {
        $args['posts_per_page'] = 20;
    }
    return $args;
}, 10, 2);
```

## Helper Functions

### Get Book Meta

```php
/**
 * Get book metadata
 * @param int $book_id Book post ID
 * @param string $meta_key Meta field key
 * @return mixed Meta value
 */
$isbn = authorkit_books_get_meta($book_id, 'book_isbn');
$title = authorkit_books_get_meta($book_id, 'book_title');
```

### Update Book Meta

```php
/**
 * Update book metadata
 * @param int $book_id Book post ID
 * @param string $meta_key Meta field key
 * @param mixed $meta_value Meta value
 */
authorkit_books_update_meta($book_id, 'book_price', 9.99);
```

### Get Books

```php
/**
 * Query books with custom parameters
 * @param array $args WP_Query arguments
 * @return WP_Query
 */
$books = authorkit_books_get_books(array(
    'posts_per_page' => 10,
    'tax_query' => array(
        array(
            'taxonomy' => 'book_category',
            'field' => 'slug',
            'terms' => 'fantasy'
        )
    )
));

if ($books->have_posts()) {
    while ($books->have_posts()) {
        $books->the_post();
        // Display book
    }
    wp_reset_postdata();
}
```

### Check Book Status

```php
/**
 * Check if book is published
 * @param int $book_id Book post ID
 * @return bool
 */
if (authorkit_books_is_published($book_id)) {
    // Book is published
}

/**
 * Check if book is coming soon
 * @param int $book_id Book post ID
 * @return bool
 */
if (authorkit_books_is_coming_soon($book_id)) {
    // Book is coming soon
}
```

## Custom Templates

### Override Book Templates

Create custom templates in your theme:

1. Copy template from plugin: `authorkit/templates/books/single-book.php`
2. Place in theme: `your-theme/authorkit/books/single-book.php`
3. Customize as needed

Available templates:
- `single-book.php` - Single book display
- `archive-books.php` - Book archive/grid
- `book-card.php` - Individual book card component

### Template Tags

Use these functions in custom templates:

```php
// Display book cover
authorkit_books_the_cover($book_id, 'large');

// Display book title
authorkit_books_the_title($book_id);

// Display book meta field
authorkit_books_the_meta($book_id, 'book_isbn');

// Display retailer links
authorkit_books_the_buy_links($book_id);

// Display series information
authorkit_books_the_series($book_id);
```

## REST API

Books are accessible via WordPress REST API:

**Endpoint**: `/wp-json/wp/v2/authorkit_book`

### Get All Books
```
GET /wp-json/wp/v2/authorkit_book
```

### Get Single Book
```
GET /wp-json/wp/v2/authorkit_book/{id}
```

### Custom Fields in API

Register book meta fields to REST API:

```php
register_rest_field('authorkit_book', 'book_isbn', array(
    'get_callback' => function($post) {
        return authorkit_books_get_meta($post['id'], 'book_isbn');
    },
    'schema' => array(
        'type' => 'string',
        'description' => 'Book ISBN'
    )
));
```

## Schema Customization

**authorkit_books_schema_data**
Filter schema.org markup data.

```php
add_filter('authorkit_books_schema_data', function($schema, $book_id) {
    // Add custom schema properties
    $schema['awards'] = authorkit_books_get_meta($book_id, 'book_awards');
    return $schema;
}, 10, 2);
```

---

**Related Documentation:**
- [Book Meta Fields](/managing-books/book-meta-fields.md)
- [Shortcodes Overview](/shortcodes/overview.md)
- [Styling Your Books](/displaying-books/styling-your-books.md)

---

*Last Updated: March 7, 2026*
