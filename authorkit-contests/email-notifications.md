# Email Notifications

Learn how to set up automated email notifications for contest participants, including entry confirmations, winner notifications, and GDPR-compliant email list integration.

## Overview

Email notifications enhance your contest experience by:

- **Entry Confirmations** - Immediately confirm successful contest entry
- **Winner Notifications** - Automatically notify winners when selected
- **Email List Integration** - Add participants to your mailing list (MailChimp, ConvertKit, etc.)
- **Follow-up Campaigns** - Engage non-winners with special offers
- **GDPR Compliance** - Proper consent and opt-in management

**Note:** AuthorKit Contests uses Google Apps Script for entries, so email notifications are configured through Google Apps Script and/or third-party email services (Zapier integration).

## Entry Confirmation Emails

Send automatic confirmation when someone enters your contest.

### Method A: Google Apps Script Email (Basic)

The Google Apps Script template includes optional email notification code.

**Setup Steps:**

1. **Open your Apps Script project** (see [Managing Entries](/authorkit-contests/managing-entries.md))
2. **Find the email code** - Scroll to bottom of `doPost` function (around line 200)
3. **Uncomment the email code** - Remove `//` from each line:

```javascript
// Original (commented out):
// MailApp.sendEmail({
//   to: data.email,
//   subject: 'Contest Entry Confirmed',
//   body: 'Thank you for entering!'
// });

// After uncommenting:
MailApp.sendEmail({
  to: data.email,
  subject: 'Contest Entry Confirmed',
  body: 'Thank you for entering!'
});
```

4. **Customize the email:**

```javascript
MailApp.sendEmail({
  to: data.email,
  subject: 'You\'re Entered! - Silent Echo Book Giveaway',
  body: 'Hi ' + data.name + ',\n\n' +
        'Your entry for the Silent Echo book giveaway has been confirmed!\n\n' +
        'Entry Number: ' + entryNumber + '\n' +
        'Contest End Date: March 14, 2026\n\n' +
        'Winner will be announced on March 17, 2026.\n\n' +
        'Good luck!\n\n' +
        'P.S. Share on social media for bonus entries!\n\n' +
        'Best,\n' +
        '[Your Name]'
});
```

5. **Save and re-deploy:**
   - Click **Deploy → Manage deployments**
   - Click pencil icon to edit
   - Select **New version**
   - Click **Deploy**

**Limitations:**
- Plain text only (no HTML formatting)
- Sent from your Google account email
- Basic personalization only
- Daily sending limits (100-500 emails per day depending on Google account type)

**Best For:** Small contests (under 100 entries) with basic confirmation needs.

### Method B: HTML Email with Apps Script

For better-designed emails, use HTML templates in Apps Script:

```javascript
MailApp.sendEmail({
  to: data.email,
  subject: 'You\'re Entered! - Silent Echo Book Giveaway',
  htmlBody: '<div style="font-family: Arial, sans-serif; max-width: 600px; margin: 0 auto;">' +
            '<h2 style="color: #ff9900;">Contest Entry Confirmed!</h2>' +
            '<p>Hi ' + data.name + ',</p>' +
            '<p>Your entry for the <strong>Silent Echo</strong> book giveaway has been confirmed!</p>' +
            '<div style="background: #f9f9f9; padding: 20px; border-radius: 8px; margin: 20px 0;">' +
            '<p><strong>Entry Number:</strong> ' + entryNumber + '</p>' +
            '<p><strong>Contest End Date:</strong> March 14, 2026</p>' +
            '<p><strong>Winner Announcement:</strong> March 17, 2026</p>' +
            '</div>' +
            '<p><a href="YOUR_CONTEST_URL" style="background: #ff9900; color: white; padding: 12px 24px; text-decoration: none; border-radius: 6px; display: inline-block;">Share for Bonus Entries</a></p>' +
            '<p>Good luck!</p>' +
            '<p>Best,<br>[Your Name]</p>' +
            '</div>'
});
```

