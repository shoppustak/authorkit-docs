# Developer Guide

Custom hooks, filters, and API endpoints for extending AuthorKit Magnets.

---

## Hooks & Filters

### Form Rendering

#### Filter: `authorkit_magnet_form_fields`

Modify form fields before rendering.

**Parameters:**
- `$fields` (array) - Form field configuration
- `$magnet_id` (int) - Magnet post ID

**Example:** Add custom field

```php
add_filter( 'authorkit_magnet_form_fields', function( $fields, $magnet_id ) {
  $fields['genre_preference'] = [
    'type' => 'select',
    'label' => 'Favorite genre',
    'options' => [ 'romance', 'thriller', 'fantasy' ],
    'required' => false
  ];
  return $fields;
}, 10, 2 );
```

#### Action: `authorkit_magnet_before_form`

Fire before form HTML is output.

**Parameters:**
- `$magnet_id` (int) - Magnet post ID

**Example:** Add custom content above form

```php
add_action( 'authorkit_magnet_before_form', function( $magnet_id ) {
  echo '<p class="magnet-intro">Join 5,000+ readers!</p>';
} );
```

#### Action: `authorkit_magnet_after_form`

Fire after form HTML is output.

**Example:** Add social proof below form

```php
add_action( 'authorkit_magnet_after_form', function( $magnet_id ) {
  echo '<p class="social-proof">★★★★★ Rated 4.8/5 by readers</p>';
} );
```

---

### Form Submission

#### Action: `authorkit_magnet_before_signup`

Fire before subscriber is saved to database.

**Parameters:**
- `$data` (array) - Form submission data

**Example:** Log signups to custom analytics

```php
add_action( 'authorkit_magnet_before_signup', function( $data ) {
  error_log( 'New signup: ' . $data['email'] );
} );
```

#### Filter: `authorkit_magnet_validate_signup`

Custom validation logic.

**Parameters:**
- `$is_valid` (bool) - Current validation status
- `$data` (array) - Form submission data

**Return:** `true` to allow signup, `false` to reject

**Example:** Block specific email domain

```php
add_filter( 'authorkit_magnet_validate_signup', function( $is_valid, $data ) {
  if ( strpos( $data['email'], '@competitor.com' ) !== false ) {
    return false; // Block competitor emails
  }
  return $is_valid;
}, 10, 2 );
```

#### Action: `authorkit_magnet_after_signup`

Fire after subscriber saved successfully.

**Parameters:**
- `$subscriber_id` (int) - New subscriber's database ID
- `$data` (array) - Subscriber data

**Example:** Send to custom CRM

```php
add_action( 'authorkit_magnet_after_signup', function( $subscriber_id, $data ) {
  wp_remote_post( 'https://mycrm.com/api/contacts', [
    'body' => json_encode([
      'email' => $data['email'],
      'name' => $data['first_name'],
      'source' => 'AuthorKit Magnet'
    ])
  ]);
}, 10, 2 );
```

---

### Email Delivery

#### Filter: `authorkit_magnet_email_subject`

Customize email subject line.

**Parameters:**
- `$subject` (string) - Default subject
- `$magnet_id` (int) - Magnet post ID
- `$subscriber` (object) - Subscriber data

**Example:** Personalize subject

```php
add_filter( 'authorkit_magnet_email_subject', function( $subject, $magnet_id, $subscriber ) {
  return "Hey {$subscriber->first_name}, here's your free book!";
}, 10, 3 );
```

#### Filter: `authorkit_magnet_email_body`

Customize email body HTML.

**Parameters:**
- `$body` (string) - Default body HTML
- `$magnet_id` (int) - Magnet post ID
- `$subscriber` (object) - Subscriber data

**Example:** Add custom footer

```php
add_filter( 'authorkit_magnet_email_body', function( $body, $magnet_id, $subscriber ) {
  $body .= '<hr><p>Follow me on Instagram: @sarahmitchellauthor</p>';
  return $body;
}, 10, 3 );
```

