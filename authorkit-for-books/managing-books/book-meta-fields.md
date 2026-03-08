# Book Meta Fields

## Complete Field Reference

AuthorKit for Books provides 27+ custom fields to capture comprehensive book information. This reference explains each field, its purpose, format, and best practices.

## Core Book Information

### Title
**Purpose:** Your book's main title
**Format:** Text
**Required:** Yes
**Location:** Top of editor

The primary title of your book as it appears on the cover. Keep it concise and memorable.

**Example:** "The Midnight Library"

---

### Subtitle
**Purpose:** Secondary descriptive title
**Format:** Text
**Required:** No
**Location:** Book Details metabox

Optional subtitle that provides additional context or describes the book's theme.

**Example:** "A Novel About All the Lives You Could Have Lived"

---

### Author
**Purpose:** Book author name(s)
**Format:** Text
**Required:** Recommended
**Location:** Book Details metabox

Author name as it should appear publicly. Can be your real name, pen name, or "by Multiple Authors" for collaborations.

**Example:** "Matt Haig" or "J.K. Rowling"

---

### Description
**Purpose:** Book synopsis or description
**Format:** Rich text (HTML editor)
**Required:** Yes
**Location:** Main content editor

Detailed book description that appears on book pages and in SEO meta tags. This is your sales pitch to readers.

**Best Practices:**
- 150-300 words ideal length
- Hook readers in opening sentence
- Describe plot without spoilers
- Include genre and themes
- End with intrigue or question
- Use short paragraphs for readability

**Example:**
```
Nora Seed finds herself in the Midnight Library, a place between life and death.
Each book represents a different version of her life, paths not taken, choices
unmade. As Nora explores infinite possibilities, she must discover which life
is truly worth living—before time runs out.

A thought-provoking exploration of regret, possibility, and what makes life
worth living.
```

## Identification Fields

### ISBN
**Purpose:** International Standard Book Number
**Format:** 10 or 13 digits (with or without hyphens)
**Required:** Recommended
**Location:** Book Details metabox

Unique identifier for your book. Most print books have ISBNs. If you have multiple editions (hardcover, paperback, ebook), each has a separate ISBN.

**Format Options:**
- ISBN-10: "0123456789"
- ISBN-13: "978-0123456789"
- With hyphens: "978-0-123-45678-9"

**Where to find:** On your book's back cover, copyright page, or publishing dashboard.

---

### ASIN
**Purpose:** Amazon Standard Identification Number
**Format:** 10 alphanumeric characters
**Required:** Optional
**Location:** Book Details metabox

Amazon's unique identifier for your ebook. Kindle books use ASINs instead of ISBNs.

**Example:** "B08ABCD123"

**Where to find:** Your Amazon KDP dashboard or the book's Amazon product page URL.

---

### Goodreads URL
**Purpose:** Link to Goodreads book page
**Format:** Full URL
**Required:** Optional
**Location:** Book Details metabox

Direct link to your book's Goodreads page for ratings, reviews, and adding to shelves.

**Example:** "https://www.goodreads.com/book/show/52578297"

## Publication Details

### Publisher
**Purpose:** Publishing house or publisher name
**Format:** Text
**Required:** Optional
**Location:** Book Details metabox

Name of the publisher or "Self-Published" if you publish independently.

**Examples:**
- "Penguin Random House"
- "Self-Published"
- "Jane Smith Publishing"

---

### Publication Date
**Purpose:** Book's official release date
**Format:** Date (MM/DD/YYYY)
**Required:** Recommended
**Location:** Book Details metabox

The date your book was (or will be) published. Used for sorting and schema markup.

**Example:** "08/29/2020"

**For Coming Soon Books:** Enter future publication date.

---

### Language
**Purpose:** Book's primary language
**Format:** Text or language code
**Required:** Optional
**Location:** Book Details metabox

The language in which the book is written.

**Examples:**
- "English"
- "Spanish"
- "French"
- "en" (language code)

---

### Format
**Purpose:** Physical format of the book
**Format:** Dropdown selection
**Required:** Optional
**Location:** Book Details metabox

**Options:**
- **Hardcover** - Hardbound physical book
- **Paperback** - Softcover physical book
- **eBook** - Digital book (Kindle, ePub, etc.)
- **Audiobook** - Audio narration
- **Board Book** - Thick cardboard pages for young children
- **Mass Market Paperback** - Smaller, cheaper paperback edition

You can create separate book entries for different formats or choose the primary format.

## Physical Specifications

### Page Count
**Purpose:** Total number of pages
**Format:** Integer (number only)
**Required:** Optional
**Location:** Book Details metabox

Total pages in the print edition. Use the longest version if you have multiple formats.

**Example:** "352"

---

### Word Count
**Purpose:** Total words in manuscript
**Format:** Integer (number only)
**Required:** Optional
**Location:** Book Details metabox

Approximate total words. Useful for readers interested in book length.

**Examples:**
- "75000" (average novel)
- "120000" (epic fantasy)
- "50000" (novella)

**Typical ranges:**
- Novella: 17,500-40,000 words
- Standard novel: 70,000-100,000 words
- Epic fantasy: 110,000-150,000+ words

## Series Information