**Benefits:**
- Professional design
- Clickable buttons
- Brand colors and styling
- Logo images (hosted externally)

### Method C: SendGrid via Apps Script (Advanced)

For high-volume contests, integrate SendGrid API:

**Prerequisites:**
- SendGrid account (free tier: 100 emails/day)
- SendGrid API key

**Code:**

```javascript
function sendConfirmationEmail(email, name, entryNumber) {
  var url = 'https://api.sendgrid.com/v3/mail/send';
  var apiKey = 'YOUR_SENDGRID_API_KEY'; // Store securely

  var payload = {
    personalizations: [{
      to: [{ email: email, name: name }],
      subject: 'You\'re Entered! - Silent Echo Book Giveaway'
    }],
    from: { email: 'you@yourdomain.com', name: 'Your Author Name' },
    content: [{
      type: 'text/html',
      value: '<h2>Contest Entry Confirmed!</h2>' +
             '<p>Hi ' + name + ',</p>' +
             '<p>Your entry number is: <strong>' + entryNumber + '</strong></p>'
    }]
  };

  var options = {
    method: 'post',
    headers: {
      'Authorization': 'Bearer ' + apiKey,
      'Content-Type': 'application/json'
    },
    payload: JSON.stringify(payload)
  };

  UrlFetchApp.fetch(url, options);
}

// Call in doPost function after sheet.appendRow():
sendConfirmationEmail(data.email, data.name, entryNumber);
```

**Benefits:**
- Higher sending limits
- Better deliverability
- Email tracking (opens, clicks)
- From your custom domain

## Winner Notification Emails

### Manual Winner Notification

After selecting a winner (see [Winner Selection](/authorkit-contests/winner-selection.md)):

1. **Get winner's email from Google Sheet**
2. **Compose email in Gmail or your email client**
3. **Use this template:**

```
Subject: Congratulations! You won the "Silent Echo" Book Giveaway

Hi [Winner Name],

Congratulations! You're the winner of our book contest for "The Silent Echo"!

PRIZE: One signed paperback copy

To claim your prize, please reply to this email within 48 hours with:
- Your full shipping address (street, city, state, ZIP)
- Confirmation that you're 18+ and a US resident (per contest terms)

If I don't hear from you by [Date 48 hours from now], I'll select an alternate winner.

I'm so excited to get your signed copy in the mail! Thank you for entering and supporting my work.

Best,
[Your Name]

P.S. If you enjoy the book, I'd be grateful for a review on Amazon or Goodreads!
```

4. **Track response in spreadsheet**
5. **Send reminder if no response after 48 hours**

### Automated Winner Notification via Zapier

For fully automated winner emails:

**Prerequisites:**
- Zapier account (free tier available)
- Email service (Gmail, MailChimp, etc.)

**Setup:**

1. **Create Zap:**
   - Trigger: Google Sheets - Updated Spreadsheet Row
   - Filter: Only continue if "Winner" column = "Yes"
   - Action: Gmail - Send Email

2. **Configure trigger:**
   - Spreadsheet: Your contest entries sheet
   - Worksheet: Sheet1
   - Trigger column: "Winner" (add this column manually)

3. **Configure action:**
   - To: Column "Email"
   - Subject: "Congratulations! You won..."
   - Body: Winner notification template

4. **Mark winner:**
   - When you select winner, add "Yes" in their Winner column
   - Zapier automatically sends email

**Note:** This requires manually adding a "Winner" column to your Google Sheet.

## Email List Integration

Add contest participants to your author mailing list automatically.

### Why Integrate Email Lists?

**Benefits:**
- Automatically add entries to newsletter
- Segment contest participants for targeted emails
- Nurture relationship beyond the contest
- Convert entries into long-term readers

**Important:** Only add people who consented. Include privacy policy link and opt-in checkbox in contest form.

### GDPR Compliance

**Requirements:**

