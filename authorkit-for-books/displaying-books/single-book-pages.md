# Single Book Pages

## Overview

Every book in AuthorKit automatically gets its own dedicated page with a unique URL. These pages display complete book information and serve as the primary destination for readers discovering your books.

## Page URL Structure

Books use WordPress permalinks with the format:
```
yoursite.com/book/book-title-slug/
```

The slug is automatically generated from your book title. You can customize it when editing the book.

## Default Page Content

Single book pages automatically display:

### Book Cover
Large, high-quality cover image prominently displayed.

### Title and Subtitle
Main title as H1 heading, subtitle as H2 if provided.

### Author Name
Author as listed in book metadata.

### Description
Full book description from the main content editor.

### Book Metadata
- Publication Date
- ISBN
- Page Count
- Word Count
- Publisher
- Format
- Language
- Price

### Purchase Links
Buttons or links to retailers where book is available:
- Amazon
- Barnes & Noble
- Apple Books
- Kobo
- Goodreads (for ratings/reviews)

### Categories and Series
- Genre tags linking to category archives
- Series information with link to series page
- Age range if specified

### Schema Markup
Invisible schema.org/Book structured data for SEO.

## Accessing Single Book Pages

### Direct URL
Navigate directly to: `yoursite.com/book/book-title/`

### From Archives
Click any book in an archive or grid to visit its page.

### From Shortcodes
Book cards in shortcodes link to single pages by default.

### Search Results
Books appear in WordPress search results with links to their pages.

## Customizing Page Content

### Via Book Editor
Edit content directly in WordPress:
1. Go to Books > All Books
2. Click the book title
3. Modify description, metadata, cover, or links
4. Click Update

### Via Shortcodes
Embed additional content in book description:
- Related books shortcodes
- Image galleries
- Video trailers
- Embedded reviews

### Via Custom Fields
Add custom metadata in Book Details metabox.

## SEO Optimization

### Title Tag
WordPress generates `<title>` from book title and site name.

Example: "The Dragon's Quest - Author Name"

### Meta Description
First 155-160 characters of book description become meta description.

### Open Graph
Social media previews show:
- Book cover as og:image
- Title as og:title
- Description as og:description

### Schema Markup
Structured data includes all book metadata for rich search results.

## Template Override

Developers can create custom single book templates:

1. Copy `authorkit/templates/books/single-book.php`
2. Place in `your-theme/authorkit/books/single-book.php`
3. Customize as needed

[See developer guide for details](/developer-guide.md)

## Common Customizations

### Add Author Bio
Include biography below book description.

### Related Books Section
Show other books in same genre or series.

### Reader Reviews
Embed testimonials or reviews.

### Newsletter Signup
Add subscription form to build email list.

### Social Sharing
Include share buttons for Twitter, Facebook, Pinterest.

## Best Practices

### Complete Information
Fill all available metadata fields for professional appearance.

### Quality Covers
Use high-resolution, professional book covers.

### Compelling Descriptions
Write hook-filled descriptions that entice readers.

### Clear Call-to-Action
Make purchase links prominent and obvious.

### Internal Links
Link to related books, series pages, and genres.

### Mobile Testing
Preview on phones and tablets to ensure proper display.

## Troubleshooting

**Page returns 404:**
- Re-save permalinks in Settings > Permalinks
- Verify book status is Published
- Check slug doesn't conflict with existing pages

**Missing information:**
- Verify metadata filled in Book Details metabox
- Check Featured Image is set
- Ensure retailer links include https://

**Layout issues:**
- Test with default WordPress theme
- Check for CSS conflicts
- Review browser console for errors

---

**Related Documentation:**
- [Book Archives](/displaying-books/book-archives.md)
- [Styling Your Books](/displaying-books/styling-your-books.md)
- [Book Meta Fields](/managing-books/book-meta-fields.md)
- [SEO & Schema](/seo-and-schema.md)

---

*Last Updated: March 7, 2026*
