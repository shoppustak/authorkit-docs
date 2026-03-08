# Adding Your First Book

## Step-by-Step Guide

Adding your first book to AuthorKit is straightforward. This guide walks you through every step, from accessing the book editor to publishing your first entry.

## Before You Start

Have these ready:
- Book title and subtitle (if applicable)
- Book description or synopsis
- Book cover image (JPG or PNG, minimum 800px wide)
- ISBN (if available)
- Publication date
- Retailer links (Amazon, Barnes & Noble, etc.)

You don't need everything to get started, but having this information ready makes the process smoother.

## Step 1: Access the Book Editor

1. Log in to your WordPress admin dashboard
2. Look for **Books** in the left sidebar menu
3. Click **Add New**

You'll see the book editor, which looks similar to the WordPress post editor.

## Step 2: Enter Basic Information

### Book Title
Enter your book's title in the large text field at the top of the page.

**Example:** "The Dragon's Quest"

### Book Description
In the main content editor, write your book description or synopsis. This appears on your book page and in search results.

**Tips:**
- Hook readers in the first sentence
- Keep it concise (150-300 words)
- Avoid major spoilers
- Include genre and themes
- End with intrigue or a call-to-action

**Example:**
```
When young farmhand Elara discovers a dragon egg in the forbidden forest,
her quiet life is shattered. As the last dragon awakens, ancient enemies
rise from the shadows, and Elara must choose between the safety of her
village and the destiny she never asked for. An epic fantasy adventure
filled with magic, betrayal, and the bonds that transcend species.
```

## Step 3: Add Book Metadata

Scroll down to find the **Book Details** metabox. This section contains 27+ fields for comprehensive book information.

### Required Fields (Recommended)

**Title** (already entered at top)
- Your book's full title

**Author**
- Your name or pen name
- Example: "Jane Smith"

**Description** (already entered in main editor)
- Book synopsis or description

**Publication Date**
- When the book was or will be published
- Format: MM/DD/YYYY
- Example: "03/15/2024"

### Identification Fields

**ISBN**
- International Standard Book Number
- 10 or 13 digits
- Example: "978-1234567890"

**ASIN**
- Amazon Standard Identification Number
- For Kindle ebooks
- Example: "B08ABCDEFG"

### Book Details

**Subtitle**
- Secondary title if applicable
- Example: "An Epic Fantasy Adventure"

**Publisher**
- Publishing house or self-published
- Example: "Dragon Press" or "Self-Published"

**Page Count**
- Number of pages
- Example: "342"

**Word Count**
- Total words (optional but useful)
- Example: "85000"

**Language**
- Primary language
- Example: "English"

**Format**
- Physical book, eBook, or Audiobook
- Select from dropdown

### Series Information

**Series**
- Select existing series or leave blank
- For standalone books, leave empty

**Series Order**
- Book's position in series
- Example: "1" for Book 1, "2" for Book 2

### Pricing

**Price**
- Current retail price
- Enter number only, no $ symbol
- Example: "9.99"

## Step 4: Upload Book Cover

The book cover is crucial for visual appeal and sales.

1. Find the **Featured Image** metabox (usually in the right sidebar)
2. Click **Set featured image**
3. Either:
   - **Upload Files** - Select an image from your computer
   - **Media Library** - Choose from previously uploaded images
4. Select your book cover image
5. Click **Set featured image**

**Cover Requirements:**
- Format: JPG, PNG, or GIF
- Minimum width: 800px (1000px+ recommended)
- Aspect ratio: 6:9 (book proportions)
- File size: Under 1MB for best performance

## Step 5: Add Retailer Links

Make it easy for readers to purchase your book.

### Available Retailer Fields

**Amazon URL**
- Your book's Amazon product page
- Example: "https://amazon.com/dp/B08ABCDEFG"

**Barnes & Noble URL**
- Your book's B&N product page
- Example: "https://www.barnesandnoble.com/w/book-title/1234567"

