# Creating Contests

This guide walks you through creating your first book contest in AuthorKit Pro. By the end, you'll have a live contest form ready to collect entries and grow your mailing list.

## Before You Start

**Prerequisites:**
- AuthorKit Pro installed and activated
- Contests module enabled (Settings → AuthorKit → Enable Contests)
- Google Apps Script URL ready (see [Managing Entries](/authorkit-contests/managing-entries.md))
- At least one book created in Books library (optional but recommended)

**Time Required:** 10-15 minutes for first contest

## Step 1: Create New Contest

1. In WordPress admin, go to **Contests → Add New**
2. You'll see the standard WordPress editor with additional metaboxes for contest details

### Contest Title

Enter a descriptive title that tells readers what they can win:

**Good Examples:**
- "Win a Signed Copy of The Silent Echo"
- "$50 Amazon Gift Card Giveaway"
- "Free ARC of My New Mystery Novel"
- "Launch Week Contest - 5 Winners!"

**Avoid:**
- Generic titles like "Book Contest" or "Giveaway #3"
- Titles without prize information
- All caps or excessive punctuation

**Tip:** The title appears in contest grids, archives, and social shares. Make it compelling.

### Contest Description

Use the main editor to write your contest description. This is what visitors see before entering.

**What to Include:**
- What prize(s) can be won
- Who is eligible (age, location restrictions if any)
- How to enter and earn bonus entries
- When the winner will be announced
- Brief book description (if contest is for a specific book)

**Example:**

```
Enter to win a signed paperback copy of my latest mystery novel,
"The Silent Echo"!

**Prize:** One signed copy shipped anywhere in the US

**How to Enter:**
1. Fill out the form below with your name and email
2. Earn bonus entries by sharing on WhatsApp or leaving a review

**Winner Announcement:** March 15, 2026

"The Silent Echo" follows detective Sarah Chen as she investigates
a series of mysterious disappearances in a coastal town. If you love
atmospheric mysteries with strong female leads, you'll love this book!

Good luck!
```

**Tips:**
- Use short paragraphs and bullet points
- Include book cover image (featured image)
- Add excitement without overselling
- Mention any entry requirements clearly

## Step 2: Set Featured Image (Book Cover)

The featured image is used as the book cover in contest displays.

1. Click **Set featured image** in the right sidebar
2. Upload your book cover or select from media library
3. Click **Set featured image**

**Image Guidelines:**
- Minimum size: 600x900px (2:3 ratio for book covers)
- Format: JPG or PNG
- File size: Under 500KB (optimize for web)
- Quality: High resolution, no pixelation

**Tip:** If you've linked a book from your Books library, the book's featured image will be used automatically. The featured image here acts as an override.

## Step 3: Configure Contest Details

Scroll down to the **Contest Details** metabox. This is where you configure all the important settings.

### Book Information

**Select Book:**
- Choose a book from your Books library (dropdown)
- This links the contest to your book metadata
- Book cover, title, and description can be pulled automatically
- Leave unselected if contest is not book-specific (e.g., gift card giveaway)

**Book Cover Override (Optional):**
- Enter a custom image URL if you want to use a different cover
- Leave empty to use the selected book's featured image
- Useful for special edition covers or contest-specific graphics

**Example Use Case:**
You're giving away signed copies with custom stickers. Use the override field to show the special cover variant.

### Contest Dates

**Start Date (Optional):**
- When the contest opens for entries
- Leave empty to start immediately upon publishing
- Useful for scheduling future contests

**End Date (Required):**
- When the contest closes for new entries
- Must be a future date
- Contest status is automatically assigned based on this date:
  - **Upcoming:** Current date before start date
  - **Active:** Current date between start and end dates
  - **Ended:** Current date after end date

**Winner Announcement Date (Optional):**
- When you plan to announce the winner
- Typically 3-7 days after end date (gives time to verify entries)
- Displayed on contest page to set expectations

**Example Timeline:**
- Start: March 1, 2026
- End: March 14, 2026 (2 weeks duration)
- Winner Announcement: March 17, 2026 (3 days to verify)

### Google Apps Script Integration

