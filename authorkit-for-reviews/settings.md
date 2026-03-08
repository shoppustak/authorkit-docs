# Settings

Configure every aspect of the Reviews module through the settings panel located at AuthorKit > Reviews > Settings. These options control display, moderation, notifications, spam protection, and form behavior.

## General Settings

Access general settings to configure basic review functionality:

**Enable Reviews Module**: Toggle to activate/deactivate reviews across your entire site. When disabled, existing reviews remain in the database but don't display.

**Reviews Per Page**: Set how many reviews display on each page (5, 10, 15, 20, or 25). Higher numbers reduce pagination but increase page load time.

**Default Sort Order**: Choose the default sorting for review display:
- Newest First (default)
- Highest Rated
- Lowest Rated
- Most Helpful (if voting enabled)

**Require Login to Review**: When enabled, only logged-in WordPress users can submit reviews. Useful for membership sites or to reduce spam.

**Auto-Approve Reviews**: Automatically approve reviews from trusted reviewers (those with previously approved reviews) without moderation. Use cautiously as this bypasses spam protection.

## Display Settings

Control what information appears in the review section:

**Show Average Rating**: Display the calculated average star rating at the top of the review section.

**Show Review Count**: Display total number of reviews (e.g., "Based on 28 reviews").

**Show Rating Distribution**: Display a breakdown chart showing how many 5-star, 4-star, 3-star, 2-star, and 1-star reviews exist.

**Show Verified Badges**: Display "Verified Purchase" badges next to reviews marked as verified.

**Show Review Dates**: Display submission dates for each review (e.g., "January 15, 2026").

**Date Format**: Choose how dates appear:
- Relative (e.g., "2 days ago")
- Absolute (e.g., "March 7, 2026")
- Custom format using PHP date format strings

**Empty State Message**: Customize the message shown when a book has no reviews yet. Default: "Be the first to review this book!"

## Form Settings

Customize the review submission form:

**Form Position**: Choose where the form appears:
- Above reviews
- Below reviews (default)
- Hidden (disable public submissions)

**Minimum Review Length**: Set minimum character count for review text (default: 10 characters). Prevents low-quality "Great!" submissions.

**Maximum Review Length**: Set maximum character count (default: 1000 characters). Prevents extremely long submissions that may be spam.

**Field Labels**: Customize the label text for:
- Name field
- Email field
- Rating field
- Review text field

**Placeholder Text**: Add helpful placeholder text inside each field to guide reviewers.

**Submit Button Text**: Customize the button text (default: "Submit Review").

**Success Message**: Customize the confirmation message shown after successful submission.

**Error Messages**: Customize messages for validation errors, duplicate submissions, and rate limiting.

## Moderation Settings

Configure how reviews are moderated:

**Default Status**: Set whether new reviews are:
- Pending (require approval)
- Approved (publish immediately)
- Rejected (block by default)

**Moderation Queue Notifications**: Email administrators when reviews enter the pending queue.

**Notification Recipients**: Specify email addresses to receive moderation alerts (comma-separated for multiple recipients).

**Notification Subject**: Customize the email subject line for moderation alerts.

**Notification Message**: Customize the email body text, including review details and moderation links.

## Spam Protection Settings

Configure spam prevention measures:

**Enable Honeypot Protection**: Add invisible fields that bots fill out, automatically rejecting those submissions.

**Rate Limiting**: Set the time period (in hours) before the same IP address can submit another review for the same book. Default: 24 hours. Set to 0 to disable.

**Block Disposable Emails**: Automatically reject reviews from temporary email services commonly used by spammers.

**Spam Keywords**: Add a list of words or phrases that trigger automatic rejection or extra scrutiny (comma-separated).

**Link Limit**: Set maximum number of URLs allowed in review text. Reviews exceeding this limit are automatically flagged. Default: 0 (no links allowed).

## Email Notification Settings

Configure emails sent to reviewers:

**Send Submission Confirmation**: Email reviewers when their review is received (pending status).

**Send Approval Notification**: Email reviewers when their review is approved and published.

**Send Rejection Notice**: Email reviewers when their review is rejected (use cautiously, as this may encourage spam responses).

**Confirmation Email Subject**: Customize subject line for submission confirmations.

**Approval Email Subject**: Customize subject line for approval notifications.

**Email From Name**: Set the sender name that appears in reviewer emails (default: site name).

**Email From Address**: Set the sender email address (default: WordPress admin email).

## Advanced Settings

Additional configuration options for power users:

**Enable Helpful Voting**: Allow readers to upvote helpful reviews, which affects "Most Helpful" sorting.

**Enable Review Reporting**: Add a "Report" link to reviews, allowing readers to flag inappropriate content for moderator review.

**Disable Review Schema**: Disable structured data markup for reviews. Leave enabled for better SEO unless it conflicts with other plugins.

**Custom CSS Classes**: Add custom CSS classes to review elements for advanced styling.

**Review Expiration**: Automatically archive reviews older than a specified number of days (0 = never expire).

## Saving Settings

Click "Save Changes" at the bottom of the settings page to apply your configuration. Changes take effect immediately across all book pages.

**Important**: Always review display settings changes on the frontend to ensure they match your design preferences.

---

**Navigation:**
- Previous: [Frontend Submission](frontend-submission.md)
- [Overview](overview.md)
- [Developer Guide](developer-guide.md)

**Last Updated:** March 7, 2026
