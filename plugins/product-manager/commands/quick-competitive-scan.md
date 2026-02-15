# Quick Competitive Scan Command

Provides a rapid competitor overview with feature parity check for fast decision-making without conducting full competitive intelligence.

## Purpose

Get a quick competitive snapshot when:
- Evaluating a feature idea against competitors
- Preparing for stakeholder meetings
- Validating market gaps quickly
- Making fast prioritization decisions
- Responding to "what do competitors do?" questions

## When to Use

**Use quick-competitive-scan when**:
- Need insights in 5-10 minutes
- Evaluating 2-5 specific competitors
- Checking feature parity on specific capabilities
- Making fast go/no-go decisions
- Early stage idea validation

**Use full competitive-intelligence skill when**:
- Need comprehensive market analysis
- Evaluating business model differences
- Analyzing pricing strategies in depth
- Building competitive positioning strategy
- Presenting to board or investors

## Command Format

```bash
/quick-competitive-scan [feature or product area] [competitor1] [competitor2] [competitor3]
```

### Optional Parameters

Add context to improve scan accuracy:

```
--focus [aspect]         What to focus on (features, pricing, UX, performance)
--our-status [status]    Current state of our product ("have", "building", "planning")
--timeframe [duration]   How urgently needed (for prioritization context)
```

## Examples

### Example 1: Basic Feature Parity Check

```bash
/quick-competitive-scan Real-time collaboration Notion Figma Miro
```

**Expected Output**:
```
Quick Competitive Scan: Real-time Collaboration

Competitor Overview (3 analyzed):

1. Notion
   ✓ Multi-user editing with live cursors
   ✓ @mentions and comments
   ✓ Change history and version control
   ✓ Presence indicators (who's viewing)
   ⚠ Occasional sync delays reported by users

2. Figma
   ✓ Industry-leading real-time collaboration
   ✓ Live cursors with user names/colors
   ✓ Audio chat built-in
   ✓ Commenting and reactions
   ✓ Version branching
   ⭐ Gold standard for real-time collab

3. Miro
   ✓ Real-time board editing (up to 50 users)
   ✓ Video chat integration
   ✓ Timer and voting features
   ✓ Presentation mode with follow-me
   ⚠ Can lag with 20+ simultaneous users

Feature Parity Matrix:
┌─────────────────────────┬────────┬────────┬──────┐
│ Capability              │ Notion │ Figma  │ Miro │
├─────────────────────────┼────────┼────────┼──────┤
│ Live cursors            │   ✓    │   ✓    │  ✓   │
│ Presence indicators     │   ✓    │   ✓    │  ✓   │
│ Real-time sync          │   ⚠    │   ✓    │  ⚠   │
│ Comments                │   ✓    │   ✓    │  ✓   │
│ Version history         │   ✓    │   ✓    │  ✓   │
│ Built-in comms          │   ✗    │   ✓    │  ✓   │
│ Offline mode            │   ✓    │   ⚠    │  ✗   │
└─────────────────────────┴────────┴────────┴──────┘

Key Insights:
• Table stakes: Live cursors, presence, comments are expected
• Differentiator: Built-in voice/video (Figma/Miro have it)
• Performance: Sync quality matters more than feature count
• Gap opportunity: Offline-first with conflict resolution

Recommendation:
MUST-HAVE: Live cursors, presence, real-time sync
CONSIDER: Built-in comms (or integrate with Slack/Teams)
DIFFERENTIATE: Better offline mode than Figma

Time estimate: 5-10 min scan
For deeper analysis: Use /competitive-intelligence skill
```

### Example 2: With Focus Parameter

```bash
/quick-competitive-scan AI writing assistant Jasper Copy.ai Writesonic --focus pricing
```

