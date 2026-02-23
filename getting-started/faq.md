# Frequently Asked Questions

## General Questions

### What is AuthorKit?

AuthorKit is a modular suite of WordPress plugins specifically designed for self-publishing authors. It helps you showcase books, manage reviews, run giveaways, and build a professional author website.

### Is AuthorKit free?

**Core and basic modules are free:**
- AuthorKit Core - Free
- AuthorKit Books - Free
- AuthorKit Reviews - Free (coming Q2 2026)
- AuthorKit Contests - Free (coming Q2 2026)

**Premium add-ons are paid:**
- Launch Countdown, Landing Pages, Series Tracker, etc. - Paid (coming Q3 2026)

### Do I need coding skills?

No! AuthorKit is designed for non-technical authors. The interface is intuitive and user-friendly. However, developers can extend functionality using our hooks and filters.

### Will AuthorKit work with my theme?

Yes! AuthorKit works with any properly coded WordPress theme. If you experience theme compatibility issues, [contact support](mailto:support@authorkit.pro).

---

## Installation & Setup

### What are the system requirements?

- WordPress 5.0+
- PHP 7.0+
- MySQL 5.6+
- HTTPS recommended

### In what order should I install plugins?

1. AuthorKit Core (required first)
2. AuthorKit Books
3. AuthorKit Reviews (when available)
4. AuthorKit Contests (when available)
5. Premium add-ons (if purchased)

### How do I update AuthorKit?

Free plugins update through WordPress.org automatically. Premium plugins update via license activation.

---

## Books Module

### How many books can I add?

Unlimited! There's no limit to the number of books you can add.

### Can I add books in multiple formats (Kindle, Paperback, Audio)?

Yes! Each book supports multiple formats with separate purchase links for each.

### Can I add books that haven't been published yet?

Yes! Use the "Coming Soon" feature to display upcoming books with release dates.

### Can I import books from another plugin?

Yes, use the Import/Export tool. [Learn more](../advanced-topics/import-export.md)

---

## Display & Design

### How do I display books on my website?

Use shortcodes! Example:
```
[authorkit_books count="6" columns="3"]
```
[View all shortcode options](../authorkit-books/shortcodes/overview.md)

### Can I customize the book display?

Yes! You can:
- Use custom CSS
- Override templates in your theme
- Use theme customizer settings
- Hire a developer for advanced customization

### Will books display properly on mobile?

Yes! All displays are fully responsive and mobile-optimized.

---

## Performance

### Will AuthorKit slow down my site?

No! AuthorKit is built with performance in mind:
- Vanilla PHP/JavaScript (no dependencies)
- Minimal database queries
- Optimized CSS/JS loading
- No external API calls

### How many books can I have before performance is affected?

AuthorKit can handle thousands of books without performance issues. We recommend:
- Optimize images (use proper sizes)
- Enable caching plugin
- Use a good hosting provider

---

## Compatibility

### Does AuthorKit work with page builders?

Yes! Works with:
- Elementor
- Beaver Builder
- Divi
- Gutenberg (Block Editor)
- WPBakery
- Most other builders

### Can I use AuthorKit with WooCommerce?

Yes! AuthorKit works alongside WooCommerce. You can:
- Display books as informational content
- Link to WooCommerce products
- Use both systems independently

### Does AuthorKit work on multisite?

Yes! AuthorKit is multisite compatible. Activate network-wide or per-site.

---

## Licensing & Premium

### How do premium licenses work?

- **Pro**: 1 site license + 1 year updates/support
- **Agency**: Unlimited sites + 1 year updates/support

### What happens when my license expires?

- Plugins continue working
- No more updates or support
- Renew anytime to restore access

### Can I use one license on multiple sites?

- **Pro**: 1 site only
- **Agency**: Unlimited sites

### Do you offer refunds?

Yes! 30-day money-back guarantee on all premium purchases.
[View Refund Policy](https://authorkit.pro/pages/refund-policy.html)

---

## Support

### Where can I get help?

**Free Users**:
- [Documentation](/)
- [Community Forum](https://wordpress.org/support/plugin/authorkit/)

**Premium Users**:
- Priority email support: [support@authorkit.pro](mailto:support@authorkit.pro)
- All of the above

### How fast is support response?

- **Free**: 24-48 hours via community forum
- **Premium**: Within 24 hours via email

### Can you help with custom development?

We don't offer custom development, but we can recommend trusted developers familiar with AuthorKit.

---

## Data & Privacy

### Where is my data stored?

All data is stored in your WordPress database. We don't store any data on external servers.

### Can I export my data?

Yes! Use **AuthorKit → Tools → Export** to download all your data as JSON/CSV.

### Is my data safe?

Yes! AuthorKit follows WordPress security best practices. Always keep WordPress and plugins updated.

---

## Common Issues

### Books not displaying on my site

**Solutions**:
1. Flush permalinks: **Settings → Permalinks → Save Changes**
2. Check if book is published (not draft)
3. Verify shortcode syntax
4. Check theme compatibility

### Images not showing correctly

**Solutions**:
1. Regenerate thumbnails
2. Check image file sizes (recommended: 600x900px for covers)
3. Verify file permissions

### Shortcodes showing as text

**Solutions**:
1. Ensure AuthorKit Books is activated
2. Check shortcode spelling
3. Disable conflicting plugins

[View more troubleshooting](../troubleshooting/common-issues.md)

---

## Still Have Questions?

- [Search the documentation](/)
- [Ask in community forum](https://wordpress.org/support/plugin/authorkit/)
- [Contact premium support](mailto:support@authorkit.pro)
