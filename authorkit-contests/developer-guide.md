# Developer Guide

Technical reference for developers customizing AuthorKit Contests. Learn about available hooks, filters, shortcode parameters, REST API endpoints, JavaScript events, and customization patterns.

## Overview

AuthorKit Contests is built with extensibility in mind. Developers can:

- Hook into contest lifecycle events
- Filter contest data and output
- Customize templates via theme overrides
- Integrate via REST API endpoints
- Listen to JavaScript events for frontend interactions
- Style with CSS custom properties
- Access database tables directly (not recommended)

**Target Audience:** WordPress developers, theme authors, plugin developers

**Prerequisites:**
- PHP 7.4+
- WordPress 6.0+
- Understanding of WordPress hooks/filters
- Basic knowledge of JavaScript (for frontend customization)

## Hooks and Filters

### Action Hooks

Action hooks allow you to execute custom code at specific points in the contest lifecycle.

#### Contest Entry Lifecycle

**`authorkit_contest_entry_added`**

Fires immediately after a contest entry is saved to the database.

```php
do_action( 'authorkit_contest_entry_added', int $contest_id, int $entry_id );
```

**Parameters:**
- `$contest_id` (int) - Contest post ID
- `$entry_id` (int) - Database entry ID from `wp_authorkit_contest_entries` table

**Example - Send custom notification:**

```php
add_action( 'authorkit_contest_entry_added', 'custom_entry_notification', 10, 2 );

function custom_entry_notification( $contest_id, $entry_id ) {
    // Get contest title
    $contest_title = get_the_title( $contest_id );

    // Get entry data
    global $wpdb;
    $table_name = $wpdb->prefix . 'authorkit_contest_entries';
    $entry = $wpdb->get_row(
        $wpdb->prepare( "SELECT * FROM $table_name WHERE id = %d", $entry_id )
    );

    // Send Slack notification
    $message = sprintf(
        'New entry for "%s": %s (%s)',
        $contest_title,
        $entry->name,
        $entry->email
    );

    // Your Slack webhook code here
    wp_remote_post( 'YOUR_SLACK_WEBHOOK_URL', [
        'body' => json_encode( [ 'text' => $message ] )
    ] );
}
```

**`authorkit_contest_bonus_claimed`**

Fires when a user claims a bonus entry (social share).

```php
do_action( 'authorkit_contest_bonus_claimed', int $contest_id, string $bonus_type, string $platform );
```

**Parameters:**
- `$contest_id` (int) - Contest post ID
- `$bonus_type` (string) - Type of bonus: `share`, `referral`, `review`
- `$platform` (string) - Platform: `whatsapp`, `facebook`, `twitter`, `instagram`

**Example - Track bonus shares in analytics:**

```php
add_action( 'authorkit_contest_bonus_claimed', 'track_bonus_shares', 10, 3 );

function track_bonus_shares( $contest_id, $bonus_type, $platform ) {
    // Send to Google Analytics
    if ( function_exists( 'gtag' ) ) {
        ?>
        <script>
        gtag('event', 'contest_bonus_claimed', {
            'event_category': 'Contest',
            'event_label': '<?php echo esc_js( $platform ); ?>',
            'contest_id': <?php echo intval( $contest_id ); ?>
        });
        </script>
        <?php
    }
}
```

#### Contest Meta Hooks

**`save_post_authorkit_contest`**

Standard WordPress hook that fires when contest post is saved.

```php
add_action( 'save_post_authorkit_contest', 'custom_contest_save', 10, 2 );

function custom_contest_save( $post_id, $post ) {
    // Don't run on autosave
    if ( defined( 'DOING_AUTOSAVE' ) && DOING_AUTOSAVE ) {
        return;
    }

    // Check if contest has ended
    $end_date = get_post_meta( $post_id, 'contest_end_date', true );
    if ( $end_date && strtotime( $end_date ) < time() ) {
        // Automatically close contest entry form
        update_post_meta( $post_id, 'contest_closed', true );
    }
}
```

### Filter Hooks

Filters allow you to modify data before it's displayed or saved.

**`authorkit_contest_fields`**

Filter the list of fields displayed in contest entry form.

