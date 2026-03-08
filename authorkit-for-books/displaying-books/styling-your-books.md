# Styling Your Books

## Introduction

AuthorKit generates semantic HTML with CSS classes that make it easy to customize book appearance without touching PHP code. This guide covers CSS selectors, common customizations, and styling best practices.

## Adding Custom CSS

### WordPress Customizer (Recommended)

1. Go to **Appearance > Customize**
2. Click **Additional CSS**
3. Add your custom styles
4. Click **Publish**

Changes appear immediately and survive plugin/theme updates.

### Child Theme stylesheet.css

Add styles to your child theme's `style.css` file for permanent customizations.

### Custom CSS Plugin

Install a plugin like "Simple Custom CSS" or "WP Add Custom CSS" for organized style management.

## CSS Class Structure

### Single Book Pages

```css
/* Book page container */
.authorkit-book-single { }

/* Book cover */
.authorkit-book-cover img { }

/* Book title */
.authorkit-book-title { }

/* Book description */
.authorkit-book-description { }

/* Metadata section */
.authorkit-book-meta { }

/* Individual meta fields */
.authorkit-book-isbn { }
.authorkit-book-pages { }
.authorkit-book-publisher { }

/* Buy links container */
.authorkit-book-buy-links { }

/* Individual retailer links */
.authorkit-buy-link { }
.authorkit-buy-link-amazon { }
.authorkit-buy-link-bn { }
```

### Book Grids

```css
/* Grid container */
.authorkit-books-grid { }

/* Column classes */
.authorkit-columns-2 { }
.authorkit-columns-3 { }
.authorkit-columns-4 { }

/* Individual book card */
.authorkit-book-card { }

/* Card elements */
.authorkit-book-card .authorkit-book-cover { }
.authorkit-book-card .authorkit-book-title { }
.authorkit-book-card .authorkit-book-description { }
```

### Book Lists

```css
/* List container */
.authorkit-books-list { }

/* List item */
.authorkit-book-list-item { }
```

### Coming Soon Books

```css
/* Coming soon badge */
.authorkit-coming-soon-badge { }

/* Coming soon books */
.authorkit-book-card.coming-soon { }
```

## Common Customizations

### Custom Book Card Styling

```css
.authorkit-book-card {
    background: #ffffff;
    border: 1px solid #e0e0e0;
    border-radius: 8px;
    padding: 20px;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.authorkit-book-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 20px rgba(0,0,0,0.1);
}
```

### Customize Book Titles

```css
.authorkit-book-title {
    font-family: 'Georgia', serif;
    font-size: 24px;
    color: #333333;
    margin-bottom: 10px;
}

.authorkit-book-card .authorkit-book-title {
    font-size: 18px;
}
```

### Style Buy Links as Buttons

```css
.authorkit-book-buy-links {
    display: flex;
    gap: 10px;
    flex-wrap: wrap;
}

.authorkit-buy-link {
    display: inline-block;
    padding: 12px 24px;
    background: #0073aa;
    color: #ffffff;
    text-decoration: none;
    border-radius: 4px;
    font-weight: bold;
    transition: background 0.3s ease;
}

.authorkit-buy-link:hover {
    background: #005a87;
}
```

### Retailer-Specific Colors

```css
.authorkit-buy-link-amazon {
    background: #ff9900;
}

.authorkit-buy-link-bn {
    background: #00a94f;
}

.authorkit-buy-link-apple {
    background: #000000;
}

.authorkit-buy-link-kobo {
    background: #0096d6;
}
```

### Custom Grid Layouts

```css
/* Responsive grid */
.authorkit-books-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    gap: 30px;
}

/* Fixed columns on desktop */
@media (min-width: 768px) {
    .authorkit-columns-3 {
        grid-template-columns: repeat(3, 1fr);
    }

    .authorkit-columns-4 {
        grid-template-columns: repeat(4, 1fr);
    }
}

/* Single column on mobile */
@media (max-width: 767px) {
    .authorkit-books-grid {
        grid-template-columns: 1fr;
    }
}
```

### Cover Image Styling

```css
.authorkit-book-cover {
    position: relative;
    overflow: hidden;
    border-radius: 4px;
    margin-bottom: 15px;
}

.authorkit-book-cover img {
    width: 100%;
    height: auto;
    display: block;
    transition: transform 0.3s ease;
}

.authorkit-book-card:hover .authorkit-book-cover img {
    transform: scale(1.05);
}
```

