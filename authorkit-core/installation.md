# Installing AuthorKit Core

This guide walks you through installing AuthorKit Core, the foundation plugin required for all AuthorKit modules.

## Before You Begin

### System Requirements Check

Ensure your WordPress site meets these requirements:

- ✅ WordPress 5.8 or higher
- ✅ PHP 7.4 or higher (PHP 8.0+ recommended)
- ✅ MySQL 5.7+ or MariaDB 10.3+
- ✅ HTTPS enabled (recommended for license activation)

**How to check:**
1. Go to **WordPress Admin → Tools → Site Health**
2. Click "Info" tab
3. Check WordPress version, PHP version, and database version

### What You'll Need

- WordPress admin access (Administrator role required)
- About 5 minutes of time
- (Optional) Pro license key from authorkit.pro

## Installation Methods

Choose the method that works best for you:

### Method 1: WordPress Plugin Directory (Recommended)

**Best for:** Most users

1. **Log into WordPress Admin**
   - Navigate to **Plugins → Add New**

2. **Search for AuthorKit**
   - Type "AuthorKit" in the search box
   - Look for "AuthorKit Core" by AuthorKit Team

3. **Install the Plugin**
   - Click "Install Now" button
   - Wait for installation to complete (10-15 seconds)

4. **Activate the Plugin**
   - Click "Activate" button
   - You'll be redirected to the AuthorKit dashboard

**Success!** AuthorKit Core is now installed and active.

### Method 2: Manual Upload

**Best for:** Users with custom setups or downloaded ZIP files

