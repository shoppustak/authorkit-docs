# Review Display

AuthorKit Reviews automatically displays approved reviews on your book pages with customizable layouts and sorting options. The display system includes star ratings, average scores, review counts, and individual review cards that integrate seamlessly with your WordPress theme.

## Automatic Display

Once you approve a review, it automatically appears on the corresponding book's page. The review section typically appears below the book description and includes:

- **Rating Summary**: Average star rating displayed as visual stars with the numeric score
- **Review Count**: Total number of approved reviews (e.g., "Based on 47 reviews")
- **Individual Reviews**: Full review cards showing each approved review
- **Submission Form**: A form for readers to add their own reviews (if under the limit)

## Rating Summary Display

The rating summary appears at the top of the review section, providing instant social proof. It shows:

- Visual star display (filled/half-filled/empty stars based on average rating)
- Numeric average (e.g., "4.5 out of 5 stars")
- Total review count with proper singular/plural formatting
- Optional rating distribution breakdown (showing how many 5-star, 4-star, etc. reviews)

**Example Display**:
```
★★★★☆ 4.3 out of 5 stars
Based on 28 reviews
```

## Individual Review Cards

Each review displays in a card format containing:

- **Reviewer Name**: The name provided during submission
- **Star Rating**: Visual star display for the specific review
- **Verified Badge**: "Verified Purchase" label if applicable
- **Review Date**: When the review was submitted (e.g., "January 15, 2026")
- **Review Text**: The full written review content
- **Helpful Count**: Optional upvote counter if helpfulness voting is enabled

## Review Sorting Options

Readers can sort reviews using a dropdown menu above the review list. Available sorting options:

- **Newest First**: Most recently submitted reviews appear first (default)
- **Highest Rated**: 5-star reviews appear first, then 4-star, etc.
- **Lowest Rated**: 1-star reviews appear first, useful for addressing concerns
- **Most Helpful**: Reviews with the most upvotes appear first (if voting is enabled)

Configure the default sorting order in AuthorKit > Reviews > Settings.

## Pagination

Control how many reviews display per page in the settings. Options typically range from 5 to 25 reviews per page. When a book has more reviews than the per-page limit, navigation links appear at the bottom allowing readers to browse through all reviews.

Pagination uses WordPress standard navigation with "Previous" and "Next" links, plus page numbers for direct access.

## Empty States

When a book has no approved reviews yet, the display shows an encouraging message like:

"Be the first to review this book! Share your thoughts with other readers."

This message appears above the review submission form, inviting engagement.

## Mobile Responsive Design

The review display automatically adapts to mobile devices, with:

- Stacked card layouts for narrow screens
- Touch-friendly star displays
- Optimized font sizes for readability
- Accessible form controls for submission

## Theme Integration

Reviews inherit your WordPress theme's typography and color scheme for seamless integration. The module uses minimal custom styling, allowing your theme to control the appearance.

If you want custom styling, add CSS targeting the `.authorkit-reviews` class in your theme's stylesheet or use the Additional CSS section in the WordPress Customizer.

## Shortcode Display

Display reviews anywhere on your site using the `[authorkit_reviews]` shortcode. Add it to any post, page, or widget area.

**Parameters**:
- `book_id`: Specify which book's reviews to display
- `limit`: Override the number of reviews shown
- `show_form`: Set to "false" to hide the submission form

**Example**:
```
[authorkit_reviews book_id="123" limit="5" show_form="false"]
```

---

**Navigation:**
- Previous: [Review Management](review-management.md)
- Next: [Frontend Submission](frontend-submission.md)
- [Developer Guide](developer-guide.md)

**Last Updated:** March 7, 2026