**Expected Output**:
```
Quick Competitive Scan: AI Writing Assistant Pricing

Competitor Pricing Models (3 analyzed):

1. Jasper
   • Boss Mode: $49/month (50k words)
   • Business: $125/month (unlimited words)
   • Free trial: 7 days
   • Annual discount: 20%
   • Positioning: Premium, for professionals

2. Copy.ai
   • Free: 2,000 words/month
   • Pro: $36/month (unlimited words)
   • Team: $186/month (5 seats)
   • Free trial: Freemium model
   • Positioning: Accessible, growth-focused

3. Writesonic
   • Free: 10,000 words (one-time)
   • Unlimited: $16/month
   • Business: $12.67/month per user (annual)
   • Free trial: Generous free tier
   • Positioning: Budget-friendly

Pricing Strategy Comparison:
┌──────────────┬─────────┬──────────┬─────────────┐
│ Aspect       │ Jasper  │ Copy.ai  │ Writesonic  │
├──────────────┼─────────┼──────────┼─────────────┤
│ Entry price  │ $49/mo  │ Free     │ Free        │
│ Mid-tier     │ $49/mo  │ $36/mo   │ $16/mo      │
│ Pro tier     │ $125/mo │ $186/mo  │ Custom      │
│ Model        │ Tiered  │ Seat+    │ Usage-based │
│ Free trial   │ 7 days  │ Forever  │ Forever     │
└──────────────┴─────────┴──────────┴─────────────┘

Key Insights:
• Market range: $0-125/month for individual users
• Freemium common: 2 of 3 offer generous free tiers
• Word limits: Mostly unlimited at paid tiers
• Seat-based: For team/business tiers
• Premium positioning: Jasper charges 3x competitors

Pricing Recommendations:
• COMPETITIVE: $19-29/month for unlimited tier
• ACQUISITION: Freemium with 5k-10k words/month
• PREMIUM: If targeting enterprise, $49+ justified
• DIFFERENTIATE: Usage-based on features, not word count

Market positioning gap:
→ Mid-tier option ($20-35) with better features than Copy.ai

Time estimate: 7 min scan
For pricing strategy: Use /monetization-strategy-review skill
```

### Example 3: Feature We're Planning

```bash
/quick-competitive-scan Export to PDF/PowerPoint Canva Pitch Beautiful.ai --our-status planning
```

**Expected Output**:
```
Quick Competitive Scan: Export Capabilities

Current Status: Planning phase

Competitor Feature Analysis (3 analyzed):

1. Canva
   ✓ PDF export (standard/high quality)
   ✓ PowerPoint export (PPTX)
   ✓ Video export (MP4)
   ✓ Animated GIF export
   ✓ PNG/JPG with transparency
   ⚠ PPTX export sometimes loses formatting
   💰 Some exports require Pro ($12.99/mo)

2. Pitch
   ✓ PDF with notes
   ✓ PowerPoint (PPTX) - excellent fidelity
   ✓ Live presentation mode
   ✓ Shareable links
   ✗ No video export
   💰 All exports available in free tier

3. Beautiful.ai
   ✓ PDF export
   ✓ PowerPoint (PPTX)
   ✓ PNG/JPG slides
   ✓ Maintains animations in PPTX
   ⚠ Limited customization on export
   💰 Pro exports require Team plan ($40/user/mo)

Feature Matrix:
┌──────────────────┬────────┬───────┬──────────────┐
│ Export Format    │ Canva  │ Pitch │ Beautiful.ai │
├──────────────────┼────────┼───────┼──────────────┤
│ PDF              │   ✓    │   ✓   │      ✓       │
│ PowerPoint       │   ⚠    │   ✓   │      ✓       │
│ Video            │   ✓    │   ✗   │      ✗       │
│ Animated GIF     │   ✓    │   ✗   │      ✗       │
│ PNG/JPG          │   ✓    │   ✗   │      ✓       │
│ Keeps formatting │   ⚠    │   ✓   │      ✓       │
│ Free tier        │   ⚠    │   ✓   │      ✗       │
└──────────────────┴────────┴───────┴──────────────┘

User Expectations:
• PDF export: Absolute minimum (all competitors have it)
• PowerPoint: Expected for B2B products
• Format fidelity: Critical - users complain when broken
• Free vs paid: Varies by market positioning

Implementation Considerations:
• PDF: Standard feature, use proven libraries
• PPTX: Complex but expected - high ROI if done well
• Video: Nice-to-have, significant dev effort
• Quality options: "Standard" and "High" quality common

Recommendation:
MVP: PDF export (high quality)
V2: PowerPoint with good fidelity (differentiator)
LATER: Video/GIF (if usage data supports)

Estimated effort:
• PDF only: 2-3 weeks
• PDF + PPTX: 6-8 weeks
• All formats: 10-12 weeks

Time estimate: 8 min scan
For implementation planning: Use /improvement-proposals skill
```