```php
apply_filters( 'authorkit_contest_fields', array $fields, int $contest_id );
```

**Parameters:**
- `$fields` (array) - Array of field definitions
- `$contest_id` (int) - Contest post ID

**Example - Add custom field:**

```php
add_filter( 'authorkit_contest_fields', 'add_custom_contest_field', 10, 2 );

function add_custom_contest_field( $fields, $contest_id ) {
    // Add "Favorite Genre" field
    $fields['favorite_genre'] = [
        'type'        => 'select',
        'label'       => 'Favorite Genre',
        'placeholder' => 'Select your favorite genre',
        'required'    => false,
        'options'     => [
            'mystery'     => 'Mystery',
            'romance'     => 'Romance',
            'scifi'       => 'Science Fiction',
            'fantasy'     => 'Fantasy',
            'thriller'    => 'Thriller',
            'historical'  => 'Historical Fiction',
        ],
    ];

    return $fields;
}
```

**`authorkit_contest_entry_data`**

Filter contest entry data before saving to database.

```php
apply_filters( 'authorkit_contest_entry_data', array $data, int $contest_id );
```

**Example - Sanitize phone numbers:**

```php
add_filter( 'authorkit_contest_entry_data', 'sanitize_contest_phone', 10, 2 );

function sanitize_contest_phone( $data, $contest_id ) {
    if ( ! empty( $data['phone'] ) ) {
        // Remove non-numeric characters
        $data['phone'] = preg_replace( '/[^0-9]/', '', $data['phone'] );
    }

    return $data;
}
```

**`authorkit_contest_shortcode_atts`**

Filter shortcode attributes before rendering.

```php
apply_filters( 'authorkit_contest_shortcode_atts', array $atts, string $shortcode );
```

**Example - Override default limit:**

```php
add_filter( 'authorkit_contest_shortcode_atts', 'custom_contest_limit', 10, 2 );

function custom_contest_limit( $atts, $shortcode ) {
    if ( $shortcode === 'authorkit_contests' && empty( $atts['limit'] ) ) {
        // Default to 12 contests instead of -1 (all)
        $atts['limit'] = 12;
    }

    return $atts;
}
```

## Shortcode Reference

### Single Contest Display

**`[authorkit_contest]`**

Display a single contest entry form and details.

**Parameters:**

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `id` | integer | (required) | Contest post ID |
| `class` | string | '' | Additional CSS class for wrapper |

**Examples:**

```php
// Basic usage
[authorkit_contest id="123"]

// With custom CSS class
[authorkit_contest id="123" class="featured-contest"]
```

**PHP Usage:**

```php
echo do_shortcode( '[authorkit_contest id="' . $contest_id . '"]' );
```

**Programmatic Usage:**

```php
$shortcode = AuthorKit_Contests_Shortcodes::get_instance();
echo $shortcode->render_single_contest( [ 'id' => 123 ] );
```

### Contest Grid

**`[authorkit_contests]`**

Display multiple contests in a grid layout.

**Parameters:**

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `limit` | integer | -1 (all) | Number of contests to display |
| `status` | string | '' (all) | Filter by status: `active`, `ended`, `upcoming` |
| `orderby` | string | 'date' | Sort field: `date`, `title`, `end_date`, `modified` |
| `order` | string | 'DESC' | Sort order: `DESC` or `ASC` |
| `class` | string | '' | Additional CSS class for wrapper |

**Examples:**

```php
// Show all active contests
[authorkit_contests status="active"]

// Show 6 most recent contests
[authorkit_contests limit="6"]

// Show upcoming contests, ordered by end date
[authorkit_contests status="upcoming" orderby="end_date" order="ASC"]

// Show ended contests (for archive page)
[authorkit_contests status="ended" limit="12" orderby="end_date" order="DESC"]

// With custom CSS class
[authorkit_contests limit="3" class="homepage-contests"]
```

### Contest Archive

**`[authorkit_contest_archive]`**

Display all contests (no limit). Essentially an alias for `[authorkit_contests limit="-1"]`.

**Parameters:**

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `class` | string | '' | Additional CSS class for wrapper |

**Example:**

```php
[authorkit_contest_archive]
```

