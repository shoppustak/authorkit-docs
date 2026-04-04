# Magnets Settings

Configure global settings for reader magnets delivery, email templates, and integrations.

---

## General Settings

Go to **Magnets → Settings → General**

### Default Delivery Method

Choose default for new magnets (can override per-magnet):

- ( ) Immediate download only
- (•) Email delivery only
- ( ) Both (immediate + email)

**Recommended:** Both (maximum delivery success rate)

### File Storage

**Upload directory:** `/wp-content/uploads/authorkit-magnets/`

**File naming:**
- ( ) Keep original filename
- (•) Generate unique filename (prevents conflicts)

**Security:**
- [x] Block direct file access (force download through AuthorKit)
- [x] Protect upload directory with .htaccess

### Download Link Settings

**Default expiration:** [7] days
**Default download limit:** [3] downloads per signup

**Link format:**
- ( ) Simple: `/download/abc123`
- (•) Secure: `/download/abc123def456ghi789` (longer, harder to guess)

---

## Email Settings

Go to **Magnets → Settings → Email**

### Sender Information

**From name:** [Sarah Mitchell]
**From email:** [sarah@authorsite.com]

**Important:** Use an email address on YOUR domain (not Gmail/Yahoo) for better deliverability.

### Email Templates

#### Delivery Email Template

**Subject:** [Your free book from {site_name}]

**Body:**
```
Hi {first_name},

Thanks for subscribing! Here's your free download:

**{magnet_title}**

{download_button}

This download link expires in {expiration_days} days.

Questions? Just reply to this email.

Best,
{site_name}
```

**Available placeholders:**
- `{first_name}` - Reader's first name
- `{last_name}` - Reader's last name
- `{email}` - Reader's email
- `{magnet_title}` - Magnet title
- `{download_link}` - Download URL (text link)
- `{download_button}` - Styled download button
- `{expiration_days}` - Days until link expires
- `{expiration_date}` - Exact expiration date
- `{site_name}` - Your site name
- `{site_url}` - Your site URL

#### Link Expiration Reminder Email

**Send reminder:** [1] day before link expires
**Subject:** [Your download link expires soon]

**Body:**
```
Hi {first_name},

Just a quick reminder - your download link for
**{magnet_title}** expires in 24 hours.

{download_button}

Haven't downloaded yet? Click above to get your book now.

Best,
{site_name}
```

**Enable reminder:** [x] Yes

---

## Form Settings

Go to **Magnets → Settings → Forms**

### Default Form Fields

**Required fields (always included):**
- Email address

**Optional fields (enable by default for new magnets):**
- [x] First name
- [ ] Last name
- [ ] Genre preferences

### Form Styling

