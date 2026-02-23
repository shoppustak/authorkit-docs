# Bookshelf Settings & Configuration

Complete guide to configuring AuthorKit Bookshelf settings for optimal book discovery.

## Access Settings

Navigate to **AuthorKit → Bookshelf Settings** in your WordPress admin to access all Bookshelf configuration options.

## General Settings

### Enable/Disable Bookshelf

Toggle the Bookshelf module on or off:
- **Enabled**: Books can be published to bookshelf.authorkit.pro
- **Disabled**: No books are synced (existing listings remain until manually removed)

### Auto-Publish New Books

When enabled, all newly created books are automatically published to Bookshelf.

**Recommended**: Leave disabled if you prefer to manually choose which books to publish.

### Exclude Coming Soon Books

Automatically exclude books with "Coming Soon" status from Bookshelf.

**Recommended**: Enable if you don't want pre-release books visible publicly.

## Author Information

### Author Name

The name displayed as the author on all your book listings.

**Default**: WordPress site name
**Recommended**: Use your author pen name or full name

### Author Website

Your author website URL displayed on book listings.

**Default**: WordPress site URL
**Can be changed**: Use a custom domain or author page URL

### Author Bio

Optional short biography (max 500 characters) displayed on your author profile.

**Recommended**: Write 2-3 sentences about your writing and genres.

## Book Visibility

### Default Visibility

Set the default visibility for new books:
- **Public**: Books visible to all readers (default)
- **Private**: Books hidden from search and browse
- **Listed**: Visible in browse but hidden from search

**Recommended**: Use "Public" for maximum discoverability.

### Book Status Filters

Choose which book statuses can be published:
- ✓ Published (always included)
- □ Draft (excluded by default)
- □ Coming Soon (optional)

### Hide Specific Books

Enter Book IDs to permanently exclude from Bookshelf (comma-separated).

**Example**: `123, 456, 789`

## Metadata Sync

Control which book metadata syncs to Bookshelf:

### Always Synced
- Title and subtitle
- Description
- Cover image
- Author name
- Genres/categories

### Optional Sync
- ✓ Publication date
- ✓ ISBN
- ✓ Price information
- ✓ Page count
- ✓ Series information
- ✓ Age range
- ✓ Language

Uncheck any you don't want to share publicly.

## Buy Links

### Affiliate Tag Configuration

Add your affiliate tags to buy links automatically:

#### Amazon Associates
- **Affiliate Tag**: Your Amazon Associates ID
- **Example**: `yoursite-20`

#### Apple Books Affiliate
- **Token**: Your Apple Affiliate token

#### Other Retailers
Configure affiliate parameters for:
- Barnes & Noble
- Kobo
- Google Play Books

**Note**: Affiliate links are appended automatically when readers click "Buy" buttons.

### Link Priority

Set the order buy buttons appear:
1. Amazon
2. Apple Books
3. Barnes & Noble
4. Kobo
5. Google Play
6. Other

Drag to reorder. Most popular retailers should be listed first.

## Advanced Settings

### Sync Frequency

How often to check for book updates:
- **Immediate** - Sync within 5 minutes of changes (default)
- **Hourly** - Sync once per hour
- **Daily** - Sync once per day

**Recommended**: Use "Immediate" for active catalogs.

### API Connection

Configure connection to bookshelf.authorkit.pro:

- **API Endpoint**: (default value - don't change)
- **Timeout**: Request timeout in seconds (default: 30)
- **Retry Failed**: Automatically retry failed syncs

### Cache Settings

- **Cache Duration**: How long to cache book data (default: 1 hour)
- **Clear Cache**: Force clear all cached book data

## Notification Settings

### Email Notifications

Receive email when:
- □ New book is published to Bookshelf
- □ Sync fails for a book
- ✓ Bookshelf module is disabled

**Email Address**: (default: WordPress admin email)

### Admin Notices

Show WordPress admin notices for:
- ✓ Successful book publications
- ✓ Sync errors
- □ Daily sync summary

## Privacy & Data

### Data Sharing

What data is sent to bookshelf.authorkit.pro:
- Book metadata (title, description, cover, etc.)
- Author name and website
- Buy links

What is **NOT** shared:
- WordPress admin email
- User accounts or customer data
- Website analytics
- Any personal information

### Data Deletion

When you unpublish a book or disable Bookshelf:
- Book listings are removed from bookshelf.authorkit.pro
- No data is retained on external servers
- All data remains on your WordPress site

### GDPR Compliance

- No personal reader data is collected
- No cookies or tracking on bookshelf.authorkit.pro
- Authors can delete all data at any time

## Troubleshooting

### Connection Test

Test your site's connection to bookshelf.authorkit.pro:

1. Click **Test Connection** button
2. View results:
   - ✓ Connection successful
   - ✗ Connection failed (with error details)

### Sync Status

Check sync status for all books:

1. Go to **AuthorKit → Bookshelf**
2. View **Sync Status** column
3. Icons indicate:
   - ✓ Synced successfully
   - ⏱ Sync pending
   - ✗ Sync failed

### Reset All Settings

To restore default Bookshelf settings:

1. Click **Reset to Defaults** at bottom of settings page
2. Confirm the action
3. Reconfigure your author information

**Warning**: This does not unpublish your books.

## Backup & Export

### Export Settings

Download your Bookshelf configuration:

1. Click **Export Settings**
2. Save the `.json` file

### Import Settings

Import previously exported settings:

1. Click **Choose File**
2. Select your `.json` file
3. Click **Import**

Useful when migrating to a new site.

## Performance Optimization

### For Small Catalogs (< 50 books)
- Sync Frequency: Immediate
- Cache Duration: 1 hour

### For Medium Catalogs (50-200 books)
- Sync Frequency: Immediate
- Cache Duration: 4 hours

### For Large Catalogs (200+ books)
- Sync Frequency: Hourly
- Cache Duration: 12 hours

## Next Steps

- [Publishing Books](publishing-books.md) - Start publishing to Bookshelf
- [Managing Listings](managing-listings.md) - Organize your published books
- [Browse Bookshelf](https://bookshelf.authorkit.pro) - See how your books appear
