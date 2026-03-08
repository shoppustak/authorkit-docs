# Shortcodes

## What are Shortcodes?

Shortcodes are simple text snippets you can insert into any WordPress page, post, or widget to display dynamic content. AuthorKit for Books provides powerful shortcodes that let you showcase your books anywhere on your website without writing code.

## How to Use Shortcodes

Simply copy the shortcode and paste it into the WordPress editor where you want your books to appear:

1. Edit any page or post
2. Place your cursor where you want books to display
3. Paste the shortcode (example: `[authorkit_books]`)
4. Publish or update the page

The shortcode will automatically be replaced with your book display when visitors view the page.

## Available Shortcodes

AuthorKit for Books includes four main shortcodes:

### [authorkit_book]
Display a single book with all its details, cover image, and purchase links.

**Use Cases:**
- Feature your latest release on your homepage
- Embed a book in a blog post review
- Create dedicated landing pages for each book

[View Full Documentation](/shortcodes/authorkit_book.md)

### [authorkit_books]
Display multiple books in a customizable grid or list layout.

**Use Cases:**
- Create a complete book catalog page
- Show your top 5 bestsellers
- Filter books by specific categories

[View Full Documentation](/shortcodes/authorkit_books.md)

### [authorkit_books_by_category]
Display all books from a specific category (genre).

**Use Cases:**
- Create genre-specific landing pages
- Show all your romance novels together
- Build a children's books section

[View Full Documentation](/shortcodes/authorkit_books_by_category.md)

### [authorkit_books_by_series]
Display all books in a series, automatically ordered.

**Use Cases:**
- Create series landing pages
- Show reading order for multi-book series
- Promote complete series collections

[View Full Documentation](/shortcodes/authorkit_books_by_series.md)

## Quick Examples

### Display All Books
```
[authorkit_books]
```

### Display Latest 6 Books
```
[authorkit_books limit="6"]
```

### Display Books by Category
```
[authorkit_books_by_category category="fantasy"]
```

### Display Specific Book
```
[authorkit_book id="123"]
```

## Shortcode Parameters

Most shortcodes accept parameters to customize their output. Parameters are added inside the shortcode brackets:

```
[shortcode_name parameter="value" another="value"]
```

Common parameters include:
- `limit` - Number of books to display
- `category` - Filter by book category
- `series` - Filter by book series
- `orderby` - Sort books (title, date, random)
- `order` - Sort direction (ASC or DESC)

See individual shortcode documentation for complete parameter lists.

## Combining with WordPress Blocks

Shortcodes work in both the Classic Editor and Block Editor:

**Block Editor (Gutenberg):**
1. Add a "Shortcode" block
2. Paste your shortcode
3. Preview to see the result

**Classic Editor:**
1. Switch to Text mode
2. Paste your shortcode
3. Switch back to Visual mode to preview

## Styling Shortcode Output

All shortcodes generate HTML with CSS classes you can target for custom styling. See the [Styling Your Books](/displaying-books/styling-your-books.md) guide for details.

## Troubleshooting

**Shortcode appears as plain text:**
- Make sure you're using square brackets `[ ]` not parentheses or curly braces
- Check for extra spaces inside the brackets
- Verify the shortcode name is spelled correctly

**No books display:**
- Verify you have published books in your catalog
- Check that category/series slugs match exactly (case-sensitive)
- Ensure book limits aren't excluding all results

**Layout looks broken:**
- Check for theme CSS conflicts
- Try deactivating other plugins temporarily
- Review the styling documentation for CSS fixes

---

**Related Documentation:**
- [Shortcodes Overview](/shortcodes/overview.md)
- [Displaying Books](/displaying-books/README.md)
- [Styling Your Books](/displaying-books/styling-your-books.md)

---

*Last Updated: March 7, 2026*
