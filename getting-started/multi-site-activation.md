# Multi-Site License Activation

How to use ONE license key on multiple WordPress sites (Pro Max only).

## How It Works

AuthorKit Pro Max uses a **single key, multiple activation slots** model:

- You receive **ONE license key** (e.g., `A3F2-D8E1-9C4B-7H6K`)
- That key can be activated on **up to 5 WordPress sites**
- You enter the **SAME key** on each site
- You can **deactivate** from any site to free up a slot

**NOT:** 5 separate keys delivered via email ❌

This is the industry standard used by WooCommerce, Gravity Forms, and Advanced Custom Fields.

---

## Activating on Multiple Sites

### Step 1: Activate on First Site

1. Install AuthorKit Free and Pro on your first WordPress site
2. Go to **AuthorKit → Settings → License**
3. Enter your license key: `A3F2-D8E1-9C4B-7H6K`
4. Click **Activate License**
5. Confirm status shows: **Active (1 of 5 sites)**

### Step 2: Activate on Second Site

1. Install AuthorKit Free and Pro on your second WordPress site
2. Go to **AuthorKit → Settings → License**
3. Enter the **SAME license key**: `A3F2-D8E1-9C4B-7H6K`
4. Click **Activate License**
5. Confirm status shows: **Active (2 of 5 sites)**

### Step 3: Repeat for Additional Sites

Repeat the process on sites 3, 4, and 5 using the **same key**.

---

## Checking Activation Status

### In WordPress

Go to **AuthorKit → Settings → License** on any activated site.

**You'll see:**
- **Status:** Active
- **Tier:** Pro
- **Sites Used:** 2 of 5 (example)
- **License Key:** A3F2-****-****-7H6K (partial display)
- **Expires:** 2027-04-04 (or "Lifetime" for lifetime licenses)

### What the Numbers Mean

- **1 of 5:** 1 site activated, 4 slots remaining
- **3 of 5:** 3 sites activated, 2 slots remaining
- **5 of 5:** All slots used, no remaining slots

---

## Deactivating Sites

### Why Deactivate?

- Free up a slot for a different site
- Moved your site to a new domain
- Deleted or shut down a site
- Want to replace a staging site with production

### How to Deactivate

**From the WordPress site:**

1. Go to **AuthorKit → Settings → License**
2. Click **Deactivate License**
3. Confirm deactivation
4. Status changes to: **Inactive (4 of 5 sites)** — slot freed

**Important:** After deactivating, Pro features stop working on that site immediately.

---

## Activation Limit Reached

### Error Message

```
Activation limit reached. This license key is already active on 5 sites.
```

### What This Means

All 5 activation slots are in use. You must deactivate from another site first.

### How to Fix

**Option 1: Deactivate from another site**
1. Log in to one of your other WordPress sites
2. Go to **AuthorKit → Settings → License**
3. Click **Deactivate License**
4. Return to the new site and try activating again

**Option 2: Upgrade to more sites**
Contact support@authorkit.pro to upgrade to a higher license tier (custom pricing available for 10+ sites).

**Option 3: Purchase additional license**
Buy a second Pro Max license for 5 more sites.

---

## Managing Multiple Sites

### Best Practices

**Keep a site list:**
Maintain a spreadsheet of which sites use your license:

| Site URL | Status | Purpose | Activated On |
|----------|--------|---------|--------------|
| authorsite1.com | Active | Production | 2026-04-01 |
| authorsite2.com | Active | Production | 2026-04-02 |
| staging.authorsite1.com | Inactive | Staging (temporary) | - |

**Use staging wisely:**
If you have a staging site, deactivate the license when done testing. Don't waste a permanent slot on temporary environments.

**Name your sites clearly:**
Use descriptive site names so you can identify them later:
- Good: "JohnDoe-MainSite", "JaneDoe-PenName"
- Bad: "Site1", "Site2", "Test"

### Common Scenarios

**Scenario 1: Staging + Production**

You have 1 production site + 1 staging site:
- Activate on **production** permanently (1 of 5)
- Activate on **staging** when testing (2 of 5)
- Deactivate from **staging** after testing (1 of 5)
- Still have 4 slots available for other sites

**Scenario 2: Multiple Pen Names**

You write under 3 pen names with separate sites:
- Activate on **Site 1** (pen name A)
- Activate on **Site 2** (pen name B)
- Activate on **Site 3** (pen name C)
- Still have 2 slots for future pen names or client sites

**Scenario 3: Agency with Client Sites**

You build author sites for 4 clients:
- Activate on **Client 1** site
- Activate on **Client 2** site
- Activate on **Client 3** site
- Activate on **Client 4** site
- 1 slot remaining for future clients

