# Frontend Submission

Readers can submit reviews directly from your book pages using a clean, accessible form that requires no WordPress account. The submission system includes spam protection, validation, and instant feedback to ensure a smooth user experience.

## Review Submission Form

The review form appears on each book page, typically below existing reviews. It includes:

- **Name Field**: Required text input for the reviewer's name
- **Email Field**: Required for notifications (never displayed publicly)
- **Star Rating**: Required visual star selector (click to select 1-5 stars)
- **Review Text**: Required textarea for written review (minimum 10 characters)
- **Submit Button**: Clearly labeled "Submit Review" button

All fields are marked as required with asterisks and validated before submission.

## Form Location

By default, the submission form appears at the bottom of the review section on each book page. This placement allows readers to browse existing reviews before adding their own, which often results in more thoughtful submissions.

Configure form placement in AuthorKit > Reviews > Settings to:
- Display above existing reviews
- Display below existing reviews (default)
- Hide the form entirely (reviews by invitation only)

## Submission Process

When a reader completes and submits the form:

1. **Client-Side Validation**: JavaScript validates required fields and minimum length before submitting
2. **Server-Side Processing**: WordPress processes the submission, checking for spam and duplicates
3. **Pending Status**: The review enters a pending state awaiting moderation
4. **Confirmation Message**: The reader sees a success message: "Thank you for your review! It will appear after moderation."
5. **Admin Notification**: Site administrators receive an email alert about the new pending review

The form uses AJAX submission, so the page doesn't reload, providing a smooth experience.

## Star Rating Selector

The star rating input uses an interactive visual selector where readers click or tap on stars to select their rating:

- Hover over stars to preview the selection (desktop)
- Click/tap a star to lock in the rating
- Selected stars appear filled/highlighted
- The exact rating (1-5) is submitted with the form

This visual interface is more intuitive than a dropdown menu and encourages engagement.

## Spam Protection

The submission form includes multiple spam prevention measures:

**Honeypot Field**: An invisible field that bots typically fill out, but humans never see. Submissions with this field filled are automatically rejected.

**Rate Limiting**: Each IP address can only submit one review per book per 24-hour period. This prevents spam flooding while allowing legitimate users to review multiple books.

**Email Validation**: The system validates email addresses for proper formatting and checks against known disposable email domains commonly used by spammers.

**Text Analysis**: Reviews with excessive links, repeated characters, or common spam phrases are automatically flagged for extra scrutiny.

No CAPTCHA is required, keeping the submission process simple for legitimate readers.

## Duplicate Prevention

Readers cannot submit multiple reviews for the same book. If someone attempts to submit a second review:

- The form displays a message: "You've already reviewed this book."
- The submission is blocked client-side
- Previous approved review is shown instead

This is tracked by email address, so changing the name doesn't bypass the restriction.

## Review Count Limits

On free tier sites, the submission form automatically hides when a book reaches 3 reviews. Visitors see a message:

"This book has reached its review limit. Upgrade to Pro for unlimited reviews."

Pro tier sites have no limits, and the form remains available indefinitely.

## Email Notifications to Reviewers

Configure whether reviewers receive confirmation emails when:
- Their review is submitted (pending confirmation)
- Their review is approved (publication notification)
- Their review is rejected (optional rejection notice)

Set these options in AuthorKit > Reviews > Settings > Email Notifications.

## Form Customization

Customize the submission form through settings:

**Field Labels**: Change the text for each form field label
**Placeholder Text**: Add helpful placeholder text inside input fields
**Button Text**: Customize the submit button text
**Success Message**: Modify the confirmation message shown after submission
**Minimum Review Length**: Set the minimum character count for review text (default: 10)

## Accessibility

The form follows WordPress accessibility standards:

- Proper label associations for screen readers
- Keyboard navigation support for star selection
- Clear error messages for validation failures
- Focus management for form submission feedback
- ARIA labels for interactive elements

## Guest Submissions

Readers don't need a WordPress account to submit reviews. The form accepts submissions from anyone visiting your site. Email addresses are collected for duplicate prevention and optional notifications but are never displayed publicly.

If you prefer to restrict reviews to logged-in users only, enable "Require Login to Review" in settings.

---

**Navigation:**
- Previous: [Review Display](review-display.md)
- Next: [Settings](settings.md)
- [Developer Guide](developer-guide.md)

**Last Updated:** March 7, 2026
