# Mintlify documentation

## Working relationship

- You can push back on ideas-this can lead to better documentation. Cite sources and explain your reasoning when you do so
- ALWAYS ask for clarification rather than making assumptions
- NEVER lie, guess, or make up information

## Project context

- Format: MDX files with YAML frontmatter
- Config: docs.json for navigation, theme, settings
- Components: Mintlify components

## docs.json Navigation Structure (CRITICAL)

**Navigation must be an OBJECT, not an array.**

❌ WRONG:
```json
"navigation": [
  {
    "group": "Getting Started",
    "pages": ["index", "quickstart"]
  }
]
```

✅ CORRECT:
```json
"navigation": {
  "groups": [
    {
      "group": "Getting Started",
      "pages": ["index", "quickstart"]
    }
  ]
}
```

**Valid navigation structures:**
- `"navigation": { "groups": [...] }` - Simple sidebar (recommended)
- `"navigation": { "tabs": [...] }` - Tabbed navigation
- `"navigation": { "anchors": [...] }` - Anchor-based navigation
- `"navigation": { "languages": [...] }` - Multi-language navigation

**Common error:**
If you see "Invalid type. Expected field to be of type 'object', received 'array'", you likely used an array instead of wrapping navigation items in a `groups`, `tabs`, `anchors`, or `languages` object.

## Content strategy

- Document just enough for user success - not too much, not too little
- Prioritize accuracy and usability of information
- Make content evergreen when possible
- Search for existing information before adding new content. Avoid duplication unless it is done for a strategic reason
- Check existing patterns for consistency
- Start by making the smallest reasonable changes

## Frontmatter requirements for pages

- title: Clear, descriptive page title
- description: Concise summary for SEO/navigation

## Writing standards

- Second-person voice ("you")
- Prerequisites at start of procedural content
- Test all code examples before publishing
- Match style and formatting of existing pages
- Include both basic and advanced use cases
- Language tags on all code blocks
- Alt text on all images
- Relative paths for internal links

## MDX Syntax Requirements (CRITICAL)

**ALWAYS escape special HTML/XML characters in MDX text content:**

### Less-than signs (<)
- ❌ WRONG: `<60%`, `<30 seconds`, `<5% of students`
- ✅ CORRECT: `&lt;60%`, `&lt;30 seconds`, `&lt;5% of students`
- **Why:** MDX parses `<` as the start of a JSX tag. When followed by a number/invalid tag name, it causes parsing errors like "Unexpected character before name"

### Greater-than signs (>)
- ❌ WRONG: `>80%`, `>100 students`
- ✅ CORRECT: `&gt;80%`, `&gt;100 students`
- **Why:** Consistency and to avoid potential parsing issues

### Ampersands (&)
- ❌ WRONG: `Features & Benefits`
- ✅ CORRECT: `Features &amp; Benefits`
- **Why:** `&` starts HTML entities and can cause issues

### Apostrophes in contractions
- ❌ WRONG: `student's progress`, `don't skip`
- ✅ CORRECT: `student&apos;s progress`, `don&apos;t skip`
- **Why:** Prevents JSX parsing errors in certain contexts

### Quotes in text
- ❌ WRONG: `"Hello World"`
- ✅ CORRECT: `&quot;Hello World&quot;` or use single quotes `'Hello World'`
- **Why:** Prevents conflicts with JSX attribute quotes

**Common Patterns to Watch:**
- Percentages with comparisons: `&lt;60%`, `&gt;85%`
- Time measurements: `&lt;30 seconds`, `&lt;1 minute`
- Counts: `&lt;5 students`, `&gt;100 pages`
- Possessives: `user&apos;s data`, `school&apos;s profile`

**Testing:**
Before committing MDX files, verify no unescaped special characters:
```bash
# Find unescaped < followed by numbers
grep -rn "<[0-9]" --include="*.mdx" .

# Find unescaped apostrophes (may have false positives)
grep -rn "[a-z]'[a-z]" --include="*.mdx" .
```

## Git workflow

- NEVER use --no-verify when committing
- Ask how to handle uncommitted changes before starting
- Create a new branch when no clear branch exists for changes
- Commit frequently throughout development
- NEVER skip or disable pre-commit hooks

## Internal Link Validation

**NEVER reference pages that don't exist:**

Before adding Card components or internal links, verify the target page exists:
```bash
# Check if a page exists
ls guides/supervisor/interventions.mdx  # Returns error if doesn't exist

# List all MDX files to see available pages
find . -name "*.mdx" -type f ! -path "./node_modules/*"
```

**Common mistake:**
Creating a Card that links to `/guides/supervisor/interventions` when that file doesn't exist causes deployment errors ("nonexistent pages").

**Solution:**
- Either create the missing page first
- Or update the link to point to an existing related page

## Emoji Policy (STRICT)

**NEVER use emojis anywhere in the documentation.**

❌ WRONG: `✅ Completed`, `📊 Dashboard`, `🎯 Goal Check`
✅ CORRECT: `Completed`, `Dashboard`, `Goal Check`

**Why:**
- User explicitly requested no emojis
- Use Mintlify icon props instead: `icon="check"`, `icon="chart"`, `icon="target"`
- Emojis can cause encoding issues and look unprofessional

**Common emoji patterns to avoid:**
- Checkmarks: ✅ ❌
- Status indicators: 🟢 🔵 🔴 ⚪
- Symbols: 🎯 📊 ⏰ 📚 🚀 🎉
- Numbers: 1️⃣ 2️⃣ 3️⃣

**Verification:**
```bash
# Check for emoji usage (will find most Unicode emojis)
grep -r "[\U0001F300-\U0001F9FF]" --include="*.mdx" .
```

## Do not

- Skip frontmatter on any MDX file
- Use absolute URLs for internal links
- Include untested code examples
- Make assumptions - always ask for clarification
- Use emojis anywhere in documentation (use icon props instead)
- Reference non-existent pages in Card hrefs or internal links
- Use unescaped special characters (<, >, &, apostrophes) in MDX text
