# License Management

Manage your Free or Pro license for AuthorKit. All license operations are handled through **AuthorKit → Settings → License**.

## Understanding Licenses

### Free License (Default)

**Included with WordPress.org install:**
- ✅ Books module (10 book limit)
- ✅ Reviews module (3 reviews per book)
- ✅ Bookshelf module (mandatory sync)
- ✅ Community support
- ✅ Regular updates via WordPress.org

**No activation required** - Free tier is automatic.

### Pro License (Premium)

**Purchase at authorkit.pro:**
- ✅ Unlimited books and reviews
- ✅ Pro modules (Pages, Launch, Contests)
- ✅ Priority email support
- ✅ Automatic updates
- ✅ 1 year of updates + support
- ✅ Valid for 1 site

**Price:** $79/year (renewable annually)

## Activating a Pro License

### Step 1: Purchase License

1. Visit [authorkit.pro/pricing](https://authorkit.pro/pricing)
2. Select "Pro License"
3. Complete checkout
4. Check email for license key

### Step 2: Activate in WordPress

1. Go to **AuthorKit → Settings → License**
2. Paste license key in "License Key" field
3. Click "Activate License"
4. Wait for confirmation (2-3 seconds)

**Success indicators:**
- Status: "Active"
- Tier: "Pro"
- Expiration date shown
- Pro modules appear in dashboard

### Step 3: Verify Activation

Check that Pro features unlocked:

1. Go to **AuthorKit → Dashboard**
2. Pages, Launch, Contests modules now visible
3. Go to **Books → All Books**
4. No 10-book limit notice

## Managing Your License

### View License Details

**AuthorKit → Settings → License** shows:

- **Status:** Active, Expired, or Invalid
- **Tier:** Free or Pro
- **Key:** First/last 4 characters (middle hidden)
- **Expiration:** Renewal date
- **Site:** Current site URL

### Renew License

**Before expiration:**
1. Log into authorkit.pro account
2. Go to "Licenses"
3. Click "Renew" next to license
4. Complete payment

**After expiration:**
- Pro features continue working
- Updates stop after 1 year
- Renew anytime to resume updates

**Grace period:** 30 days after expiration

### Deactivate License

Move license to another site:

1. Go to **AuthorKit → Settings → License**
2. Click "Deactivate License"
3. Confirm deactivation
4. Tier reverts to Free immediately

**What happens:**
- Pro modules hidden (Pages, Launch, Contests)
- Books limited to 10 visible
- Reviews limited to 3 per book
- Updates revert to WordPress.org

**Important:** Deactivate before moving sites!

### Transfer License

**To move license between sites:**

1. **Old site:** Deactivate license
2. **New site:** Install AuthorKit
3. **New site:** Activate with same key
4. **Verify:** Check license status

**Site limit:** 1 active site per license

## License Validation

### How Validation Works

AuthorKit checks license status:

**Frequency:** Every 24 hours (automatic)

**Process:**
1. WordPress → authorkit.pro API
2. API validates with Lemon Squeezy
3. Returns tier + expiration
4. WordPress updates local status

### Offline Mode

If license API unreachable:

**Behavior:** Cached tier used for 7 days

**Fallback:** After 7 days, tier reverts to Free

**Reason:** Prevents unauthorized Pro access

### Manual Validation

Force license check:

1. Go to **AuthorKit → Settings → License**
2. Click "Revalidate License"
3. Wait for API response
4. Status updates

## Troubleshooting

### License Activation Fails

**Error:** "Invalid license key"

**Causes:**
- Typo in license key
- License already active on another site
- License expired

**Fix:**
1. Copy key carefully (no extra spaces)
2. Deactivate on other sites first
3. Renew if expired
4. Contact support if persists

### License Shows "Expired"

**Error:** "License expired on [date]"

**Fix:**
1. Renew at authorkit.pro
2. No need to re-enter key
3. Status updates automatically within 24 hours
4. Click "Revalidate" for immediate update

### License Deactivation Fails

**Error:** "Could not deactivate license"

**Causes:**
- No internet connection
- API temporarily down

**Fix:**
1. Check internet connection
2. Try again in 5 minutes
3. Contact support to manually deactivate

### Pro Features Not Appearing

**Symptoms:** License active but no Pro modules

**Fix:**
1. Verify license status shows "Pro"
2. Go to **AuthorKit → Dashboard**
3. Refresh page (Ctrl+R or Cmd+R)
4. Clear WordPress cache
5. Check PHP error log

### HTTPS Required Error

**Error:** "HTTPS required for license activation"

**Cause:** License API requires secure connection

**Fix:**
1. Enable SSL certificate on your site
2. Update WordPress URL to `https://`
3. Retry activation

## API Endpoints

License validation uses these endpoints:

**Activate:**
```
POST https://authorkit.pro/api/activate-license
{
  "license_key": "AK-XXXX-XXXX-XXXX",
  "site_url": "https://yoursite.com"
}
```

**Validate:**
```
POST https://authorkit.pro/api/validate-license
{
  "license_key": "AK-XXXX-XXXX-XXXX"
}
```

**Response:**
```json
{
  "status": "active",
  "tier": "pro",
  "expires": "2027-03-07",
  "site_limit": 1
}
```

## Upgrade/Downgrade Flow

### Free → Pro Upgrade

**What happens automatically:**

1. **License activated**
   - Tier changes from Free to Pro
   - Pro modules become available

2. **Limits removed**
   - All books become visible (not just 10)
   - Unlimited reviews allowed
   - Bookshelf syncs all books

3. **No data loss**
   - Books 11+ remain in database
   - Reviews 4+ remain in database
   - Everything becomes visible again

### Pro → Free Downgrade

**What happens on deactivation:**

1. **Tier reverts to Free**
   - Pro modules hidden (Pages, Launch, Contests)
   - Limits enforced

2. **Visibility enforcement**
   - Only 10 oldest books visible
   - Only 3 reviews per book visible
   - Bookshelf syncs only visible books

3. **Data preserved**
   - Books 11+ hidden but NOT deleted
   - Reviews 4+ hidden but NOT deleted
   - Reactivate Pro to restore visibility

**Important:** Downgrade is reversible!

## Security

### License Key Storage

- Encrypted in database
- Not exposed in JavaScript
- Not in HTML source
- Admin-only access

### API Communication

- HTTPS only (SSL required)
- Nonce verification
- Capability checks
- Rate limiting (100 requests/hour)

### Best Practices

- ✅ Use HTTPS for activation
- ✅ Deactivate before moving sites
- ✅ Don't share license keys
- ✅ Keep license info private
- ❌ Don't commit keys to Git
- ❌ Don't activate on development + production

## FAQ

**Q: Can I use one license on multiple sites?**
A: No, each license valid for 1 site. Purchase multiple licenses for multiple sites.

**Q: What happens if I don't renew?**
A: Pro features continue working, but you won't receive updates after 1 year.

**Q: Can I upgrade from Free to Pro anytime?**
A: Yes! Purchase Pro license and activate immediately - no data loss.

**Q: Do I lose my books when downgrading?**
A: No, books are hidden (not deleted). Reactivate Pro to restore them.

**Q: Can I get a refund?**
A: Yes, 30-day money-back guarantee. Email support@authorkit.pro.

## Support

**Free users:**
- [WordPress.org Forums](https://wordpress.org/support/plugin/authorkit/)
- [Documentation](https://docs.authorkit.pro)

**Pro users:**
- Priority email: support@authorkit.pro
- Response time: 24 hours (weekdays)

---

**Last Updated:** March 7, 2026
**Applies to:** AuthorKit Core 1.0.0+
