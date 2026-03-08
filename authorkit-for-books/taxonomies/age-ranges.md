# Age Ranges

## Overview

Age ranges help categorize books by appropriate reader age groups. This taxonomy is particularly useful for children's books, young adult fiction, and educational materials, allowing readers and parents to find age-appropriate content.

## Accessing Age Ranges

From WordPress admin:
1. Navigate to **Books > Age Ranges**
2. View all existing age ranges
3. Add new ranges or edit existing ones

## Standard Age Ranges

### Early Childhood
**0-2 Years (Board Books)**
- Sturdy board books
- Simple images
- Few or no words
- Sensory elements

**3-5 Years (Picture Books)**
- Picture-driven stories
- Simple narratives
- Read-aloud friendly
- Basic concepts

### Children's Books
**6-8 Years (Early Readers)**
- Beginning chapter books
- Simple vocabulary
- Short chapters
- Illustrations throughout

**9-12 Years (Middle Grade)**
- Full chapter books
- Age-appropriate themes
- Growing independence
- Adventure and discovery

### Teen and Adult
**13-18 Years (Young Adult)**
- Coming-of-age themes
- Teen protagonists
- Complex issues
- Identity exploration

**18+ Years (Adult)**
- Mature themes
- Adult perspectives
- No content restrictions
- Complex narratives

## Creating Age Ranges

### From Age Ranges Screen

1. Go to **Books > Age Ranges**
2. Enter age range name (e.g., "Young Adult (13-18)")
3. Slug auto-generates (e.g., "young-adult-13-18")
4. Add description (optional)
5. Click **Add New Age Range**

### While Editing a Book

1. Edit any book
2. Find **Age Ranges** metabox
3. Click **+ Add New Age Range**
4. Enter range name
5. Click **Add New Age Range**

## Assigning Age Ranges

Unlike categories and series, books typically have only **one age range**.

### During Book Creation

1. Create or edit a book
2. Find **Age Ranges** metabox (right sidebar)
3. Select appropriate age range
4. Save the book

### Best Practices
- Choose the primary target age
- Consider reader maturity level
- Match content appropriateness
- Follow industry standards

## Age Range Descriptions

Add helpful descriptions:

**Good Description:**
```
Books for young adults aged 13-18 featuring teen protagonists navigating
coming-of-age challenges, identity, relationships, and the transition to
adulthood. Themes include independence, self-discovery, and finding one's
place in the world.
```

## Age Range Archives

WordPress creates automatic archive pages:

**URL Format:**
```
yoursite.com/age-range/young-adult/
yoursite.com/age-range/middle-grade/
yoursite.com/age-range/picture-books/
```

## Using Age Ranges in Shortcodes

### Filter by Age Range
```
[authorkit_books age_range="young-adult"]
```

### Multiple Age Ranges
```
[authorkit_books age_range="young-adult,middle-grade"]
```

## Creating Age-Specific Pages

### Dedicated Age Range Page

```
# Books for Young Adults

Perfect for readers aged 13-18 exploring identity, independence, and
the challenges of growing up.

[authorkit_books age_range="young-adult" orderby="date" order="DESC"]
```

### Browse by Age Page

```
## For Young Readers

### Picture Books (Ages 3-5)
[authorkit_books age_range="picture-books" limit="6"]

### Early Readers (Ages 6-8)
[authorkit_books age_range="early-readers" limit="6"]

### Middle Grade (Ages 9-12)
[authorkit_books age_range="middle-grade" limit="6"]
```

## Content Guidelines by Age

### Board Books (0-2)
- No scary content
- Bright, simple illustrations
- Basic concepts (colors, shapes, animals)
- Durable format

### Picture Books (3-5)
- Simple plots
- Positive messages
- Minimal text per page
- Engaging illustrations

### Early Readers (6-8)
- Short sentences
- Familiar situations
- Problem-solving themes
- Encouraging messages

### Middle Grade (9-12)
- Age-appropriate challenges
- Friendship themes
- Adventure and discovery
- Some complexity

### Young Adult (13-18)
- Coming-of-age themes
- Identity exploration
- Real-world issues
- Teen protagonists

### Adult (18+)
- No age restrictions
- Mature themes possible
- Complex narratives
- Adult perspectives

## Marketing with Age Ranges

### Parent Resources
Help parents find appropriate books:
- Clear age range labeling
- Content warnings if needed
- Reading level guidance

### School and Library Sales
Age ranges help educators select appropriate materials.

### Cross-Age Appeal
Some books appeal to multiple ages:
- Harry Potter: Middle Grade to Adult
- The Giver: Young Adult to Adult

Choose the primary target age range.

## Editing Age Ranges

1. Go to **Books > Age Ranges**
2. Click age range name
3. Modify name, slug, or description
4. Click **Update**

## Deleting Age Ranges

1. Go to **Books > Age Ranges**
2. Hover over range name
3. Click **Delete**
4. Confirm

Books remain but age range assignment is removed.

## SEO Considerations

### Use Standard Terms
Stick to recognized age categories:
- "Young Adult" not "Teen Books"
- "Middle Grade" not "Tween Books"

### Descriptions
Include age numbers and grade levels for better search matching:
```
Middle Grade books for ages 9-12 (grades 4-6)
```

### Parent Searches
Parents often search: "books for 10 year olds" or "age-appropriate books for teens"

## Combining with Categories

Age ranges work alongside categories:

**Example:**
- Category: Fantasy
- Age Range: Young Adult
- Result: Young Adult Fantasy

This combination helps readers find exactly what they want.

## International Considerations

Age ranges vary by country:
- US: Middle Grade (9-12)
- UK: Junior Fiction (8-12)
- Some countries use grade levels

Choose terms that resonate with your primary audience.

## Troubleshooting

**Books appear in multiple age ranges:**
- Age ranges should be single-select
- Check that only one is assigned
- Verify custom code isn't allowing multiple

**Age range archive empty:**
- Verify books assigned to age range
- Check books are Published
- Clear cache if needed

**Wrong age range showing:**
- Edit book and update assignment
- Save changes
- Clear browser and WordPress cache

---

**Related Documentation:**
- [Book Categories](/taxonomies/book-categories.md)
- [Book Series](/taxonomies/book-series.md)
- [Managing Books](/managing-books/README.md)
- [Shortcodes Overview](/shortcodes/overview.md)

---

*Last Updated: March 7, 2026*