#### Action: `authorkit_magnet_before_email_sent`

Fire before email is sent.

**Parameters:**
- `$subscriber_id` (int)
- `$email_data` (array) - Email details

**Example:** Log email sends

```php
add_action( 'authorkit_magnet_before_email_sent', function( $subscriber_id, $email_data ) {
  update_option( 'total_magnet_emails_sent', get_option( 'total_magnet_emails_sent', 0 ) + 1 );
}, 10, 2 );
```

---

### Download Handling

#### Filter: `authorkit_magnet_download_link`

Modify download link URL before displaying.

**Parameters:**
- `$link` (string) - Download URL
- `$subscriber_id` (int)
- `$magnet_id` (int)

**Example:** Add UTM parameters

```php
add_filter( 'authorkit_magnet_download_link', function( $link, $subscriber_id, $magnet_id ) {
  return add_query_arg([
    'utm_source' => 'magnet',
    'utm_medium' => 'email',
    'utm_campaign' => 'reader-magnet'
  ], $link );
}, 10, 3 );
```

#### Action: `authorkit_magnet_file_downloaded`

Fire when file is downloaded.

**Parameters:**
- `$subscriber_id` (int)
- `$magnet_id` (int)
- `$file_path` (string) - Downloaded file path

**Example:** Track downloads in Google Analytics

```php
add_action( 'authorkit_magnet_file_downloaded', function( $subscriber_id, $magnet_id, $file_path ) {
  // Send event to GA via Measurement Protocol
  wp_remote_post( 'https://www.google-analytics.com/collect', [
    'body' => http_build_query([
      'v' => 1,
      'tid' => 'UA-XXXXX-Y',
      't' => 'event',
      'ec' => 'Magnet',
      'ea' => 'Download',
      'el' => get_the_title( $magnet_id )
    ])
  ]);
}, 10, 3 );
```

---

## Template Overrides

### Override Form Template

**Default location:** `authorkit-pro/templates/magnets/form.php`

**Override in theme:**
1. Create directory: `your-theme/authorkit-magnets/`
2. Copy `form.php` to that directory
3. Customize HTML

**Example custom form template:**

```php
<?php
// your-theme/authorkit-magnets/form.php
?>
<div class="my-custom-magnet-form">
  <h3><?php echo esc_html( $magnet_title ); ?></h3>

  <form method="post" action="<?php echo esc_url( $form_action ); ?>">
    <?php wp_nonce_field( 'authorkit_magnet_signup' ); ?>

    <input type="email" name="email" placeholder="Your email" required>
    <input type="text" name="first_name" placeholder="Your name">

    <button type="submit">Get My Free Book</button>
  </form>
</div>
```

### Override Email Template

**Default location:** `authorkit-pro/templates/magnets/email-delivery.php`

**Override in theme:** `your-theme/authorkit-magnets/email-delivery.php`

**Example custom email:**

```php
<?php
// your-theme/authorkit-magnets/email-delivery.php
?>
<!DOCTYPE html>
<html>
<body style="font-family: Arial, sans-serif;">
  <h1>Hi <?php echo esc_html( $subscriber->first_name ); ?>!</h1>

  <p>Thanks for joining my reader community.</p>

  <p><a href="<?php echo esc_url( $download_link ); ?>" style="background: #0073aa; color: white; padding: 15px 30px; text-decoration: none; display: inline-block;">
    Download Your Book
  </a></p>

  <p><small>Link expires in <?php echo $expiration_days; ?> days.</small></p>
</body>
</html>
```

---

## REST API Endpoints

### Get Magnet Details

**Endpoint:** `GET /wp-json/authorkit/v1/magnets/{id}`

**Response:**
```json
{
  "id": 123,
  "title": "Prequel Novella",
  "description": "Exclusive 60-page prequel",
  "file_url": "https://yoursite.com/download/abc123",
  "total_downloads": 1543,
  "total_signups": 2105,
  "conversion_rate": 73.3
}
```

