# Creating Reader Magnets

Step-by-step guide to create and publish your first reader magnet.

---

## Before You Start

### Prepare Your Magnet File

**Supported formats:**
- EPUB (recommended for fiction ebooks)
- MOBI (for Kindle users)
- PDF (universal format, works on any device)
- MP3/M4A (audiobook samples)
- ZIP (bundle multiple formats)

**File size limits:**
- Maximum: 50 MB per file
- Recommended: Under 10 MB for fast downloads

**Best practices:**
- Include multiple formats (EPUB + MOBI + PDF in a ZIP)
- Add copyright notice inside the file
- Include link back to your website
- Test on multiple devices before uploading

### Create a Landing Page (Optional)

While not required, a dedicated landing page converts better than a simple form:

**Good landing page includes:**
- Compelling headline ("Get my FREE prequel novella!")
- Book cover image
- Short description (2-3 sentences)
- What reader gets (format, length, genre)
- Email capture form
- Social proof (optional: "Join 5,000+ readers")

**WordPress page example:**
```
Title: Free Prequel: The Silent Echo Begins

Headline: Get the FREE prequel to The Silent Echo series!

Description:
Before Sarah Mitchell became a bestselling author, she wrote this
exclusive 60-page novella revealing how detective Jake Morrison
solved his first case.

Available in EPUB, MOBI, and PDF formats.

[Magnet signup form shortcode here]
```

---

## Step 1: Create New Magnet

1. Go to **WordPress admin → Magnets → Add New**
2. Enter magnet title: "The Silent Echo: Origins (Prequel)"
3. Add description in main editor:
   ```
   Exclusive 60-page prequel novella. Find out how it all began
   in this action-packed origin story available only to newsletter
   subscribers.
   ```

---

## Step 2: Upload Magnet File

### Single File Upload

In the **Magnet File** meta box:

1. Click **Upload File**
2. Select your EPUB/MOBI/PDF from computer
3. Click **Upload**
4. File appears with filename and size
5. (Optional) Add download button text: "Download Your Free Book"

### Multiple Formats (Recommended)

**Option 1: ZIP bundle**
1. Create ZIP containing: `prequel.epub`, `prequel.mobi`, `prequel.pdf`
2. Upload ZIP file
3. Reader downloads ZIP with all formats

**Option 2: Separate downloads**
1. Upload EPUB file
2. Click **Add Another File**
3. Upload MOBI file
4. Click **Add Another File**
5. Upload PDF file
6. Reader chooses preferred format at download

---

## Step 3: Configure Email Capture Form

In the **Email Capture Settings** meta box:

### Form Fields

**Required fields (cannot be removed):**
- Email address

**Optional fields (enable/disable):**
- [ ] First name
- [ ] Last name
- [ ] Reader preferences (genre checkboxes)

**Recommended:** Enable "First name" for email personalization.

### Consent & Privacy

**GDPR consent checkbox:**
- [x] Require consent checkbox
- Text: "I agree to receive emails from [Your Author Name]"
- Link to privacy policy: `/privacy-policy`

### Form Labels

Customize form field labels:
- Email label: "Your email address"
- Name label: "Your first name"
- Submit button: "Get My Free Book"

### Success Message

**After successful signup, show:**
```
Success! Check your email for your download link.

(If using immediate download, you can also download now: [Download Link])
```

---

## Step 4: Set Delivery Method

In the **Delivery Settings** meta box:

### Option 1: Immediate Download (Highest Conversion)

- [x] Show download link immediately after signup
- [ ] Also send email with download link

**Best for:** Maximum conversions, single-format files (PDF)

**Reader experience:**
1. Submits form
2. Sees "Download Your Book" button instantly
3. Clicks and downloads

### Option 2: Email-Only Delivery

- [ ] Show download link immediately after signup
- [x] Send email with download link

**Email template:**
```
Subject: Your free book is ready!

Hi {first_name},

Thanks for subscribing! Here's your free prequel novella:

[Download The Silent Echo: Origins]

This link expires in 7 days.

Enjoy the book!
{Your Author Name}
```

