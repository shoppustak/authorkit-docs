# SEO & Schema

## Automatic Schema Markup

AuthorKit for Books automatically generates schema.org structured data for every book you add. This markup helps search engines understand your content and can enable rich snippets in search results, increasing click-through rates and visibility.

## Book Schema Implementation

Each book page includes schema.org/Book markup with the following properties:

### Core Book Properties
- **name**: Book title and subtitle
- **author**: Author name (Person schema)
- **isbn**: International Standard Book Number
- **bookFormat**: Physical, eBook, or Audiobook
- **datePublished**: Publication date
- **numberOfPages**: Page count
- **inLanguage**: Book language
- **publisher**: Publisher name (Organization schema)

### Commercial Properties
- **offers**: Price and availability information
- **url**: Canonical book page URL

### Descriptive Properties
- **description**: Book description/synopsis
- **genre**: Book categories and genres
- **image**: Book cover image URL

### Series Information
When a book is part of a series, additional schema properties are included:
- **isPartOf**: BookSeries schema
- **position**: Order within the series

## SEO Best Practices

### Book Titles
Use descriptive, unique titles that include your main keywords naturally. Avoid keyword stuffing. If you have a subtitle, use it to provide additional context.

**Good**: "The Dragon's Quest: An Epic Fantasy Adventure"
**Poor**: "Book Fantasy Dragon Magic Adventure Story Novel"

### Book Descriptions
Write compelling 150-300 word descriptions that:
- Hook readers in the first sentence
- Include relevant keywords naturally
- Describe the plot without spoilers
- Mention the genre and themes
- End with a call-to-action

### Book Cover Images
- Use high-resolution images (minimum 1000px width)
- Include descriptive alt text with the book title
- Optimize file size without sacrificing quality
- Use consistent aspect ratios across your catalog

### URL Structure
AuthorKit creates SEO-friendly URLs automatically:
- Format: `yoursite.com/book/book-title-slug/`
- Keep slugs short and descriptive
- Use hyphens between words
- Avoid special characters

## Meta Tags

Each book page automatically includes:

### Title Tags
Generated from your book title, optimized for search engines (60 characters or less recommended).

### Meta Descriptions
Pulled from your book description field. The first 155-160 characters appear in search results, so front-load important information.

### Open Graph Tags
For social media sharing:
- `og:title`: Book title
- `og:description`: Book description
- `og:image`: Book cover
- `og:type`: book
- `og:url`: Canonical URL

### Twitter Cards
Large image cards display your book cover prominently when shared on Twitter/X.

## Search Engine Optimization Tips

### Internal Linking
Link between related books, series pages, and author bio pages. This helps search engines understand your site structure and distributes page authority.

### Fresh Content
Regularly update book pages with:
- Reader reviews and testimonials
- Awards and recognition
- Updated purchase links
- Series order changes

### Mobile Optimization
All AuthorKit book templates are mobile-responsive by default. Search engines prioritize mobile-friendly pages in rankings.

### Page Speed
Optimize book cover images and minimize custom CSS/JavaScript to maintain fast page load times. Google considers speed a ranking factor.

## Monitoring SEO Performance

Use Google Search Console to:
- Monitor book page impressions and clicks
- Identify which search queries drive traffic
- Check for schema markup errors
- Track mobile usability issues

Use Google's Rich Results Test to verify your book schema markup is implemented correctly: `search.google.com/test/rich-results`

## Coming Soon Books

Books marked as "Coming Soon" include additional schema properties:
- **availabilityStarts**: Pre-order or release date
- **bookStatus**: Upcoming/announced status

This helps search engines index your books before publication, building early visibility.

---

**Related Documentation:**
- [Book Meta Fields](/managing-books/book-meta-fields.md)
- [Single Book Pages](/displaying-books/single-book-pages.md)
- [Book Cover Images](/managing-books/book-cover-images.md)

---

*Last Updated: March 7, 2026*
