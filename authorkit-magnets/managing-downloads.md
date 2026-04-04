# Managing Downloads & Subscribers

Track downloads, view analytics, and export your subscriber list.

---

## Analytics Dashboard

### Viewing Analytics

Go to **Magnets → Analytics** to see:

**Overall stats:**
- Total signups (all magnets)
- Total downloads
- Conversion rate
- Growth trend (this month vs last month)

**Per-magnet stats:**
- Signups per magnet
- Downloads per magnet
- Conversion rate (visits → signups)
- Top-performing magnet

### Conversion Metrics

**Key metrics tracked:**

| Metric | Formula | Good Benchmark |
|--------|---------|----------------|
| Signup rate | (Signups / Page views) × 100 | 15-25% |
| Download rate | (Downloads / Signups) × 100 | 90-95% |
| Email delivery rate | (Emails sent / Emails delivered) × 100 | 95-98% |

**Low signup rate?** Improve your landing page copy or offer.
**Low download rate?** Check email delivery or link expiration settings.

### Date Range Filters

View analytics for specific periods:
- Today
- Last 7 days
- Last 30 days
- Last 90 days
- Custom date range

### Export Analytics

Download analytics as CSV:
1. Select date range
2. Click **Export CSV**
3. Open in Excel or Google Sheets
4. Analyze trends, create charts

---

## Subscriber List

### Viewing Subscribers

Go to **Magnets → Subscribers** to see all signups.

**Table columns:**
- Name
- Email
- Magnet signed up for
- Signup date
- Download count
- Status (active, unsubscribed, bounced)

### Search & Filter

**Search by:**
- Name
- Email address

**Filter by:**
- Magnet (show only subscribers to specific magnet)
- Date range (signups between X and Y)
- Status (active only, unsubscribed, etc.)

**Example:** "Show me everyone who signed up for 'Prequel Novella' in March"

### Sorting

Click column headers to sort by:
- Name (A-Z or Z-A)
- Email (alphabetical)
- Signup date (newest first or oldest first)
- Download count (most active subscribers)

---

## Export Subscribers

### Export to CSV

Export your list to import into email marketing services:

1. Go to **Magnets → Subscribers**
2. (Optional) Filter by magnet or date range
3. Click **Export CSV**
4. CSV downloads with columns:
   - First name
   - Last name
   - Email
   - Signup date
   - Magnet name
   - Download count

### Import to Email Service

**Mailchimp:**
1. Log in to Mailchimp
2. Go to Audience → Import contacts
3. Upload CSV
4. Map fields (Email → Email, First name → First name)
5. Complete import

**ConvertKit:**
1. Log in to ConvertKit
2. Go to Subscribers → Import
3. Upload CSV
4. Tag imported contacts (e.g., "Magnet: Prequel Novella")
5. Complete import

**MailerLite:**
1. Log in to MailerLite
2. Go to Subscribers → Import
3. Upload CSV
4. Map fields
5. Add to group
6. Complete import

---

## Automatic Email Integration

Skip manual exports with automatic integrations.

### Mailchimp Integration

**Setup:**
1. Go to **Magnets → Settings → Integrations**
2. Click **Connect Mailchimp**
3. Enter Mailchimp API key
4. Select list to add subscribers to
5. (Optional) Choose tag to apply

**What happens:**
- Reader signs up for magnet
- AuthorKit instantly adds them to Mailchimp
- Mailchimp sends welcome email (if automation enabled)
- You never touch the data manually

### ConvertKit Integration

**Setup:**
1. Go to **Magnets → Settings → Integrations**
2. Click **Connect ConvertKit**
3. Enter ConvertKit API key
4. Select form to add subscribers to
5. (Optional) Choose tag to apply

**Per-magnet tags:**
You can tag subscribers differently based on which magnet they downloaded:
- Magnet A → Tag "Interested in Fantasy"
- Magnet B → Tag "Interested in Romance"
- Send targeted emails based on tags

### Webhook Integration (Advanced)

Connect to any service with webhook support:

**Services supported:**
- ActiveCampaign
- Drip
- GetResponse
- AWeber
- Any platform with webhook URLs

**Setup:**
1. Go to **Magnets → Settings → Integrations**
2. Click **Add Webhook**
3. Enter webhook URL from your email service
4. Map fields (name → first_name, email → email)
5. Test webhook
6. Save

**Payload sent on signup:**
```json
{
  "first_name": "John",
  "last_name": "Doe",
  "email": "john@example.com",
  "magnet_id": 123,
  "magnet_title": "Prequel Novella",
  "signup_date": "2026-04-04T10:30:00Z",
  "source": "https://yoursite.com/free-prequel"
}
```

---

## Download Links

### Viewing Download Links

Go to **Magnets → Downloads** to see all download activity.

**Table shows:**
- Email address
- Magnet downloaded
- Download date/time
- IP address (for security)
- User agent (device type)
- Link status (active, expired, used)

### Resending Download Links

If a subscriber lost their link:

1. Go to **Magnets → Subscribers**
2. Find the subscriber by email
3. Click **Resend Link**
4. New email sent with fresh download link

### Expiring Links Manually

If you need to revoke access:

1. Go to **Magnets → Downloads**
2. Find the download record
3. Click **Expire Link**
4. Link immediately stops working