1. **Clear Consent:**
   - Checkbox: "I agree to receive emails from [Your Name]"
   - Must be unchecked by default (explicit opt-in)
   - Separate from contest entry (can't be bundled)

2. **Privacy Policy:**
   - Link to privacy policy in contest form
   - Explain how email will be used
   - Right to unsubscribe anytime

3. **Unsubscribe Option:**
   - Every email must include unsubscribe link
   - One-click unsubscribe (no login required)
   - Process requests within 30 days (GDPR requirement)

**AuthorKit Contests GDPR Features:**
- Built-in consent checkbox option
- Privacy policy link field
- "I consent to marketing emails" separate from entry

**Best Practice:** Even if not in EU, follow GDPR standards. Builds trust and improves deliverability.

### Integration Method 1: Zapier (Recommended)

**Connect Google Sheets → Email Service:**

**Example: Google Sheets → MailChimp**

1. **Create Zap:**
   - Trigger: Google Sheets - New Spreadsheet Row
   - Action: MailChimp - Add/Update Subscriber

2. **Configure Trigger:**
   - Spreadsheet: Your contest entries sheet
   - Worksheet: Sheet1
   - Trigger column: Any (triggers on new row)

3. **Configure Action:**
   - Audience: Your main newsletter list
   - Subscriber Email: Column "Email"
   - Subscriber Status: Choose "subscribed" (if GDPR consent collected)
   - First Name: Column "Name"
   - Tags: "Contest Entry - March 2026", "Silent Echo Giveaway"
   - Merge Fields: Map custom fields if needed

4. **Test and Enable:**
   - Submit test entry
   - Verify subscriber added to MailChimp
   - Turn on Zap

**Supported Services via Zapier:**
- MailChimp
- ConvertKit
- ActiveCampaign
- MailerLite
- Constant Contact
- AWeber
- Drip
- And 1000+ others

**Cost:** Free Zapier tier supports 100 tasks/month. Paid plans for higher volume.

### Integration Method 2: Direct API (Advanced)

For developers, integrate directly with email service APIs:

**Example: ConvertKit API in Google Apps Script**

```javascript
function addToConvertKit(email, firstName) {
  var apiKey = 'YOUR_CONVERTKIT_API_KEY';
  var formId = 'YOUR_FORM_ID'; // ConvertKit form ID
  var url = 'https://api.convertkit.com/v3/forms/' + formId + '/subscribe';

  var payload = {
    api_key: apiKey,
    email: email,
    first_name: firstName,
    tags: ['Contest Entry', 'Silent Echo Giveaway']
  };

  var options = {
    method: 'post',
    contentType: 'application/json',
    payload: JSON.stringify(payload)
  };

  UrlFetchApp.fetch(url, options);
}

// Call in doPost function after sheet.appendRow():
addToConvertKit(data.email, data.name);
```

**Benefits:**
- Real-time integration (no Zapier delay)
- More control over data
- Custom tagging and segmentation

**Drawbacks:**
- Requires coding knowledge
- Must maintain API keys securely
- Service-specific code (not portable)

### Segmentation Strategies

Tag contest participants for targeted follow-up:

**Recommended Tags:**
- "Contest Entry" (all participants)
- "Contest Entry - [Month/Year]"
- "[Book Title] Giveaway"
- "Contest Winner" (for winner only)
- "Contest Non-Winner" (for follow-up offer)

**Use Cases:**

**Tag: "Contest Entry"**
- Send welcome series introducing yourself
- Share exclusive content (bonus chapters)
- Announce new contests early

**Tag: "[Book Title] Giveaway"**
- Send related book recommendations
- Promote other books in same genre
- Request reviews if they purchase

**Tag: "Contest Winner"**
- Request testimonial about prize
- Invite to join launch team
- Ask for Amazon/Goodreads review

**Tag: "Contest Non-Winner"**
- Send consolation discount code
- Offer free bonus content
- Early access to next contest

## Follow-Up Email Campaigns

Nurture relationships with contest participants after the contest ends.

### Welcome Series for New Subscribers

If contest drove email list growth, send automated welcome series:

**Email 1 (Immediately after contest):**
```
Subject: Thanks for entering! Here's what's next...

Hi [Name],

Thank you so much for entering the Silent Echo book giveaway!

Winner will be announced on March 17, 2026. I'll email all participants
with the results.

In the meantime, here's what to expect from me:
- Behind-the-scenes author updates
- Exclusive content and bonus chapters
- Early announcements for new releases
- Advance reader copy opportunities

You can unsubscribe anytime (but I hope you'll stick around!).

Best,
[Your Name]

P.S. Want a free bonus chapter from my previous book? Reply and I'll send it!
```

**Email 2 (After winner announcement):**
```
Subject: Contest winner announced + special offer inside

Hi [Name],

The contest winner has been announced! [Winner Name] from [Location]
won the signed copy of Silent Echo.

Didn't win? I've got something for you!

Use code CONTEST20 for 20% off any of my books:
[Link to your bookstore]

This code expires in 7 days, so grab your copy now.

Thanks again for participating!

Best,
[Your Name]
```

**Email 3 (One week later):**
```
Subject: What I'm working on now...

Hi [Name],

I wanted to share a quick behind-the-scenes update on my current project...

[Personal author update, next book tease, etc.]

I love connecting with readers like you. Hit reply anytime - I read every email!

Best,
[Your Name]
```

### Non-Winner Consolation Email

Send special offer to participants who didn't win:

```
Subject: You didn't win, but I've got something for you!

Hi [Name],

The Silent Echo contest has ended, and while you weren't the lucky winner,
I didn't want you to leave empty-handed.

Here's an exclusive offer for contest participants:

20% OFF + FREE SHIPPING
Use code: CONTEST20
Valid through: [Date]

[Button: Shop Now]

Plus, as a thank you for your interest, here's a free bonus chapter from
my previous book: [Link]

I appreciate your support, and I hope you'll give Silent Echo a try!

Best,
[Your Name]

P.S. I run contests regularly. Want first access to the next one?
Stay subscribed and I'll let you know before I announce publicly.
```

**Conversion Tip:** Include urgency (limited time code) and scarcity (limited quantity) to encourage immediate purchase.

### Winner Follow-Up Email

After winner receives prize:

```
Subject: Did your signed book arrive?

Hi Sarah,

I hope your signed copy of Silent Echo arrived safely!

I'd love to hear what you think of it. If you enjoy the book, would you
consider leaving a review on Amazon or Goodreads? Reader reviews help
authors more than you might think!

[Button: Leave a Review]

Also, I'm building a launch team for my next book. Interested in joining?
You'd get an advance copy in exchange for an honest review. Let me know!

Thanks again for entering the contest and supporting my work.

Best,
[Your Name]
```

## Best Practices

### Email Deliverability

**Improve inbox placement:**

1. **Use reputable email service:**
   - MailChimp, ConvertKit, SendGrid
   - Avoid sending from free Gmail/Yahoo
   - Dedicated sending domain (you@yourdomain.com)

2. **Authenticate your domain:**
   - Set up SPF records
   - Configure DKIM
   - Enable DMARC

3. **Maintain list hygiene:**
   - Remove bounced emails
   - Don't email unengaged subscribers forever
   - Honor unsubscribe requests immediately

4. **Write quality content:**
   - Avoid spam trigger words ("FREE!!!", "ACT NOW!!!")
   - Don't use all caps in subject lines
   - Include text version (not just HTML)

### Email Frequency

**Recommended Schedule:**

**First Week (Contest Active):**
- Day 1: Entry confirmation (immediate)
- Day 3: Reminder to share for bonus entries
- Day 7: "Contest ends in 7 days!" reminder

**After Contest Ends:**
- Day 1: Winner announcement to all participants
- Day 2: Non-winner consolation offer
- Week 2: Welcome to newsletter / author introduction
- Week 4: Next contest announcement (if recurring)

**Avoid:**
- Daily emails (too aggressive)
- Silence after contest (missed opportunity)
- Emailing only when you want something (sales emails only)

### Personalization

**Basic Personalization:**
- Use first name in greeting
- Reference their contest entry
- Mention which contest they entered (if you run multiple)

**Advanced Personalization:**
- Reference their review/rating if they left one
- Tailor book recommendations based on Source field (came from Amazon? Recommend similar authors)
- Segment by location (mention local book events)

**Example:**

```
Basic: "Hi [Name], thanks for entering!"

Advanced: "Hi Sarah, I saw you gave Silent Echo 5 stars in your entry!
Since you mentioned you found the contest on Goodreads and love atmospheric
mysteries, I think you'd also enjoy [Similar Book]. Plus, I'm doing a book
signing in Portland next month if you're interested!"
```

## Troubleshooting

### Emails Going to Spam

**Common Causes:**
- Sending from free Gmail/Yahoo account
- No SPF/DKIM authentication
- High spam complaint rate
- Purchased/scraped email lists (never do this)

**Solutions:**
- Use professional email service (MailChimp, etc.)
- Authenticate your domain
- Only email people who explicitly opted in
- Include clear unsubscribe link

### Low Open Rates

**Benchmarks:**
- Industry average: 15-25%
- Author newsletters: 20-35%
- Contest emails: 30-50% (first email)

**Improve Open Rates:**
- Write compelling subject lines
- Personalize subject with first name
- Send from your name, not "noreply@"
- Test send times (Tuesday/Thursday 10am often works well)

### Zapier Not Triggering

**Check:**
- Zap is turned ON (green toggle)
- Google Sheet permissions allow Zapier access
- Trigger column is correct (row is being added)
- Task limit not exceeded (free tier: 100/month)

**Debug:**
- Test step by step in Zapier editor
- Check Zap history for errors
- Verify Google Sheet row format matches expected data

## Legal Considerations

**Disclaimer:** This is not legal advice. Consult an attorney for legal compliance.

### CAN-SPAM Act (US)

**Requirements:**
- Don't use deceptive subject lines
- Include your physical mailing address
- Honor unsubscribe requests within 10 days
- Clearly identify email as advertisement (if promotional)

### GDPR (EU)

**Requirements:**
- Explicit opt-in (pre-checked boxes not allowed)
- Clear purpose (what emails they'll receive)
- Easy unsubscribe process
- Right to data deletion (honor requests within 30 days)

**Even if you're US-based:** Following GDPR builds trust and improves deliverability globally.

### CASL (Canada)

**Requirements:**
- Express consent before sending commercial emails
- Identify sender clearly
- Provide unsubscribe mechanism

## Next Steps

Now that you understand email notifications:

1. **Choose your method** - Apps Script, Zapier, or direct API
2. **Set up entry confirmations** - Test with sample entry
3. **Plan winner notification** - Draft email template
4. **Integrate email list** - Connect Google Sheets to MailChimp/ConvertKit
5. **Prepare follow-up campaigns** - Welcome series and consolation emails

## Related Documentation

- **[Overview](/authorkit-contests/overview.md)** - Contest module features
- **[Creating Contests](/authorkit-contests/creating-contests.md)** - Contest setup
- **[Managing Entries](/authorkit-contests/managing-entries.md)** - Google Apps Script configuration
- **[Winner Selection](/authorkit-contests/winner-selection.md)** - Picking and announcing winners
- **[Developer Guide](/authorkit-contests/developer-guide.md)** - Advanced customization

---

**Need Help?**

- [AuthorKit Support](https://authorkit.pro/support)
- [FAQ](https://docs.authorkit.pro/getting-started/faq)
- [Common Issues](https://docs.authorkit.pro/troubleshooting/common-issues)

---

*Last Updated: April 4, 2026*
