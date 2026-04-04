# AuthorKit Contests Overview

## What is AuthorKit Contests?

AuthorKit Contests is a Pro module that helps authors run professional book giveaways and contests directly from their WordPress site. Unlike generic contest plugins, it's built specifically for authors who want to grow their mailing list, build buzz before a book release, and engage readers during launches.

**Key Features:**

- **Secure Google Sheets Integration** - Entries are saved to your Google Sheet via Google Apps Script, protecting your WordPress database from bot attacks and malware
- **Customizable Entry Forms** - Collect name, email, phone, ratings, reviews, and bonus entry sources
- **Email List Building** - Capture verified email addresses for your mailing list (MailChimp, ConvertKit, etc. via Zapier)
- **Automated Entry Counting** - Real-time entry counter fetches totals from your Google Sheet
- **Bonus Entry System** - Award extra entries for social shares, reviews, or referrals
- **Winner Selection Tools** - Export entries and use random selection methods to pick winners fairly
- **Multiple Display Options** - Show contests via shortcodes, widgets, or archive pages
- **GDPR Compliant** - Built-in consent checkboxes and privacy policy links

## Why Authors Need Contests

### 1. Grow Your Email List

Book contests are proven email list builders. Readers happily provide their email in exchange for a chance to win:
- Free signed copies of your new release
- Gift cards (Amazon, Barnes & Noble)
- Exclusive merchandise
- Early access to advance reader copies (ARCs)

**Result:** Build a targeted email list of engaged readers who actually want to hear from you.

### 2. Build Buzz Before Release

Running a contest 2-4 weeks before your book launch creates:
- Social media conversations about your upcoming release
- Word-of-mouth marketing from participants sharing with friends
- Reviews and testimonials before launch day
- A pool of potential launch team members

**Result:** Enter launch day with momentum and an audience primed to buy.

### 3. Engage Readers During Launch

Launch week contests encourage readers to:
- Leave reviews on Amazon/Goodreads
- Share your book on social media
- Tell friends about your new release
- Join your reader community

**Result:** Higher visibility on retailer algorithms and more organic reach.

### 4. Collect Reader Testimonials

Contest forms can include fields for:
- Star ratings (1-5 stars)
- Written reviews
- What readers loved most about your book
- Reader demographics (age, genre preferences)

**Result:** Authentic testimonials you can use in future marketing.

## How It Works

### For Authors (You)

1. **Create a Contest** - Add a new contest in WordPress (Contests → Add New)
2. **Set Up Google Sheet** - Follow the simple setup guide to connect a Google Sheet
3. **Configure Entry Form** - Choose which fields to collect (email required, others optional)
4. **Display on Your Site** - Use shortcodes to show the contest form anywhere
5. **Monitor Entries** - Watch entries flow into your Google Sheet in real-time
6. **Select Winner** - Use random selection tools when the contest ends
7. **Announce Winner** - Update the contest to display winner details

### For Readers (Your Visitors)

1. **Find Contest** - Visit your contest page or see the form on your homepage
2. **Enter Details** - Fill out a simple form (name, email, optional review)
3. **Earn Bonus Entries** - Share on WhatsApp/Facebook for extra entries
4. **See Entry Count** - Watch the total entries increase (builds excitement)
5. **Wait for Winner** - Check back after contest ends to see who won

## Security First: Why Google Sheets?

AuthorKit Contests uses **Google Apps Script** instead of saving entries directly to your WordPress database. Here's why:

**Security Benefits:**
- **No Direct Database Access** - Bots can't inject malware or spam into your WordPress database
- **Rate Limiting** - Google automatically limits submission rates to prevent abuse
- **Isolated Data** - Contest entries live separately from your WordPress core
- **Easy to Clean** - Delete spam entries in Google Sheets without touching your database

**Practical Benefits:**
- **You Own the Data** - Your Google Sheet, your data, forever
- **Easy Analysis** - Use Google Sheets tools to filter, sort, and analyze entries
- **Automatic Backup** - Google Drive handles backups automatically
- **Team Collaboration** - Share the sheet with assistants for winner selection

**Simple Setup:**
- Takes 10-15 minutes (one-time setup per contest)
- No coding required - we provide the complete script
- Copy-paste configuration with step-by-step guide
- See [Managing Entries](/authorkit-contests/managing-entries.md) for complete setup instructions

## Key Features in Detail

### Customizable Entry Forms

Choose exactly which information to collect:

| Field | Purpose | Required? |
|-------|---------|-----------|
| Name | Winner announcement | Optional (recommended) |
| Email | Mailing list, winner notification | Required |
| Phone | SMS notifications (future) | Optional |
| Rating | Book rating (1-5 stars) | Optional |
| Source | Track where they heard about contest | Optional |
| Review | Collect testimonials | Optional |

### Bonus Entry System

Encourage social sharing by offering bonus entries:
- Share on WhatsApp (most popular for authors)
- Share on Facebook
- Share on Twitter
- Share on Instagram Stories
- Refer a friend (custom tracking link)

Each bonus action generates a unique tracking link to prevent abuse.

### Entry Counter Display

Show real-time entry counts on your contest page:
- Fetches current total from Google Sheet
- Updates every page load
- Builds urgency ("347 entries and counting!")
- Encourages more people to enter

### Winner Selection

Multiple methods supported:
- Google Sheets `RANDBETWEEN` function
- Third-party tools (random.org, wheel spinner)
- Export to CSV and use external tools
- Built-in duplicate email detection

