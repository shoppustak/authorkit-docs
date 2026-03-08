# Displaying Books

## Introduction

Once you've added books to AuthorKit, the next step is displaying them on your website. AuthorKit provides multiple options for showing books: single book pages, archive pages, shortcodes, and custom templates. This guide covers everything you need to know about book display.

## Display Methods

### Single Book Pages

Each book automatically gets its own dedicated page with a unique URL. These pages display the complete book information: cover, description, metadata, purchase links, and more.

[Learn about single book pages](/displaying-books/single-book-pages.md)

### Book Archives

WordPress automatically creates archive pages showing all your books in a grid or list layout. Archives can be filtered by category, series, or age range.

[Learn about book archives](/displaying-books/book-archives.md)

### Shortcodes

Insert books anywhere on your website using shortcodes in pages, posts, or widgets. Display single books, book grids, category-filtered lists, or series collections.

[View shortcodes documentation](/shortcodes/README.md)

### Custom Templates

For advanced users, override AuthorKit's default templates with custom designs that match your theme perfectly.

[Learn about template customization](/developer-guide.md)

## Automatic Features

### Responsive Design

All AuthorKit displays are mobile-responsive by default. Books look great on desktops, tablets, and phones without additional configuration.

### SEO Optimization

Book pages include automatic schema.org markup, optimized meta tags, and semantic HTML for search engine visibility.

### Social Sharing

Open Graph and Twitter Card tags ensure books display beautifully when shared on social media platforms.

### Performance

Optimized queries and caching support ensure fast page loads even with large book catalogs.

## Styling and Customization

AuthorKit generates clean, semantic HTML with CSS classes for easy styling. You can customize the appearance to match your website's design without touching PHP code.

[Complete styling guide](/displaying-books/styling-your-books.md)

## Common Display Scenarios

### Homepage Book Feature

Display your latest release on your homepage:
```
[authorkit_book id="123"]
```

### Complete Book Catalog Page

Create a "My Books" page with all titles:
```
[authorkit_books orderby="date" order="DESC"]
```

### Genre Landing Pages

Dedicated pages for each genre:
```
[authorkit_books_by_category category="fantasy"]
```

### Series Pages

Show all books in a series in reading order:
```
[authorkit_books_by_series series="trilogy-name"]
```

### Sidebar Widget

Feature a random book in your sidebar:
```
[authorkit_books orderby="random" limit="1" show_description="false"]
```

## Book URLs

### Default URL Structure

**Single Books:**
```
yoursite.com/book/book-title-slug/
```

**Category Archives:**
```
yoursite.com/book-category/fantasy/
yoursite.com/book-category/romance/
```

**Series Archives:**
```
yoursite.com/book-series/harry-potter/
yoursite.com/book-series/lord-of-the-rings/
```

**All Books Archive:**
```
yoursite.com/books/
```

### Custom Permalinks

WordPress allows customizing book permalinks in **Settings > Permalinks**. However, changing defaults can break existing links, so only modify if absolutely necessary.

## Best Practices

### Use Hierarchical Structure

Create a logical information architecture:
1. Main Books page (all books)
2. Genre pages (filtered by category)
3. Series pages (books in reading order)
4. Individual book pages (complete details)

### Internal Linking

Link between related pages:
- Link from book pages to their category archive
- Link from book pages to their series archive
- Link from series pages to individual books
- Cross-link related books in descriptions

### Call-to-Action

Include clear next steps on every book page:
- Purchase links prominently displayed
- "Read More Books" linking to catalog
- Newsletter signup for updates
- Social sharing buttons

### Page Speed

Optimize for performance:
- Compress book cover images
- Limit books per page (use pagination)
- Enable caching plugins
- Minimize custom CSS/JavaScript

## Template Hierarchy

WordPress follows a template hierarchy for displaying books:

1. Custom template in your theme: `your-theme/authorkit/books/single-book.php`
2. AuthorKit's default template: `authorkit/templates/books/single-book.php`
3. WordPress fallback: `single.php` or `index.php`

You can override any AuthorKit template by copying it to your theme and customizing.

## Accessibility

All AuthorKit templates follow accessibility best practices:

### Semantic HTML
- Proper heading hierarchy (H1, H2, H3)
- List elements for book grids
- Descriptive link text

### Alt Text
- Book covers include descriptive alt attributes
- Decorative images hidden from screen readers

### Keyboard Navigation
- All interactive elements keyboard accessible
- Logical tab order maintained
- Focus states visible

### Color Contrast
- Text meets WCAG AA standards (4.5:1 minimum)
- Links distinguishable from body text

## Multilingual Support

AuthorKit works with popular translation plugins:

**WPML** - Full compatibility
**Polylang** - Supports multiple languages
**TranslatePress** - Visual translation interface

Create translated versions of your book pages to reach global audiences.

## Troubleshooting Display Issues

**Books don't appear:**
- Check book status is "Published" not "Draft"
- Verify shortcode spelling
- Clear cache

**Layout looks broken:**
- Check for theme CSS conflicts
- Inspect with browser developer tools
- Try default WordPress theme to isolate issue

**Images don't load:**
- Verify image upload completed
- Check file permissions
- Test with different image formats

**Wrong books display:**
- Review shortcode parameters (category, series)
- Check taxonomy assignments
- Verify book publication dates

---

**Related Documentation:**
- [Single Book Pages](/displaying-books/single-book-pages.md)
- [Book Archives](/displaying-books/book-archives.md)
- [Styling Your Books](/displaying-books/styling-your-books.md)
- [Shortcodes Overview](/shortcodes/overview.md)

---

*Last Updated: March 7, 2026*