### Example 4: Gap Analysis

```bash
/quick-competitive-scan Keyboard shortcuts Slack Discord Twist --focus UX
```

**Expected Output**:
```
Quick Competitive Scan: Keyboard Shortcuts (UX Focus)

Competitor UX Analysis (3 analyzed):

1. Slack
   ✓ Extensive shortcuts (50+)
   ✓ Cmd+K quick switcher (power feature)
   ✓ Cmd+/ shows shortcut list
   ✓ Customizable shortcuts
   ✓ Platform-specific (Mac/Win/Linux)
   ⭐ Industry standard for productivity

2. Discord
   ✓ 30+ keyboard shortcuts
   ✓ Ctrl+K quick switcher
   ✓ Unread navigation (Alt+Shift+↑/↓)
   ✓ Mute/deafen shortcuts
   ⚠ Shortcuts not customizable
   ⚠ Less discoverable than Slack

3. Twist
   ✓ Basic shortcuts (20+)
   ✓ Thread-specific navigation
   ✓ Quick actions (mark read, star)
   ✗ No quick switcher
   ⚠ Limited compared to competitors

Common Patterns:
┌────────────────────────┬────────┬─────────┬───────┐
│ Feature                │ Slack  │ Discord │ Twist │
├────────────────────────┼────────┼─────────┼───────┤
│ Quick switcher (Cmd+K) │   ✓    │    ✓    │   ✗   │
│ Show shortcuts         │   ✓    │    ⚠    │   ✓   │
│ Channel navigation     │   ✓    │    ✓    │   ✓   │
│ Unread jumping         │   ✓    │    ✓    │   ✓   │
│ Search                 │   ✓    │    ✓    │   ✓   │
│ Customizable           │   ✓    │    ✗    │   ✗   │
│ Discoverable           │   ⭐   │    ⚠    │   ⚠   │
└────────────────────────┴────────┴─────────┴───────┘

UX Insights:
• Quick switcher (Cmd+K): Essential power user feature
• Discoverability: Cmd+/ to show shortcuts is standard
• Progressive disclosure: Basic shortcuts + advanced
• Customization: Only leader (Slack) offers it
• Platform parity: Must work on Mac, Win, Linux

Best Practices Observed:
1. Quick switcher for instant navigation
2. Help/tutorial on first use
3. Visual hints (tooltips showing shortcuts)
4. Vim-style navigation for power users (optional)
5. Sensible defaults aligned with platform conventions

Gap Opportunity:
→ Contextual shortcut hints (show relevant shortcuts per view)
→ Learning mode (highlights shortcuts as you work)
→ Smart shortcuts (adapt to user's frequent actions)

Minimum Viable Shortcuts:
MUST HAVE:
• Cmd+K quick switcher
• Cmd+/ show all shortcuts
• Basic navigation (↑↓, Enter, Esc)
• Search (Cmd+F)

POWER USER:
• Mark read/unread
• Star/favorite
• Jump to unread
• Reply/thread actions

DIFFERENTIATION:
• Adaptive shortcuts (learn user patterns)
• Conflict-free customization

Time estimate: 9 min scan
For UX strategy: Use /persona-definition skill
```