See [Winner Selection](/authorkit-contests/winner-selection.md) for detailed methods.

### Display Options

Show contests anywhere on your site:

**Single Contest:**
```
[authorkit_contest id="123"]
```

**Contest Grid (6 contests):**
```
[authorkit_contests limit="6" status="active"]
```

**Full Archive:**
```
[authorkit_contest_archive]
```

See [Developer Guide](/authorkit-contests/developer-guide.md) for all shortcode options.

## Who Should Use AuthorKit Contests?

### Perfect For:

- **Launching a new book** - Build buzz 2-4 weeks before release
- **Growing an email list** - Turn website visitors into subscribers
- **Engaging existing readers** - Keep your community active between releases
- **Collecting reviews** - Gather testimonials for future book promotions
- **Building a launch team** - Find readers willing to review and share

### Not Ideal For:

- **One-time standalone giveaways** - Better to use Instagram/Facebook native contests if you don't need the mailing list integration
- **Physical product stores** - AuthorKit is built for authors, not general eCommerce
- **Sweepstakes requiring legal compliance** - This tool doesn't handle official sweepstakes rules/disclaimers

## AuthorKit Contests vs. Generic Plugins

| Feature | AuthorKit Contests | Generic Contest Plugins |
|---------|-------------------|------------------------|
| **Built for Authors** | Book-specific features (link to Books library, cover images, reviews) | Generic products |
| **Security** | Google Sheets (no direct DB access) | WordPress database (vulnerable to spam/bots) |
| **Email List Focus** | Designed for author mailing lists | Generic lead capture |
| **Book Integration** | Links to Books module, pulls metadata | No book awareness |
| **Testimonial Collection** | Star ratings, written reviews | Basic text fields |
| **Setup Complexity** | 10-15 min one-time setup | Immediate but less secure |

## Pro-Only Module

AuthorKit Contests is included in **AuthorKit Pro** only. It's not available in the free Core plugin.

**Why Pro?**
- Advanced features require ongoing development and support
- Google Sheets integration needs detailed documentation
- Bonus entry tracking requires server resources
- Winner announcement system uses custom templates

**[View AuthorKit Pro Pricing](https://authorkit.pro/pricing)**

## Real-World Use Cases

### Case 1: Pre-Launch Buzz

**Scenario:** Sarah is launching her mystery novel "The Silent Echo" in 3 weeks.

**Contest Setup:**
- **Prize:** 5 signed paperback copies
- **Entry Form:** Name, email, favorite mystery subgenre
- **Bonus Entries:** Share on WhatsApp, leave a review on Goodreads
- **Duration:** 2 weeks (ends 1 week before launch)

**Results:**
- 437 entries in 2 weeks
- 312 new email subscribers (71% conversion)
- 28 pre-launch reviews on Goodreads
- 89 social shares generating 1,200+ impressions

### Case 2: Email List Growth

**Scenario:** Mike has a website but no email list. He wants to build one.

**Contest Setup:**
- **Prize:** $50 Amazon gift card
- **Entry Form:** Name, email, genre preferences
- **Bonus Entries:** Share on Facebook, follow on Instagram
- **Duration:** 30 days (ongoing promotion)

**Results:**
- 623 entries in 30 days
- 595 new email subscribers (95% conversion)
- 156 new Instagram followers
- Monthly recurring contest builds consistent list growth

### Case 3: Launch Day Engagement

**Scenario:** Emma is launching today and wants maximum first-day sales.

**Contest Setup:**
- **Prize:** Free signed copy + $25 bookstore gift card
- **Entry Form:** Name, email, Amazon review screenshot
- **Bonus Entries:** Share purchase on social media
- **Duration:** 48 hours (launch weekend only)

**Results:**
- 89 entries in 48 hours
- 76 Amazon reviews in first 2 days
- Book hit #3 in category due to sales velocity
- Launch team of 89 readers willing to promote future releases

## Getting Started

Ready to run your first contest?

1. **Ensure AuthorKit Pro is active** - Contests module must be enabled in Settings
2. **Create a Google Sheet** - Follow [Managing Entries](/authorkit-contests/managing-entries.md) setup guide
3. **Create Your First Contest** - See [Creating Contests](/authorkit-contests/creating-contests.md)
4. **Configure Entry Form** - Choose which fields to collect
5. **Display on Your Site** - Add shortcode to a page or post
6. **Test It** - Submit a test entry and verify it appears in your Google Sheet
7. **Promote** - Share contest link on social media, newsletters, etc.

## Next Steps

- **[Managing Entries](/authorkit-contests/managing-entries.md)** - Complete Google Apps Script setup guide
- **[Creating Contests](/authorkit-contests/creating-contests.md)** - Step-by-step contest creation
- **[Winner Selection](/authorkit-contests/winner-selection.md)** - How to pick and announce winners
- **[Email Notifications](/authorkit-contests/email-notifications.md)** - Set up entry confirmations
- **[Developer Guide](/authorkit-contests/developer-guide.md)** - Hooks, filters, and customization

---

**Need Help?**

- [AuthorKit Support](https://authorkit.pro/support)
- [FAQ](https://docs.authorkit.pro/getting-started/faq)
- [Common Issues](https://docs.authorkit.pro/troubleshooting/common-issues)

---

*Last Updated: April 4, 2026*
