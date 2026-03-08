# Settings & Configuration

Configure AuthorKit Core to match your needs. All settings are found under **AuthorKit → Settings** in your WordPress admin.

## General Settings

Navigate to **AuthorKit → Settings → General**

### Cache Duration

**Default:** 12 hours

Controls how long book queries and review aggregations are cached for optimal performance.

```
Recommended values:
- High traffic sites: 6 hours
- Medium traffic: 12 hours (default)
- Low traffic: 24 hours
```

**To change:**
1. Enter duration in hours (1-48)
2. Click "Save Changes"
3. Clear existing cache if needed

### Debug Mode

**Default:** Disabled

Enables detailed logging for troubleshooting. Logs are written to `/wp-content/debug.log`.

**When to enable:**
- Troubleshooting errors
- Testing custom code
- Reporting bugs to support

**Warning:** Disable on production sites (slows performance).

### Uninstall Behavior

**Default:** Remove all data

Choose what happens when you delete AuthorKit:

- **Remove all data** - Complete cleanup (books, reviews, settings deleted)
- **Keep data** - Only remove plugin files (data remains for reinstall)

**Recommendation:** Keep data unless you're permanently removing AuthorKit.

## License Settings

Navigate to **AuthorKit → Settings → License**

### License Activation

**For Free users:** Status shows "Free" - no action needed.

**For Pro users:**
1. Paste your license key from authorkit.pro
2. Click "Activate License"
3. Status changes to "Active (Pro)"

### License Information

View current license details:
- **Status:** Active, Expired, or Invalid
- **Tier:** Free or Pro
- **Expiration:** License renewal date
- **Sites:** Sites using this license

### Deactivation

To move your license to another site:
1. Click "Deactivate License"
2. Install on new site
3. Activate with same key

**Note:** Each license valid for 1 site.

## Module Settings

Navigate to **AuthorKit → Dashboard**

### Enable/Disable Modules

Toggle modules on/off to improve performance:

**Books Module**
- Toggle: ON by default
- Dependencies: None
- Impact: Disables book management entirely

**Reviews Module**
- Toggle: ON by default
- Dependencies: Requires Books
- Impact: Removes review functionality

**Bookshelf Module**
- Toggle: ON by default
- Dependencies: Requires Books
- Impact: Disables bookshelf sync

**Pro Modules** (Pro license required)
- Pages, Launch, Contests
- Automatically enabled on Pro activation

### Performance Tip

Disable unused modules to:
- Reduce database queries
- Decrease page load time
- Simplify admin interface

## Advanced Settings

### Database Optimization

**Automatic cleanup runs:**
- Every 7 days (post revisions)
- Every 30 days (transients)
- On uninstall (if configured)

**Manual cleanup:**
```bash
# Via WP-CLI
wp authorkit cache clear
wp authorkit optimize-database
```

### Template Override

**Default template location:** `/wp-content/plugins/authorkit/templates/`

**Override in your theme:**
1. Create folder: `/wp-content/themes/your-theme/authorkit/`
2. Copy template from plugin
3. Customize as needed
4. Theme template takes priority

### Security Settings

All security settings are automatic:

- ✅ Nonce verification on all forms
- ✅ Capability checks on admin actions
- ✅ SQL injection prevention (prepared statements)
- ✅ XSS protection (escaped output)
- ✅ CSRF protection

**No configuration needed** - security enabled by default.

## Import/Export Settings

### Export Configuration

Backup your settings before making changes:

1. Go to **AuthorKit → Settings → General**
2. Scroll to "Import/Export"
3. Click "Export Settings"
4. Save JSON file

### Import Configuration

Restore settings on new install:

1. Go to **AuthorKit → Settings → General**
2. Click "Choose File"
3. Select exported JSON
4. Click "Import Settings"

**Note:** License keys are NOT included in exports (security).

## Multisite Settings

For WordPress multisite installations:

### Network Activation

Activate AuthorKit network-wide:
1. Go to **Network Admin → Plugins**
2. Click "Network Activate" under AuthorKit

**Result:** All subsites get AuthorKit automatically.

### Per-Site Activation

Activate only on specific subsites:
1. Visit subsite admin
2. Go to **Plugins**
3. Activate AuthorKit normally

### License Management

**Option 1: Network License**
- Activate in Network Admin
- Applies to all subsites

**Option 2: Per-Site Licenses**
- Each subsite manages own license
- Useful for different site owners

## REST API Settings

AuthorKit exposes REST API endpoints for external integrations.

### Endpoint Base

```
https://yoursite.com/wp-json/authorkit/v1/
```

### Available Endpoints

- `/books` - List books
- `/reviews` - List reviews
- `/book/{id}` - Get single book
- `/stats` - Get book statistics

### Authentication

**Public endpoints:** No auth required
**Admin endpoints:** Require valid API key

**Generate API key:**
1. Go to **AuthorKit → Settings → API**
2. Click "Generate New Key"
3. Copy key for use in requests

### Example Request

```bash
curl https://yoursite.com/wp-json/authorkit/v1/books
```

## Troubleshooting Settings

### Settings Not Saving

**Cause:** Caching plugin interference

**Fix:**
1. Clear all caches (plugin + server)
2. Disable caching temporarily
3. Save settings again
4. Re-enable caching

### License Activation Fails

**Cause:** HTTPS not enabled or license expired

**Fix:**
1. Enable HTTPS (required for license API)
2. Check license hasn't expired
3. Verify license key is correct
4. Contact support if issue persists

### Module Won't Disable

**Cause:** Dependencies exist

**Fix:**
- Reviews depends on Books - disable Reviews first
- Bookshelf depends on Books - disable Bookshelf first
- Then disable Books

## Default Settings Reference

Quick reference for default values:

```
Cache Duration: 12 hours
Debug Mode: Disabled
Uninstall: Remove all data
License: Free tier
Modules: All enabled (Books, Reviews, Bookshelf)
API Access: Disabled (require key generation)
Template Override: Disabled
Database Cleanup: Every 7 days
```

## Next Steps

- **[License Management](license-management.md)** - Activate Pro license
- **[Developer Reference](developer-reference.md)** - Custom integrations
- **[Books Module](../authorkit-for-books/overview.md)** - Add your first book

---

**Last Updated:** March 7, 2026
**Applies to:** AuthorKit Core 1.0.0+
