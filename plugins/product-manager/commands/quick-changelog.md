# Quick Changelog Command

Generates a user-facing changelog from recent commits in 3-5 minutes, perfect for release notes, update announcements, or quick status updates.

## Purpose

Create a quick changelog when:
- Preparing for a release or deploy
- Need update notes for stakeholders
- Writing a "What's New" announcement
- Documenting a sprint's user-facing changes
- Creating release notes for App Store/Product Hunt

## When to Use

**Use quick-changelog when**:
- Need changelog in 3-5 minutes
- Covering last 5-20 commits
- Simple user-facing summary needed
- Informal update announcement
- Quick stakeholder communication

**Use full changelog-creation skill when**:
- Need comprehensive release notes
- Multiple versions to document
- Requires detailed categorization
- User research/impact analysis needed
- Publishing to external audiences

## Command Format

```bash
/quick-changelog [number of commits or date range]
```

### Optional Parameters

Add context to improve changelog quality:

```
--since [date/tag]       Start from date or git tag (e.g., "v1.2.0", "2 weeks ago")
--format [style]         Output style: "markdown", "slack", "email", "tweet"
--audience [type]        Target audience: "users", "developers", "internal"
--repo [path]           Repository path (defaults to current directory)
```

## Examples

### Example 1: Basic Recent Changes

```bash
/quick-changelog 10
```

**Expected Output**:
```
## What's New (Last 10 commits)

### ✨ New Features
- **AI-powered search**: Find content faster with natural language queries
- **Dark mode**: Easy on the eyes with automatic theme switching
- **Bulk export**: Export multiple documents at once as PDF

### 🔧 Improvements
- Faster page load times (40% improvement)
- Better mobile navigation with bottom tab bar
- Improved error messages with helpful suggestions

### 🐛 Bug Fixes
- Fixed: Images not loading on slow connections
- Fixed: Crash when uploading files >10MB
- Fixed: Notifications not clearing properly

---
Generated from commits a3f9c21...d8b2e45
Date range: Feb 1 - Feb 15, 2026
Time to generate: 3 minutes
For detailed release notes: Use /changelog-creation skill
```

### Example 2: Since Last Release

```bash
/quick-changelog --since v2.1.0 --format slack
```

**Expected Output**:
```
:rocket: *Product Update: v2.2.0*

*New stuff you'll love:*
:sparkles: AI-powered search - Just describe what you're looking for
:art: Dark mode - Automatic switching based on system preferences
:package: Bulk export - Save time exporting multiple docs

*Under the hood improvements:*
:zap: 40% faster page loads
:iphone: Better mobile navigation
:speech_balloon: Clearer error messages

*Squashed bugs:*
:bug: Images now load on slow connections
:bug: Large file uploads (up to 10MB) work perfectly
:bug: Notifications clear as expected

Rolled out: Feb 15, 2026
Questions? Drop them in #product-feedback

---
Generated from v2.1.0...HEAD (23 commits)
Time to generate: 4 minutes
```

### Example 3: Last Two Weeks for Email

```bash
/quick-changelog --since "2 weeks ago" --format email --audience users
```

**Expected Output**:
```
Subject: Product Updates - February 2026

Hi there,

We've been busy making your experience better! Here's what's new in the last two weeks:

🎉 NEW FEATURES

AI-Powered Search
You asked, we delivered! Find anything with natural language queries like "meeting notes from last week with Sarah." Just type naturally and we'll find it.

Dark Mode
Late-night working? We've got you covered. Dark mode automatically switches based on your system preferences, or toggle it manually.

Bulk Export
Need to export multiple documents? Select them all and export as PDF in one click. Big time-saver for end-of-week reporting.

⚡ IMPROVEMENTS

• Page Load Speed: We optimized our caching layer, resulting in 40% faster load times, especially on slower connections.

• Mobile Navigation: New bottom tab bar makes it easier to switch between sections on mobile. Much more thumb-friendly!

• Error Messages: When something goes wrong, we now show you exactly what happened and how to fix it.

🐛 BUG FIXES

• Images now load reliably on slower connections
• Large files (up to 10MB) upload without issues
• Notifications properly clear when you've read them

That's all for now! Got feedback? Reply to this email or use the feedback button in the app.

Happy building,
The Product Team

---
Release: v2.2.0
Date: February 15, 2026
Based on: 23 commits since Feb 1, 2026
```

### Example 4: Developer-Focused Changelog

```bash
/quick-changelog 15 --audience developers
```

**Expected Output**:
```
## Changelog (Last 15 commits)

### Features
- Add Elasticsearch integration for semantic search (#245)
  - Implements natural language query parsing
  - Adds vector similarity scoring
  - Includes query result caching (5min TTL)

- Implement dark mode theme support (#238)
  - CSS custom properties for theme switching
  - Persists preference to localStorage
  - Respects prefers-color-scheme media query

- Add bulk PDF export endpoint (#242)
  - New POST /api/export/bulk endpoint
  - Supports up to 50 documents per request
  - Uses Puppeteer for PDF generation

### Improvements
- Optimize React component rendering with memo (#241)
  - Reduces re-renders by 60% on document list
  - Implements virtual scrolling for 1000+ items

- Migrate to React Router v6 (#239)
  - Updates routing API usage
  - Removes deprecated Switch/Redirect

- Add request tracing with OpenTelemetry (#243)
  - Full distributed tracing
  - Exports to Jaeger

### Bug Fixes
- Fix image loading race condition (#244)
  - Adds retry logic with exponential backoff
  - Handles CORS properly for external images

- Increase max file upload size to 10MB (#240)
  - Updates nginx config
  - Adds proper error handling for oversized files

- Fix notification WebSocket reconnection (#237)
  - Implements exponential backoff
  - Handles auth token refresh

### Technical Debt
- Remove deprecated API v1 endpoints (#246)
- Update dependencies to latest stable versions (#236)

---
Commit range: a3f9c21...d8b2e45
Breaking changes: API v1 endpoints removed (use v2)
Database migrations: 2 new migrations (run before deploy)

Time to generate: 5 minutes
For detailed technical docs: Use /changelog-creation skill
```