**Example usage:**

```javascript
fetch('/wp-json/authorkit/v1/magnets/123')
  .then(response => response.json())
  .then(data => {
    console.log(`Total downloads: ${data.total_downloads}`);
  });
```

### Submit Signup (AJAX)

**Endpoint:** `POST /wp-json/authorkit/v1/magnets/{id}/signup`

**Parameters:**
- `email` (required)
- `first_name` (optional)
- `last_name` (optional)

**Response (success):**
```json
{
  "success": true,
  "message": "Thank you for subscribing!",
  "download_link": "https://yoursite.com/download/abc123"
}
```

**Response (error):**
```json
{
  "success": false,
  "message": "Invalid email address"
}
```

**Example AJAX form submission:**

```javascript
jQuery('#magnet-form').submit(function(e) {
  e.preventDefault();

  jQuery.ajax({
    url: '/wp-json/authorkit/v1/magnets/123/signup',
    method: 'POST',
    data: {
      email: jQuery('#email').val(),
      first_name: jQuery('#first_name').val()
    },
    success: function(response) {
      if (response.success) {
        alert('Download link: ' + response.download_link);
      } else {
        alert('Error: ' + response.message);
      }
    }
  });
});
```

### Get Analytics

**Endpoint:** `GET /wp-json/authorkit/v1/magnets/{id}/analytics`

**Response:**
```json
{
  "magnet_id": 123,
  "total_signups": 2105,
  "total_downloads": 1543,
  "conversion_rate": 73.3,
  "signups_by_day": {
    "2026-04-01": 45,
    "2026-04-02": 52,
    "2026-04-03": 38
  }
}
```

---

## CSS Customization

### Default CSS Classes

**Form container:**
```css
.authorkit-magnet-form {
  max-width: 500px;
  margin: 0 auto;
  padding: 20px;
}
```

**Input fields:**
```css
.authorkit-magnet-form input[type="email"],
.authorkit-magnet-form input[type="text"] {
  width: 100%;
  padding: 10px;
  margin-bottom: 10px;
  border: 1px solid #ddd;
}
```

**Submit button:**
```css
.authorkit-magnet-form button[type="submit"] {
  background: #0073aa;
  color: white;
  padding: 12px 30px;
  border: none;
  cursor: pointer;
}

.authorkit-magnet-form button[type="submit"]:hover {
  background: #005a87;
}
```

**Success message:**
```css
.authorkit-magnet-success {
  background: #d4edda;
  color: #155724;
  padding: 15px;
  border: 1px solid #c3e6cb;
  margin-bottom: 20px;
}
```

**Error message:**
```css
.authorkit-magnet-error {
  background: #f8d7da;
  color: #721c24;
  padding: 15px;
  border: 1px solid #f5c6cb;
  margin-bottom: 20px;
}
```

### Custom Styling Example

Add to your theme's `style.css`:

```css
/* Dark theme magnet form */
.authorkit-magnet-form {
  background: #1a1a1a;
  color: #ffffff;
  padding: 30px;
  border-radius: 8px;
}

.authorkit-magnet-form input {
  background: #2a2a2a;
  color: #ffffff;
  border: 1px solid #444;
}

.authorkit-magnet-form button {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
```

---

## Database Schema

### Table: `wp_authorkit_magnet_subscribers`

```sql
CREATE TABLE wp_authorkit_magnet_subscribers (
  id bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  magnet_id bigint(20) unsigned NOT NULL,
  email varchar(100) NOT NULL,
  first_name varchar(50) DEFAULT NULL,
  last_name varchar(50) DEFAULT NULL,
  ip_address varchar(45) DEFAULT NULL,
  signup_date datetime NOT NULL,
  status varchar(20) DEFAULT 'active',
  PRIMARY KEY (id),
  KEY magnet_id (magnet_id),
  KEY email (email)
);
```

### Table: `wp_authorkit_magnet_downloads`

