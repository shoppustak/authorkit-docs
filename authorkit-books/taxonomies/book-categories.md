# Book Categories

## Overview

Book categories (genres) help organize your catalog by subject, genre, or topic. Readers can browse books by category, and you can create dedicated landing pages for each genre. Books can belong to multiple categories, making it easy to classify cross-genre titles.

## Accessing Categories

From WordPress admin:
1. Navigate to **Books > Categories**
2. View all existing categories
3. Add new categories or edit existing ones

## Adding Categories

### Method 1: From Categories Screen

1. Go to **Books > Categories**
2. Enter category name (e.g., "Fantasy")
3. Slug auto-generates (e.g., "fantasy")
4. Add description (optional but recommended)
5. Click **Add New Category**

### Method 2: While Editing a Book

1. Edit any book
2. Find **Categories** metabox in sidebar
3. Click **+ Add New Category**
4. Enter category name
5. Click **Add New Category**

The category is created and automatically assigned to the book.

## Common Book Categories

### Fiction Genres
- Fantasy
- Science Fiction
- Romance
- Mystery / Thriller
- Horror
- Historical Fiction
- Literary Fiction
- Contemporary Fiction
- Dystopian
- Paranormal
- Western

### Non-Fiction Categories
- Biography / Memoir
- Self-Help
- Business
- History
- Science
- Travel
- Cookbooks
- True Crime
- Essays

### Age-Specific Categories
- Children's Books
- Young Adult
- Middle Grade
- Adult

### Format-Based Categories
- Graphic Novels
- Poetry
- Short Stories
- Anthologies

## Category Best Practices

### Keep It Simple
Start with 8-12 main categories. Too many categories dilute your catalog and confuse readers.

### Use Standard Genre Names
Stick to widely-recognized genres that readers search for:
- Good: "Science Fiction"
- Confusing: "Speculative Future Tales"

### Multiple Categories
Assign books to 2-3 relevant categories:
- A paranormal romance might be tagged: Romance, Paranormal, Fantasy

### Avoid Over-Categorization
Don't create hyper-specific categories:
- Instead of: "Vampire Romance", "Werewolf Romance", "Witch Romance"
- Use: "Paranormal Romance"

## Category Descriptions

Add descriptions for SEO and reader context:

**Good Description:**
```
Dive into epic fantasy adventures filled with magic, dragons, mythical
creatures, and heroes on impossible quests. These stories transport you
to imaginary worlds where anything is possible.
```

**Poor Description:**
```
Fantasy books.
```

Descriptions appear:
- At the top of category archive pages
- In meta tags for SEO
- In social media previews

## Assigning Categories to Books

### During Book Creation

1. Create or edit a book
2. Find **Categories** metabox (right sidebar)
3. Check boxes for relevant categories
4. Save the book

### Bulk Assignment

1. Go to **Books > All Books**
2. Select multiple books using checkboxes
3. Choose **Bulk Actions > Edit**
4. Select categories to add
5. Click **Update**

## Category Archives

WordPress creates automatic archive pages:

**URL Format:**
```
yoursite.com/book-category/fantasy/
yoursite.com/book-category/romance/
yoursite.com/book-category/mystery/
```

Archives display all books in that category in grid/list format.

## Using Categories in Shortcodes

### Show Books from Specific Category
```
[authorkit_books category="fantasy"]
```

### Show Books from Multiple Categories
```
[authorkit_books category="fantasy,sci-fi,paranormal"]
```

### Category-Specific Shortcode
```
[authorkit_books_by_category category="romance"]
```

This displays category name, description, and all books in that genre.

## Creating Category Landing Pages

### Manual Page Creation

1. Create new page: "Fantasy Books"
2. Add shortcode:
```
[authorkit_books_by_category category="fantasy"]
```
3. Customize with additional content
4. Publish

### Menu Navigation

Add category links to your site menu:

1. Go to **Appearance > Menus**
2. Add **Custom Link**
3. URL: `/book-category/fantasy/`
4. Link Text: "Fantasy Books"
5. Save menu

## SEO Optimization

### Category Names
Use search-friendly names:
- "Science Fiction Books" (better for SEO)
- "Sci-Fi" (less search volume)

### Category Slugs
Keep slugs simple and descriptive:
- Good: `science-fiction`
- Poor: `sci-fi-scifi-sf-books`

### Descriptions
Write 100-200 word descriptions with natural keyword usage.

### Internal Linking
Link from book descriptions to related category pages.

## Editing Categories

1. Go to **Books > Categories**
2. Click category name
3. Modify name, slug, or description
4. Click **Update**

**Warning:** Changing slugs breaks existing URLs and links.

## Deleting Categories

1. Go to **Books > Categories**
2. Hover over category
3. Click **Delete**
4. Confirm

Books remain intact but category assignment is removed.

## Troubleshooting

**Category archive shows no books:**
- Verify books are assigned to category
- Check books are Published not Draft
- Clear cache if using caching plugin

**Category appears empty:**
- Reassign books to the category
- Check taxonomy assignments
- Re-save permalinks: Settings > Permalinks > Save

**Wrong slug generated:**
- Edit category and manually set slug
- Use lowercase with hyphens
- Save changes

---

**Related Documentation:**
- [Book Series](/taxonomies/book-series.md)
- [Age Ranges](/taxonomies/age-ranges.md)
- [Shortcodes Overview](/shortcodes/overview.md)
- [Managing Books](/managing-books/README.md)

---

*Last Updated: March 7, 2026*