### Example 5: Twitter/Social Format

```bash
/quick-changelog 5 --format tweet
```

**Expected Output**:
```
🚀 Just shipped v2.2.0!

✨ AI-powered search - find anything with natural language
🌙 Dark mode - automatic theme switching
📦 Bulk export - multiple docs to PDF at once
⚡ 40% faster page loads
🐛 Fixed image loading issues

Try it now: [your-product.com]

#ProductUpdate #NewFeatures

---
Character count: 267/280
Alternative shorter version (if needed):

🚀 v2.2.0 is live!

✨ AI search
🌙 Dark mode
📦 Bulk export
⚡ 40% faster

Try it: [link]

[168 characters]

Time to generate: 3 minutes
```

## Generation Methodology

The command uses fast processing for speed:

### Commit Analysis

```
1. Fetch commits from range
2. Parse commit messages (conventional commits preferred)
3. Group by type (feat, fix, chore, etc.)
4. Filter out internal/technical changes
5. Rewrite in user-friendly language
6. Add relevant emojis/formatting
```

### Categorization

```
Features (feat):
- ✨ New features
- New user-facing capabilities

Improvements (refactor, perf):
- 🔧 Enhancements
- Performance improvements
- UX refinements

Bug Fixes (fix):
- 🐛 Bug fixes
- Issues resolved

Skipped:
- Chore commits (unless user-impacting)
- Test updates
- Internal refactoring
- CI/CD changes
```

### Language Transformation

```
Commit: "feat: add elasticsearch integration for semantic search"
User-facing: "AI-powered search: Find content with natural language"

Commit: "fix: handle CORS errors in image loading"
User-facing: "Fixed: Images not loading on slow connections"

Commit: "perf: optimize React rendering with memo"
User-facing: "Faster page load times (40% improvement)"
```

## Output Format

Every quick changelog includes:

1. **Categorized Changes**
   - Features (what's new)
   - Improvements (what's better)
   - Bug Fixes (what's fixed)

2. **User-Friendly Language**
   - Benefit-focused, not technical
   - Active voice, clear impact
   - Emojis for visual scanning (format-dependent)

3. **Metadata**
   - Commit range or date range
   - Number of commits analyzed
   - Time to generate
   - Link to full skill for detail

4. **Format-Specific Elements**
   - Markdown: Clean headers and bullets
   - Slack: Emoji bullets and bold text
   - Email: Friendly tone with sections
   - Tweet: Concise with character count

## Limitations

**Quick changelog is NOT suitable for**:
- Major version releases (use full skill)
- External announcement (App Store, Product Hunt)
- Detailed technical documentation
- Marketing launch content
- Comprehensive migration guides

**Accuracy factors**:
- Relies on good commit messages
- May miss context without issue references
- Automated categorization (no manual review)
- Best for recent, well-documented changes
- User impact inferred from commit messages

## Improving Changelog Quality

To get better automated changelogs:

1. **Use conventional commits**: feat, fix, perf, refactor, etc.
2. **Write descriptive messages**: What changed and why
3. **Include issue numbers**: Links to PRs/issues add context
4. **Tag releases**: Makes --since v1.0.0 work perfectly
5. **Use full skill**: When accuracy and polish matter

### Conventional Commit Examples

```bash
# Good commit messages for changelog generation
feat: add dark mode with system preference detection
fix: resolve image loading on slow connections
perf: optimize React rendering, 40% faster page loads
refactor: migrate to React Router v6 (internal)

# Less useful for changelog
Fixed stuff
Update components
Changes
WIP
```

## Common Use Cases

### Release Notes
```bash
/quick-changelog --since v2.1.0
# Generate release notes for v2.2.0
```

### Sprint Review
```bash
/quick-changelog --since "2 weeks ago" --audience internal
# Summarize sprint for team demo
```

### Stakeholder Update
```bash
/quick-changelog 20 --format email --audience users
# Monthly update email to users
```

### Social Announcement
```bash
/quick-changelog 5 --format tweet
# Quick social post about latest updates
```

### Developer Changelog
```bash
/quick-changelog --since v2.1.0 --audience developers
# Technical changelog for API consumers
```

## Tips for Better Changelogs

1. **Good commit hygiene**: Quality in = quality out

2. **Use --since tags**: More accurate than commit counts

3. **Match audience**: Users want benefits, developers want details

4. **Choose right format**: Slack for quick updates, email for formal

5. **Review before publishing**: Auto-generated content needs a human check

6. **Link to docs**: Reference full docs for complex features

7. **Highlight breaking changes**: Call out anything that needs action

## Integration with Other Skills

- **changelog-creation**: Use for comprehensive, polished release notes
- **improvement-proposals**: Generate changelog from implemented PRDs
- **competitive-intelligence**: Compare your updates to competitor features

## Related Commands

- `/changelog-creation` - Full changelog with user research and polish
- `/feature-impact-estimate` - Estimate which changes matter most to users
- `/quick-competitive-scan` - See how your updates compare to competitors

---

**Remember**: Quick changelogs are drafts. Review and refine before publishing to external audiences. For major releases, use the full changelog-creation skill.
