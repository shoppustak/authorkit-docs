# Winner Selection

This guide walks you through selecting and announcing contest winners fairly and transparently. Learn how to access entries, pick random winners, verify eligibility, and make the announcement.

## Overview

After your contest ends, you need to:

1. Access all contest entries
2. Select winner(s) randomly
3. Verify winner eligibility
4. Contact the winner
5. Announce publicly (optional)

**Time Required:** 15-30 minutes depending on entry count

## Step 1: Access Contest Entries

Your contest entries are stored in your Google Sheet. There are two ways to access them:

### Method A: Direct Google Sheet Access

1. Open your Google Sheet (the one you created during [Managing Entries](/authorkit-contests/managing-entries.md) setup)
2. All entries appear as rows with these columns:
   - Entry Number
   - Name
   - Email
   - Phone (if collected)
   - Rating (if collected)
   - Source (if collected)
   - Review (if collected)
   - Timestamp
   - Date Submitted

**Tip:** The header row has a purple background. Entry #1 is row 2 in the sheet.

### Method B: WordPress Admin Entries Page

1. In WordPress, go to **Contests → Entries**
2. Select your contest from the dropdown
3. View entries in a filterable table
4. Export to CSV if needed

**Note:** This requires the Entries page to be implemented. If not available in your version, use Method A (Google Sheet).

### Review Entry Data

Before selecting a winner, review the entries:

**Check for:**
- Duplicate entries (same email multiple times)
- Fake/spam entries (gibberish names, invalid emails)
- Incomplete entries (missing required fields)
- Test entries you submitted during testing

**Common Red Flags:**
- Email: `test@test.com`, `asdf@asdf.com`, `admin@domain.com`
- Name: "Test", "Asdfgh", keyboard mashing
- Review: Copy-pasted spam or promotional content
- Timestamp: Multiple entries from same IP in seconds (check Apps Script logs)

## Step 2: Clean Up Invalid Entries

Remove spam and test entries before winner selection.

### In Google Sheets:

1. **Identify invalid entries** - Look for the red flags above
2. **Right-click the row number** - Select entire row
3. **Delete row** - Right-click → Delete row
4. **Save** - Changes are automatic in Google Sheets

**Important:** Do NOT delete the header row (row 1). Only delete data rows (row 2 and below).

### Handle Duplicate Entries

If someone entered multiple times with the same email:

**Option 1: Keep All (Default)**
- Each entry is separate (they may have earned bonus entries)
- Fair if they legitimately shared on multiple platforms
- Google Sheets will handle random selection

**Option 2: Keep First Entry Only**
1. Sort by Email (Data → Sort sheet by column → Email)
2. Identify duplicate emails
3. Delete duplicate rows, keeping only the first entry
4. Re-sort by Entry Number to restore order

**Recommendation:** Keep all entries unless contest rules explicitly state "one entry per person." Bonus entries are meant to allow multiple chances.

## Step 3: Select Winner Randomly

There are several methods to pick a winner fairly. Choose the one you're most comfortable with.

### Method A: Google Sheets RANDBETWEEN Function (Recommended)

This is the simplest method and uses Google's built-in randomization.

**Steps:**

1. **Count Total Entries** - Note the last row number (e.g., row 125 = 124 entries, since row 1 is the header)
2. **Open your Google Sheet**
3. **Click an empty cell** (e.g., cell K2)
4. **Enter this formula:**
   ```
   =RANDBETWEEN(2, 125)
   ```
   Replace `125` with your last row number
5. **Press Enter** - A random number appears (e.g., 47)
6. **Find that row** - Row 47 is your winner
7. **Record winner details** - Copy their name, email, and entry number

**Example:**

If the formula returns `47`, scroll to row 47. The entry there is:
- Entry Number: 46 (row 2 is entry 1)
- Name: Sarah Mitchell
- Email: sarah@email.com
- This is your winner!

**Tip:** Press F9 (or Cmd+Shift+R on Mac) to recalculate and get a new random number if you need to pick multiple winners.

### Method B: Random.org

Use an independent third-party random number generator for full transparency.

**Steps:**