## Scan Methodology

The command uses rapid analysis for speed:

### Information Sources

```
Primary:
- Public product documentation
- Feature comparison pages
- User reviews (G2, Capterra)
- Product demos/videos
- Pricing pages

Limitations:
- Surface-level only
- May miss enterprise features
- Based on current public info
- No hands-on testing
```

### Feature Assessment

```
✓ = Has feature, works well
⚠ = Has feature, with caveats
✗ = Missing or very limited
⭐ = Industry-leading
💰 = Pricing note
```

### Competitor Selection

```
Include in scan:
- Direct competitors (same category)
- 2-5 competitors max for quick scan
- Mix of leaders and challengers

For comprehensive analysis:
- Use competitive-intelligence skill
- Analyze 5-10+ competitors
- Include indirect competitors
```

## Output Format

Every quick scan includes:

1. **Competitor Overview**
   - Key features for each competitor
   - Notable strengths/weaknesses
   - Quick assessment markers

2. **Feature Parity Matrix**
   - Visual comparison table
   - Quick-scan capabilities
   - Clear gaps identified

3. **Key Insights**
   - Market expectations (table stakes)
   - Differentiation opportunities
   - Common patterns

4. **Recommendation**
   - What's must-have vs nice-to-have
   - Differentiation strategy
   - Quick go/no-go guidance

## Limitations

**Quick scan is NOT suitable for**:
- Comprehensive market analysis
- Business model evaluation
- Strategic positioning decisions
- Board/investor presentations
- Patent or IP analysis

**Accuracy factors**:
- Surface-level feature comparison only
- Based on public information
- May miss nuances or recent changes
- No hands-on product testing
- Best for directional guidance

## Improving Scan Quality

To get more comprehensive insights:

1. **Be specific**: "Keyboard shortcuts" vs "productivity features"
2. **Choose right competitors**: Direct competitors most relevant
3. **Use focus parameter**: Target specific aspect (pricing, UX, etc.)
4. **Provide context**: Share your current status/plans
5. **Follow up**: Use competitive-intelligence for deep analysis

## Common Use Cases

### Feature Prioritization
```bash
/quick-competitive-scan Dark mode support Notion Figma Linear
# Quick check if it's expected by market
```

### Pricing Validation
```bash
/quick-competitive-scan SaaS pricing models --focus pricing [competitors]
# Validate your pricing strategy
```

### Gap Identification
```bash
/quick-competitive-scan [your niche feature] [competitor1] [competitor2]
# Find differentiation opportunities
```

### Pre-Meeting Prep
```bash
/quick-competitive-scan [feature in question] [competitors]
# Get talking points for stakeholder meeting
```

### Build vs Buy
```bash
/quick-competitive-scan [feature] [tool1] [tool2] [tool3]
# Compare building vs integrating existing tools
```

## Tips for Better Scans

1. **Name 2-5 specific competitors**: More focused than "scan the market"

2. **Use focus parameter**: Target what matters (features, pricing, UX, performance)

3. **Provide context**: Mention if you're planning, building, or have the feature

4. **Look for patterns**: What do ALL competitors have? (That's table stakes)

5. **Find gaps**: What does NO ONE have? (Opportunity)

6. **Follow standards**: When everyone does it, users expect it

## Integration with Other Skills

- **competitive-intelligence**: Use for comprehensive competitive analysis
- **improvement-proposals**: Use scan insights to build detailed PRD
- **persona-definition**: Understand which features matter to your users
- **product-evolution-analysis**: See how competitors evolved over time

## Related Commands

- `/competitive-intelligence` - Full competitive analysis with market positioning
- `/persona-quick-reference` - Quick user profile to inform feature decisions
- `/feature-impact-estimate` - Estimate ROI of building competitive features

---

**Remember**: Quick scans trade depth for speed. Use them for fast directional guidance, but validate with comprehensive analysis before major feature investments.
