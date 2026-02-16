# Quick Instruction Audit Command

Provides a rapid 5-7 minute CLAUDE.md review identifying top 3 optimization opportunities with token savings estimates and quick win recommendations.

## Purpose

Get fast actionable insights when:
- Need to quickly assess instruction file health
- Want to identify low-hanging optimization fruit
- Preparing for optimization sprint
- Responding to "are our instructions efficient?" questions
- Quick check before major changes

## When to Use

**Use quick-instruction-audit when**:
- Need insights in 5-7 minutes
- Want top 3-5 issues only
- Looking for quick wins (<2 hours effort)
- Making fast go/no-go decisions
- Spot-checking single instruction file

**Use full claude-instructions-optimization skill when**:
- Need comprehensive token analysis
- Planning major refactoring effort
- Creating detailed optimization roadmap
- Documenting before/after changes
- Optimizing entire project (multiple files)

## Command Format

```bash
/quick-instruction-audit [file_path]
```

If no file_path provided, audits main CLAUDE.md file.

## Examples

### Example 1: Audit Main CLAUDE.md

```bash
/quick-instruction-audit
```

**Expected Output**:
```
Quick Instruction Audit: CLAUDE.md
Time: 5 minutes | Tokens: 6,800 | Status: ⚠ Moderate Issues

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TOP 3 OPTIMIZATION OPPORTUNITIES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

🔴 ISSUE 1: Conversational Tone (High Impact)
Location: Lines 45-89, 120-156, 200-240
Problem: 42 instances of "you should", "please", "try to"
Example: "You should always try to read files before editing"
Fix: Convert to imperative: "Read files before editing"
Savings: ~125 tokens (1.8% reduction)
Effort: 30 minutes (find and replace)
Priority: P0 (Quick win)

🟡 ISSUE 2: Redundant Explanation (Medium Impact)
Location: Lines 110-145 (Tool usage), Lines 230-265 (Same content)
Problem: Tool usage guidelines repeated twice
Example: "Use Read not cat, Write not echo..." (full explanation x2)
Fix: Keep one explanation, reference it in second location
Savings: ~180 tokens (2.6% reduction)
Effort: 15 minutes (deduplicate)
Priority: P0 (Quick win)

🟢 ISSUE 3: Vague Constraints (Quality Issue)
Location: Lines 67, 89, 134, 178, 201
Problem: 5 constraints lack specificity
Examples:
  • "Keep responses concise" (how concise?)
  • "Be thorough" (what does thorough mean?)
  • "Use tools appropriately" (which? when?)
Fix: Add specific limits and measurable criteria
Impact: +50 tokens but reduces ambiguity by ~70%
Effort: 45 minutes (specify each constraint)
Priority: P1 (Quality > tokens)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
QUICK WINS (< 1 hour total)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

✅ Remove "In order to" → "To" (12 instances, 24 tokens, 10 min)
✅ Remove obvious context (line 23-28, 90 tokens, 15 min)
✅ Deduplicate tool guidelines (180 tokens, 15 min)
✅ Convert conversational phrases (125 tokens, 30 min)

Total Quick Wins: 70 minutes, 419 tokens saved (6.2%)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SUMMARY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Current State:
• Total tokens: 6,800
• Optimization potential: 419 tokens (6.2% quick wins)
• Quality issues: 5 vague constraints
• Structure: Good (adequate headers)

Recommended Actions:
1. [30 min] Convert conversational to imperative (125 tokens)
2. [15 min] Deduplicate tool guidelines (180 tokens)
3. [25 min] Remove redundant phrases (114 tokens)
4. [45 min] Specify vague constraints (quality improvement)

Total Time: 115 minutes (2 hours)
Total Savings: 419 tokens baseline + quality improvements

Health Score: 7/10 (Good with room for improvement)

Next Steps:
• Apply quick wins today (70 min, 419 tokens)
• Schedule constraint specification (45 min next week)
• For deeper analysis: /claude-instructions-optimization
```

### Example 2: Audit Agent Definition

```bash
/quick-instruction-audit plugins/product-manager/agents/product-manager.md
```