## Custom Template Overrides

Override contest templates in your theme without modifying plugin files.

### Template Hierarchy

AuthorKit Contests uses WordPress template hierarchy:

```
your-theme/
└── authorkit/
    └── contests/
        ├── single-contest.php       (single contest display)
        ├── contest-card.php         (grid item)
        ├── archive-contest.php      (contest archive)
        └── entry-form.php           (entry form)
```

If a template exists in your theme's `authorkit/contests/` directory, it will be used instead of the plugin's default template.

### Example: Custom Contest Card

**File:** `your-theme/authorkit/contests/contest-card.php`

```php
<?php
/**
 * Contest Card Template
 *
 * Override this file in your theme by creating:
 * your-theme/authorkit/contests/contest-card.php
 *
 * @var int $contest_id Contest post ID (passed as template arg)
 */

$contest_id = isset( $contest_id ) ? $contest_id : get_the_ID();
$end_date = get_post_meta( $contest_id, 'contest_end_date', true );
$prize = get_post_meta( $contest_id, 'prize_description', true );
?>

<div class="custom-contest-card">
    <div class="contest-image">
        <?php the_post_thumbnail( 'medium' ); ?>
    </div>

    <div class="contest-content">
        <h3><?php the_title(); ?></h3>

        <?php if ( $prize ) : ?>
            <div class="contest-prize">
                Prize: <?php echo esc_html( $prize ); ?>
            </div>
        <?php endif; ?>

        <?php if ( $end_date ) : ?>
            <div class="contest-deadline">
                Ends: <?php echo date( 'F j, Y', strtotime( $end_date ) ); ?>
            </div>
        <?php endif; ?>

        <a href="<?php the_permalink(); ?>" class="contest-button">
            Enter Contest
        </a>
    </div>
</div>
```

## REST API Endpoints

Access contest data via WordPress REST API.

### Base URL

```
/wp-json/authorkit/v1/contests
```

### Endpoints

#### Get All Contests

```http
GET /wp-json/authorkit/v1/contests
```

**Query Parameters:**

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `status` | string | 'all' | Filter: `all`, `active`, `closed`, `upcoming` |
| `per_page` | integer | 10 | Results per page (max 100) |
| `page` | integer | 1 | Page number |

**Example Request:**

```bash
curl https://yoursite.com/wp-json/authorkit/v1/contests?status=active&per_page=5
```

**Example Response:**

```json
{
  "contests": [
    {
      "id": 123,
      "title": "Win a Signed Copy of The Silent Echo",
      "status": "active",
      "start_date": "2026-03-01",
      "end_date": "2026-03-14",
      "prize": "Signed Paperback Copy",
      "entry_count": 347,
      "permalink": "https://yoursite.com/contests/silent-echo-giveaway/"
    }
  ],
  "total": 1,
  "pages": 1
}
```

#### Get Active Contests

```http
GET /wp-json/authorkit/v1/contests/active
```

**Query Parameters:**

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `limit` | integer | 5 | Number of contests (max 50) |

**Example Request:**

```bash
curl https://yoursite.com/wp-json/authorkit/v1/contests/active?limit=3
```

#### Get Single Contest

```http
GET /wp-json/authorkit/v1/contests/{id}
```

**Example Request:**

```bash
curl https://yoursite.com/wp-json/authorkit/v1/contests/123
```

**Example Response:**

```json
{
  "id": 123,
  "title": "Win a Signed Copy of The Silent Echo",
  "description": "<p>Enter to win...</p>",
  "status": "active",
  "start_date": "2026-03-01",
  "end_date": "2026-03-14",
  "prize": {
    "amount": null,
    "currency": "₹",
    "description": "Signed Paperback Copy"
  },
  "book": {
    "id": 456,
    "title": "The Silent Echo",
    "cover_url": "https://yoursite.com/wp-content/uploads/book-cover.jpg"
  },
  "entry_count": 347,
  "max_entries": 500,
  "fields": ["name", "email", "review"],
  "share_platforms": ["whatsapp", "facebook"],
  "permalink": "https://yoursite.com/contests/silent-echo-giveaway/"
}
```

### JavaScript API Usage

