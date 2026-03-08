# [authorkit_books_by_series]

## Display Books in a Series

The `[authorkit_books_by_series]` shortcode displays all books from a specific series, automatically ordered by series position. Essential for creating series landing pages and showing readers the correct reading order for multi-book series.

## Basic Usage

```
[authorkit_books_by_series series="harry-potter"]
```

Replace `harry-potter` with your series slug to display all books in proper series order.

## Finding Series Slugs

1. Go to **Books > Series** in WordPress admin
2. Hover over a series name
3. Look at the browser's status bar (bottom-left)
4. The URL shows the slug: `taxonomy=book_series&tag_ID=123&term_slug=harry-potter`
5. The slug is lowercase with hyphens (example: `lord-of-the-rings`, `hunger-games`)

## Parameters

### Required Parameters

**series** (required)
- The series slug to display books from
- Type: String
- Example: `series="lord-of-the-rings"`
- Example: `series="discworld"`

### Sorting Parameters

**orderby**
- How to sort books
- Options: `series_order`, `date`, `title`, `menu_order`
- Default: `series_order` (respects series position metadata)
- Example: `orderby="series_order"`

**order**
- Sort direction
- Options: `ASC`, `DESC`
- Default: `ASC` (Book 1, 2, 3...)
- Example: `order="DESC"`

### Layout Parameters

**layout**
- Display layout
- Options: `grid`, `list`
- Default: `grid`
- Example: `layout="list"`

**columns**
- Number of columns (grid layout)
- Options: 1-6
- Default: 3
- Example: `columns="4"`

### Display Control Parameters

**show_series_description**
- Display series description at top
- Type: true/false
- Default: true
- Example: `show_series_description="false"`

**show_series_name**
- Display series name as heading
- Type: true/false
- Default: true
- Example: `show_series_name="false"`

**show_order_numbers**
- Display book numbers (Book 1, Book 2, etc.)
- Type: true/false
- Default: true
- Example: `show_order_numbers="false"`

**show_cover**
- Display book cover images
- Type: true/false
- Default: true
- Example: `show_cover="false"`

**show_description**
- Display book descriptions
- Type: true/false
- Default: true
- Example: `show_description="false"`

**description_length**
- Limit description word count
- Type: Integer
- Default: 55
- Example: `description_length="40"`

**show_meta**
- Display book metadata
- Type: true/false
- Default: true
- Example: `show_meta="false"`

**show_buy_links**
- Display retailer links
- Type: true/false
- Default: true
- Example: `show_buy_links="false"`

**limit**
- Maximum books to display
- Type: Integer
- Default: -1 (all books in series)
- Example: `limit="3"` (show first 3 books only)

## Usage Examples

### Complete Series Display
```
[authorkit_books_by_series series="lord-of-the-rings"]
```
All books in reading order with series numbers.

### Trilogy List Layout
```
[authorkit_books_by_series series="hunger-games" layout="list"]
```
Vertical list showing all 3 books.

### Series without Numbers
```
[authorkit_books_by_series series="discworld" show_order_numbers="false"]
```
Don't show "Book 1", "Book 2" labels.

### Compact Series Grid
```
[authorkit_books_by_series series="wheel-of-time" show_description="false" columns="4"]
```
4-column grid, covers and titles only.

### First Three Books Only
```
[authorkit_books_by_series series="game-of-thrones" limit="3"]
```
Show first 3 books in the series.

### Series Page without Header
```
[authorkit_books_by_series series="chronicles-of-narnia" show_series_name="false" show_series_description="false"]
```
Just the books, no series header.

### Reverse Order (Latest First)
```
[authorkit_books_by_series series="jack-reacher" order="DESC"]
```
Show newest book first (Book 25, 24, 23...).

## HTML Output

```html
<div class="authorkit-books-by-series" data-series="lord-of-the-rings">
    <div class="authorkit-series-header">
        <h2 class="authorkit-series-name">The Lord of the Rings</h2>
        <p class="authorkit-series-description">An epic fantasy trilogy...</p>
    </div>

    <div class="authorkit-books-grid authorkit-columns-3">
        <div class="authorkit-book-card authorkit-series-book" data-book-id="123" data-series-order="1">
            <span class="authorkit-book-number">Book 1</span>
            <div class="authorkit-book-cover">
                <img src="fellowship.jpg" alt="The Fellowship of the Ring" />
            </div>
            <h3 class="authorkit-book-title">The Fellowship of the Ring</h3>
            <!-- More book content -->
        </div>
        <!-- More books... -->
    </div>
</div>
```