---

## Transferring Between Sites

### Moving a Site to a New Domain

**Old domain:** oldauthorsite.com
**New domain:** newauthorsite.com

**Steps:**

1. **On old site:** Go to **AuthorKit → Settings → License** → Click **Deactivate**
2. **Migrate site:** Move WordPress to new domain (via your host or migration plugin)
3. **On new site:** Go to **AuthorKit → Settings → License** → Enter key → Click **Activate**

**Important:** Deactivate on the old domain BEFORE migrating to avoid counting it twice.

### Replacing a Site

**Scenario:** Shutting down Site A, launching Site B

**Steps:**

1. **On Site A:** Deactivate license (frees 1 slot)
2. **On Site B:** Install AuthorKit Free + Pro
3. **On Site B:** Activate with your license key

**No waiting period** — you can reuse slots immediately.

---

## Troubleshooting

### "License already active on another site" Error

**Cause:** You're trying to activate on a 6th site when all 5 slots are full.

**Fix:**
1. Check how many sites are using the license
2. Deactivate from a site you no longer use
3. Try activating again

### Can't Remember Which Sites Are Activated

**Solution:**
Contact support@authorkit.pro with your license key. We can tell you:
- Which domains have active activations
- When each site was activated
- How many slots are in use

### Accidentally Activated on Wrong Site

**Fix:**
1. Go to that site's **AuthorKit → Settings → License**
2. Click **Deactivate License**
3. Slot is freed immediately
4. Activate on the correct site

### Domain Changed, Can't Deactivate Old Domain

**Scenario:** Site was at oldsite.com, now at newsite.com. Can't access old domain to deactivate.

**Fix:**
Contact support@authorkit.pro with:
- Your license key
- Old domain name
- New domain name

We'll manually deactivate the old domain so you can activate the new one.

---

## Frequently Asked Questions

### Do I get 5 separate license keys?

**No.** You get **ONE key** that works on **5 sites**. Enter the same key on each site.

### Can I use the key on 3 sites and give 2 slots to a friend?

**No.** License keys are non-transferable. All 5 activations must be for sites you own/manage.

### What if I need more than 5 sites?

Contact support@authorkit.pro for custom pricing on 10-site, 25-site, or unlimited-site licenses.

### Can I have unlimited staging sites?

Yes, as long as you **deactivate** after testing. Activate on staging when testing, deactivate when done. Repeat as needed.

### Does each site need separate WordPress installs?

**Yes.** Each of the 5 activations must be on a separate WordPress installation. Multisite networks count as 1 activation (all subsites share the license).

### What happens if I exceed 5 sites?

The 6th site will fail to activate with an "Activation limit reached" error. You must deactivate from another site first.

### Can I move activations between sites anytime?

**Yes.** Deactivate from Site A, activate on Site B. No limits on how often you can do this.

### Do activations carry over when I renew?

**Yes (Annual licenses).** When you renew your Pro Max Annual license, your existing activations remain active. No need to re-enter keys.

---

## Multi-Site WordPress (WordPress Multisite)

### How Licenses Work with Multisite

If you use **WordPress Multisite**, the license applies to the **entire network**, not individual subsites.

**Example:**
- Network: authornetwork.com
- Subsites: author1.authornetwork.com, author2.authornetwork.com, author3.authornetwork.com

**Activation:** 1 license activation covers the entire network (counts as 1 of 5 sites).

**Benefits:**
- Activate once on network, all subsites get Pro features
- Only uses 1 of your 5 slots
- Great for publishers managing many authors

**Note:** Each subsite still needs AuthorKit Free + Pro installed network-wide.

---

## Compare to Other Plugins

AuthorKit's multi-site licensing is identical to industry leaders:

| Plugin | Model |
|--------|-------|
| **WooCommerce** | 1 key, 5 activations (Pro tier) |
| **Gravity Forms** | 1 key, 3 or 15 activations (Pro/Elite) |
| **Advanced Custom Fields Pro** | 1 key, unlimited activations |
| **AuthorKit Pro Max** | 1 key, 5 activations ✓ |

**Why this model?**
- Simpler than managing 5 separate keys
- Industry standard (customers understand it)
- Self-service (deactivate/reactivate without support)
- More secure (one key to protect, not five)

---

## Need Help?

**Can't activate?** Check our [License Troubleshooting Guide](../authorkit-core/license-management.md#troubleshooting)

**Need to upgrade to more sites?** Email support@authorkit.pro

**Questions?** Reply to your purchase email or visit [authorkit.pro/support](https://authorkit.pro/support)

---

**Last Updated:** April 4, 2026
**Applies to:** AuthorKit Pro Max 1.0+