**Example - Fetch active contests:**

```javascript
fetch('/wp-json/authorkit/v1/contests/active?limit=3')
  .then(response => response.json())
  .then(data => {
    data.contests.forEach(contest => {
      console.log(`${contest.title} - ${contest.entry_count} entries`);
    });
  });
```

**Example - Display in React:**

```jsx
import React, { useState, useEffect } from 'react';

function ActiveContests() {
  const [contests, setContests] = useState([]);

  useEffect(() => {
    fetch('/wp-json/authorkit/v1/contests/active?limit=5')
      .then(res => res.json())
      .then(data => setContests(data.contests));
  }, []);

  return (
    <div className="contests-widget">
      <h3>Active Giveaways</h3>
      {contests.map(contest => (
        <div key={contest.id} className="contest-item">
          <a href={contest.permalink}>{contest.title}</a>
          <span>{contest.entry_count} entries</span>
        </div>
      ))}
    </div>
  );
}
```

## JavaScript Events

Listen to frontend JavaScript events for custom functionality.

### Available Events

**`authorkit:contestSubmitted`**

Fires after contest entry is successfully submitted.

```javascript
document.addEventListener('authorkit:contestSubmitted', function(event) {
    const data = event.detail;
    console.log('Entry submitted:', data.contestId, data.entryNumber);

    // Example: Track in Google Analytics
    if (typeof gtag !== 'undefined') {
        gtag('event', 'contest_entry', {
            'event_category': 'Contest',
            'event_label': data.contestTitle,
            'value': data.entryNumber
        });
    }
});
```

**Event Detail Properties:**
- `contestId` (int) - Contest post ID
- `contestTitle` (string) - Contest title
- `entryNumber` (int) - Entry number assigned
- `email` (string) - Entrant email

**`authorkit:bonusClaimed`**

Fires when bonus entry is claimed.

```javascript
document.addEventListener('authorkit:bonusClaimed', function(event) {
    const data = event.detail;
    console.log('Bonus claimed:', data.platform, data.bonusType);

    // Example: Show custom thank you message
    const message = `Thanks for sharing on ${data.platform}!`;
    alert(message);
});
```

**Event Detail Properties:**
- `contestId` (int) - Contest post ID
- `platform` (string) - Share platform
- `bonusType` (string) - Type of bonus
- `shareUrl` (string) - Generated share URL

**`authorkit:entryCountUpdated`**

Fires when entry counter is updated.

```javascript
document.addEventListener('authorkit:entryCountUpdated', function(event) {
    const data = event.detail;
    console.log('Entry count:', data.count);

    // Example: Update custom counter element
    document.getElementById('custom-counter').textContent = data.count;
});
```

**Event Detail Properties:**
- `contestId` (int) - Contest post ID
- `count` (int) - Total entry count
- `timestamp` (int) - Update timestamp

## CSS Custom Properties

Override contest styles using CSS custom properties (variables).

### Available Variables

```css
:root {
    /* Primary colors */
    --authorkit-contest-primary: #ff9900;
    --authorkit-contest-secondary: #667eea;

    /* Button styles */
    --authorkit-contest-button: #ff9900;
    --authorkit-contest-button-hover: #e68a00;
    --authorkit-contest-button-text: #ffffff;

    /* Border and backgrounds */
    --authorkit-contest-border: #e5e5e5;
    --authorkit-contest-background: #ffffff;
    --authorkit-contest-input-background: #f9f9f9;

    /* Typography */
    --authorkit-contest-font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
    --authorkit-contest-heading-color: #1a1a1a;
    --authorkit-contest-text-color: #646970;

    /* Spacing */
    --authorkit-contest-spacing: 20px;
    --authorkit-contest-border-radius: 8px;
}
```

### Example - Customize for Your Brand

```css
/* In your theme's style.css */
:root {
    --authorkit-contest-button: #2c3e50;
    --authorkit-contest-button-hover: #1a252f;
    --authorkit-contest-primary: #e74c3c;
    --authorkit-contest-border-radius: 4px;
}

/* Further customization */
.authorkit-contest-form {
    max-width: 600px;
    margin: 0 auto;
    padding: 40px;
    box-shadow: 0 4px 6px rgba(0,0,0,0.1);
}

.authorkit-contest-card {
    border: 2px solid var(--authorkit-contest-primary);
    transition: transform 0.3s ease;
}

.authorkit-contest-card:hover {
    transform: translateY(-5px);
}
```