**Best for:** Double opt-in, building relationship, confirming email validity

### Option 3: Both (Recommended)

- [x] Show download link immediately after signup
- [x] Also send email with download link

**Best for:** Maximum delivery success (immediate + backup email)

---

## Step 5: Configure Security Settings

In the **Security & Anti-Piracy** meta box:

### Download Link Expiration

Choose link expiration:
- ( ) Never expire (not recommended)
- (•) 24 hours (default)
- ( ) 7 days
- ( ) 30 days
- ( ) Custom: ____ days

**Recommended:** 7 days (enough time but prevents long-term sharing)

### Download Limits

Choose download limit per email:
- ( ) Unlimited downloads
- (•) 3 downloads per signup (recommended)
- ( ) 1 download only (strict)

**Why 3?** Readers may download to multiple devices (phone, tablet, Kindle).

### Anti-Spam Protection

Enable spam prevention:
- [x] Enable Google reCAPTCHA (requires API key)
- [x] Enable honeypot field (invisible spam trap)
- [x] Rate limiting (max 5 signups per IP per hour)

---

## Step 6: Set Up Analytics Tracking (Optional)

In the **Tracking & Analytics** meta box:

### Google Analytics

Track magnet conversions:
- [x] Send event to Google Analytics on signup
- Event name: `magnet_signup`
- Event category: `Reader Magnets`
- Event label: `The Silent Echo Prequel`

### Facebook Pixel

Track for ad retargeting:
- [ ] Send Facebook Pixel event on signup
- Pixel ID: `123456789012345`
- Event type: `Lead`

### UTM Parameters

Track traffic sources:
- Campaign source: `website`
- Campaign medium: `reader-magnet`
- Campaign name: `silent-echo-prequel`

Add to your landing page URL:
```
https://yoursite.com/free-prequel?utm_source=website&utm_medium=reader-magnet&utm_name=silent-echo-prequel
```

---

## Step 7: Preview and Test

Before publishing:

### Preview the Form

1. Click **Preview** button
2. View signup form on frontend
3. Check styling and layout
4. Ensure all fields display correctly

### Test Signup Flow

1. Enter test email address
2. Submit form
3. Check success message appears
4. Verify email delivery (check inbox/spam)
5. Click download link
6. Confirm file downloads correctly

### Test on Multiple Devices

- [ ] Desktop (Chrome, Firefox, Safari)
- [ ] Mobile (iOS Safari, Android Chrome)
- [ ] Tablet (iPad, Android tablet)

### Test Anti-Spam

1. Try submitting form multiple times rapidly
2. Confirm rate limiting works
3. Test with invalid email formats
4. Verify reCAPTCHA challenges appear

---

## Step 8: Publish Magnet

Once testing is complete:

1. Click **Publish** button
2. Magnet is now live
3. Copy the shortcode from the meta box: `[authorkit_magnet id="123"]`
4. Add shortcode to your landing page

---

## Adding Magnet to Landing Page

### Method 1: Shortcode (Recommended)

Edit your WordPress page and add:

```
[authorkit_magnet id="123"]
```

Replace `123` with your magnet's ID (shown in meta box).

### Method 2: Gutenberg Block

1. Add new block
2. Search for "AuthorKit Magnet"
3. Select your magnet from dropdown
4. Block auto-displays form

### Method 3: Widget

1. Go to **Appearance → Widgets**
2. Add "AuthorKit Magnet" widget to sidebar
3. Select your magnet from dropdown
4. Widget displays form in sidebar

---

## Shortcode Options

Customize the form display with shortcode attributes:

### Basic Shortcode

```
[authorkit_magnet id="123"]
```

### Custom Button Text

```
[authorkit_magnet id="123" button_text="Download My Free Novella"]
```

### Custom Success Message

```
[authorkit_magnet id="123" success_message="Thank you! Check your inbox."]
```