**Apple Books URL**
- Your book's Apple Books link
- Example: "https://books.apple.com/us/book/id1234567890"

**Kobo URL**
- Your book's Kobo store link
- Example: "https://www.kobo.com/us/en/ebook/book-title"

**Goodreads URL**
- Your book's Goodreads page (not a purchase link but useful)
- Example: "https://www.goodreads.com/book/show/12345678"

**Tip:** Paste the complete URL including `https://`

## Step 6: Assign Categories and Taxonomies

### Categories (Genres)

1. Find the **Categories** metabox (right sidebar)
2. Check boxes for relevant genres
3. Examples: Fantasy, Romance, Young Adult

You can select multiple categories. If your category doesn't exist:
1. Click **+ Add New Category**
2. Enter the category name
3. Click **Add New Category**

### Age Ranges (Optional)

1. Find the **Age Ranges** metabox
2. Select appropriate age range
3. Examples: 13-18 (Young Adult), 18+ (Adult)

## Step 7: Set Book Status

In the **Publish** metabox (right sidebar), choose the book's status:

### Published
Book is live and visible on your website immediately.

### Draft
Book is saved but not public. Use for works in progress.

### Coming Soon
Book is visible but marked as upcoming/pre-release.

For your first book, we recommend **Published** so you can see it on your site.

## Step 8: Publish Your Book

1. Review all information for accuracy
2. Click the blue **Publish** button (or **Save Draft** to save without publishing)
3. WordPress confirms: "Book published"

Congratulations! Your first book is now live on your website.

## Step 9: View Your Book

After publishing, WordPress shows a success message with a **View Book** link.

1. Click **View Book** to see your live book page
2. Verify everything displays correctly
3. Check that the cover, description, and purchase links work

## Step 10: Display Your Book

Now add your book to your website using shortcodes:

### Homepage Feature
Add to any page:
```
[authorkit_book id="YOUR_BOOK_ID"]
```

Replace `YOUR_BOOK_ID` with your book's ID (shown in the browser URL: `post=123`).

### Complete Catalog
Create a Books page with:
```
[authorkit_books]
```

[Learn more about shortcodes](/shortcodes/overview.md)

## Next Steps

Now that you've added your first book:

1. **Add More Books** - Repeat this process for your other titles
2. **Organize with Series** - Group related books into series
3. **Create Genre Pages** - Use category shortcodes for genre landing pages
4. **Optimize SEO** - Fill in all metadata fields for better search visibility
5. **Customize Display** - Adjust styling to match your brand

## Editing Your Book

To make changes after publishing:

1. Go to **Books > All Books**
2. Hover over the book title
3. Click **Edit**
4. Make your changes
5. Click **Update**

## Quick Tips

**Use Drafts:** Save books as drafts while gathering information. Publish when ready.

**Complete Metadata:** The more fields you fill, the better your SEO and reader experience.

**Professional Covers:** Invest in quality book covers. They're the first thing readers notice.

**Update Regularly:** Keep retailer links, prices, and descriptions current.

**Test Shortcodes:** Preview books on your website before announcing to readers.

## Troubleshooting

**Book doesn't appear on site:**
- Ensure status is set to "Published" not "Draft"
- Clear browser cache
- Check shortcode is spelled correctly

**Cover image doesn't show:**
- Verify you clicked "Set featured image"
- Check image file size (should be under 5MB)
- Ensure image format is JPG or PNG

**Can't publish more books:**
- Free tier limited to 10 books
- Upgrade to Pro for unlimited books

**Purchase links don't work:**
- Include full URLs with `https://`
- Verify links go to correct product pages
- Test links in incognito/private browser window

---

**Related Documentation:**
- [Book Meta Fields](/managing-books/book-meta-fields.md)
- [Book Cover Images](/managing-books/book-cover-images.md)
- [Shortcodes Overview](/shortcodes/overview.md)
- [Managing Books](/managing-books/README.md)

---

*Last Updated: March 7, 2026*