## Database Schema

Direct database access (use with caution - prefer hooks/filters).

### Tables

**`wp_authorkit_contest_entries`**

Stores contest entries (fallback if Google Sheets fails).

```sql
CREATE TABLE wp_authorkit_contest_entries (
  id bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  contest_id bigint(20) unsigned NOT NULL,
  name varchar(255),
  email varchar(255) NOT NULL,
  phone varchar(50),
  rating tinyint(1),
  source varchar(100),
  review text,
  timestamp datetime NOT NULL,
  ip_address varchar(45),
  user_agent varchar(255),
  PRIMARY KEY (id),
  KEY contest_id (contest_id),
  KEY email (email),
  KEY timestamp (timestamp)
);
```

**`wp_authorkit_contest_bonuses`**

Tracks bonus entry claims.

```sql
CREATE TABLE wp_authorkit_contest_bonuses (
  id bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  contest_id bigint(20) unsigned NOT NULL,
  entry_id bigint(20) unsigned NOT NULL,
  bonus_type varchar(50) NOT NULL,
  platform varchar(50),
  claimed_at datetime NOT NULL,
  share_token varchar(100),
  PRIMARY KEY (id),
  KEY contest_id (contest_id),
  KEY entry_id (entry_id),
  KEY share_token (share_token)
);
```

### Example Queries

**Get total entries for a contest:**

```php
global $wpdb;
$contest_id = 123;
$count = $wpdb->get_var( $wpdb->prepare(
    "SELECT COUNT(*) FROM {$wpdb->prefix}authorkit_contest_entries WHERE contest_id = %d",
    $contest_id
) );
```

**Get recent entries:**

```php
global $wpdb;
$contest_id = 123;
$entries = $wpdb->get_results( $wpdb->prepare(
    "SELECT * FROM {$wpdb->prefix}authorkit_contest_entries
     WHERE contest_id = %d
     ORDER BY timestamp DESC
     LIMIT 10",
    $contest_id
) );
```

**Note:** Direct database queries bypass hooks and filters. Use `AuthorKit_Contests_Entries` class methods when possible.

## Security Best Practices

### Nonce Verification

Always verify nonces when processing contest forms:

```php
if ( ! wp_verify_nonce( $_POST['_wpnonce'], 'authorkit_contest_entry' ) ) {
    wp_die( 'Security check failed' );
}
```

### Data Sanitization

Sanitize all user input:

```php
$name = sanitize_text_field( $_POST['name'] );
$email = sanitize_email( $_POST['email'] );
$review = wp_kses_post( $_POST['review'] ); // Allow safe HTML
```

### Capability Checks

Check user capabilities for admin operations:

```php
if ( ! current_user_can( 'manage_options' ) ) {
    wp_die( 'Unauthorized' );
}
```

### Rate Limiting

The plugin includes built-in rate limiting for entries. To customize:

```php
add_filter( 'authorkit_contest_rate_limit', 'custom_rate_limit', 10, 2 );

function custom_rate_limit( $limit, $contest_id ) {
    // Allow 1 entry per IP per hour (default is per day)
    return HOUR_IN_SECONDS;
}
```

## Code Examples

### Custom Winner Selection Script

Automate winner selection with Google Apps Script:

```javascript
// Add to your Google Apps Script project
function selectRandomWinner() {
  var sheet = SpreadsheetApp.getActiveSheet();
  var lastRow = sheet.getLastRow();

  // Exclude header row
  if (lastRow <= 1) {
    Browser.msgBox('No entries found');
    return;
  }

  // Random number between 2 (first entry) and lastRow
  var winnerRow = Math.floor(Math.random() * (lastRow - 1)) + 2;

  // Get winner data
  var winnerName = sheet.getRange(winnerRow, 2).getValue(); // Column B (Name)
  var winnerEmail = sheet.getRange(winnerRow, 3).getValue(); // Column C (Email)

  // Highlight winner row
  sheet.getRange(winnerRow, 1, 1, sheet.getLastColumn()).setBackground('#FFD700');

  // Show winner
  Browser.msgBox('Winner',
    'Winner: ' + winnerName + ' (' + winnerEmail + ')\nRow: ' + winnerRow,
    Browser.Buttons.OK);
}
```