**Google Apps Script URL:**
- Paste your Web App URL from Google Apps Script setup
- Format: `https://script.google.com/macros/s/AKfycby.../exec`
- This connects contest entries to your Google Sheet
- **Required** for contest form to work

**If you haven't set up Google Apps Script yet:**
1. Follow the complete setup guide: [Managing Entries](/authorkit-contests/managing-entries.md)
2. It takes 10-15 minutes (one-time setup)
3. Copy the Web App URL when finished
4. Paste it here

**Per-Contest vs. Global URL:**
- You can set a global default URL in **Contests → Settings**
- This field overrides the global setting for this specific contest
- Useful if you want different contests saving to different Google Sheets

### Entry Limits

**Maximum Entries (Optional):**
- Limit total number of entries allowed
- Leave empty or set to 0 for unlimited entries
- When limit is reached, form displays "Contest Full" message

**Example Use Cases:**
- Limited prize budget: "First 100 entries only"
- Create urgency: "Only 500 spots available!"
- Beta reader recruiting: "Limited to 50 ARC readers"

**Tip:** Entry limits create scarcity and urgency, often increasing early participation.

### Prize Details

**Prize Amount:**
- Enter numeric value (e.g., `50` for $50)
- Used for gift card contests
- Leave empty if prize is physical item (book, merchandise)

**Prize Currency:**
- Default: ₹ (Indian Rupee) or your site's default currency
- Options: $, £, €, ₹, ¥, etc.
- Only shown if Prize Amount is filled

**Prize Description:**
- Brief description of what winner receives
- Examples:
  - "Signed Paperback Copy"
  - "Amazon Gift Card"
  - "Exclusive Author Merchandise Bundle"
  - "Free ARC + Signed Bookmark"

**Display Example:**
If Prize Amount = `50` and Prize Description = "Amazon Gift Card", contest card shows:
**Prize: $50 Amazon Gift Card**

If only Prize Description = "Signed Paperback", shows:
**Prize: Signed Paperback**

### Contest Rules & Legal

**Contest Terms and Conditions (Optional):**
- Official rules, eligibility requirements, disclaimers
- Displayed as expandable section on contest page
- Important for compliance in some regions

**Example Terms:**

```
Eligibility: Must be 18+ and a resident of the United States.

Prize: One signed paperback copy of "The Silent Echo"
(approximate retail value: $15.99).

Winner Selection: One winner will be selected at random from all
eligible entries on March 17, 2026.

Winner Notification: Winner will be notified by email within 48 hours
and must respond within 7 days to claim prize.

No Purchase Necessary: No purchase or payment required to enter or win.

Privacy: Email addresses will be added to our author newsletter.
You may unsubscribe at any time.
```

**Legal Note:** AuthorKit Contests does not provide legal advice. If running a contest with specific legal requirements (sweepstakes laws, multi-state regulations), consult an attorney.

## Step 4: Configure Entry Form Fields

Scroll to the **Entry Form Configuration** metabox to choose which fields appear on your contest form.

### Available Fields

| Field | Purpose | Default |
|-------|---------|---------|
| **Name** | Collect entrant's name for winner announcement | Enabled |
| **Email** | Required for mailing list and winner notification | Always enabled |
| **Phone** | Phone number (optional, for SMS notifications in future) | Disabled |
| **Rating** | Star rating (1-5 stars) for book reviews | Enabled |
| **Source** | How they heard about the contest (tracking) | Enabled |
| **Review** | Written testimonial or book review | Enabled |

**Email is always required** - you can't disable it since it's essential for contact and mailing list building.

### Field Configuration Options

For each enabled field, you can configure:

**Label:**
- Text shown above the input field
- Default: "Name", "Email", "Phone", etc.
- Customize to match your brand voice

**Placeholder:**
- Hint text inside empty field
- Example: "Enter your full name" or "your@email.com"

**Required:**
- Make field mandatory (checkmark)
- Email is always required
- Recommended: Name (for winner announcement)

**Example Custom Configuration:**

**Name Field:**
- Label: "Your Name"
- Placeholder: "First and last name"
- Required: Yes

**Rating Field:**
- Label: "How would you rate this book?"
- Placeholder: (not applicable for star ratings)
- Required: No