**Button color:** [#0073aa] (WP blue)
**Button text color:** [#ffffff] (white)
**Error color:** [#dc3232] (red)
**Success color:** [#46b450] (green)

**Custom CSS:**
```css
/* Add custom styles here */
.authorkit-magnet-form {
  max-width: 500px;
  margin: 0 auto;
}
```

### Consent & Privacy

**GDPR consent:**
- [x] Require consent checkbox on all forms
- Default text: "I agree to receive emails about new releases and updates"
- Link to privacy policy: [/privacy-policy]

**Double opt-in:**
- [ ] Require email confirmation before sending download
- Confirmation email subject: "Please confirm your email"

**Note:** Double opt-in reduces spam but also reduces conversion ~30%.

---

## Security & Anti-Spam

Go to **Magnets → Settings → Security**

### reCAPTCHA

Prevent bot signups with Google reCAPTCHA v3:

**Enable reCAPTCHA:** [x] Yes
**Site key:** [your-recaptcha-site-key]
**Secret key:** [your-recaptcha-secret-key]

**Get keys:** [Get reCAPTCHA keys →](https://www.google.com/recaptcha/admin)

**Version:** reCAPTCHA v3 (invisible, scores users 0-1 for bot likelihood)

### Honeypot Field

Invisible spam trap field (bots fill it, humans don't):

**Enable honeypot:** [x] Yes

### Rate Limiting

Prevent abuse by limiting signups per IP address:

**Max signups per IP:** [5] signups
**Time window:** [1] hour

**Example:** Same IP can sign up maximum 5 times per hour.

### IP Blocklist

Block specific IP addresses or ranges:

**Blocked IPs:**
```
192.168.1.100
10.0.0.0/24
```

**One IP per line.** Use CIDR notation for ranges.

### Email Domain Blocklist

Block disposable/temporary email services:

**Blocked domains:**
```
temp-mail.com
10minutemail.com
guerrillamail.com
```

**One domain per line.**

**Predefined lists:**
- [x] Block known disposable email services (1000+ domains)

---

## Email Integrations

Go to **Magnets → Settings → Integrations**

### Mailchimp

**Status:** Not connected

**Setup:**
1. Click **Connect Mailchimp**
2. Enter Mailchimp API key ([Get API key →](https://mailchimp.com/help/about-api-keys/))
3. Select audience (list) to add subscribers to
4. Choose tag to apply (optional): [Magnet Subscriber]
5. Click **Save & Test Connection**

**Per-magnet override:**
You can choose different Mailchimp lists/tags for each magnet.

**What syncs:**
- First name → Mailchimp FNAME
- Last name → Mailchimp LNAME
- Email → Mailchimp email
- Magnet name → Mailchimp tag (optional)

### ConvertKit

**Status:** Not connected

**Setup:**
1. Click **Connect ConvertKit**
2. Enter ConvertKit API key ([Get API key →](https://app.convertkit.com/account/edit))
3. Select form to add subscribers to
4. Choose tag to apply (optional): [Reader Magnet]
5. Click **Save & Test Connection**

**What syncs:**
- First name → ConvertKit first_name
- Email → ConvertKit email
- Magnet name → ConvertKit tag

### MailerLite

**Status:** Not connected

**Setup:**
1. Click **Connect MailerLite**
2. Enter MailerLite API key ([Get API key →](https://app.mailerlite.com/integrations/api))
3. Select group to add subscribers to
4. Click **Save & Test Connection**

**What syncs:**
- Name → MailerLite name
- Email → MailerLite email
- Magnet name → MailerLite field (optional)

### Custom Webhook

Connect to any service with webhook support:

**Webhook URL:** [https://yourservice.com/webhooks/authorkit]
**Method:** [POST]
**Content-Type:** [application/json]

**Payload sent on signup:**
```json
{
  "first_name": "John",
  "last_name": "Doe",
  "email": "john@example.com",
  "magnet_id": 123,
  "magnet_title": "Prequel Novella",
  "signup_date": "2026-04-04T10:30:00Z",
  "ip_address": "192.168.1.1",
  "source_url": "https://yoursite.com/free-prequel"
}
```

**Custom headers (optional):**
```
X-API-Key: your-api-key
Authorization: Bearer your-token
```

**Test webhook:** Click **Send Test Payload** to verify connection.

---

## Analytics Settings

Go to **Magnets → Settings → Analytics**

### Google Analytics

Track magnet signups in Google Analytics:

**Enable GA tracking:** [x] Yes
**Measurement ID:** [G-XXXXXXXXXX]

**Events sent:**
- `magnet_view` - Form displayed
- `magnet_signup` - Form submitted
- `magnet_download` - Download link clicked

### Facebook Pixel

Track for retargeting ads:

**Enable Facebook Pixel:** [ ] Yes
**Pixel ID:** [123456789012345]

**Events sent:**
- `Lead` - Form submitted
- `CompleteRegistration` - Download completed

### Download Tracking

**Track downloads:** [x] Yes (anonymized IP addresses)

**Data stored:**
- Download date/time
- Magnet downloaded
- User agent (browser/device type)
- Anonymized IP (last octet removed: 192.168.1.XXX)

**Retention:** Delete download logs older than [90] days

---

## Advanced Settings

Go to **Magnets → Settings → Advanced**

### Email Delivery

**Delivery method:**
- ( ) WordPress mail() function (default, may be unreliable)
- (•) SMTP (recommended for reliable delivery)

**If using SMTP, install:** [WP Mail SMTP plugin →](https://wordpress.org/plugins/wp-mail-smtp/)

**Recommended SMTP services:**
- SendGrid (free tier: 100 emails/day)
- Mailgun (free tier: 5,000 emails/month)
- Amazon SES (very cheap: $0.10 per 1,000 emails)

### File Upload Limits

**Max file size:** [50] MB
**Allowed file types:** EPUB, MOBI, PDF, ZIP, MP3, M4A

**Increase max file size:**
Edit `wp-config.php`:
```php
define('WP_MEMORY_LIMIT', '256M');
```

Edit `.htaccess`:
```
php_value upload_max_filesize 50M
php_value post_max_size 50M
```

### Database Cleanup

**Auto-delete unsubscribes:** [x] After 30 days
**Auto-delete expired links:** [x] After 7 days
**Auto-delete bounced emails:** [x] After 90 days

**Keeps database clean and GDPR-compliant.**

### Debug Mode

**Enable debug logging:** [ ] Yes (only enable for troubleshooting)

**Log location:** `/wp-content/uploads/authorkit-magnets/logs/`

**What's logged:**
- Email sending attempts (success/failure)
- API integration calls (Mailchimp, ConvertKit, etc.)
- Download link generation
- Errors and warnings

**Note:** Disable debug mode in production (can expose sensitive data in logs).

---

## Import/Export Settings

### Export Settings

**Backup your configuration:**

1. Click **Export Settings**
2. JSON file downloads
3. Save file safely

**Use case:** Moving to new site, backing up before changes.

### Import Settings

**Restore configuration:**

1. Click **Choose File**
2. Select settings JSON file
3. Click **Import Settings**
4. Settings restored

**Note:** Imports everything except API keys (must re-enter for security).

---

## Troubleshooting Settings

### Emails Not Sending

**Check:**
1. **From email** uses your domain (not Gmail)
2. **SMTP** configured (not using WordPress mail())
3. **SPF/DKIM** records set on domain (ask your host)
4. Test email via **Tools → Site Health → Mail Check**

**Common fix:** Install WP Mail SMTP plugin and configure with SendGrid.

### Forms Not Appearing

**Check:**
1. **Shortcode** is correct: `[authorkit_magnet id="123"]`
2. **Magnet** is published (not draft)
3. **Cache** cleared (WP Super Cache, W3 Total Cache)
4. **JavaScript** errors in browser console (F12 → Console tab)

### Mailchimp Integration Failing

**Check:**
1. **API key** is correct (copy from Mailchimp dashboard)
2. **Audience** is selected
3. **Test connection** shows success message
4. Mailchimp account is active (not expired trial)

**Common issue:** API key expired or Mailchimp plan downgraded.

### Download Links Expiring Too Quickly

**Fix:**
1. Go to **Settings → General**
2. Increase **Default expiration** from 1 day to 7 days
3. Save settings
4. Re-save individual magnets to apply new default

---

## Best Practices

### Email Deliverability

**To maximize inbox delivery:**
1. Use domain-based from email (sarah@authorsite.com, not sarah@gmail.com)
2. Set up SPF/DKIM records (ask your hosting provider)
3. Use SMTP (SendGrid, Mailgun) instead of WordPress mail()
4. Warm up your domain (send small volumes at first, increase gradually)
5. Include unsubscribe link in every email

### Security

**Recommended settings:**
- ✅ Enable reCAPTCHA
- ✅ Enable honeypot field
- ✅ Rate limit: 5 signups per hour per IP
- ✅ Block disposable email domains
- ✅ Secure link format (long, random)
- ✅ Link expiration: 7 days max
- ✅ Download limit: 3 per signup

### Performance

**For high-traffic sites:**
- Use CDN for file delivery (Cloudflare, BunnyCDN)
- Enable object caching (Redis, Memcached)
- Offload email sending to SMTP service
- Clean database regularly (auto-delete old records)

---

## Next Steps

- [Create your first magnet →](creating-magnets.md)
- [View analytics dashboard →](managing-downloads.md)
- [Customize with developer hooks →](developer-guide.md)

---

**Last Updated:** April 4, 2026
**Requires:** AuthorKit Pro 1.0+