```sql
CREATE TABLE wp_authorkit_magnet_downloads (
  id bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  subscriber_id bigint(20) unsigned NOT NULL,
  magnet_id bigint(20) unsigned NOT NULL,
  download_date datetime NOT NULL,
  ip_address varchar(45) DEFAULT NULL,
  user_agent varchar(255) DEFAULT NULL,
  PRIMARY KEY (id),
  KEY subscriber_id (subscriber_id),
  KEY magnet_id (magnet_id)
);
```

---

## Helper Functions

### Get Magnet Data

```php
$magnet = authorkit_get_magnet( $magnet_id );

echo $magnet->title;           // Magnet title
echo $magnet->file_url;        // Download URL
echo $magnet->total_signups;   // Total subscriber count
echo $magnet->total_downloads; // Total download count
```

### Get Subscriber Count

```php
$count = authorkit_get_subscriber_count( $magnet_id );
echo "Total subscribers: {$count}";
```

### Check if Email Subscribed

```php
$is_subscribed = authorkit_is_email_subscribed( 'user@example.com', $magnet_id );

if ( $is_subscribed ) {
  echo 'Already subscribed!';
}
```

### Generate Download Link

```php
$link = authorkit_generate_download_link( $subscriber_id, $magnet_id );
echo "<a href='{$link}'>Download</a>";
```

---

## Security Considerations

### Nonce Verification

Always verify nonces in custom handlers:

```php
if ( ! wp_verify_nonce( $_POST['_wpnonce'], 'authorkit_magnet_signup' ) ) {
  wp_die( 'Security check failed' );
}
```

### Capability Checks

Check user capabilities before admin actions:

```php
if ( ! current_user_can( 'manage_options' ) ) {
  wp_die( 'Unauthorized' );
}
```

### Sanitize Input

Always sanitize user input:

```php
$email = sanitize_email( $_POST['email'] );
$name = sanitize_text_field( $_POST['first_name'] );
```

### Escape Output

Escape data before displaying:

```php
echo esc_html( $subscriber->first_name );
echo esc_url( $download_link );
echo esc_attr( $magnet_title );
```

---

## Example: Custom Integration

### Send to ActiveCampaign on Signup

```php
add_action( 'authorkit_magnet_after_signup', function( $subscriber_id, $data ) {
  $api_url = 'https://youraccountname.api-us1.com/api/3/contacts';
  $api_key = 'YOUR_ACTIVECAMPAIGN_API_KEY';

  wp_remote_post( $api_url, [
    'headers' => [
      'Api-Token' => $api_key,
      'Content-Type' => 'application/json'
    ],
    'body' => json_encode([
      'contact' => [
        'email' => $data['email'],
        'firstName' => $data['first_name'],
        'fieldValues' => [
          [
            'field' => '1', // Custom field ID
            'value' => 'Reader Magnet'
          ]
        ]
      ]
    ])
  ]);
}, 10, 2 );
```

---

## Troubleshooting

### Enable Debug Logging

```php
define( 'AUTHORKIT_MAGNETS_DEBUG', true );
```

**Log file location:** `/wp-content/uploads/authorkit-magnets/debug.log`

### Common Issues

**Emails not sending:**
- Check SMTP configuration
- Verify from email domain has SPF/DKIM records
- Test with WP Mail SMTP plugin

**Downloads not tracking:**
- Clear object cache (Redis/Memcached)
- Check file permissions on upload directory
- Verify JavaScript not blocked by ad blocker

**Form not submitting:**
- Check for JavaScript errors (F12 console)
- Verify nonce is being generated
- Confirm AJAX endpoint is accessible

---

## Support

**Documentation:** [docs.authorkit.pro](https://docs.authorkit.pro)
**Email support:** support@authorkit.pro
**Developer forum:** [community.authorkit.pro](https://community.authorkit.pro)

---

**Last Updated:** April 4, 2026
**Requires:** AuthorKit Pro 1.0+