**Use case:** Subscriber shared link publicly, you want to stop unauthorized downloads.

---

## Subscriber Actions

### Bulk Actions

Select multiple subscribers and perform actions:

**Available bulk actions:**
- Export selected to CSV
- Delete selected
- Mark as unsubscribed
- Resend download link

**Example:** Select 50 subscribers, export to CSV, import to MailerLite.

### Individual Subscriber Actions

Click subscriber name to view details:

**Actions available:**
- Edit name/email
- View download history
- Resend download link
- Mark as unsubscribed
- Delete permanently

**Subscriber detail page shows:**
- Signup date
- IP address at signup
- Magnet signed up for
- Number of downloads
- Last download date
- Email delivery status (sent, delivered, bounced, opened)

---

## Download Security

### Preventing Abuse

**AuthorKit Magnets protects against:**

**Link sharing:** Unique download links per subscriber (not guessable)
**Expired links:** Links stop working after X days (configurable)
**Download limits:** Max 3 downloads per signup (prevent unlimited sharing)
**Hotlinking:** Direct file URLs blocked (must go through download system)
**Bots:** reCAPTCHA and honeypot fields prevent automated signups

### Monitoring Suspicious Activity

**Red flags to watch for:**
- Same IP address, multiple signups (bot or abusive user)
- Download links accessed 100+ times (publicly shared link)
- Signups from disposable email domains (temp-mail.com, etc.)

**How to investigate:**
1. Go to **Magnets → Downloads**
2. Sort by "Download count" (highest first)
3. Look for unusual patterns (same IP, rapid downloads)
4. Expire suspicious links
5. Block abusive IP addresses via **Settings → Security**

### IP Blocking

Block specific IP addresses from signing up:

1. Go to **Magnets → Settings → Security**
2. Add IP address to blocklist
3. Users from that IP see error: "Signups from your location are not allowed"

**When to use:**
- Repeated bot signups from same IP
- Known VPN/proxy abuse
- Spam signups from specific countries (optional geofencing)

---

## GDPR & Privacy Compliance

### Data Stored

AuthorKit Magnets stores:
- First name, last name (if collected)
- Email address
- Signup date/time
- IP address at signup
- Download history (dates, IP addresses)

**Not stored:**
- Credit card information (no payment processing)
- Sensitive personal information
- Tracking cookies (unless you enable Google Analytics)

### User Rights

**Right to access:**
Users can request their data. Go to **Magnets → Subscribers**, search by email, click **Export User Data** to generate JSON file.

**Right to deletion:**
Users can request deletion. Go to **Magnets → Subscribers**, find user, click **Delete** → **Delete permanently** (removes all records).

**Right to unsubscribe:**
Every email includes unsubscribe link. User clicks → marked as unsubscribed in database → no more emails.

### Privacy Policy

Include this in your privacy policy:

```
Email Collection for Reader Magnets:

When you download a free book from our website, we collect your
name and email address to deliver the download link and send you
occasional updates about new releases.

Your information is stored securely and never sold to third parties.
You can unsubscribe at any time by clicking the link in any email.

We use AuthorKit Magnets (self-hosted WordPress plugin) to manage
downloads. Your data is stored on our server, not with a third-party
service.
```

---

## Troubleshooting

### No Download Data Showing

**Cause:** Analytics not enabled or tracking blocked

**Fix:**
1. Go to **Magnets → Settings → Analytics**
2. Enable "Track downloads"
3. Save settings
4. Test by downloading a magnet yourself

### Subscriber List Empty

**Cause:** No signups yet or database issue

**Fix:**
1. Test signup yourself to confirm form works
2. Check **Magnets → Subscribers** for test entry
3. If still empty, check error logs: **Tools → Site Health**

### Export CSV Not Downloading

**Cause:** Browser blocking download or server issue

**Fix:**
1. Try different browser (Chrome, Firefox)
2. Disable pop-up blocker temporarily
3. Check file permissions on server (/wp-content/uploads/)

### Email Service Integration Failing

**Cause:** Invalid API key or network issue

**Fix:**
1. Re-enter API key (copy from email service dashboard)
2. Test connection via **Settings → Integrations → Test Connection**
3. Check error message for specific issue (invalid key, rate limit, etc.)

---

## Best Practices

### Clean Your List Regularly

**Monthly task:**
1. Export subscribers
2. Remove invalid emails (bounces, unsubscribes)
3. Import cleaned list to email service
4. Delete unsubscribes from AuthorKit (GDPR compliance)

### Segment by Magnet

Tag subscribers based on which magnet they downloaded:
- Downloaded romance magnet → "Interested in romance"
- Downloaded thriller magnet → "Interested in thrillers"
- Send targeted book launch emails based on tags

### Monitor Trends

**Track over time:**
- Signup rate (improving or declining?)
- Best-performing magnet (promote it more)
- Drop-off points (form abandonment, email delivery issues)

**Adjust based on data:**
- Low signups → improve landing page
- Low downloads → check email delivery
- High unsubscribes → adjust email frequency or content

---

## Next Steps

- [Customize magnet settings →](settings.md)
- [Integrate with email services →](settings.md#email-integrations)
- [Create additional magnets →](creating-magnets.md)
- [Developer customization →](developer-guide.md)

---

**Last Updated:** April 4, 2026
**Requires:** AuthorKit Pro 1.0+
