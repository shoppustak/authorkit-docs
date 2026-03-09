# Google Apps Script Setup

## Overview

AuthorKit Contests uses Google Apps Script to securely collect contest entries in your Google Sheet. This architecture protects your WordPress database from bot attacks and malware while giving you complete control over your contest data.

**Why Google Sheets?**
- **Security:** Prevents direct database access from bots and malware
- **Ownership:** Your contest data lives in YOUR Google Sheet
- **Analysis:** Easy to review, filter, and export entries
- **Backup:** Automatic cloud backup through Google
- **Sharing:** Simple to share with team members for winner selection

## How It Works

When a visitor submits a contest entry:
1. Form data is sent to your Google Apps Script endpoint
2. The script validates and saves the entry to your Google Sheet
3. Entry counter updates automatically
4. You can review entries anytime in your Google Sheet

**Important:** Each contest requires a Google Apps Script setup. This guide walks you through the complete process.

## Before You Start

You'll need:
- A Google account
- 10-15 minutes for setup
- Basic familiarity with Google Sheets

No coding knowledge required - we provide the complete script.

## Step 1: Create a Google Sheet

1. Go to [Google Sheets](https://sheets.google.com)
2. Click **Blank** to create a new spreadsheet
3. Name it something descriptive like "My Book Contest Entries"
4. Leave the sheet open - you'll need it in the next steps

**Tip:** The script will automatically create column headers on the first entry, so you don't need to set anything up.

## Step 2: Get Your Spreadsheet ID

Your Spreadsheet ID is a long string of letters and numbers in the Google Sheets URL.

1. Look at your browser's address bar
2. Find the URL that looks like this:
   ```
   https://docs.google.com/spreadsheets/d/SPREADSHEET_ID_HERE/edit#gid=0
   ```
3. Copy the long string between `/d/` and `/edit`
4. Example: `1BxiMVs0XRA5nFMdKvBdBZjgmUUqptlbs74OgvE2upms`
5. Save this somewhere - you'll need it shortly

## Step 3: Open Apps Script Editor

1. In your Google Sheet, click **Extensions** in the top menu
2. Click **Apps Script**
3. A new tab opens with the Apps Script editor
4. You'll see a default `Code.gs` file with sample code

## Step 4: Copy the AuthorKit Script

Now you'll replace the default code with the AuthorKit contest script.

### Option A: Get the Script from AuthorKit Plugin

If you have access to your WordPress files:

1. Navigate to: `/wp-content/plugins/authorkit/`
2. Find the script template at: `docs/templates/google-apps-script-template.js`
3. Open the file and copy all the code
4. Go back to Apps Script editor
5. Delete all the default code
6. Paste the AuthorKit script

### Option B: Copy from Documentation

<details>
<summary>Click to expand the complete script code</summary>

```javascript
// ============================================
// AuthorKit Contests - Google Apps Script
// ============================================
//
// SETUP INSTRUCTIONS:
// 1. Create a new Google Sheet
// 2. Copy the Spreadsheet ID from the URL (the long string between /d/ and /edit)
// 3. Replace 'YOUR_SPREADSHEET_ID_HERE' below with your actual Spreadsheet ID
// 4. Save this script (Ctrl+S or Cmd+S)
// 5. Click Deploy → New deployment → Web app
// 6. Set "Execute as: Me" and "Who has access: Anyone"
// 7. Click Deploy and copy the Web app URL
// 8. Paste the URL in AuthorKit → Contests → Settings
//
// DOCUMENTATION: https://docs.authorkit.pro/modules/contests-google-script-setup
// ============================================

// ============================================
// GET Handler - For fetching entry count
// ============================================
function doGet(e) {
  try {
    // ⚠️ REPLACE THIS with your actual Spreadsheet ID
    var spreadsheetId = 'YOUR_SPREADSHEET_ID_HERE';
    var sheet = SpreadsheetApp.openById(spreadsheetId).getActiveSheet();

    // Handle different GET actions
    var action = e.parameter.action;

    if (action === 'getCount') {
      // Count total entries (excluding header row)
      var lastRow = sheet.getLastRow();
      var totalEntries = lastRow > 0 ? lastRow - 1 : 0;

      return ContentService.createTextOutput(JSON.stringify({
        success: true,
        totalEntries: totalEntries
      })).setMimeType(ContentService.MimeType.JSON);
    }

    // Default response if no action specified
    return ContentService.createTextOutput(JSON.stringify({
      success: false,
      error: 'No action specified'
    })).setMimeType(ContentService.MimeType.JSON);

  } catch(error) {
    return ContentService.createTextOutput(JSON.stringify({
      success: false,
      error: error.toString()
    })).setMimeType(ContentService.MimeType.JSON);
  }
}

// ============================================
// POST Handler - For form submissions
// ============================================
function doPost(e) {
  try {
    // ⚠️ REPLACE THIS with your actual Spreadsheet ID
    var spreadsheetId = 'YOUR_SPREADSHEET_ID_HERE';
    var sheet = SpreadsheetApp.openById(spreadsheetId).getActiveSheet();

    // Parse the incoming data
    var data = JSON.parse(e.postData.contents);

    // If this is the first entry, add headers
    if (sheet.getLastRow() === 0) {
      sheet.appendRow([
        'Entry Number',
        'Name',
        'Email',
        'Phone',
        'Rating',
        'Source',
        'Review',
        'Timestamp',
        'Date Submitted'
      ]);

      // Format header row
      var headerRange = sheet.getRange(1, 1, 1, 9);
      headerRange.setFontWeight('bold');
      headerRange.setBackground('#667eea');
      headerRange.setFontColor('#ffffff');
    }

    // Calculate entry number (current rows - header)
    var entryNumber = sheet.getLastRow();

    // Format timestamp as readable date
    // 📍 OPTIONAL: Change 'Asia/Kolkata' to your timezone
    // See: https://en.wikipedia.org/wiki/List_of_tz_database_time_zones
    var timestamp = new Date(data.timestamp);
    var formattedDate = Utilities.formatDate(timestamp, 'Asia/Kolkata', 'dd-MMM-yyyy hh:mm a');

    // Add the new row
    sheet.appendRow([
      entryNumber,
      data.name || '',
      data.email || '',
      data.phone || '',
      data.rating || '5',
      data.source || '',
      data.review || '',
      data.timestamp || new Date().toISOString(),
      formattedDate
    ]);

    // Auto-resize columns for better readability
    sheet.autoResizeColumns(1, 9);

    // Add alternating row colors for better readability
    var lastRow = sheet.getLastRow();
    if (lastRow > 1) {
      var dataRange = sheet.getRange(lastRow, 1, 1, 9);
      if (lastRow % 2 === 0) {
        dataRange.setBackground('#f8f9fa');
      }
    }

    return ContentService.createTextOutput(JSON.stringify({
      success: true,
      entryNumber: entryNumber
    })).setMimeType(ContentService.MimeType.JSON);

  } catch(error) {
    return ContentService.createTextOutput(JSON.stringify({
      success: false,
      error: error.toString()
    })).setMimeType(ContentService.MimeType.JSON);
  }
}
```

</details>

## Step 5: Configure the Spreadsheet ID

This is the most important step - connecting the script to your Google Sheet.

1. In the Apps Script editor, find **Line 23** (in the `doGet` function):
   ```javascript
   var spreadsheetId = 'YOUR_SPREADSHEET_ID_HERE';
   ```
2. Replace `YOUR_SPREADSHEET_ID_HERE` with your actual Spreadsheet ID from Step 2
3. Find **Line 62** (in the `doPost` function):
   ```javascript
   var spreadsheetId = 'YOUR_SPREADSHEET_ID_HERE';
   ```
4. Replace `YOUR_SPREADSHEET_ID_HERE` again with the same Spreadsheet ID

**Example:**
```javascript
// Before:
var spreadsheetId = 'YOUR_SPREADSHEET_ID_HERE';

// After:
var spreadsheetId = '1BxiMVs0XRA5nFMdKvBdBZjgmUUqptlbs74OgvE2upms';
```

**Tip:** Both instances must use the same Spreadsheet ID.

## Step 6: (Optional) Set Your Timezone

By default, the script formats dates using the 'Asia/Kolkata' timezone. To change it:

1. Find **Line 95** in the `doPost` function:
   ```javascript
   var formattedDate = Utilities.formatDate(timestamp, 'Asia/Kolkata', 'dd-MMM-yyyy hh:mm a');
   ```
2. Replace `'Asia/Kolkata'` with your timezone
3. Examples:
   - `'America/New_York'` - Eastern Time
   - `'America/Chicago'` - Central Time
   - `'America/Los_Angeles'` - Pacific Time
   - `'Europe/London'` - UK Time
   - `'Australia/Sydney'` - Sydney Time

[See complete timezone list](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)

## Step 7: Save the Script

1. Click the **Save** icon (floppy disk) in the toolbar
2. Or press **Ctrl+S** (Windows) / **Cmd+S** (Mac)
3. You may be prompted to name your project - enter "AuthorKit Contests" or similar

## Step 8: Deploy as Web App

Now you'll make the script accessible to your WordPress site.

1. Click **Deploy** in the top-right corner
2. Select **New deployment**
3. Click the gear icon next to "Select type"
4. Choose **Web app**
5. Configure the deployment settings:
   - **Description:** "AuthorKit Contests Integration" (optional)
   - **Execute as:** Select **Me**
   - **Who has access:** Select **Anyone**
6. Click **Deploy**

## Step 9: Authorize the Script

Google will ask for permissions since this is the first deployment.

1. Click **Authorize access**
2. Select your Google account
3. Google shows: "This app isn't verified" - this is normal for personal scripts
4. Click **Advanced**
5. Click **Go to [Your Project Name] (unsafe)** at the bottom
6. Click **Allow** to grant permissions

**Why this happens:** Google shows this warning for custom scripts. Since you created this script yourself, it's safe to authorize.

## Step 10: Copy the Web App URL

After authorization, Google Apps Script provides your Web App URL.

1. You'll see a success message with a **Web app URL**
2. The URL looks like: `https://script.google.com/macros/s/AKfycby.../exec`
3. Click **Copy** to copy the complete URL
4. Save it somewhere - you'll need it in the next step

**Important:** Keep this URL private. Anyone with this URL can submit entries to your sheet.

## Step 11: Add URL to AuthorKit

Now connect the script to your WordPress site.

### Option A: Global Default (All Contests)

Set a default script URL for all contests:

1. In WordPress, go to **Contests → Settings**
2. Find the **Google Script Integration** section
3. Paste your Web App URL into the **Default Google Apps Script URL** field
4. Click **Save Changes**

### Option B: Per-Contest Override

Set a unique script URL for a specific contest:

1. Go to **Contests → All Contests**
2. Edit the contest you want to configure
3. Scroll to the **Contest Details** metabox
4. Find the **Google Apps Script URL** field
5. Paste your Web App URL
6. Click **Update**

**Tip:** Per-contest URLs override the global default, allowing different contests to use different Google Sheets.

## Step 12: Test Your Setup

Let's verify everything works correctly.

1. Visit your contest page on your website
2. Fill out the contest form with test data
3. Submit the entry
4. Go to your Google Sheet
5. Refresh the page

You should see:
- Column headers automatically created
- Your test entry in row 2
- Formatted date and entry number
- Alternating row colors for readability

## What Data Gets Collected

The script captures these fields from contest entries:

| Column | Description |
|--------|-------------|
| Entry Number | Sequential entry count (1, 2, 3...) |
| Name | Contestant's name |
| Email | Contestant's email address |
| Phone | Phone number (if provided) |
| Rating | Star rating (typically 5 stars) |
| Source | Where they heard about the contest |
| Review | Their book review/testimonial |
| Timestamp | ISO 8601 timestamp |
| Date Submitted | Human-readable formatted date |

## Customizing the Sheet

### Change Column Order

To rearrange columns:
1. The header row is created automatically on first entry
2. After the first entry, you can drag column headers to reorder
3. Don't delete the header row - it's used for reference

### Add Conditional Formatting

Highlight important entries:
1. Select the data range
2. Click **Format → Conditional formatting**
3. Set rules (e.g., highlight 5-star reviews in green)

### Create Charts

Visualize your contest data:
1. Select your data range
2. Click **Insert → Chart**
3. Choose chart type (pie chart for sources, line chart for entries over time)

### Export Data

Export entries to other tools:
1. Click **File → Download**
2. Choose format:
   - CSV for Excel
   - PDF for sharing
   - Excel for advanced analysis

## Managing Multiple Contests

### Strategy 1: Multiple Sheets in One Spreadsheet

1. Create tabs (sheets) in your Google Spreadsheet
2. Each contest uses a different tab
3. Deploy separate scripts pointing to different sheet tabs
4. Use per-contest URLs in AuthorKit

### Strategy 2: Separate Spreadsheets

1. Create a new Google Sheet for each contest
2. Deploy a separate script for each
3. Configure per-contest URLs in AuthorKit
4. Keeps data completely isolated

**Recommendation:** Start with Strategy 1 (multiple sheets) unless you have specific privacy requirements.

## Updating the Script

To make changes after deployment:

1. Edit your code in the Apps Script editor
2. Click **Save**
3. Click **Deploy → Manage deployments**
4. Click the pencil icon next to your active deployment
5. Change the version to **New version**
6. Add description of changes (optional)
7. Click **Deploy**

**Important:** The Web App URL stays the same - you don't need to update AuthorKit.

## Troubleshooting

### Entries not appearing in sheet

**Check spreadsheet ID:**
- Verify the ID in the script matches your Google Sheet URL
- Both `doGet` and `doPost` functions must use the same ID

**Check deployment:**
- Ensure **"Who has access"** is set to **Anyone**
- Re-deploy if you changed settings

**Check the URL:**
- Copy the complete Web App URL including `/exec` at the end
- Don't use the Apps Script editor URL

### "Authorization required" errors

**Solution:**
1. Go to Apps Script editor
2. Click **Deploy → Manage deployments**
3. Click the pencil icon
4. Re-authorize the script
5. Click **Deploy**

### Wrong timezone in sheet

**Solution:**
- Update the timezone string in Line 95
- Use proper timezone identifier from [Wikipedia](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)
- Save and re-deploy

### Can't find Spreadsheet ID

**Solution:**
1. Open your Google Sheet
2. Look at the URL: `https://docs.google.com/spreadsheets/d/SPREADSHEET_ID/edit`
3. The ID is between `/d/` and `/edit`
4. It's usually 40-50 characters long

### Script works but counter doesn't update

**Note:** The entry counter on contest pages uses the `getCount` action from your Google Apps Script. If entries appear in your sheet but the counter doesn't update:

1. Verify the `doGet` function is using the correct Spreadsheet ID
2. Test the counter endpoint by visiting: `YOUR_WEB_APP_URL?action=getCount`
3. You should see: `{"success":true,"totalEntries":X}`
4. If you see an error, check the Apps Script execution logs

## Privacy & Security

### Data Storage

- Entries are stored in YOUR Google Sheet
- AuthorKit does not have access to your sheet
- You control all data

### Access Control

- Only people with the Web App URL can submit entries
- Keep the URL private
- Don't share the URL publicly

### Deleting Data

To remove contest data:
1. Delete rows from your Google Sheet (entries)
2. To revoke all access, go to **Deploy → Manage deployments** and disable the deployment

## Email Notifications (Optional)

The script includes optional code for email notifications when entries are submitted.

To enable:

1. Open your Apps Script editor
2. Scroll to the bottom (around Line 138)
3. Find the commented code block:
   ```javascript
   // MailApp.sendEmail({
   //   to: 'your-email@example.com',
   //   ...
   // });
   ```
4. Uncomment the code (remove `//` from each line)
5. Replace `your-email@example.com` with your actual email
6. Replace `[YOUR_SHEET_URL]` with your Google Sheet URL
7. Save and re-deploy

You'll receive an email for each new contest entry.

## Advanced Customization

### Add Custom Columns

To capture additional data:

1. Modify the header row array (around Line 70)
2. Add your custom field to the data row (around Line 99)
3. Update the column count in `autoResizeColumns` (Line 112)
4. Save and re-deploy

### Change Styling

Customize the sheet appearance:

**Header color:**
- Line 85: `headerRange.setBackground('#667eea');`
- Replace `#667eea` with your brand color

**Alternating rows:**
- Line 119: `dataRange.setBackground('#f8f9fa');`
- Change color as desired

### Filter Spam Entries

Add validation to prevent spam:

```javascript
// Add before sheet.appendRow() around Line 99
if (!data.email || !data.email.includes('@')) {
  return ContentService.createTextOutput(JSON.stringify({
    success: false,
    error: 'Invalid email'
  })).setMimeType(ContentService.MimeType.JSON);
}
```

## Next Steps

Now that your Google Script is set up:

1. **Test thoroughly** - Submit multiple test entries
2. **Create charts** - Visualize entry data in Google Sheets
3. **Set reminders** - Check your sheet daily during active contests
4. **Export data** - Download entries for winner selection
5. **Share insights** - Show entry progress to your team

## Related Documentation

- [Creating Contests](/authorkit-contests/creating-contests.md)
- [Managing Entries](/authorkit-contests/managing-entries.md)
- [Winner Selection](/authorkit-contests/winner-selection.md)
- [Email Notifications](/authorkit-contests/email-notifications.md)

---

**Need Help?**

If you encounter issues not covered in troubleshooting:
1. Visit [AuthorKit Support](https://authorkit.pro/support)
2. Check the [FAQ](https://docs.authorkit.pro/getting-started/faq)
3. Review [Common Issues](https://docs.authorkit.pro/troubleshooting/common-issues)

---

*Last Updated: March 9, 2026*
