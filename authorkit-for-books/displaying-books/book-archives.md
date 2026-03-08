# Book Archives

## Overview

WordPress automatically creates archive pages that display all your books in grid or list layouts. These archives provide browseable catalogs of your complete library and can be filtered by category, series, or age range.

## Archive Types

### Main Books Archive
URL: `yoursite.com/books/`

Shows all published books, typically in reverse chronological order (newest first).

### Category Archives
URL: `yoursite.com/book-category/fantasy/`

Shows books from a specific category (genre).

### Series Archives
URL: `yoursite.com/book-series/harry-potter/`

Shows all books in a series, ordered by series position.

### Age Range Archives
URL: `yoursite.com/age-range/young-adult/`

Shows books tagged with specific age ranges.

## Default Archive Display

Archives automatically include:

### Archive Title
Page heading indicating the archive type and name.

Example: "Fantasy Books" or "Harry Potter Series"

### Archive Description
Category or series description if provided in taxonomy settings.

### Book Grid
Responsive grid of book cards, each showing:
- Book cover thumbnail
- Title and author
- Brief description (excerpt)
- Purchase link or "Read More" button

### Pagination
Navigation to view more books if catalog exceeds per-page limit.

## Configuring Archives

### Posts Per Page

Set how many books display per archive page:

1. Go to Settings > Reading
2. Find "Blog pages show at most"
3. Set number (default: 10)
4. Save Changes

This affects all archives globally.

### Sort Order

Default sort is by publication date (newest first). Customize using:

- Custom shortcodes with orderby parameter
- Theme customization
- Developer filters

[See developer guide](/developer-guide.md)

## Creating Archive Navigation

### Main Menu Links

Add archive links to your site navigation:

1. Go to Appearance > Menus
2. Click "Books" or create "Custom Links"
3. Add these URLs:
   - `/books/` - All books
   - `/book-category/fantasy/` - Fantasy books
   - `/book-series/your-series/` - Series archive

### Archive Widget

Use WordPress Archive widget to list archives by month/year.

### Category List

Create category browsing page:

1. Create new page "Browse by Genre"
2. Add links to each category archive manually or using shortcodes

### Series List

List all series with links to each series archive.

## Customizing Archive Appearance

### WordPress Customizer

Some themes support archive customization via Appearance > Customize.

### Custom CSS

Add styling to override defaults:

```css
.authorkit-books-archive {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 30px;
}
```

[See styling guide](/displaying-books/styling-your-books.md)

### Template Override

Copy archive template to your theme for full control:

1. Copy `authorkit/templates/books/archive-books.php`
2. Place in `your-theme/authorkit/books/archive-books.php`
3. Customize HTML/PHP as needed

## Using Shortcodes Instead

For more control, use shortcodes instead of automatic archives:

### Replace Main Archive

Create a page with URL `/books/`:
```
[authorkit_books]
```

### Replace Category Archives

Create pages for each genre:
```
[authorkit_books_by_category category="fantasy"]
```

### Replace Series Archives

Create pages for each series:
```
[authorkit_books_by_series series="trilogy-name"]
```

This provides full control over layout, filtering, and sorting.

## SEO for Archives

### Archive Titles
WordPress generates SEO-friendly titles automatically.

### Archive Descriptions
Add descriptions in Books > Categories or Books > Series. These appear:
- At top of archive pages
- In meta description tags
- In schema markup

### Canonical URLs
Archives use canonical tags to prevent duplicate content issues.

### Pagination
Proper rel="next" and rel="prev" tags for multi-page archives.

## Common Issues

**Empty archives:**
- Verify books are Published not Draft
- Check books assigned to correct categories/series
- Ensure at least one book exists

**404 errors:**
- Re-save permalinks: Settings > Permalinks > Save
- Check .htaccess file permissions
- Verify books post type is registered

**Wrong sorting:**
- Check Settings > Reading for posts per page
- Use custom shortcodes for custom sorting
- Contact theme support for theme-specific sorting

**Layout broken:**
- Test with default WordPress theme
- Check for CSS conflicts
- Review responsive styling on mobile devices

---

**Related Documentation:**
- [Single Book Pages](/displaying-books/single-book-pages.md)
- [Shortcodes Overview](/shortcodes/overview.md)
- [Book Categories](/taxonomies/book-categories.md)
- [Book Series](/taxonomies/book-series.md)

---

*Last Updated: March 7, 2026*