**Expected Output**:
```
Quick Instruction Audit: product-manager.md
Time: 6 minutes | Tokens: 4,100 | Status: ✓ Healthy

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TOP 3 OPTIMIZATION OPPORTUNITIES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

🟡 ISSUE 1: Long Examples (Medium Impact)
Location: Lines 155-210 (RICE framework example)
Problem: 56-line detailed RICE explanation repeated in skill file
Example: Full RICE calculation with explanatory paragraphs
Fix: Compress to core formula + one example
Savings: ~400 tokens (9.8% reduction) if deduped across files
Effort: 1 hour (consolidate, update references)
Priority: P1 (High ROI across multiple files)

🟢 ISSUE 2: Framework Explanations (Low Impact)
Location: Lines 150-180 (Kano), Lines 200-225 (JTBD)
Problem: Moderate verbosity in framework descriptions
Example: "The Kano model helps you understand..." (full explanation)
Fix: Use concise definitions, link to examples
Savings: ~180 tokens (4.4% reduction)
Effort: 45 minutes (compress frameworks)
Priority: P2 (Moderate impact)

🟢 ISSUE 3: Minor Redundancy (Low Impact)
Location: Lines 85-92, Lines 230-238
Problem: "You are designed to..." statement repeated
Example: Similar phrasing about agent capabilities in 2 sections
Fix: Consolidate into single capabilities section
Savings: ~60 tokens (1.5% reduction)
Effort: 15 minutes (reorganize)
Priority: P2 (Nice-to-have)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
QUICK WINS (< 30 min total)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

✅ Consolidate capability statements (60 tokens, 15 min)
✅ Remove 3 instances of "you can" → implicit (18 tokens, 10 min)

Total Quick Wins: 25 minutes, 78 tokens saved (1.9%)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SUMMARY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Current State:
• Total tokens: 4,100
• Optimization potential: 78 tokens (quick wins only)
• Larger opportunity: 640 tokens if optimized across all files
• Structure: ✓ Excellent (clear hierarchy, good headers)
• Clarity: ✓ Excellent (specific, measurable)
• Tone: ✓ Good (mostly imperative)

Recommended Actions:
1. [15 min] Consolidate capability statements (60 tokens)
2. [10 min] Remove implicit phrases (18 tokens)
3. [1 hour] Deduplicate RICE framework across 3 files (400 tokens total)

Health Score: 9/10 (Excellent, minor optimizations)

Next Steps:
• Agent is well-optimized, focus on cross-file deduplication
• For framework consolidation: /claude-instructions-optimization
```

### Example 3: Audit Skill File

```bash
/quick-instruction-audit plugins/product-manager/skills/improvement-proposals/SKILL.md
```

**Expected Output**:
```
Quick Instruction Audit: improvement-proposals SKILL.md
Time: 7 minutes | Tokens: 14,800 | Status: ⚠ Verbose

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TOP 3 OPTIMIZATION OPPORTUNITIES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

🔴 ISSUE 1: Verbose Examples (High Impact)
Location: Lines 612-920 (detailed proposal examples)
Problem: 308-line exhaustive examples (could be 150 lines)
Example: Full proposal with 15 sections per example
Fix: Compress to framework structure + key points
Savings: ~2,400 tokens (16.2% reduction)
Effort: 3 hours (rewrite examples while keeping value)
Priority: P1 (Highest impact in skill)

🟡 ISSUE 2: Repeated Framework Explanations (Medium Impact)
Location: Lines 155-180 (RICE), Lines 440-475 (RICE again)
Problem: RICE framework explained twice in same file
Example: Full RICE definition + calculation (duplicate content)
Fix: Reference first explanation from second location
Savings: ~550 tokens (3.7% reduction)
Effort: 20 minutes (deduplicate internal)
Priority: P0 (Quick win)

🟡 ISSUE 3: Long Methodology Sections (Medium Impact)
Location: Lines 28-158 (Step 1 examples)
Problem: Very detailed examples in step instructions
Example: 130 lines of example output in Step 1
Fix: Reduce examples by 50%, keep structure
Savings: ~1,200 tokens (8.1% reduction)
Effort: 2 hours (compress while preserving pedagogy)
Priority: P1 (Significant impact)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
QUICK WINS (< 45 min total)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

✅ Deduplicate RICE explanation (550 tokens, 20 min)
✅ Remove "For example" → "Example:" (24 instances, 48 tokens, 15 min)
✅ Consolidate repeated lists (85 tokens, 10 min)

Total Quick Wins: 45 minutes, 683 tokens saved (4.6%)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SUMMARY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Current State:
• Total tokens: 14,800
• Optimization potential: 683 tokens (quick wins)
• Larger opportunity: 4,150 tokens (28% with example compression)
• Structure: ✓ Good (clear 6-step framework)
• Clarity: ✓ Excellent (very detailed, perhaps too much)
• Examples: ⚠ Very verbose (pedagogically valuable but token-heavy)

Recommended Actions:
QUICK (45 min, 683 tokens):
1. Deduplicate RICE framework internally
2. Consolidate repeated phrases
3. Remove conversational transitions

STRATEGIC (5 hours, 3,600 tokens):
4. Compress all examples by 40-50%
5. Reduce step methodology verbosity
6. Convert some examples to "see appendix" references

Health Score: 6/10 (Functional but verbose)

Trade-off Consideration:
• Skill is very educational and comprehensive
• Examples teach users how to apply framework
• Compressing may reduce pedagogical value
• Recommendation: Compress examples to 70% (keep structure, remove verbosity)

Next Steps:
• Apply quick wins today (45 min, 683 tokens)
• For comprehensive rewrite: /claude-instructions-optimization
• Consider: Is this token investment worth it for teaching value?
```

