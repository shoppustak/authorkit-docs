# Installation Guide

Complete installation instructions for all AuthorKit plugins.

## Before You Begin

### System Requirements

- **WordPress**: 5.0 or higher
- **PHP**: 7.0 or higher
- **MySQL**: 5.6 or higher
- **HTTPS**: Recommended (not required)

### Compatibility

AuthorKit works with:
- Any properly coded WordPress theme
- Classic Editor and Gutenberg
- Most page builders (Elementor, Beaver Builder, Divi, etc.)
- WooCommerce (optional integration)
- Multisite installations

---

## Installation Methods

### Method 1: WordPress.org (Recommended)

**For: AuthorKit Free plugin**

1. Log in to WordPress admin
2. Go to **Plugins → Add New**
3. Search for "AuthorKit"
4. Click **Install Now**
5. Click **Activate**

The free plugin is now active with Books, Reviews, and Bookshelf features (with limits).

### Method 2: Upload via WordPress Admin

**For: AuthorKit Pro add-on or manual installation**

1. Download the plugin ZIP file from your purchase email
2. Go to **Plugins → Add New → Upload Plugin**
3. Click **Choose File** and select the ZIP
4. Click **Install Now**
5. Click **Activate**

**Important for Pro:** AuthorKit Free must be installed and activated FIRST before installing Pro add-on.

### Method 3: FTP Upload

**For: Advanced users**

1. Download and extract the plugin ZIP file
2. Upload the extracted folder to `/wp-content/plugins/` via FTP
3. Go to **Plugins** in WordPress admin
4. Find the plugin and click **Activate**

---

## Installation Order

**Important**: Install in this order:

### 1. Install AuthorKit Free First
```
AuthorKit Free (from WordPress.org)
  ↳ Includes: Books, Reviews, Bookshelf (with limits)
```

### 2. Install AuthorKit Pro (Optional)
```
AuthorKit Pro add-on (purchased from authorkit.pro)
  ↳ Requires: AuthorKit Free must be installed first
  ↳ Adds: Contests module, Reader Magnets module, removes limits
```

**Pro is a companion plugin** - it extends AuthorKit Free with additional features. It's not a standalone plugin.

---

## Installing Pro Add-on

### Prerequisites

Before installing Pro:
1. Install and activate **AuthorKit Free** from WordPress.org
2. Purchase a Pro license from [authorkit.pro/pricing](https://authorkit.pro/pricing)
3. Check your email for the download link and license key

### Installation Steps

1. **Download Pro ZIP** from your purchase confirmation email
2. Go to **Plugins → Add New → Upload Plugin** in WordPress
3. Choose the `authorkit-pro.zip` file
4. Click **Install Now**
5. Click **Activate**
6. Go to **AuthorKit → Settings → License**
7. Enter your license key and click **Activate License**

### Verify Pro is Working

After activation, you should see:
- **AuthorKit → Contests** menu item appears
- **AuthorKit → Magnets** menu item appears
- No more 10-book limit on Books page
- License status shows "Active" and "Pro" tier

---

## Post-Installation

### Step 1: Verify Installation

1. Go to **Plugins** in WordPress admin
2. Confirm AuthorKit Free (and Pro if purchased) show as "Active"
3. Look for the **AuthorKit** menu in the sidebar

### Step 2: Configure Settings

1. Go to **AuthorKit → Settings**
2. Review general settings
3. Configure Bookshelf sync preferences

### Step 3: Activate Pro License (Pro Users Only)

If you purchased Pro:
1. Go to **AuthorKit → Settings → License**
2. Enter your license key
3. Click **Activate License**
4. Confirm "License Active" status and "Pro" tier

### Step 4: Start Using

- **Books**: Go to **Books → Add New** (Free: 10 max, Pro: unlimited)
- **Reviews**: Add reviews to any book (Free: 3 per book, Pro: unlimited)
- **Contests**: Go to **Contests → Add New** (Pro only)
- **Magnets**: Go to **Magnets → Add New** (Pro only)

---

## Troubleshooting Installation

### Plugin Not Appearing After Activation

**Solution**:
1. Deactivate and reactivate the plugin
2. Clear your browser cache
3. Check for JavaScript errors in browser console

### "Plugin requires AuthorKit Free" Error

**Solution**:
1. Install and activate AuthorKit Free from WordPress.org first
2. Then install and activate AuthorKit Pro add-on

### White Screen After Activation

**Solution**:
1. Increase PHP memory limit (add to wp-config.php):
   ```php
   define('WP_MEMORY_LIMIT', '256M');
   ```
2. Contact your hosting provider

### Plugin Conflicts

**Solution**:
1. Deactivate all other plugins
2. Activate AuthorKit plugins only
3. Reactivate other plugins one by one to find the conflict
4. [Report the conflict](mailto:support@authorkit.pro)

---

## Uninstallation

### Deactivating vs Deleting

- **Deactivate**: Turns off the plugin but keeps all data
- **Delete**: Removes the plugin AND all data (irreversible!)

### How to Uninstall

1. Deactivate the plugin first
2. Go to **Plugins → Installed Plugins**
3. Find the plugin and click **Delete**
4. Confirm deletion

**Warning**: This will delete all books, reviews, and settings.

### Data Export Before Uninstall

1. Go to **AuthorKit → Tools → Export**
2. Download your data as JSON/CSV
3. Save the file safely before deleting

---

## Need Help?

- [FAQ](faq.md)
- [Common Issues](../troubleshooting/common-issues.md)
- [Community Forum](https://wordpress.org/support/plugin/authorkit/)
- [Premium Support](mailto:support@authorkit.pro)
