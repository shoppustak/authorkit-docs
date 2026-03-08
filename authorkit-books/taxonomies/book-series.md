# Book Series

## Overview

Book series organize related books into collections with proper reading order. Series are essential for trilogies, sagas, and multi-book storylines. AuthorKit automatically maintains series order and creates dedicated series pages showing all books in sequence.

## Accessing Series

From WordPress admin:
1. Navigate to **Books > Series**
2. View all existing series
3. Add new series or edit existing ones

## Creating Series

### Method 1: From Series Screen

1. Go to **Books > Series**
2. Enter series name (e.g., "The Lord of the Rings")
3. Slug auto-generates (e.g., "lord-of-the-rings")
4. Add description (optional but recommended)
5. Click **Add New Series**

### Method 2: While Editing a Book

1. Edit any book
2. Find **Series** metabox in sidebar
3. Click **+ Add New Series**
4. Enter series name
5. Click **Add New Series**

The series is created and automatically assigned to the book.

## Series Order

The series order field determines reading sequence:

### Setting Series Order

1. Edit a book
2. Find **Series** metabox
3. Select series from dropdown
4. Enter **Series Order** number (1, 2, 3, etc.)
5. Save the book

**Examples:**
- First book: `1`
- Second book: `2`
- Novella between books: `2.5`

### Why Series Order Matters

- Books display in correct reading sequence
- Readers see proper progression
- Series shortcodes auto-sort by order
- Book numbers appear on covers

## Series Descriptions

Add comprehensive series descriptions:

**Good Description:**
```
Follow Frodo Baggins and the Fellowship on an epic quest across Middle-earth
to destroy the One Ring. This groundbreaking trilogy redefined modern fantasy
literature with its rich world-building, complex characters, and themes of
friendship, sacrifice, and hope against darkness.
```

Descriptions appear:
- At top of series archive pages
- In schema markup
- When using series shortcodes

## Assigning Books to Series

### During Book Creation

1. Create or edit a book
2. Find **Series** metabox (right sidebar)
3. Select series from dropdown
4. Enter series order number
5. Save the book

### For Existing Books

1. Edit the book
2. Select series
3. Add series order
4. Click **Update**

## Series Archives

WordPress automatically creates series archive pages:

**URL Format:**
```
yoursite.com/book-series/harry-potter/
yoursite.com/book-series/hunger-games/
yoursite.com/book-series/discworld/
```

Archives display:
- Series name
- Series description
- All books in reading order
- Book numbers (Book 1, Book 2, etc.)

## Using Series in Shortcodes

### Show Books from Specific Series
```
[authorkit_books series="harry-potter"]
```

### Series-Specific Shortcode
```
[authorkit_books_by_series series="lord-of-the-rings"]
```

Displays series header, description, and books in correct order.

### Show Series Order Numbers
```
[authorkit_books_by_series series="trilogy-name" show_order_numbers="true"]
```

## Creating Series Landing Pages

### Dedicated Series Page

1. Create new page: "The Harry Potter Series"
2. Add shortcode:
```
[authorkit_books_by_series series="harry-potter"]
```
3. Add custom content about the series
4. Publish

### Multi-Series Page

Show all your series on one page:

```
## Fantasy Series

[authorkit_books_by_series series="fantasy-trilogy" show_series_description="false"]

## Science Fiction Series

[authorkit_books_by_series series="space-saga" show_series_description="false"]
```

## Series Best Practices

### Clear Naming
Use the official series name as published:
- "Harry Potter" not "HP Series"
- "The Lord of the Rings" not "LOTR"

### Complete Information
- Add all books in the series
- Set correct series order for each
- Write compelling series descriptions
- Link books together

### Reading Order
For complex series with multiple reading paths:
- Use primary publication order
- Mention alternate orders in description
- Consider creating series guides on separate pages

### Standalone Books
Leave series field empty for books not part of a collection.

## Series Types

### Traditional Series
Books read in sequential order (1, 2, 3...).
Example: Hunger Games trilogy

### Companion Series
Books in same universe but can be read independently.
Example: Discworld series

### Anthology Series
Connected short stories or novellas.
Example: Sherlock Holmes stories

### Long-Running Series
Ongoing series with 10+ books.
Example: Jack Reacher series

## Editing Series

1. Go to **Books > Series**
2. Click series name
3. Modify name, slug, or description
4. Click **Update**

**Warning:** Changing slugs breaks URLs. Update links if you change series slugs.

## Deleting Series

1. Go to **Books > Series**
2. Hover over series name
3. Click **Delete**
4. Confirm

Books remain but series assignment is removed.

## Series Marketing

### Series Pages
Create dedicated landing pages promoting complete series.

### Bundle Promotions
Offer complete series at discounted prices.

### Reading Order Guides
Help readers navigate complex series with proper ordering.

### New Reader Entry Points
Indicate if later books can serve as entry points for new readers.

## SEO for Series

### Series Names
Use full, official series names for better search visibility.

### Descriptions
Write detailed, keyword-rich descriptions (200-300 words).

### Internal Linking
- Link from individual books to series page
- Link from series page back to books
- Cross-link related series

### Schema Markup
AuthorKit automatically adds BookSeries schema.org markup.

## Troubleshooting

**Books appear in wrong order:**
- Check series order numbers are sequential (1, 2, 3)
- Verify no duplicate order numbers
- Confirm orderby parameter set to `series_order`

**Series archive empty:**
- Verify books assigned to series
- Check books are Published
- Re-save permalinks if needed

**Book numbers don't show:**
- Ensure books have series order set
- Use `show_order_numbers="true"` in shortcode
- Check theme template isn't hiding numbers

---

**Related Documentation:**
- [Book Categories](/taxonomies/book-categories.md)
- [Book Meta Fields](/managing-books/book-meta-fields.md)
- [Shortcodes Overview](/shortcodes/overview.md)
- [Series Shortcode](/shortcodes/authorkit_books_by_series.md)

---

*Last Updated: March 7, 2026*