## Audit Methodology

The command performs rapid analysis:

### What Gets Checked (5-7 min)

```
✓ Token count and baseline
✓ Conversational vs imperative tone
✓ Redundant content patterns
✓ Vague constraints (lacks specificity)
✓ Obvious context that's redundant
✓ Internal duplication
✓ Structure and scannability
✓ Examples verbosity
```

### What's NOT Checked (Use Full Skill)

```
✗ Cross-file deduplication
✗ Comprehensive token analysis
✗ Best practices compliance (full audit)
✗ Before/after rewrites
✗ Implementation planning
✗ Success metrics tracking
```

## Output Format

Every quick audit includes:

1. **Header**: File, time, token count, health status
2. **Top 3 Issues**: Most impactful optimization opportunities
3. **Quick Wins**: < 1 hour fixes with token savings
4. **Summary**: Current state, health score, recommendations
5. **Next Steps**: Immediate actions + when to use full skill

## Health Score Interpretation

```
10/10: Perfect - No optimizations needed
9/10:  Excellent - Minor tweaks only
8/10:  Good - Few small issues
7/10:  Good - Moderate issues, some optimization value
6/10:  Fair - Significant optimization opportunities
5/10:  Fair - Many issues, refactoring recommended
4/10:  Poor - Major issues, high token waste
3/10:  Poor - Needs comprehensive rewrite
1-2/10: Critical - Immediate optimization required
```

## Common Issues Detected

### High Priority (Fix First)

- **Conversational tone**: "you should", "please", "try to"
- **Redundant content**: Same explanation repeated
- **Vague constraints**: "be concise" without limits
- **Obvious context**: Explaining what Claude already knows

### Medium Priority (Fix After)

- **Long examples**: Verbose illustrations
- **Poor structure**: Missing headers, flat organization
- **Implicit phrases**: "you can", "it is important"

### Low Priority (Nice-to-Have)

- **Minor redundancy**: Similar phrasing in sections
- **Slightly verbose**: Could be more concise
- **Formatting**: Could improve scannability

## Tips for Better Audits

1. **Run on largest files first**: Biggest token consumers = highest ROI
2. **Focus on quick wins**: 80/20 rule - 20% effort = 80% savings
3. **Check health scores**: < 7/10 = worth optimizing
4. **Batch optimizations**: Fix multiple files in one session
5. **Track savings**: Measure tokens before/after

## Integration with Other Commands

- **quick-instruction-audit** - This command (rapid assessment)
- **quick-token-snapshot** - Quick token breakdown across all files
- **/claude-instructions-optimization** - Full comprehensive optimization

---

**Remember**: Quick audits trade depth for speed. Use them for fast checks and quick wins, but run full optimization skill for comprehensive improvements.