**Review Field:**
- Label: "Why do you want to read this book?"
- Placeholder: "Tell us what excites you about this mystery..."
- Required: No

### Source Field Options

If you enable the "Source" field, you can customize the dropdown options:

**Default Options:**
- Facebook
- Instagram
- Twitter
- Author Newsletter
- Friend Referral
- Amazon
- Goodreads
- Other

**To Customize:**
1. Click **Edit Source Options** (if available in your version)
2. Add/remove/reorder options
3. Use to track which marketing channels drive most entries

**Why Track Source?**
- Identify which social platforms work best
- Measure newsletter effectiveness
- Calculate ROI on paid promotions
- Focus future marketing on high-performing channels

## Step 5: Configure Social Sharing (Bonus Entries)

Scroll to the **Bonus Entry Options** metabox.

### Share Platforms

Select which social platforms offer bonus entries:

- **WhatsApp** (Most popular for authors - high sharing rate)
- **Facebook**
- **Twitter**
- **Instagram** (note: Stories only, can't share direct links)
- **Telegram**

**How It Works:**
1. Visitor enters the contest (gets 1 entry)
2. After submission, they see "Earn Bonus Entries" section
3. Each share link is unique and trackable
4. Clicking a share platform opens pre-filled message with contest link
5. Bonus entry is recorded when someone clicks their shared link

**Recommended Platforms for Authors:**
- **WhatsApp:** Highest conversion (people share with book clubs, friends)
- **Facebook:** Good reach, especially for older demographics
- **Twitter:** Lower conversion but good for author branding
- **Instagram:** Limited (Stories only), better for awareness than entries

### Bonus Entry Configuration

**Entries Per Share:**
- Default: 1 bonus entry per platform
- Some authors set higher values (2-3 entries) to incentivize sharing

**Share Message Template:**
- Pre-filled message for social shares
- Include contest title, prize, and link
- Keep under 280 characters for Twitter compatibility

**Example Share Message:**

```
Enter to win a signed copy of "The Silent Echo" by [Your Name]!
Mystery lovers, don't miss this giveaway.
[CONTEST_LINK]
```

`[CONTEST_LINK]` is automatically replaced with the unique tracking URL.

## Step 6: Configure Winner Announcement (Optional)

If you've already selected a winner, you can add winner details in the **Winner Announcement** metabox.

**When to Use:**
- Contest has ended
- You've selected winner via random selection
- You want to display winner publicly

### Winner Information

**Winner Name (Required):**
- Full name or first name + last initial
- Example: "Sarah Mitchell" or "Sarah M."

**Winner Location (Optional):**
- City, State/Country
- Example: "Portland, OR" or "London, UK"
- Adds authenticity to announcement

**Social Platform:**
- Where winner can be contacted/followed
- Options: Instagram, Facebook, Twitter, LinkedIn, Goodreads
- Shows platform icon next to name

**Social Link/Handle:**
- Winner's profile URL or @username
- Examples:
  - Instagram: `@sarahreadsbooks` or `https://instagram.com/sarahreadsbooks`
  - Twitter: `@sarahmitchell`
  - Facebook: Full profile URL
  - Goodreads: Profile URL

**Winner Announcement Message (Optional):**
- Custom message shown above winner details
- Default: "Congratulations to the winner of [Contest Title]!"
- Personalize: "Huge congrats to Sarah! Check your email for prize details."

### Winner Display

Once winner information is saved:
- Winner announcement appears at top of contest page
- Contest status automatically changes to "Ended"
- Entry form is hidden (no new entries accepted)
- "Active Contests" section appears below winner (promotes other contests)

**Privacy Note:** Only display winner information with their permission. Some winners prefer to remain anonymous.

## Step 7: Display Your Contest

Now that your contest is created, you need to display it on your site.

### Option A: Dedicated Contest Page

Create a new Page (Pages → Add New):

1. Title: "Book Giveaway Contest" or similar
2. Content: Brief intro + shortcode
3. Insert shortcode: `[authorkit_contest id="123"]` (replace 123 with your contest ID)
4. Publish the page

**Example Page Content:**

```
# Win a Signed Copy of The Silent Echo!

I'm giving away signed copies of my latest mystery novel to celebrate
the launch. Enter below for your chance to win!

[authorkit_contest id="456"]
```

### Option B: Homepage Contest Section

Add contest to your homepage or blog:

1. Edit your homepage
2. Add a section titled "Current Giveaway" or "Enter to Win"
3. Insert shortcode: `[authorkit_contest id="123"]`
4. Update page

### Option C: Sidebar Widget

Add contest to sidebar (appears on all pages):

1. Go to **Appearance → Widgets**
2. Add **Custom HTML** widget to desired sidebar
3. Insert shortcode: `[authorkit_contest id="123"]`
4. Save widget

**Note:** Sidebar display works best for simple contests. Complex forms may need full-page width.

### Option D: Contest Grid (Multiple Contests)

Show multiple contests in a grid:

```
[authorkit_contests limit="6" status="active"]
```

**Parameters:**
- `limit`: Number of contests to show (default: all)
- `status`: Filter by status - `active`, `ended`, `upcoming`
- `orderby`: Sort by `date`, `title`, `end_date`
- `order`: `DESC` (newest first) or `ASC` (oldest first)

**Example - Show 3 active contests:**

```
[authorkit_contests limit="3" status="active" orderby="end_date" order="ASC"]
```

### Finding Your Contest ID

**Method 1: Edit Screen**
- Go to **Contests → All Contests**
- Hover over contest title
- Look at URL in browser status bar: `post=456` (456 is the ID)

**Method 2: Edit URL**
- Edit the contest
- Check URL: `post.php?post=456&action=edit` (456 is the ID)

## Step 8: Test Your Contest

Before promoting publicly, test the full entry flow:

### Testing Checklist

**1. Visual Check:**
- [ ] Contest displays correctly on the page
- [ ] Book cover image shows properly
- [ ] Prize details are visible
- [ ] Entry form fields are appropriate

**2. Submit Test Entry:**
- [ ] Fill out the form with test data
- [ ] Submit the entry
- [ ] Verify success message appears
- [ ] Check Google Sheet for new entry row

**3. Bonus Entry Test:**
- [ ] After submission, verify "Earn Bonus Entries" section appears
- [ ] Click a share platform link
- [ ] Verify pre-filled message is correct
- [ ] Check that unique tracking link works

**4. Entry Counter Test:**
- [ ] Note current entry count
- [ ] Submit a test entry
- [ ] Refresh page
- [ ] Verify counter increased by 1

**5. Mobile Test:**
- [ ] View contest on mobile device
- [ ] Test form submission on mobile
- [ ] Verify bonus sharing works on mobile

**Troubleshooting Common Issues:**

**Form doesn't submit:**
- Verify Google Apps Script URL is correct and ends with `/exec`
- Check that script is deployed as "Web app" with "Anyone" access
- Test script directly: Visit `YOUR_URL?action=getCount` (should return JSON)

**Entry doesn't appear in Google Sheet:**
- Check Spreadsheet ID in script matches your sheet
- Verify both `doGet` and `doPost` functions use same Spreadsheet ID
- Check Apps Script execution logs for errors

**Counter shows 0 despite entries:**
- Verify `doGet` function has correct Spreadsheet ID
- Test counter endpoint: `YOUR_URL?action=getCount`
- Check that sheet has header row (script creates on first entry)

## Step 9: Promote Your Contest

Your contest is live. Now drive traffic to it.

### Social Media Promotion

**Facebook:**
- Share contest page link
- Post in relevant book groups
- Pin post to top of your page
- Use eye-catching book cover image

**Instagram:**
- Story swipe-up (if you have 10k+ followers)
- Link in bio
- Reel showcasing the prize
- Stories with countdown sticker

**Twitter:**
- Pin tweet with contest link
- Use relevant hashtags (#bookgiveaway #amreading)
- Tag book community accounts
- Thread explaining how to enter

**BookBub, Goodreads:**
- List contest in giveaway sections
- Share in book club groups
- Engage with readers discussing the genre

### Email Newsletter

Send dedicated email to your list:

**Subject Lines:**
- "Enter to Win [Book Title]"
- "Free Book Giveaway - 5 Winners!"
- "Launch Week Contest Inside"

**Email Content:**
- Clear call-to-action button/link
- Prize details and value
- Deadline to enter
- Easy sharing options

### Author Website

- Homepage banner or hero section
- Blog post announcement
- Footer callout on all pages
- Exit intent popup (advanced)

### Paid Promotion (Optional)

- Facebook Ads to contest page (target book readers)
- BookBub Featured Deals (include contest mention)
- Amazon Ads (link to contest in author bio)

**Budget Tip:** Start with organic promotion. Add paid promotion if you're not hitting entry goals by week 1.

## Best Practices

### Contest Duration

**Optimal Length:**
- **2 weeks:** Standard duration, builds momentum
- **1 week:** Quick burst, great for launch week
- **30 days:** Long-term email list building
- **48 hours:** Flash contest for urgency

**Avoid:**
- Under 24 hours (not enough time to spread)
- Over 60 days (participants forget, lose interest)

### Prize Selection

**Most Effective Prizes for Authors:**
1. Signed books (physical connection, exclusive)
2. Amazon gift cards ($25-$50 range)
3. Book bundles (entire series)
4. Exclusive merchandise (bookmarks, tote bags)
5. ARC access (for super fans)

**Less Effective:**
- Ebooks only (low perceived value for contest)
- Non-book-related prizes (attracts wrong audience)
- Generic prizes (iPad, etc. - you want readers, not bargain hunters)

### Entry Form Optimization

**Keep It Simple:**
- Only collect data you'll actually use
- Required fields: Email + Name only
- Optional fields: 2-3 maximum
- Short review field (100-200 characters)

**Why Less Is More:**
- Higher completion rates
- Less friction = more entries
- Easier to manage winner selection

### Timing Your Contest

**Best Times to Launch:**

**Pre-Launch (2-4 weeks before release):**
- Build buzz before book is available
- Collect email list for launch day
- Generate pre-orders via contest hype

**Launch Week:**
- Maximize release week visibility
- Encourage reviews (bonus entry for review)
- Celebrate with your readers

**Mid-List Promotion:**
- Re-engage readers between releases
- Keep mailing list active
- Test new book ideas via survey questions

**Avoid:**
- Major holidays (people are busy)
- Same time as major releases in your genre
- When you're unavailable to manage it

## Advanced Features

### Multiple Winners

To select multiple winners:

1. Use Google Sheets `RANDBETWEEN` multiple times
2. Record all winners in Winner Announcement section
3. Display as "5 Winners Selected!"
4. List all names (or just count if anonymous)

### Recurring Contests

Run monthly contests to build list consistently:

1. Create template contest with standard fields
2. Duplicate for each month
3. Update prize and dates
4. Set up automatic social promotion schedule

### Integration with Email Services

Connect entries to your email platform:

**Via Zapier:**
1. Trigger: Google Sheets - New Row
2. Action: Add subscriber to MailChimp/ConvertKit/etc.
3. Map email field to subscriber email
4. Add tags: "Contest Entry - [Month]"

**See:** [Email Notifications](/authorkit-contests/email-notifications.md) for detailed integration guides

## Next Steps

Now that your contest is created:

1. **Monitor Entries** - Check Google Sheet daily
2. **Engage Participants** - Like/reply to social shares
3. **Update Entry Count** - Share milestones ("100 entries!")
4. **Plan Winner Selection** - Review [Winner Selection](/authorkit-contests/winner-selection.md)
5. **Set Up Email Confirmations** - See [Email Notifications](/authorkit-contests/email-notifications.md)

## Related Documentation

- **[Overview](/authorkit-contests/overview.md)** - Learn why contests work for authors
- **[Managing Entries](/authorkit-contests/managing-entries.md)** - Google Apps Script setup
- **[Winner Selection](/authorkit-contests/winner-selection.md)** - How to pick and announce winners
- **[Email Notifications](/authorkit-contests/email-notifications.md)** - Automate entry confirmations
- **[Developer Guide](/authorkit-contests/developer-guide.md)** - Customize with code

---

**Need Help?**

- [AuthorKit Support](https://authorkit.pro/support)
- [FAQ](https://docs.authorkit.pro/getting-started/faq)
- [Common Issues](https://docs.authorkit.pro/troubleshooting/common-issues)

---

*Last Updated: April 4, 2026*