### Series
**Purpose:** Book series assignment
**Format:** Taxonomy selection
**Required:** Optional (for series books)
**Location:** Series metabox

Select the series this book belongs to. For standalone books, leave empty.

**Creating a new series:**
1. Click "+ Add New Series"
2. Enter series name
3. Click "Add New Series"

**Example:** "Harry Potter" series

---

### Series Order
**Purpose:** Book's position in series
**Format:** Integer (number only)
**Required:** Optional (for series books)
**Location:** Series metabox

The sequential number of this book in the series. Critical for displaying books in correct reading order.

**Examples:**
- "1" for first book
- "2" for second book
- "3.5" for a novella between books 3 and 4

## Retailer Links

Add purchase links to major book retailers. Include the full URL with `https://`.

### Amazon URL
**Purpose:** Amazon product page
**Format:** Full URL
**Example:** "https://www.amazon.com/dp/B08ABCD123"

---

### Barnes & Noble URL
**Purpose:** Barnes & Noble product page
**Format:** Full URL
**Example:** "https://www.barnesandnoble.com/w/book-title/1234567890"

---

### Apple Books URL
**Purpose:** Apple Books store link
**Format:** Full URL
**Example:** "https://books.apple.com/us/book/id1234567890"

---

### Kobo URL
**Purpose:** Kobo store link
**Format:** Full URL
**Example:** "https://www.kobo.com/us/en/ebook/book-title"

**Best Practices for Retailer Links:**
- Use direct product URLs, not affiliate links (unless permitted)
- Test links before publishing
- Update if URLs change
- Use all platforms where book is available
- Include country-specific URLs if relevant

## Pricing and Availability

### Price
**Purpose:** Current retail price
**Format:** Decimal number (no $ symbol)
**Required:** Optional
**Location:** Book Details metabox

Current retail price in your primary currency. Enter number only without currency symbol.

**Examples:**
- "9.99" (standard ebook)
- "14.99" (paperback)
- "24.99" (hardcover)
- "0" (free)

**For multiple formats:** Use the paperback or primary edition price.

---

### Status
**Purpose:** Publication/availability status
**Format:** Dropdown selection
**Required:** Yes
**Location:** Publish metabox

**Options:**

**Published** - Book is available for purchase
- Displays publicly on website
- Included in archives and shortcodes
- Full schema markup

**Coming Soon** - Book announced but not yet released
- Displays publicly with "Coming Soon" badge
- Shows expected publication date
- Builds pre-release interest

**Draft** - Work in progress
- Not visible publicly
- Only visible in WordPress admin
- Use while setting up book entry

## Taxonomies

### Categories (Genres)
**Purpose:** Book genres and categories
**Format:** Taxonomy (multiple selection)
**Required:** Recommended
**Location:** Categories metabox

Tag books with relevant genres. Books can have multiple categories.

**Common Categories:**
- Fantasy
- Science Fiction
- Romance
- Mystery / Thriller
- Young Adult
- Literary Fiction
- Non-Fiction
- Historical Fiction
- Horror
- Contemporary

---

### Age Ranges
**Purpose:** Target age group
**Format:** Taxonomy (single selection)
**Required:** Optional
**Location:** Age Ranges metabox

**Standard Age Ranges:**
- 0-2 (Board Books)
- 3-5 (Picture Books)
- 6-8 (Early Readers)
- 9-12 (Middle Grade)
- 13-18 (Young Adult)
- 18+ (Adult)

## Featured Image (Book Cover)

### Book Cover
**Purpose:** Visual representation of your book
**Format:** Image (JPG, PNG, or GIF)
**Required:** Highly recommended
**Location:** Featured Image metabox

The most important visual element. Your book cover sells the book.

**Requirements:**
- Minimum width: 800px (1000px+ recommended)
- Aspect ratio: 2:3 or 6:9 (standard book proportions)
- File format: JPG (best compression) or PNG
- File size: Under 1MB for performance
- High quality, sharp text
- Professional design

[See complete book cover guide](/managing-books/book-cover-images.md)

## Field Completion Tips

### Priority Fields
Fill these first for best results:
1. Title
2. Description
3. Book Cover
4. Author
5. Publication Date
6. ISBN
7. At least one retailer link
8. At least one category

### SEO Fields
These improve search engine visibility:
- Complete description (150-300 words)
- ISBN
- Publisher
- Publication date
- Page count
- Language
- Categories

### Optional But Valuable
- Word count (writers love this)
- ASIN (for Kindle readers)
- Goodreads link (for discovery)
- All retailer links (maximize purchase options)
- Series information (essential for series books)

## Field Validation

AuthorKit validates certain fields automatically:

**Numbers-only fields:**
- Page Count
- Word Count
- Series Order
- Price

**URL fields:**
- Must start with `http://` or `https://`
- Validates URL format

**Date fields:**
- Must use MM/DD/YYYY format

If validation fails, you'll see an error message when saving.

---

**Related Documentation:**
- [Adding Your First Book](/managing-books/adding-your-first-book.md)
- [Book Cover Images](/managing-books/book-cover-images.md)
- [Coming Soon Books](/managing-books/coming-soon-books.md)
- [SEO & Schema](/seo-and-schema.md)

---

*Last Updated: March 7, 2026*