### Custom Email Integration

Send entry data to external API:

```php
add_action( 'authorkit_contest_entry_added', 'send_to_crm', 10, 2 );

function send_to_crm( $contest_id, $entry_id ) {
    global $wpdb;
    $table = $wpdb->prefix . 'authorkit_contest_entries';
    $entry = $wpdb->get_row( $wpdb->prepare(
        "SELECT * FROM $table WHERE id = %d",
        $entry_id
    ) );

    if ( ! $entry ) {
        return;
    }

    // Send to HubSpot (example)
    $response = wp_remote_post( 'https://api.hubapi.com/contacts/v1/contact/', [
        'headers' => [
            'Authorization' => 'Bearer YOUR_API_KEY',
            'Content-Type' => 'application/json',
        ],
        'body' => json_encode( [
            'properties' => [
                ['property' => 'email', 'value' => $entry->email],
                ['property' => 'firstname', 'value' => $entry->name],
                ['property' => 'contest_entry', 'value' => get_the_title( $contest_id )],
            ],
        ] ),
    ] );
}
```

### Custom Contest Status

Add a custom "Featured" status:

```php
add_action( 'add_meta_boxes', 'add_featured_contest_meta_box' );

function add_featured_contest_meta_box() {
    add_meta_box(
        'featured_contest',
        'Featured Contest',
        'render_featured_contest_meta_box',
        'authorkit_contest',
        'side',
        'high'
    );
}

function render_featured_contest_meta_box( $post ) {
    $featured = get_post_meta( $post->ID, 'contest_featured', true );
    ?>
    <label>
        <input type="checkbox" name="contest_featured" value="1" <?php checked( $featured, '1' ); ?>>
        Mark as featured
    </label>
    <?php
}

add_action( 'save_post_authorkit_contest', 'save_featured_contest_meta', 10, 2 );

function save_featured_contest_meta( $post_id, $post ) {
    if ( isset( $_POST['contest_featured'] ) ) {
        update_post_meta( $post_id, 'contest_featured', '1' );
    } else {
        delete_post_meta( $post_id, 'contest_featured' );
    }
}
```

## Troubleshooting

### Enable Debug Mode

```php
// In wp-config.php
define( 'WP_DEBUG', true );
define( 'WP_DEBUG_LOG', true );
define( 'WP_DEBUG_DISPLAY', false );

// Contest-specific debugging
add_filter( 'authorkit_contest_debug', '__return_true' );
```

### Check Error Logs

```bash
tail -f wp-content/debug.log
```

### Common Issues

**Hooks not firing:**
- Verify hook name spelling
- Check priority (default is 10)
- Ensure callback function is defined before hook runs

**Template overrides not working:**
- Check file path: `your-theme/authorkit/contests/template-name.php`
- Clear all caches (WordPress, theme, server)
- Verify file permissions (should be 644)

**REST API errors:**
- Check permalink structure (Settings → Permalinks → Save)
- Verify `rest_api_init` hook fires
- Test with different permalinks (Post name vs Plain)

## Related Documentation

- **[Overview](/authorkit-contests/overview.md)** - Contest module overview
- **[Creating Contests](/authorkit-contests/creating-contests.md)** - User guide
- **[Managing Entries](/authorkit-contests/managing-entries.md)** - Google Apps Script setup
- **[Winner Selection](/authorkit-contests/winner-selection.md)** - Winner selection process
- **[Email Notifications](/authorkit-contests/email-notifications.md)** - Email integration

## Support

For development support:

- [GitHub Repository](https://github.com/authorkit/authorkit-pro)
- [Developer Forums](https://authorkit.pro/developers)
- [Code Reference](https://docs.authorkit.pro/code-reference/)
- [Support Tickets](https://authorkit.pro/support)

---

*Last Updated: April 4, 2026*
