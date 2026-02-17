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
- ✅ Any properly coded WordPress theme
- ✅ Classic Editor and Gutenberg
- ✅ Most page builders (Elementor, Beaver Builder, Divi, etc.)
- ✅ WooCommerce (optional integration)
- ✅ Multisite installations

---

## Installation Methods

### Method 1: WordPress.org (Recommended)

**For: AuthorKit Core, AuthorKit for Books** (Free plugins)

1. Log in to WordPress admin
2. Go to **Plugins → Add New**
3. Search for the plugin name
4. Click **Install Now**
5. Click **Activate**

✅ **That's it!** The plugin is now active.

### Method 2: Upload via WordPress Admin

**For: Premium plugins or manual installation**

1. Download the plugin ZIP file
2. Go to **Plugins → Add New → Upload Plugin**
3. Click **Choose File** and select the ZIP
4. Click **Install Now**
5. Click **Activate**

### Method 3: FTP Upload

**For: Advanced users**

1. Download and extract the plugin ZIP file
2. Upload the extracted folder to `/wp-content/plugins/` via FTP
3. Go to **Plugins** in WordPress admin
4. Find the plugin and click **Activate**

---

## Installation Order

⚠️ **Important**: Install plugins in this order:

### 1. Install Core First
```
✅ AuthorKit Core (required for all other plugins)
```

### 2. Install Modules
```
📚 AuthorKit for Books (requires Core)
⭐ AuthorKit for Reviews (requires Core + Books) - Coming Soon
🎁 AuthorKit for Contests (requires Core) - Coming Soon
```

### 3. Install Premium Add-ons (Optional)
```
💎 Premium modules (require Core + respective free module)
```

---

## Post-Installation

### Step 1: Verify Installation

1. Go to **Plugins** in WordPress admin
2. Confirm all plugins show as "Active"
3. Look for the **AuthorKit** menu in the sidebar

### Step 2: Configure Settings

1. Go to **AuthorKit → Settings**
2. Review general settings
3. Configure license keys (for premium plugins)

### Step 3: Activate License (Premium Only)

1. Go to **AuthorKit → License**
2. Enter your license key
3. Click **Activate License**
4. Confirm "License Active" status

### Step 4: Start Using

- **Books**: Go to **AuthorKit for Books → Add New**
- **Reviews**: Configure in **AuthorKit → Settings → Reviews**
- **Contests**: Go to **AuthorKit for Contests → Add New**

---

## Troubleshooting Installation

### Plugin Not Appearing After Activation

**Solution**:
1. Deactivate and reactivate the plugin
2. Clear your browser cache
3. Check for JavaScript errors in browser console

### "Plugin requires AuthorKit Core" Error

**Solution**:
1. Install and activate AuthorKit Core first
2. Then activate the module plugin

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

⚠️ **Warning**: This will delete all books, reviews, and settings!

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
