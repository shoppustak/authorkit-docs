# Taxonomies

## Introduction

Taxonomies are WordPress's way of organizing and classifying content. AuthorKit for Books uses three taxonomies to help you organize your book catalog: Categories (genres), Series, and Age Ranges. These taxonomies make it easy for readers to browse and discover books by topic, collection, or suitability.

## Available Taxonomies

### Book Categories (Genres)
Organize books by genre, subject, or topic. Books can belong to multiple categories.

Examples: Fantasy, Romance, Mystery, Science Fiction, Non-Fiction

[Learn about book categories](/taxonomies/book-categories.md)

### Book Series
Group related books into series with proper ordering. Essential for trilogies, sagas, and multi-book collections.

Examples: Harry Potter, Lord of the Rings, Chronicles of Narnia

[Learn about book series](/taxonomies/book-series.md)

### Age Ranges
Tag books with appropriate age groups for readers. Useful for children's books and educational content.

Examples: 3-5 (Picture Books), 13-18 (Young Adult), 18+ (Adult)

[Learn about age ranges](/taxonomies/age-ranges.md)

## How Taxonomies Work

### Assignment
When editing a book, assign it to one or more taxonomies using checkboxes or dropdowns in the sidebar.

### Archives
WordPress automatically creates archive pages for each taxonomy term, showing all books in that category, series, or age range.

### Filtering
Use taxonomy terms to filter shortcodes and display specific subsets of books.

### SEO Benefits
Taxonomy pages receive their own URLs, titles, and descriptions, improving search engine discoverability.

## Managing Taxonomies

### Accessing Taxonomy Screens

From WordPress admin:
- **Books > Categories** - Manage book genres
- **Books > Series** - Manage book series
- **Books > Age Ranges** - Manage age ranges

### Adding New Terms

1. Navigate to the taxonomy screen
2. Enter **Name** (e.g., "Fantasy")
3. Enter **Slug** (auto-generated, e.g., "fantasy")
4. Add **Description** (optional but recommended for SEO)
5. Click **Add New Category/Series/Age Range**

### Editing Terms

1. Click the term name in the list
2. Modify name, slug, or description
3. Click **Update**

### Deleting Terms

1. Hover over term name
2. Click **Delete**
3. Books will remain but taxonomy assignment removed

## Best Practices

### Naming Conventions
- Use consistent capitalization
- Keep names concise
- Avoid abbreviations unless standard
- Use singular or plural consistently

### Descriptions
Add descriptions to taxonomy terms:
- Helps readers understand the category
- Appears on archive pages
- Used in meta descriptions for SEO
- Provides context for browsing

### Organization
- Don't create too many categories (8-15 is ideal)
- Group similar genres together
- Consider parent/child relationships for categories
- Keep series list manageable

### Slugs
- Slugs appear in URLs
- Use lowercase, hyphens between words
- Keep short but descriptive
- Don't change after books are assigned (breaks links)

## Using Taxonomies in Shortcodes

### Filter by Category
```
[authorkit_books category="fantasy"]
```

### Filter by Series
```
[authorkit_books series="harry-potter"]
```

### Category-Specific Shortcode
```
[authorkit_books_by_category category="romance"]
```

### Series-Specific Shortcode
```
[authorkit_books_by_series series="trilogy-name"]
```

## Taxonomy Archives

WordPress automatically creates archive URLs:

### Category Archives
```
yoursite.com/book-category/fantasy/
yoursite.com/book-category/romance/
```

### Series Archives
```
yoursite.com/book-series/harry-potter/
yoursite.com/book-series/lord-of-the-rings/
```

### Age Range Archives
```
yoursite.com/age-range/young-adult/
yoursite.com/age-range/middle-grade/
```

## Common Taxonomy Scenarios

### Multi-Genre Books
Assign books to multiple categories when they span genres:
- Fantasy + Romance = Romantic Fantasy
- Science Fiction + Mystery = Sci-Fi Thriller

### Standalone Books
Leave Series field empty for books not part of a collection.

### Series without Order
Some series (like anthologies) don't require reading order. Assign to series but leave series order empty.

### Cross-Age Appeal
Choose the primary target age range even if book appeals to multiple ages.

## SEO with Taxonomies

### Optimize Category/Series Names
Use search-friendly names that readers actually search for:
- Good: "Science Fiction Books"
- Less optimal: "Sci-Fi"

### Write Compelling Descriptions
Category/series descriptions appear in search results and on archive pages. Make them engaging and keyword-rich without stuffing.

### Internal Linking
Link from book pages to category/series archives, and vice versa, to build site structure.

---

**Related Documentation:**
- [Book Categories](/taxonomies/book-categories.md)
- [Book Series](/taxonomies/book-series.md)
- [Age Ranges](/taxonomies/age-ranges.md)
- [Shortcodes Overview](/shortcodes/overview.md)

---

*Last Updated: March 7, 2026*
