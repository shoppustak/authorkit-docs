# [authorkit_books_by_category]

## Display Books by Category

The `[authorkit_books_by_category]` shortcode displays all books from a specific category (genre). Perfect for creating dedicated genre pages, organizing your catalog by topic, and helping readers find books in their favorite categories.

## Basic Usage

```
[authorkit_books_by_category category="fantasy"]
```

Replace `fantasy` with your category slug to display all books in that category.

## Finding Category Slugs

1. Go to **Books > Categories** in WordPress admin
2. Hover over a category name
3. Look at your browser's status bar (bottom-left)
4. The URL shows: `taxonomy=book_category&tag_ID=123&term_slug=fantasy`
5. The slug is the lowercase, hyphenated version (example: `fantasy`, `science-fiction`, `young-adult`)

## Parameters

### Required Parameters

**category** (required)
- The category slug to display books from
- Type: String
- Example: `category="romance"`
- Example: `category="science-fiction"`

### Filtering Parameters

**limit**
- Maximum number of books to display
- Type: Integer
- Default: -1 (unlimited)
- Example: `limit="12"`

**exclude**
- Exclude specific book IDs
- Type: Comma-separated IDs
- Example: `exclude="45,67"`

### Sorting Parameters

**orderby**
- How to sort books
- Options: `date`, `title`, `random`, `menu_order`
- Default: `date`
- Example: `orderby="title"`

**order**
- Sort direction
- Options: `ASC`, `DESC`
- Default: `DESC`
- Example: `order="ASC"`

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

**show_category_description**
- Display category description at top
- Type: true/false
- Default: true
- Example: `show_category_description="false"`

**show_category_name**
- Display category name as heading
- Type: true/false
- Default: true
- Example: `show_category_name="false"`

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

## Usage Examples

### Simple Genre Page
```
[authorkit_books_by_category category="mystery"]
```
All mystery books with default settings.

### Fantasy Books Alphabetically
```
[authorkit_books_by_category category="fantasy" orderby="title" order="ASC"]
```
Sort fantasy books A-Z by title.

### Limited Romance Grid
```
[authorkit_books_by_category category="romance" limit="12" columns="4"]
```
Show 12 romance books in 4 columns.

### Compact Science Fiction List
```
[authorkit_books_by_category category="science-fiction" layout="list" show_description="false"]
```
Vertical list without descriptions.

### Young Adult Page without Header
```
[authorkit_books_by_category category="young-adult" show_category_name="false" show_category_description="false"]
```
Just the books, no category header.

### Top Thrillers
```
[authorkit_books_by_category category="thriller" limit="10" orderby="menu_order"]
```
Manually curated top 10 thrillers.

### Random Horror Picks
```
[authorkit_books_by_category category="horror" orderby="random" limit="6"]
```
6 random horror books.

## HTML Output

```html
<div class="authorkit-books-by-category" data-category="fantasy">
    <div class="authorkit-category-header">
        <h2 class="authorkit-category-name">Fantasy</h2>
        <p class="authorkit-category-description">Epic adventures in magical worlds...</p>
    </div>

    <div class="authorkit-books-grid authorkit-columns-3">
        <div class="authorkit-book-card" data-book-id="123">
            <!-- Book content -->
        </div>
        <!-- More books... -->
    </div>
</div>
```

## Styling

### Category Header

```css
/* Category header styling */
.authorkit-category-header {
    margin-bottom: 40px;
    text-align: center;
}

.authorkit-category-name {
    font-size: 32px;
    color: #333;
    margin-bottom: 10px;
}

.authorkit-category-description {
    font-size: 18px;
    color: #666;
    max-width: 800px;
    margin: 0 auto;
}
```

### Category-Specific Styling

```css
/* Style different categories uniquely */
.authorkit-books-by-category[data-category="fantasy"] .authorkit-book-card {
    border-color: #9b59b6;
}

.authorkit-books-by-category[data-category="romance"] .authorkit-book-card {
    border-color: #e74c3c;
}

.authorkit-books-by-category[data-category="mystery"] .authorkit-book-card {
    border-color: #34495e;
}
```

## Common Use Cases

### Dedicated Genre Landing Pages

Create a page for each major genre:

**Fantasy Page:**
```
[authorkit_books_by_category category="fantasy" orderby="title" order="ASC"]
```

**Romance Page:**
```
[authorkit_books_by_category category="romance" limit="20"]
```

**Mystery Page:**
```
[authorkit_books_by_category category="mystery" columns="4"]
```

### Multi-Genre Browsing

Create a "Browse by Genre" page with multiple shortcodes:

```
## Fantasy Books
[authorkit_books_by_category category="fantasy" limit="6"]

## Romance Books
[authorkit_books_by_category category="romance" limit="6"]

## Mystery Books
[authorkit_books_by_category category="mystery" limit="6"]
```

### Category Widgets

Use in sidebars or footers:

```
[authorkit_books_by_category category="bestsellers" limit="3" show_description="false" columns="1"]
```

## Adding Category Descriptions

Category descriptions appear above the book grid when `show_category_description="true"`:

1. Go to **Books > Categories**
2. Click on a category
3. Fill in the **Description** field
4. Save changes

Example description:
```
Dive into epic fantasy adventures filled with magic, dragons, and heroes on impossible quests.
These stories transport you to imaginary worlds where anything is possible.
```

## Multiple Categories

To display books from multiple categories, use the `[authorkit_books]` shortcode instead:

```
[authorkit_books category="fantasy,sci-fi,paranormal" limit="20"]
```

## Category Archives

WordPress automatically creates category archive pages at:
```
yoursite.com/book-category/fantasy/
yoursite.com/book-category/romance/
```

These use AuthorKit's default category template. Use this shortcode to create custom category pages with more control.

## Troubleshooting

**No books display:**
- Verify the category slug is correct (case-sensitive, use hyphens not spaces)
- Check that books are assigned to this category
- Ensure books are published, not drafts

**Wrong category name shows:**
- WordPress pulls the category name from the category settings
- Edit the category in **Books > Categories** to change the display name

**Category description doesn't appear:**
- Check that `show_category_description="true"` (or use default)
- Verify you've added a description in **Books > Categories**
- Ensure your theme isn't hiding the description with CSS

**Books appear in wrong order:**
- Check `orderby` and `order` parameters
- Verify publication dates are correct if using `orderby="date"`
- For manual ordering, use `orderby="menu_order"` and set order in WordPress

---

**Related Documentation:**
- [Book Categories](/taxonomies/book-categories.md)
- [Shortcodes Overview](/shortcodes/overview.md)
- [Managing Categories](/taxonomies/book-categories.md)
- [Styling Your Books](/displaying-books/styling-your-books.md)

---

*Last Updated: March 7, 2026*
