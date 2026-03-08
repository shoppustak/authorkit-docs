# [authorkit_book]

## Display a Single Book

The `[authorkit_book]` shortcode displays a single book with all its details, cover image, metadata, and purchase links. Perfect for featuring specific books in blog posts, landing pages, or promotional content.

## Basic Usage

```
[authorkit_book id="123"]
```

Replace `123` with your book's post ID. This displays the book with all default settings enabled.

## Finding Your Book ID

1. Go to **Books > All Books** in WordPress admin
2. Hover over the book title you want to display
3. Look at the bottom-left of your browser window
4. The URL will show something like `post.php?post=123&action=edit`
5. The number after `post=` is your book ID

## Parameters

### Required Parameters

**id** (required)
- The WordPress post ID of the book to display
- Type: Integer
- Example: `id="123"`

### Display Control Parameters

**show_cover**
- Display the book cover image
- Type: true/false
- Default: true
- Example: `show_cover="false"`

**show_title**
- Display the book title and subtitle
- Type: true/false
- Default: true
- Example: `show_title="false"`

**show_description**
- Display the full book description
- Type: true/false
- Default: true
- Example: `show_description="false"`

**show_meta**
- Display book metadata (ISBN, pages, publication date, etc.)
- Type: true/false
- Default: true
- Example: `show_meta="false"`

**show_buy_links**
- Display retailer purchase links
- Type: true/false
- Default: true
- Example: `show_buy_links="false"`

**show_series**
- Display series information if book is part of a series
- Type: true/false
- Default: true
- Example: `show_series="false"`

**show_categories**
- Display book genres/categories
- Type: true/false
- Default: true
- Example: `show_categories="false"`

### Layout Parameters

**layout**
- Visual layout style
- Options: `full`, `compact`, `sidebar`
- Default: `full`
- Example: `layout="compact"`

**image_size**
- Book cover image size
- Options: `thumbnail`, `medium`, `large`, `full`
- Default: `large`
- Example: `image_size="medium"`

**alignment**
- Image alignment relative to content
- Options: `left`, `right`, `center`
- Default: `left`
- Example: `alignment="center"`

## Usage Examples

### Full Book Display (Default)
```
[authorkit_book id="123"]
```
Displays everything: cover, title, description, metadata, and buy links.

### Minimal Book Card
```
[authorkit_book id="123" show_description="false" show_meta="false" layout="compact"]
```
Shows just the cover, title, and buy links in a compact format.

### Sidebar Widget Style
```
[authorkit_book id="123" layout="sidebar" image_size="medium" show_description="false"]
```
Compact display suitable for sidebar widgets.

### Cover and Title Only
```
[authorkit_book id="123" show_description="false" show_meta="false" show_buy_links="false"]
```
Displays only the book cover and title.

### Center-Aligned Full Display
```
[authorkit_book id="123" alignment="center"]
```
Centers the book cover with content flowing around it.

### Blog Post Feature
```
[authorkit_book id="123" show_meta="false" show_categories="false" layout="compact"]
```
Great for mentioning a book in blog content without overwhelming the post.

## HTML Output

The shortcode generates semantic HTML with CSS classes for styling:

```html
<div class="authorkit-book-single" data-book-id="123">
    <div class="authorkit-book-cover">
        <img src="cover.jpg" alt="Book Title" />
    </div>
    <div class="authorkit-book-content">
        <h2 class="authorkit-book-title">Book Title</h2>
        <p class="authorkit-book-description">...</p>
        <div class="authorkit-book-meta">...</div>
        <div class="authorkit-book-buy-links">...</div>
    </div>
</div>
```

## Styling

Add custom CSS to override default styles:

```css
/* Custom book card styling */
.authorkit-book-single {
    border: 2px solid #333;
    padding: 20px;
    background: #f9f9f9;
}

/* Customize book title */
.authorkit-book-title {
    color: #0073aa;
    font-size: 24px;
}

/* Style buy links */
.authorkit-book-buy-links a {
    background: #0073aa;
    color: white;
    padding: 10px 20px;
    text-decoration: none;
    display: inline-block;
    margin: 5px;
}
```

## Common Use Cases

### Homepage Book Feature
Place on your homepage to showcase your latest release:
```
[authorkit_book id="456" alignment="center"]
```

### Author Blog Integration
Mention books naturally within blog posts:
```
My new book [authorkit_book id="789" layout="compact" show_meta="false"] is now available!
```

### Dedicated Book Landing Page
Create a full page for a single book:
```
[authorkit_book id="123"]
```

### Email Newsletter
Generate HTML to copy into email campaigns (note: some email clients have limitations):
```
[authorkit_book id="123" layout="compact" show_description="false"]
```

## Troubleshooting

**Shortcode shows as plain text:**
- Ensure you're using square brackets `[ ]`, not other bracket types
- Check that the book ID is correct
- Verify the shortcode is spelled exactly: `authorkit_book`

**Book doesn't display:**
- Confirm the book ID exists and the book is published
- Check if the book was moved to trash
- Verify you have permission to view the book

**Layout looks broken:**
- Check for theme CSS conflicts
- Try different layout options
- Add custom CSS to override theme styles

**Buy links don't appear:**
- Ensure you've added retailer URLs to the book's meta fields
- Check if `show_buy_links="true"` (or remove parameter to use default)
- Verify the links are properly formatted URLs

---

**Related Documentation:**
- [Shortcodes Overview](/shortcodes/overview.md)
- [Book Meta Fields](/managing-books/book-meta-fields.md)
- [Styling Your Books](/displaying-books/styling-your-books.md)
- [Single Book Pages](/displaying-books/single-book-pages.md)

---

*Last Updated: March 7, 2026*
