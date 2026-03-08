# AuthorKit Core Overview

AuthorKit Core is the foundation plugin that powers the entire AuthorKit ecosystem. It provides the shared infrastructure, settings management, and licensing system that all other AuthorKit modules depend on.

## What is AuthorKit Core?

AuthorKit Core is a **required foundation plugin** that must be installed before any other AuthorKit modules (Books, Reviews, Bookshelf, etc.). Think of it as the engine that makes everything else run smoothly.

### Key Responsibilities

**1. Plugin Infrastructure**
- Shared settings API for all modules
- Centralized cache management for optimal performance
- Database optimization and query management
- Security and data sanitization layer

**2. License Management**
- Free tier activation and validation
- Pro license activation and renewal
- Automatic tier detection (Free vs Pro)
- Seamless upgrade/downgrade handling

**3. Module Coordination**
- Loads and initializes all enabled modules
- Manages module dependencies
- Handles module activation/deactivation
- Enforces tier-based feature availability

**4. Template System**
- Shared template loader for all modules
- Theme compatibility layer
- Custom template override support
- Gutenberg block registration

## Free vs Pro Features

### Free Features (WordPress.org)

AuthorKit Core is **100% free** and includes:

- ✅ Full settings management
- ✅ Template system and theme compatibility
- ✅ Performance optimization (caching, database)
- ✅ Security layer (sanitization, validation, nonce checks)
- ✅ Developer hooks and filters
- ✅ Support for all free modules (Books, Reviews, Bookshelf)

### Pro Features (authorkit.pro)

When you activate a Pro license, Core unlocks:

- ✅ Pro module loading (Pages, Launch, Contests)
- ✅ Unlimited limits for Books and Reviews
- ✅ Priority support
- ✅ Advanced customization options
- ✅ Automatic updates for Pro modules

## System Requirements

**WordPress:**
- Version 5.8 or higher
- PHP 7.4 or higher (8.0+ recommended)
- MySQL 5.7+ or MariaDB 10.3+

**Server:**
- Memory: 64MB minimum (128MB recommended)
- Disk space: 5MB for Core
- HTTPS recommended for license activation

**Recommended Plugins:**
- None required! AuthorKit Core has zero dependencies

## Core Architecture

AuthorKit Core uses a **modular monolithic architecture**:

```
AuthorKit Core (Foundation)
    │
    ├── Books Module (Optional)
    ├── Reviews Module (Optional)
    ├── Bookshelf Module (Optional)
    ├── Pages Module (Pro Only)
    ├── Launch Module (Pro Only)
    └── Contests Module (Pro Only)
```

### How It Works

1. **Initialization**: Core loads first and sets up the environment
2. **Tier Detection**: Determines if user has Free or Pro license
3. **Module Loading**: Loads only enabled modules based on tier
4. **Settings Registration**: Each module registers its settings
5. **Template Loading**: Core provides templates for frontend display

## Key Components

### 1. Settings API

Provides a simple, consistent way for all modules to register settings:

- Dashboard cards for each module
- Tabbed settings pages
- Automatic save/validation
- Import/export functionality

### 2. Cache Manager

Optimizes performance by caching expensive operations:

- Book queries cached for 12 hours
- Review aggregations cached
- Transient-based with automatic cleanup
- WP-CLI commands for cache management

### 3. License Manager

Handles Free and Pro license states:

- Validates licenses with authorkit.pro API
- Stores activation status locally
- Auto-renewal checks (daily)
- Graceful fallback to Free on errors

### 4. Capability Manager

Manages WordPress user permissions:

- Module-specific capabilities
- Tier-based capability assignment
- Role-based access control
- Developer-friendly permission checks

### 5. Template Loader

Powers theme compatibility:

- Searches theme first, then plugin templates
- Child theme support
- Gutenberg block templates
- Developer override hooks

## Database Tables

AuthorKit Core uses **zero custom tables** by design. All data stored in:

- `wp_posts` (for CPTs like books, reviews, contests)
- `wp_postmeta` (for book fields, review ratings, etc.)
- `wp_options` (for plugin settings)
- `wp_term_taxonomy` (for categories, series, genres)

This ensures:
- Easy backups (standard WP export works)
- No orphaned tables on uninstall
- Better compatibility with hosting providers
- Simpler database maintenance

## Performance

AuthorKit Core is built for **speed**:

**Vanilla PHP/JS:**
- No React, Vue, or jQuery dependencies
- Zero npm packages or build tools
- Native WordPress APIs only

**Conditional Loading:**
- Modules load only when enabled
- Assets load only on relevant pages
- Database queries optimized with caching

**Benchmarks (Tested with 100 books, 300 reviews):**
- Admin dashboard: <200ms load time
- Frontend book page: <50ms PHP execution
- Settings page: <150ms load time

## Security Features

AuthorKit Core implements WordPress security best practices:

**Input Validation:**
- All user input sanitized
- SQL injection prevention (prepared statements)
- XSS protection (escaping output)
- CSRF protection (nonces on all forms)

**Data Security:**
- License keys encrypted in database
- API keys stored securely
- No sensitive data in JavaScript
- Secure API communication (HTTPS only)

**Capability Checks:**
- All admin actions require permissions
- AJAX endpoints verify capabilities
- REST API routes protected
- Developer hooks allow custom checks

## Developer-Friendly

AuthorKit Core provides extensive customization options:

**200+ Hooks:**
- Action hooks for custom functionality
- Filter hooks for modifying data
- Template override hooks
- Settings extension hooks

**Clean Code:**
- WordPress Coding Standards compliant
- Fully documented (PHPDoc)
- Logical file structure
- Consistent naming conventions

**Developer Tools:**
- Debug mode for detailed logging
- WP-CLI commands for automation
- REST API endpoints
- JavaScript events for frontend

## What's Next?

Now that you understand what AuthorKit Core does, explore:

- **[Installation Guide](installation.md)** - Install and activate Core
- **[Settings & Configuration](settings-and-configuration.md)** - Configure your setup
- **[License Management](license-management.md)** - Activate Free or Pro licenses
- **[Developer Reference](developer-reference.md)** - Hooks, filters, and APIs

## Need Help?

- **Documentation**: You're reading it!
- **Community Support**: [WordPress.org Forums](https://wordpress.org/support/plugin/authorkit/)
- **Pro Support**: Email support@authorkit.pro (Pro license holders only)
- **Bug Reports**: [GitHub Issues](https://github.com/shoppustak/authorkit/issues)

---

**Version**: 1.0.0
**Last Updated**: March 7, 2026
**License**: GPL v2.0+
