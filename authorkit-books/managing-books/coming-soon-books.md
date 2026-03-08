# Coming Soon Books

## What are Coming Soon Books?

Coming Soon books are upcoming releases that you want to announce and promote before publication. They appear publicly on your website with special "Coming Soon" status, letting readers discover and anticipate your new book while you're still preparing for launch.

## Why Use Coming Soon Status?

### Build Anticipation
Announce your book early to generate excitement and build a reader following before release day.

### Collect Interest
Gauge reader interest through social shares, email signups, and pre-order conversions.

### SEO Advantage
Start ranking in search engines months before publication, building discoverability early.

### Marketing Preparation
Share your upcoming book on social media, in email newsletters, and on your website to prime your audience.

## Setting Up a Coming Soon Book

### Step 1: Create the Book Entry

1. Go to **Books > Add New**
2. Enter title, description, and book details
3. Upload book cover (use preliminary cover if final isn't ready)
4. Fill in available metadata fields

Even without final details, set up the entry with what you know.

### Step 2: Set Status to Coming Soon

In the **Publish** metabox (right sidebar):

1. Click **Edit** next to Status
2. Select **Coming Soon** from dropdown
3. Enter future **Publication Date** in the Book Details metabox
4. Click **Publish**

Your book is now live with Coming Soon status.

### Step 3: Add Pre-Order Links

If you have pre-order links available:

1. Add Amazon pre-order URL
2. Add other retailer pre-order links
3. Consider adding "Pre-Order Now" button text in description

These links will display as "Pre-Order" instead of "Buy Now" when status is Coming Soon.

## What Visitors See

### Coming Soon Badge
Books marked as Coming Soon display a special badge or indicator on:
- Book cards in grids
- Single book pages
- Archive pages
- Shortcode displays

### Publication Date
The expected publication date displays prominently, letting readers know when to expect release.

### Pre-Order Links
If you've added retailer URLs, they appear as "Pre-Order" buttons instead of standard purchase links.

### Full Book Information
Readers can see all the book details you've entered, just like a published book, but with Coming Soon indicators.

## Best Practices

### Timing

**Announce 3-6 Months Early:**
- Gives time to build anticipation
- Allows for pre-order period
- Provides marketing runway

**Don't Announce Too Early:**
- Avoid announcing years in advance
- Wait until you have a confirmed release date
- Be realistic with timelines

### Information to Include

**Minimum Required:**
- Title
- Description/synopsis
- Book cover (even if preliminary)
- Expected publication date
- Genre/categories

**Recommended:**
- Author note about the book
- Series information if applicable
- Pre-order links when available
- Goodreads link to add to "Want to Read"

**Optional:**
- Excerpt or first chapter
- Cover reveal story
- Behind-the-scenes content
- Character descriptions

### Update Regularly

Keep Coming Soon books current:

**Cover Updates:**
If your cover changes, update it immediately.

**Description Refinement:**
Update synopsis as you finalize the story.

**Pre-Order Links:**
Add retailer links as soon as pre-orders go live.

**Publication Date Changes:**
Update dates promptly if timeline shifts.

## Schema Markup

Coming Soon books include special schema.org markup:

### Book Availability
- `availabilityStarts`: Publication date
- `itemCondition`: NewCondition
- `availability`: PreOrder (if pre-orders available)

### Publication Status
- Schema indicates upcoming/announced status
- Search engines understand release timeline
- Can appear in "upcoming releases" searches

This helps search engines properly index your upcoming books and can qualify for special search features.

## Marketing Your Coming Soon Books

### Homepage Feature

Add to your homepage:
```
[authorkit_book id="123"]
```

The Coming Soon badge automatically displays.

### Coming Soon Page

Create a dedicated page:
```
## Upcoming Releases

[authorkit_books status="coming-soon"]
```

Shows all your upcoming books.

### Email Newsletter

Include in newsletter:
- Book cover image
- Brief description
- Publication date
- Pre-order link

Link to your book page for full details.

### Social Media

Share announcements:
- Cover reveal posts
- Publication date announcement
- Pre-order launch
- Chapter excerpts
- Countdown posts

Link back to your book page for traffic and SEO.

### Blog Posts

Write posts about:
- Book inspiration
- Character development
- Research process
- Cover design story
- Writing journey

Each post can link to the Coming Soon book page.

## Converting to Published

When your book releases:

### Step 1: Update Book Details

1. Edit the book
2. Verify all information is accurate
3. Update description if needed
4. Replace preliminary cover with final cover
5. Add final retailer links (not pre-order links)

### Step 2: Change Status

1. In **Publish** metabox, change status to **Published**
2. Verify **Publication Date** is set to actual release date
3. Click **Update**

### Step 3: Announce the Release

- Update social media
- Send email to newsletter subscribers
- Update homepage feature
- Write launch blog post

Your book now appears as fully published with purchase links.

## Shortcodes with Coming Soon Books

### Show Only Coming Soon

```
[authorkit_books status="coming-soon"]
```

Displays only upcoming books.

### Include Coming Soon in General Display

```
[authorkit_books status="published,coming-soon"]
```

Shows both published and upcoming books.

### Exclude Coming Soon

```
[authorkit_books status="published"]
```

Shows only available books (default behavior).

## FAQs

### Can I have pre-orders without Coming Soon status?
Yes. You can keep status as Published and simply add pre-order links. Coming Soon is optional but provides better UX.

### What if my publication date changes?
Update the Publication Date field anytime. Changes reflect immediately on your website.

### Should I include ISBN before publication?
If you have it, yes. But it's okay to add it later when received from your publisher or ISBN agency.

### Can readers purchase Coming Soon books?
Readers can pre-order if you provide pre-order links. Otherwise, Coming Soon indicates the book isn't available yet.

### How long should I leave Coming Soon status?
Change to Published on release day. Don't leave as Coming Soon after publication.

### Does Coming Soon count toward book limits?
Yes. Coming Soon books count toward the 10-book limit on free tier.

## Examples

### New Series Announcement

```
I'm thrilled to announce my new fantasy trilogy!

The first book, The Dragon's Awakening, releases March 2027.

[authorkit_book id="456"]

Join my newsletter for exclusive excerpts and updates!
```

### Pre-Order Launch

```
Pre-orders are now live for my upcoming thriller!

Reserve your copy today and be among the first to read it.

[authorkit_book id="789"]
```

### Multiple Upcoming Books

```
## Coming in 2027

I have three exciting releases planned this year:

[authorkit_books status="coming-soon" orderby="date" order="ASC"]

Subscribe to stay updated on all release dates!
```

## Troubleshooting

**Coming Soon badge doesn't show:**
- Verify status is set to "Coming Soon" not "Published"
- Clear browser cache
- Clear WordPress cache if using caching plugin

**Book shows as Published:**
- Check status in Publish metabox
- Ensure changes were saved
- Refresh page to see updates

**Pre-order links say "Buy Now":**
- Theme/template may not differentiate
- Customize button text in description
- Consider adding custom CSS

**Publication date doesn't display:**
- Enter date in **Publication Date** field (Book Details metabox)
- Use MM/DD/YYYY format
- Save and refresh

---

**Related Documentation:**
- [Book Meta Fields](/managing-books/book-meta-fields.md)
- [Adding Your First Book](/managing-books/adding-your-first-book.md)
- [Shortcodes Overview](/shortcodes/overview.md)
- [SEO & Schema](/seo-and-schema.md)

---

*Last Updated: March 7, 2026*