1. Count total entries (e.g., 124 entries)
2. Visit [Random.org](https://www.random.org/integers/)
3. Configure:
   - **Min:** 1
   - **Max:** 124 (your total entry count)
   - **Quantity:** 1 (or number of winners needed)
4. Click **Generate**
5. Note the random number (e.g., 47)
6. Find entry #47 in your Google Sheet (row 48, since row 1 is header and row 2 is entry #1)

**Advantage:** Third-party generator adds credibility and can be screenshot for transparency.

### Method C: Wheel Spinner

Visual method that's great for live announcements on social media.

**Steps:**

1. Export entries to list of names:
   - Select the Name column in Google Sheets (column B)
   - Copy all names (excluding header)
2. Visit [Wheel of Names](https://wheelofnames.com/) or similar spinner tool
3. Paste names into the wheel
4. Spin the wheel
5. Record or screenshot the winner

**Advantage:** Visual and engaging. Great for live Instagram/Facebook winner announcements.

**Disadvantage:** Can be slow with 100+ entries. Better for smaller contests (under 50 entries).

### Method D: Spreadsheet Randomization

Randomize the entire sheet, then pick the first entry.

**Steps:**

1. **Add random number column:**
   - Click cell J1 and type "Random"
   - In J2, type `=RAND()`
   - Drag the formula down to all rows
2. **Sort by random column:**
   - Select all data (A1:J125)
   - Data → Sort range → Sort by column J (Random)
3. **Winner is row 2** (first entry after header)
4. **Record winner details**

**Note:** This changes your entry order. Consider making a copy first (File → Make a copy).

## Step 4: Select Multiple Winners

If your contest has multiple prizes (e.g., "5 winners will each receive a signed copy"):

### Option 1: Repeat RANDBETWEEN

1. Use `=RANDBETWEEN(2, 125)` and record first winner
2. **Mark winner row** with a color or note
3. Run formula again for second winner
4. If it returns the same number, run again until you get a different winner
5. Repeat for all winners

### Option 2: Random.org Multiple Numbers

1. Visit Random.org
2. Set **Quantity** to 5 (for 5 winners)
3. Click Generate
4. You get: 47, 12, 89, 103, 56
5. Find entries 47, 12, 89, 103, and 56 in your sheet

### Option 3: Randomize and Pick Top N

1. Use Method D (Spreadsheet Randomization)
2. After sorting randomly, pick rows 2-6 (5 winners)
3. Record all winner details

## Step 5: Verify Winner Eligibility

Before announcing, verify the winner is legitimate and eligible.

### Check Eligibility Requirements

Review your contest terms and verify:

**Common Requirements:**
- [ ] Age (18+, 21+, etc.)
- [ ] Location (US residents only, worldwide, etc.)
- [ ] Entry date (submitted before contest end date)
- [ ] Complete entry (all required fields filled)

**How to Verify:**

**Age:**
- Usually based on honor system
- Can ask winner to confirm they meet age requirement

**Location:**
- Check email domain (.uk, .ca, etc.) or phone country code
- Ask winner to confirm address when sending prize

**Entry Date:**
- Check Timestamp column in Google Sheet
- Verify it's before contest end date/time

**Complete Entry:**
- Verify Name and Email are filled
- If required fields were mandatory, this is automatic

### Contact Winner Privately First

**Before public announcement:**

1. **Send email to winner** using the email from their entry
2. **Subject:** "Congratulations! You won [Contest Name]"
3. **Include:**
   - Confirmation they won
   - Prize details
   - Next steps (provide shipping address, confirm eligibility)
   - Deadline to respond (typically 48-72 hours)
   - Your contact information

**Example Email:**

```
Subject: Congratulations! You won the "Silent Echo" Book Giveaway

Hi Sarah,

Congratulations! You're the winner of our book contest for "The Silent Echo"!

Prize: One signed paperback copy

To claim your prize, please reply to this email within 48 hours with:
- Your full shipping address
- Confirmation you're 18+ and a US resident (per contest terms)

If I don't hear from you by [Date], I'll select an alternate winner.

Looking forward to getting your signed copy to you!

Best,
[Your Name]
```

### Handle Non-Responsive Winners

If winner doesn't respond within deadline:

1. **Send one reminder email** after 48 hours
2. **Wait additional 24 hours**
3. **If still no response**, select an alternate winner:
   - Run random selection again (exclude original winner)
   - Contact new winner
4. **Document the change** (for transparency if needed)

### Alternate Winner Selection

To select backup winner(s) in case first winner doesn't respond:

1. **At time of original selection**, pick 1-2 alternate winners
2. **Don't contact them yet**
3. **If first winner doesn't claim prize**, contact first alternate
4. **Repeat if needed**

**Tip:** Always have at least one backup winner identified before announcement.

## Step 6: Announce the Winner

Once winner has responded and confirmed eligibility, make the public announcement.

### Method A: Update Contest in WordPress

1. Go to **Contests → All Contests**
2. Edit your contest
3. Scroll to **Winner Announcement** metabox
4. Fill in:
   - **Winner Name:** "Sarah Mitchell" (or "Sarah M." for privacy)
   - **Winner Location:** "Portland, OR" (optional)
   - **Social Platform:** Instagram (if they shared their handle)
   - **Social Link/Handle:** @sarahreadsbooks
   - **Announcement Message:** "Congratulations Sarah! Check your email for prize details."
5. Click **Update**

**Result:** Winner announcement appears at the top of your contest page, and the entry form is hidden.

### Method B: Social Media Announcement

Share the winner on your social platforms:

**Facebook/Instagram Post:**

```
CONTEST WINNER ANNOUNCEMENT

Congratulations to Sarah Mitchell from Portland, OR!

Sarah won our "Silent Echo" book giveaway. We're sending a signed copy her way!

Thank you to everyone who entered - we had [X] entries and it was so hard to choose!

Stay tuned for our next giveaway coming soon.
```

**Twitter/X:**

```
WINNER 🎉

Congrats to Sarah Mitchell (@sarahreadsbooks) who won our #TheSilentEcho giveaway!

Thanks to all [X] people who entered. Next contest coming soon!
```

**Email Newsletter:**

```
Subject: Book Contest Winner Announced!

Our recent contest winner is... Sarah Mitchell!

Congratulations Sarah! Your signed copy of "The Silent Echo" is on its way.

Thank you to the [X] readers who entered. Your support means the world to me.

Didn't win this time? Don't worry - I'm planning another giveaway for [next month/next book]. Stay subscribed to be the first to know!
```

### Privacy Considerations

**Get Winner's Permission:**
- Ask winner if they're comfortable being named publicly
- Offer options: Full name, first name + last initial, or anonymous
- Respect their preference

**Anonymous Announcement:**

```
Congratulations to our winner from Portland, OR!

We had [X] entries and selected the winner randomly.
Thank you all for participating!
```

**What to Share:**
- Winner's first name (minimum)
- City/State (optional, adds credibility)
- Social handle (only with permission)

**What NOT to Share:**
- Full email address
- Phone number
- Detailed address
- Personal information beyond what they consented to

## Step 7: Export Winner Data

Keep a record of your contest results for future reference.

### Export from Google Sheets

1. Open your Google Sheet
2. **File → Download → CSV (.csv)**
3. Save with descriptive name: `silent-echo-contest-entries-march-2026.csv`
4. Store in a secure location

**Alternative:** Make a copy of the sheet and archive it (File → Make a copy → Rename with date).

### What to Record

For each contest, save:
- Contest name and dates
- Total entries received
- Winner name and email
- Runner-up names (if applicable)
- Date winner was contacted
- Date winner responded
- Date prize was sent
- Any issues or notes

**Example Record:**

```
Contest: Silent Echo Book Giveaway
Dates: March 1-14, 2026
Total Entries: 437
Winner: Sarah Mitchell (sarah@email.com)
Contacted: March 15, 2026
Responded: March 15, 2026
Prize Sent: March 17, 2026
Notes: Winner very excited, posted review on Goodreads unprompted
```

### Why Keep Records

- **Future contests:** Learn what worked (entry counts, best platforms)
- **Legal protection:** Prove contest was run fairly if questioned
- **Tax purposes:** Prize values may be deductible business expenses
- **Relationship building:** Follow up with past winners for launch teams

## Best Practices

### Transparency

**Build Trust with Participants:**
- Announce winner within promised timeframe
- Be clear about selection method (random)
- Screenshot random number generator (optional but builds trust)
- Don't change rules mid-contest

### Timing

**When to Announce:**

**Ideal Timeline:**
- Contest ends: March 14
- Review entries: March 15 (1 day)
- Select winner: March 15 (same day)
- Contact winner: March 15 (same day)
- Winner responds: March 15-17 (48 hours)
- Public announcement: March 17 (3 days after contest end)

**Avoid:**
- Announcing immediately without verifying eligibility
- Waiting weeks to announce (participants lose interest)
- Changing winner after announcement (unless fraud discovered)

### Multiple Winners Strategy

**How to Choose Number of Winners:**

**Factors to Consider:**
- Prize cost (can you afford 5 signed books + shipping?)
- Entry count (5 winners for 50 entries = 10% chance, feels generous)
- Goal (email list building = 1 grand prize; engagement = multiple winners)

**Common Strategies:**
- **1 Grand Prize:** One winner, high-value prize ($100+ gift card, full series)
- **3-5 Winners:** Multiple prizes, builds more goodwill
- **10+ Winners:** Small prizes (digital book, bookmark) for huge entry counts (500+)

**Example: Tiered Prizes**
- 1st Prize: Signed book + $25 gift card
- 2nd-5th Prize: Signed book
- 6th-10th Prize: Ebook copy

### Consolation Strategies

**For Non-Winners:**

Even though they didn't win, keep them engaged:

**Option 1: Discount Code**
- Email all participants: "Thanks for entering! Here's 20% off your purchase"
- Converts participants into customers

**Option 2: Exclusive Content**
- Send all entrants a bonus chapter or deleted scene
- Builds goodwill and keeps them connected

**Option 3: Early Access**
- Give entrants first access to your next contest or book launch
- Makes them feel valued

**Option 4: Newsletter Engagement**
- Welcome email series for new subscribers from contest
- Introduce yourself, share your author journey
- Build relationship beyond the contest

## Troubleshooting

### No One Responds

**If winner doesn't respond within 72 hours:**

1. Check email didn't go to spam
2. Send one follow-up email
3. Try social media if they included a handle
4. After 5 days total, select alternate winner
5. Document for transparency

### Winner is Ineligible

**If winner doesn't meet requirements:**

1. Thank them for entering
2. Explain which requirement wasn't met (age, location, etc.)
3. Apologize and select new winner
4. Don't announce original winner publicly

**Example Email:**

```
Hi [Name],

Thank you so much for entering our contest! Unfortunately, the contest
was limited to US residents only, and I see you're located in [Country].

I'm so sorry - I know that's disappointing. I'm selecting an alternate
winner, but I'd love to send you a special discount code as thanks for
your interest!

Best,
[Your Name]
```

### Suspected Fraud

**If winner's entry looks suspicious:**

**Red Flags:**
- Newly created email (temp-mail.com, etc.)
- No social media presence when required
- Won't provide verification
- Entry details seem fake

**Action:**
1. Request additional verification (photo ID if prize is valuable)
2. If they can't/won't verify, select new winner
3. For future contests, add CAPTCHA or phone verification

### Too Many Entries to Review

**For contests with 500+ entries:**

1. **Use Google Sheets filters** to identify obvious spam:
   - Filter Email column for common spam domains
   - Filter Name column for "test", "asdf", etc.
   - Delete spam in bulk
2. **Random selection before review:**
   - Pick winner randomly first
   - Only verify THAT entry (saves time)
   - Keep 2-3 alternates ready
3. **Automate with scripts:**
   - Use Google Apps Script to auto-flag suspicious entries
   - See [Developer Guide](/authorkit-contests/developer-guide.md)

## Advanced Tips

### Multiple Contest Rounds

Run ongoing contests to maintain list growth:

1. **Monthly recurring:** Same prize, new contest each month
2. **Track winners:** Keep spreadsheet of past winners
3. **Exclude previous winners:** Optional rule to spread prizes
4. **Analyze trends:** Which months get most entries? Adjust promotion.

### Winner Showcase

Build social proof by featuring past winners:

1. Create "Past Winners" page on website
2. Share winner testimonials ("I loved my signed copy!")
3. Feature winners in newsletter
4. Build community of engaged readers

### Data Analysis

Use entry data to improve marketing:

**Analyze:**
- **Source field:** Which platform drove most entries?
- **Entry timing:** What time/day had most submissions?
- **Bonus shares:** Which platform had best sharing rate?

**Apply to Next Contest:**
- Focus promotion on high-performing channels
- Schedule posts at peak entry times
- Emphasize best bonus entry options

## Next Steps

After announcing your winner:

1. **Send prize** - Ship signed book, send gift card code, etc.
2. **Ask for feedback** - "Did you receive it? What did you think?"
3. **Request review** - If they read the book, kindly ask for Amazon/Goodreads review
4. **Build relationship** - Add to launch team for next book
5. **Plan next contest** - Use lessons learned to improve

## Related Documentation

- **[Overview](/authorkit-contests/overview.md)** - Why run contests
- **[Creating Contests](/authorkit-contests/creating-contests.md)** - Set up your contest
- **[Managing Entries](/authorkit-contests/managing-entries.md)** - Google Apps Script setup
- **[Email Notifications](/authorkit-contests/email-notifications.md)** - Automate winner notifications
- **[Developer Guide](/authorkit-contests/developer-guide.md)** - Custom winner selection scripts

---

**Need Help?**

- [AuthorKit Support](https://authorkit.pro/support)
- [FAQ](https://docs.authorkit.pro/getting-started/faq)
- [Common Issues](https://docs.authorkit.pro/troubleshooting/common-issues)

---

*Last Updated: April 4, 2026*
