# Shortcodes Overview

## Complete Shortcode Reference

This page lists all available shortcodes for AuthorKit for Books with their most common use cases and parameter options.

## Single Book Display

### [authorkit_book]

Display a single book with complete details.

**Basic Usage:**
```
[authorkit_book id="123"]
```

**Common Parameters:**
- `id` - Book post ID (required)
- `show_cover` - Display cover image (true/false, default: true)
- `show_description` - Display book description (true/false, default: true)
- `show_meta` - Display book details like ISBN, pages (true/false, default: true)
- `show_buy_links` - Display retailer links (true/false, default: true)

**Example:**
```
[authorkit_book id="123" show_meta="false"]
```

[Full Documentation](/shortcodes/authorkit_book.md)

---

## Multiple Books Display

### [authorkit_books]

Display multiple books in a grid or list layout with flexible filtering and sorting options.

**Basic Usage:**
```
[authorkit_books]
```

**Common Parameters:**
- `limit` - Number of books to show (default: 10)
- `category` - Filter by category slug
- `series` - Filter by series slug
- `orderby` - Sort by: title, date, random, menu_order (default: date)
- `order` - ASC or DESC (default: DESC)
- `layout` - grid or list (default: grid)
- `columns` - Number of columns for grid (default: 3)

**Examples:**
```
[authorkit_books limit="6" orderby="title" order="ASC"]

[authorkit_books category="fantasy" columns="4"]

[authorkit_books layout="list" limit="5"]
```

[Full Documentation](/shortcodes/authorkit_books.md)

---

## Category-Based Display

### [authorkit_books_by_category]

Display all books from a specific category, perfect for genre pages.

**Basic Usage:**
```
[authorkit_books_by_category category="fantasy"]
```

**Common Parameters:**
- `category` - Category slug (required)
- `limit` - Number of books (default: unlimited)
- `orderby` - Sort by: title, date, random (default: date)
- `order` - ASC or DESC (default: DESC)
- `columns` - Grid columns (default: 3)
- `show_category_description` - Show category description (true/false, default: true)

**Examples:**
```
[authorkit_books_by_category category="romance" limit="12"]

[authorkit_books_by_category category="mystery" orderby="title" columns="4"]
```

[Full Documentation](/shortcodes/authorkit_books_by_category.md)

---

## Series-Based Display

### [authorkit_books_by_series]

Display all books in a series, automatically ordered by series position.

**Basic Usage:**
```
[authorkit_books_by_series series="harry-potter"]
```

**Common Parameters:**
- `series` - Series slug (required)
- `orderby` - Sort by: series_order, title, date (default: series_order)
- `order` - ASC or DESC (default: ASC)
- `layout` - grid or list (default: grid)
- `columns` - Grid columns (default: 3)
- `show_series_description` - Show series description (true/false, default: true)
- `show_order_numbers` - Display book numbers (true/false, default: true)

**Examples:**
```
[authorkit_books_by_series series="lord-of-the-rings"]

[authorkit_books_by_series series="discworld" layout="list" show_order_numbers="true"]
```

[Full Documentation](/shortcodes/authorkit_books_by_series.md)

---

## Common Parameters Across All Shortcodes

### Sorting Parameters

**orderby** - Controls how books are sorted:
- `date` - Publication date (newest first)
- `title` - Alphabetical by title
- `random` - Random order (changes on each page load)
- `menu_order` - Manual order set in WordPress
- `series_order` - Order within a series (series shortcodes only)

**order** - Sort direction:
- `DESC` - Descending (Z to A, newest to oldest)
- `ASC` - Ascending (A to Z, oldest to newest)

### Display Parameters

**layout** - Visual layout:
- `grid` - Responsive grid of book cards
- `list` - Vertical list with more details

**columns** - Number of columns (grid layout only):
- Values: 1-6 (default: 3)
- Automatically responsive on mobile devices

**limit** - Maximum number of books to display:
- Any positive integer
- Use `-1` for unlimited (use cautiously)

### Visibility Parameters

**show_cover** - Display book cover images (true/false)
**show_description** - Display book descriptions (true/false)
**show_meta** - Display metadata like ISBN, pages (true/false)
**show_buy_links** - Display retailer purchase links (true/false)

## Finding Category and Series Slugs

### Category Slugs
1. Go to Books > Categories in WordPress admin
2. Click on a category
3. Look at the URL: `tag_ID=123&taxonomy=book_category&post_type=authorkit_book&term_slug=fantasy`
4. The slug is after `term_slug=` (example: `fantasy`)

### Series Slugs
1. Go to Books > Series in WordPress admin
2. Click on a series
3. Look at the URL for the slug
4. The slug is the lowercase, hyphenated version of the series name

### Book IDs
1. Go to Books > All Books
2. Hover over a book title
3. Look at the bottom of your browser for the URL
4. The ID is the number after `post=` (example: `post=123`)

## Performance Tips

### Use Limits Wisely
Displaying too many books on one page can slow down your site. Recommended limits:
- Homepage: 3-6 books
- Category pages: 12-24 books
- Complete catalog: Consider pagination or filtering

### Cache Shortcode Output
For high-traffic pages, consider using a caching plugin to store shortcode output and reduce database queries.

### Optimize Book Cover Images
Large images slow page load times. Use optimized images around 800-1200px wide for best performance.

---

**Related Documentation:**
- [Shortcodes Introduction](/shortcodes/README.md)
- [Managing Books](/managing-books/README.md)
- [Displaying Books](/displaying-books/README.md)
- [Styling Your Books](/displaying-books/styling-your-books.md)

---

*Last Updated: March 7, 2026*