### Coming Soon Badge

```css
.authorkit-coming-soon-badge {
    position: absolute;
    top: 10px;
    right: 10px;
    background: #e74c3c;
    color: #ffffff;
    padding: 5px 10px;
    border-radius: 4px;
    font-size: 12px;
    font-weight: bold;
    text-transform: uppercase;
    z-index: 10;
}
```

### Book Metadata Styling

```css
.authorkit-book-meta {
    font-size: 14px;
    color: #666666;
    margin: 15px 0;
}

.authorkit-book-meta dt {
    font-weight: bold;
    color: #333333;
    margin-top: 8px;
}

.authorkit-book-meta dd {
    margin: 0 0 8px 0;
}
```

### Series Information

```css
.authorkit-book-series {
    background: #f5f5f5;
    padding: 10px 15px;
    border-left: 4px solid #0073aa;
    margin: 20px 0;
}

.authorkit-series-order {
    font-weight: bold;
    color: #0073aa;
}
```

## Responsive Design

### Mobile-First Approach

```css
/* Base styles (mobile) */
.authorkit-book-card {
    padding: 15px;
}

/* Tablet */
@media (min-width: 768px) {
    .authorkit-book-card {
        padding: 20px;
    }
}

/* Desktop */
@media (min-width: 1024px) {
    .authorkit-book-card {
        padding: 25px;
    }
}
```

### Responsive Typography

```css
.authorkit-book-title {
    font-size: clamp(18px, 4vw, 28px);
}

.authorkit-book-description {
    font-size: clamp(14px, 2.5vw, 16px);
    line-height: 1.6;
}
```

## Accessibility Styling

### Focus States

```css
.authorkit-buy-link:focus {
    outline: 3px solid #0073aa;
    outline-offset: 2px;
}

.authorkit-book-card a:focus {
    outline: 2px solid #0073aa;
    outline-offset: 4px;
}
```

### High Contrast

```css
@media (prefers-contrast: high) {
    .authorkit-book-card {
        border: 2px solid #000000;
    }

    .authorkit-buy-link {
        border: 2px solid #ffffff;
    }
}
```

## Dark Mode Support

```css
@media (prefers-color-scheme: dark) {
    .authorkit-book-card {
        background: #1e1e1e;
        border-color: #444444;
        color: #e0e0e0;
    }

    .authorkit-book-title {
        color: #ffffff;
    }

    .authorkit-book-meta {
        color: #aaaaaa;
    }
}
```

## Print Styles

```css
@media print {
    .authorkit-book-buy-links {
        display: none;
    }

    .authorkit-book-cover img {
        max-width: 200px;
    }
}
```

## Best Practices

### Use CSS Variables

```css
:root {
    --book-accent-color: #0073aa;
    --book-card-padding: 20px;
    --book-border-radius: 8px;
}

.authorkit-book-card {
    padding: var(--book-card-padding);
    border-radius: var(--book-border-radius);
}

.authorkit-buy-link {
    background: var(--book-accent-color);
}
```

### Maintain Specificity

Avoid `!important` by using appropriate specificity:

```css
/* Too general - may be overridden */
.book-title { }

/* Good specificity */
.authorkit-book-title { }

/* Higher specificity if needed */
.authorkit-books-grid .authorkit-book-card .authorkit-book-title { }
```

### Test Across Devices

Always test customizations on:
- Desktop browsers (Chrome, Firefox, Safari, Edge)
- Mobile devices (iOS, Android)
- Tablets
- Different screen sizes

## Troubleshooting

**Styles don't apply:**
- Clear browser cache
- Check CSS specificity (use browser dev tools)
- Verify selectors are correct
- Ensure CSS is loading (view page source)

**Responsive issues:**
- Test with browser dev tools responsive mode
- Check media query syntax
- Verify viewport meta tag exists

**Conflicts with theme:**
- Use more specific selectors
- Check theme's CSS load order
- Consider using child theme

---

**Related Documentation:**
- [Single Book Pages](/displaying-books/single-book-pages.md)
- [Book Archives](/displaying-books/book-archives.md)
- [Developer Guide](/developer-guide.md)

---

*Last Updated: March 7, 2026*