### Hide Specific Fields

```
[authorkit_magnet id="123" show_name="false"]
```

### Custom CSS Class

```
[authorkit_magnet id="123" class="my-custom-magnet-form"]
```

---

## Email Template Customization

### Default Email Template

AuthorKit sends this email by default:

```
Subject: Your free book from {site_name}

Hi {first_name},

Thanks for signing up! Here's your free download:

**{magnet_title}**

{download_button}

This download link expires in {expiration_days} days.

Questions? Just reply to this email.

Best,
{site_name}
```

### Custom Email Template

To customize the email:

1. Go to **Magnets → Settings → Email Templates**
2. Edit "Magnet Delivery Email" template
3. Use placeholders:
   - `{first_name}` - Reader's first name
   - `{magnet_title}` - Magnet title
   - `{download_link}` - Download URL
   - `{download_button}` - Styled download button
   - `{expiration_days}` - Days until link expires
   - `{site_name}` - Your site name
   - `{site_url}` - Your site URL

**Example custom template:**

```
Subject: Here's your FREE prequel, {first_name}!

Hey {first_name},

I'm so excited to share this exclusive prequel with you!

{download_button}

This story reveals how Jake Morrison became a detective -
before the events of The Silent Echo.

Your download link works for the next {expiration_days} days.

Happy reading!
Sarah Mitchell
{site_url}

P.S. Reply to this email if you have any trouble downloading.
```

---

## Promoting Your Magnet

### Where to Promote

**On your website:**
- Homepage banner
- Blog post sidebar
- Footer call-to-action
- Book pages ("Want more?")
- About page

**Social media:**
- Facebook page pinned post
- Instagram bio link
- Twitter pinned tweet
- TikTok link in bio
- Pinterest pin

**Book back matter:**
- Last page of every book
- "Read more by [Your Name]" section
- Author bio

**Email signature:**
- Link to magnet landing page
- "Get my free prequel" CTA

### Promotional Copy Examples

**Short (social media):**
```
Want a FREE prequel to The Silent Echo?
Get it instantly: [link]
```

**Medium (blog sidebar):**
```
Join 5,000+ readers and get the exclusive
prequel novella FREE when you subscribe.
[Get Your Free Book →]
```

**Long (landing page):**
```
Before Sarah Mitchell's bestselling series began,
there was THIS story...

Get the 60-page prequel novella that reveals how
Detective Jake Morrison solved his very first case.

Available in EPUB, MOBI, and PDF.
Yours free when you join my newsletter.

[Get Your Free Prequel →]
```

---

## Troubleshooting

### Form Not Appearing

**Cause:** Shortcode incorrect or magnet unpublished

**Fix:**
1. Verify magnet is published (not draft)
2. Check shortcode ID matches magnet ID
3. Clear cache (WP Super Cache, W3 Total Cache, etc.)

### Emails Not Sending

**Cause:** WordPress mail() function issue

**Fix:**
1. Install SMTP plugin (WP Mail SMTP recommended)
2. Configure with Gmail, SendGrid, or Mailgun
3. Test email delivery via SMTP plugin

### Download Link Not Working

**Cause:** File not uploaded or permalink issue

**Fix:**
1. Verify file appears in Magnet File meta box
2. Re-save magnet (click Update button)
3. Test download link in private browser window

### Spam Signups

**Cause:** Bots submitting forms

**Fix:**
1. Enable Google reCAPTCHA (Settings → reCAPTCHA)
2. Enable honeypot field (Settings → Anti-Spam)
3. Reduce rate limit (Settings → Security)

---

## Next Steps

- [View download analytics →](managing-downloads.md)
- [Export subscribers to email service →](managing-downloads.md#export-subscribers)
- [Customize magnet settings →](settings.md)
- [Integrate with Mailchimp/ConvertKit →](settings.md#email-integrations)

---

**Last Updated:** April 4, 2026
**Requires:** AuthorKit Pro 1.0+