1. **Download the Plugin**
   - Visit [wordpress.org/plugins/authorkit](https://wordpress.org/plugins/authorkit/)
   - Click "Download" button
   - Save `authorkit.zip` to your computer

2. **Upload to WordPress**
   - Go to **Plugins → Add New → Upload Plugin**
   - Click "Choose File" and select `authorkit.zip`
   - Click "Install Now"

3. **Activate the Plugin**
   - Click "Activate Plugin" after installation completes
   - You'll see the AuthorKit dashboard

### Method 3: FTP/SFTP Upload

**Best for:** Developers or users with server access

1. **Download and Extract**
   - Download `authorkit.zip` from WordPress.org
   - Extract the ZIP file on your computer
   - You'll have an `authorkit/` folder

2. **Upload via FTP**
   - Connect to your server via FTP/SFTP
   - Navigate to `/wp-content/plugins/`
   - Upload the entire `authorkit/` folder

3. **Activate in WordPress**
   - Go to **Plugins → Installed Plugins**
   - Find "AuthorKit Core"
   - Click "Activate"

### Method 4: WP-CLI (Advanced)

**Best for:** Developers and automation

```bash
# Install from WordPress.org
wp plugin install authorkit --activate

# Or install from local ZIP
wp plugin install /path/to/authorkit.zip --activate

# Verify installation
wp plugin list | grep authorkit
```

## First-Time Setup

After activation, you'll see the **AuthorKit Welcome Screen**:

### 1. Dashboard Overview

The AuthorKit dashboard shows:

- **Module Cards**: Books, Reviews, Bookshelf (all enabled by default)
- **License Status**: "Free" tier active
- **Quick Actions**: Links to settings, documentation, support

### 2. Enable/Disable Modules

By default, all free modules are enabled. To disable a module:

1. Go to **AuthorKit → Dashboard**
2. Find the module card (e.g., "Books")
3. Toggle the switch to OFF
4. Click "Save Changes"

**Note:** You can disable modules you don't need to improve performance.

### 3. Configure Basic Settings

Navigate to **AuthorKit → Settings**:

**General Tab:**
- Uninstall behavior (keep or remove data on uninstall)
- Debug mode (for troubleshooting)
- Performance settings (cache duration)

**License Tab:**
- Enter Pro license key (if purchased)
- View license status and expiration
- Manage license activation

## Installing Additional Modules

AuthorKit Core is just the foundation. Install these modules as needed:

### AuthorKit Books (Free)

Manage your book catalog with 27+ custom fields.

**Install:**
1. Go to **Plugins → Add New**
2. Search "AuthorKit Books"
3. Click "Install Now" → "Activate"

**Result:** Books module appears in AuthorKit dashboard

### AuthorKit Reviews (Free)

Add Amazon-style reviews to your books.

**Install:**
1. Go to **Plugins → Add New**
2. Search "AuthorKit Reviews"
3. Click "Install Now" → "Activate"

**Requires:** AuthorKit Core + AuthorKit Books

### AuthorKit Bookshelf (Free)

Showcase your books on bookshelf.authorkit.pro directory.

**Install:**
1. Go to **Plugins → Add New**
2. Search "AuthorKit Bookshelf"
3. Click "Install Now" → "Activate"

**Requires:** AuthorKit Core + AuthorKit Books

### AuthorKit Pro (Premium)

Unlocks Pages, Launch, and Contests modules + unlimited limits.

**Install:**
1. Purchase license at [authorkit.pro](https://authorkit.pro)
2. Download ZIP from your account
3. Upload via **Plugins → Add New → Upload Plugin**
4. Activate and enter license key

**Requires:** AuthorKit Core + respective module plugins

## Activating a Pro License

If you purchased AuthorKit Pro:

1. **Get Your License Key**
   - Log into your account at authorkit.pro
   - Go to "Downloads & Licenses"
   - Copy your license key

2. **Activate in WordPress**
   - Go to **AuthorKit → Settings → License**
   - Paste license key in "License Key" field
   - Click "Activate License"

3. **Verify Activation**
   - Status should show "Active"
   - Tier should change from "Free" to "Pro"
   - Pro features unlock immediately

**Troubleshooting:**
- Ensure HTTPS is enabled on your site
- Check that your license hasn't expired
- Verify you haven't exceeded site limit (1 site per license)

## Verifying Installation

### Quick Verification Checklist

✅ **AuthorKit Dashboard appears** in WordPress admin sidebar
✅ **Module cards display** on dashboard (Books, Reviews, Bookshelf)
✅ **No error messages** appear on activation
✅ **Settings page loads** without errors
✅ **License status shows** "Free" (or "Pro" if activated)

### Test Core Functionality

1. **Check Cache System**
   - Go to **AuthorKit → Settings → General**
   - Cache settings should be visible
   - Default: 12 hours cache duration

2. **Verify Module Loading**
   - Dashboard cards should have ON/OFF toggles
   - Toggling should work without errors
   - Disabled modules shouldn't load assets

3. **Test Template System**
   - Create a test page
   - Template loader should work without errors

## Common Installation Issues

### Issue: "Plugin could not be activated"

**Cause:** PHP version too old or memory limit too low

**Fix:**
1. Check PHP version: **Tools → Site Health → Info**
2. Upgrade to PHP 7.4+ (contact your host)
3. Increase memory limit (add to wp-config.php):
   ```php
   define('WP_MEMORY_LIMIT', '128M');
   ```

### Issue: "The plugin does not have a valid header"

**Cause:** Incorrect upload (double-nested folder)

**Fix:**
1. Delete the plugin via FTP
2. Extract ZIP correctly (should have `authorkit/authorkit.php`, not `authorkit/authorkit/authorkit.php`)
3. Re-upload correctly

### Issue: "Fatal error: Cannot redeclare..."

**Cause:** Plugin conflict or duplicate installation

**Fix:**
1. Deactivate all other plugins
2. Activate AuthorKit Core alone
3. Reactivate other plugins one by one to find conflict

### Issue: White screen after activation

**Cause:** Memory limit or PHP error

**Fix:**
1. Enable debug mode in `wp-config.php`:
   ```php
   define('WP_DEBUG', true);
   define('WP_DEBUG_LOG', true);
   ```
2. Check `/wp-content/debug.log` for errors
3. Increase memory limit or fix conflicting code

## Updating AuthorKit Core

### Automatic Updates (Recommended)

WordPress notifies you when updates are available:

1. Go to **Dashboard → Updates**
2. Check the box next to "AuthorKit Core"
3. Click "Update Plugins"

**Note:** Pro users get automatic updates. Free users update via WordPress.org.

### Manual Update

If automatic updates fail:

1. **Backup First**
   - Use a backup plugin (e.g., UpdraftPlus)
   - Or manually backup via hosting control panel

2. **Deactivate (Don't Delete)**
   - Go to **Plugins → Installed Plugins**
   - Click "Deactivate" under AuthorKit Core
   - Your data remains intact

3. **Delete Old Version**
   - Click "Delete" after deactivating
   - Confirm deletion

4. **Install New Version**
   - Follow installation steps above
   - Activate the plugin

5. **Verify Data Intact**
   - Check that your settings survived
   - Test module functionality

## Uninstalling AuthorKit Core

If you need to remove AuthorKit completely:

### Before Uninstalling

**⚠️ Warning:** Uninstalling removes ALL AuthorKit data (books, reviews, settings) unless you configure data retention.

**To Keep Your Data:**
1. Go to **AuthorKit → Settings → General**
2. Find "Uninstall Behavior"
3. Select "Keep data on uninstall"
4. Save changes

### Uninstall Steps

1. **Deactivate Modules First**
   - Deactivate Books, Reviews, Bookshelf, etc.
   - Then deactivate AuthorKit Core

2. **Delete Plugin**
   - Go to **Plugins → Installed Plugins**
   - Click "Delete" under AuthorKit Core
   - Confirm deletion

3. **Verify Cleanup**
   - Check **Posts** menu (custom post types removed)
   - Check **Settings** (AuthorKit menu removed)
   - Check database (tables removed if configured)

### Manual Cleanup (If Needed)

If uninstall doesn't clean up completely:

```sql
-- Delete AuthorKit options
DELETE FROM wp_options WHERE option_name LIKE 'authorkit_%';

-- Delete book posts
DELETE FROM wp_posts WHERE post_type = 'authorkit_book';

-- Delete review posts
DELETE FROM wp_posts WHERE post_type = 'authorkit_review';

-- Delete post meta
DELETE FROM wp_postmeta WHERE post_id NOT IN (SELECT ID FROM wp_posts);
```

**Caution:** Only run SQL if you know what you're doing. Backup first!

## Next Steps

Now that AuthorKit Core is installed:

- **[Configure Settings](settings-and-configuration.md)** - Customize your setup
- **[Activate License](license-management.md)** - Upgrade to Pro (optional)
- **[Install Books Module](../authorkit-for-books/overview.md)** - Start adding books
- **[Developer Reference](developer-reference.md)** - Extend with custom code

## Need Help?

- **Community Support**: [WordPress.org Forums](https://wordpress.org/support/plugin/authorkit/)
- **Documentation**: [docs.authorkit.pro](https://docs.authorkit.pro)
- **Pro Support**: Email support@authorkit.pro (Pro users only)
- **Bug Reports**: [GitHub](https://github.com/shoppustak/authorkit/issues)

---

**Last Updated**: March 7, 2026
**Applies to**: AuthorKit Core 1.0.0+
