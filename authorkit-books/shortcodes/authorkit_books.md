# [authorkit_books]

## Display Multiple Books

The `[authorkit_books]` shortcode displays multiple books in a grid or list layout. It's the most versatile shortcode, offering extensive filtering, sorting, and display options for creating book catalogs, featured collections, and curated lists.

## Basic Usage

```
[authorkit_books]
```

Without parameters, displays your 10 most recently published books in a 3-column grid.

## Parameters

### Filtering Parameters

**limit**
- Maximum number of books to display
- Type: Integer
- Default: 10
- Use `-1` for unlimited (caution: may slow page load)
- Example: `limit="6"`

**category**
- Filter books by category slug
- Type: String (category slug)
- Multiple categories: separate with commas
- Example: `category="fantasy"`
- Example: `category="fantasy,sci-fi"`

**series**
- Filter books by series slug
- Type: String (series slug)
- Example: `series="harry-potter"`

**status**
- Filter by publication status
- Options: `published`, `coming-soon`, `draft`
- Default: `published`
- Example: `status="coming-soon"`

**exclude**
- Exclude specific books by ID
- Type: Comma-separated book IDs
- Example: `exclude="12,34,56"`

**include**
- Include only specific books by ID
- Type: Comma-separated book IDs
- Example: `include="12,34,56"`

### Sorting Parameters

**orderby**
- How to sort books
- Options: `date`, `title`, `random`, `menu_order`, `modified`
- Default: `date`
- Example: `orderby="title"`

**order**
- Sort direction
- Options: `ASC` (ascending), `DESC` (descending)
- Default: `DESC`
- Example: `order="ASC"`

### Layout Parameters

**layout**
- Display layout style
- Options: `grid`, `list`
- Default: `grid`
- Example: `layout="list"`

**columns**
- Number of columns (grid layout only)
- Options: 1-6
- Default: 3
- Automatically responsive on mobile
- Example: `columns="4"`

### Display Control Parameters

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
- Limit description to number of words
- Type: Integer
- Default: 55
- Example: `description_length="30"`

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

**show_categories**
- Display book categories/genres
- Type: true/false
- Default: false
- Example: `show_categories="true"`

**show_series**
- Display series information
- Type: true/false
- Default: false
- Example: `show_series="true"`

## Usage Examples

### Latest 6 Books
```
[authorkit_books limit="6"]
```
Perfect for homepage "Recent Releases" section.

### All Fantasy Books Alphabetically
```
[authorkit_books category="fantasy" orderby="title" order="ASC" limit="-1"]
```
Complete fantasy catalog sorted A-Z.

### 4-Column Grid
```
[authorkit_books columns="4" limit="12"]
```
Wider grid layout for large screens.

### List Layout with Full Descriptions
```
[authorkit_books layout="list" limit="5" description_length="150"]
```
Vertical list with longer descriptions.

### Coming Soon Books
```
[authorkit_books status="coming-soon" limit="3"]
```
Showcase upcoming releases.

### Random Book Recommendations
```
[authorkit_books orderby="random" limit="3" show_meta="false"]
```
Display 3 random books, changes on each page load.

### Multiple Genres
```
[authorkit_books category="fantasy,sci-fi,mystery" limit="12"]
```
Show books from multiple categories.

### Compact Book Grid (No Descriptions)
```
[authorkit_books limit="9" show_description="false" columns="3"]
```
Cover images and titles only.

### Featured Books Only
```
[authorkit_books include="45,67,89,123" orderby="menu_order"]
```
Display specific books in custom order.

### Exclude Specific Books
```
[authorkit_books category="romance" exclude="12,34" limit="10"]
```
Show romance books except certain titles.

## HTML Output

Grid layout generates:

```html
<div class="authorkit-books-grid authorkit-columns-3">
    <div class="authorkit-book-card" data-book-id="123">
        <div class="authorkit-book-cover">
            <img src="cover.jpg" alt="Book Title" />
        </div>
        <h3 class="authorkit-book-title">Book Title</h3>
        <p class="authorkit-book-description">...</p>
        <div class="authorkit-book-meta">...</div>
        <div class="authorkit-book-buy-links">...</div>
    </div>
    <!-- More book cards... -->
</div>
```

List layout generates:

```html
<div class="authorkit-books-list">
    <div class="authorkit-book-list-item" data-book-id="123">
        <!-- Book content -->
    </div>
    <!-- More list items... -->
</div>
```

## Styling

### Grid Layout Customization

```css
/* Adjust grid spacing */
.authorkit-books-grid {
    gap: 30px;
}

/* Customize book cards */
.authorkit-book-card {
    border: 1px solid #ddd;
    padding: 20px;
    background: white;
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

/* Hover effects */
.authorkit-book-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 4px 8px rgba(0,0,0,0.2);
    transition: all 0.3s ease;
}
```

### List Layout Customization

```css
/* List item spacing */
.authorkit-book-list-item {
    margin-bottom: 40px;
    padding-bottom: 40px;
    border-bottom: 2px solid #eee;
}

/* Alternate row colors */
.authorkit-book-list-item:nth-child(even) {
    background: #f9f9f9;
}
```

## Common Use Cases

### Complete Book Catalog Page
```
[authorkit_books limit="-1" orderby="title" order="ASC"]
```

### Homepage "Latest Releases"
```
[authorkit_books limit="3" show_meta="false"]
```

### Genre Landing Pages
```
[authorkit_books category="romance" limit="20" columns="4"]
```

### "You Might Also Like" Recommendations
```
[authorkit_books orderby="random" limit="4" show_description="false"]
```

### Bestsellers Showcase
```
[authorkit_books include="12,45,67,89" orderby="menu_order"]
```

### Pre-Order Campaign Page
```
[authorkit_books status="coming-soon" layout="list"]
```

## Pagination

For large book collections, consider breaking into multiple pages:

**Page 1:**
```
[authorkit_books limit="12" orderby="date"]
```

**Page 2:**
```
[authorkit_books limit="12" offset="12" orderby="date"]
```

Note: The `offset` parameter skips the first N books.

## Performance Considerations

**Limit Book Count:** Displaying 50+ books on one page can slow load times. Use reasonable limits or implement pagination.

**Optimize Images:** Ensure book covers are optimized for web (compressed, appropriate dimensions).

**Use Caching:** Install a caching plugin to store shortcode output and reduce database queries.

**Minimize Descriptions:** Use `description_length` to limit text and reduce page weight.

## Troubleshooting

**No books display:**
- Verify you have published books
- Check category/series slugs are correct (case-sensitive)
- Ensure `status="published"` or remove status parameter

**Wrong books appear:**
- Double-check category/series slug spelling
- Verify filter parameters aren't too restrictive
- Check if books are actually published, not drafts

**Layout breaks on mobile:**
- AuthorKit is responsive by default
- Check for theme CSS conflicts
- Try reducing column count for smaller screens

**Slow page load:**
- Reduce `limit` value
- Use `show_description="false"` to reduce content
- Optimize book cover images
- Enable caching plugin

---

**Related Documentation:**
- [Shortcodes Overview](/shortcodes/overview.md)
- [Book Categories](/taxonomies/book-categories.md)
- [Book Series](/taxonomies/book-series.md)
- [Styling Your Books](/displaying-books/styling-your-books.md)

---

*Last Updated: March 7, 2026*