## Styling

### Series Header

```css
/* Series header styling */
.authorkit-series-header {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    padding: 40px;
    text-align: center;
    margin-bottom: 40px;
    border-radius: 8px;
}

.authorkit-series-name {
    font-size: 36px;
    margin-bottom: 10px;
}

.authorkit-series-description {
    font-size: 18px;
    opacity: 0.9;
}
```

### Book Numbers

```css
/* Book number badges */
.authorkit-book-number {
    position: absolute;
    top: 10px;
    left: 10px;
    background: #0073aa;
    color: white;
    padding: 5px 10px;
    border-radius: 4px;
    font-weight: bold;
    font-size: 14px;
    z-index: 10;
}

/* Highlight first book */
.authorkit-series-book[data-series-order="1"] .authorkit-book-number {
    background: #d4af37;
}
```

### Series-Specific Styling

```css
/* Custom styling per series */
.authorkit-books-by-series[data-series="harry-potter"] {
    --series-color: #740001;
}

.authorkit-books-by-series[data-series="lord-of-the-rings"] {
    --series-color: #228b22;
}

.authorkit-book-card {
    border-left: 4px solid var(--series-color, #0073aa);
}
```

## Setting Series Order

To ensure books display in correct reading order:

1. Edit a book in WordPress admin
2. Find the **Series** meta box
3. Select the series from dropdown
4. Enter the **Series Order** number (1, 2, 3, etc.)
5. Save the book

The shortcode automatically sorts by this series order field.

## Adding Series Descriptions

Series descriptions appear above the book grid:

1. Go to **Books > Series** in WordPress admin
2. Click on a series
3. Fill in the **Description** field
4. Save changes

Example description:
```
Follow Frodo Baggins and the Fellowship as they journey across Middle-earth
to destroy the One Ring. This epic trilogy defined modern fantasy literature.
```

## Common Use Cases

### Dedicated Series Landing Pages

Create a page for each major series:

```
# The Hunger Games Trilogy

[authorkit_books_by_series series="hunger-games" layout="list"]

Follow Katniss Everdeen's journey from the arena to revolution.
```

### Series Widget in Sidebar

```
[authorkit_books_by_series series="current-series" limit="3" show_description="false" columns="1"]
```

### Author's Complete Works by Series

Create a page showing all series:

```
## Harry Potter Series
[authorkit_books_by_series series="harry-potter" show_series_description="false"]

## Cormoran Strike Series
[authorkit_books_by_series series="cormoran-strike" show_series_description="false"]
```

### "Start Here" Reading Guide

```
New to my books? Start with these series:

[authorkit_books_by_series series="standalone-trilogy" limit="3" show_order_numbers="true"]
```

## Standalone Books

For standalone books not in a series, you can create a "Standalone Books" series or use:

```
[authorkit_books series="" limit="10"]
```

This displays books without a series assignment.

## Series Archives

WordPress automatically creates series archive pages:
```
yoursite.com/book-series/harry-potter/
yoursite.com/book-series/lord-of-the-rings/
```

Use this shortcode for more control over series pages.

## Troubleshooting

**Books appear in wrong order:**
- Verify each book has a **Series Order** number in its meta fields
- Check that series order numbers are sequential (1, 2, 3, not 1, 1, 3)
- Ensure `orderby="series_order"` is set (or use default)

**Missing books:**
- Verify all books are assigned to the series in **Books > Series**
- Check books are published, not drafts
- Ensure series slug matches exactly

**Book numbers don't show:**
- Set `show_order_numbers="true"` (or use default)
- Verify books have series order metadata
- Check theme CSS isn't hiding the numbers

**Series description missing:**
- Add description in **Books > Series**
- Ensure `show_series_description="true"`
- Check theme styling isn't hiding it

**Wrong series name displays:**
- Edit series name in **Books > Series**
- WordPress uses the official series name, not the slug
- Clear cache if using a caching plugin

---

**Related Documentation:**
- [Book Series](/taxonomies/book-series.md)
- [Shortcodes Overview](/shortcodes/overview.md)
- [Managing Series](/taxonomies/book-series.md)
- [Book Meta Fields](/managing-books/book-meta-fields.md)

---

*Last Updated: March 7, 2026*
