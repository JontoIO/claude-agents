# Token Usage Snapshot Command

Provides a 2-3 minute quick token analysis showing total usage, top consumers, and immediate optimization opportunities across all instruction files.

## Purpose

Get instant token insights when:
- Need fast token usage overview
- Want to identify biggest token consumers
- Checking token efficiency quickly
- Prioritizing optimization efforts
- Monitoring token usage over time

## When to Use

**Use token-usage-snapshot when**:
- Need insights in 2-3 minutes
- Want quick token breakdown
- Identifying top 5 optimization targets
- Monthly token usage review
- Before/after optimization comparison

**Use full token-optimization-audit skill when**:
- Need comprehensive token analysis
- Planning optimization roadmap
- Calculating ROI and cost savings
- Identifying caching opportunities
- Architectural token optimization

## Command Format

```bash
/token-usage-snapshot
```

Analyzes all instruction files in current project.

## Example Output

```bash
/token-usage-snapshot
```

**Output**:
```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
TOKEN USAGE SNAPSHOT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Generated: 2026-02-16 | Analysis Time: 2 minutes

📊 TOTAL TOKEN USAGE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Total Tokens: 62,000
Total Files: 23 files
Average per file: 2,696 tokens

Breakdown:
  Skills:    42,100 tokens (68%) - 8 files
  Agents:    16,600 tokens (27%) - 5 files
  CLAUDE.md:  3,300 tokens (5%)  - 2 files
  Commands:   2,800 tokens (5%)  - 8 files

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🔥 TOP 10 TOKEN CONSUMERS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

1. 📄 improvement-proposals SKILL.md
   14,800 tokens (24%) | ⚠ Very High
   Opportunity: Compress examples (-2,400 tokens, 16% reduction)

2. 📄 product-evolution-analysis SKILL.md
   9,500 tokens (15%) | ⚠ High
   Opportunity: Deduplicate frameworks (-1,200 tokens, 13%)

3. 📄 competitive-intelligence SKILL.md
   8,200 tokens (13%) | ⚠ High
   Opportunity: Compress examples (-1,100 tokens, 13%)

4. 📄 CLAUDE.md (root)
   6,800 tokens (11%) | ⚠ Moderate
   Opportunity: Remove conversational tone (-500 tokens, 7%)

5. 📄 ai-specialist agent
   4,700 tokens (8%) | ✓ Reasonable
   Opportunity: Minor optimization (-200 tokens, 4%)

6. 📄 product-manager agent
   4,100 tokens (7%) | ✓ Reasonable
   Opportunity: Dedupe RICE (-400 tokens, 10%)

7. 📄 persona-definition SKILL.md
   3,600 tokens (6%) | ✓ Reasonable
   Opportunity: Compress examples (-300 tokens, 8%)

8. 📄 financial-advisor agent
   2,900 tokens (5%) | ✓ Good
   Opportunity: Minor tweaks (-100 tokens, 3%)

9. 📄 test-engineer agent
   2,700 tokens (4%) | ✓ Good
   Opportunity: Well-optimized (-50 tokens, 2%)

10. 📄 security-auditor agent
    2,200 tokens (4%) | ✓ Good
    Opportunity: Well-optimized (-50 tokens, 2%)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
⚡ IMMEDIATE OPTIMIZATION OPPORTUNITIES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Quick Wins (< 2 hours, 3,100 tokens):
  ✅ Deduplicate RICE framework (3 files)
     Impact: -870 tokens (1.4%)
     Effort: 1 hour
     Files: product-manager.md, improvement-proposals SKILL.md, feature-impact-estimate.md

  ✅ Remove conversational phrases (all files)
     Impact: -525 tokens (0.8%)
     Effort: 1.5 hours
     Examples: "you should", "please", "try to" → imperative

  ✅ Deduplicate best practices (5 files)
     Impact: -1,200 tokens (1.9%)
     Effort: 1 hour
     Files: Various agents

  ✅ Remove obvious context
     Impact: -450 tokens (0.7%)
     Effort: 30 minutes
     Example: Explaining what Claude already knows

Total Quick Wins: 4 hours, -3,045 tokens (4.9% reduction)

High-Impact Opportunities (10 hours, 8,500 tokens):
  🎯 Compress skill examples (3 skills)
     Impact: -4,800 tokens (7.7%)
     Effort: 6 hours
     Strategy: Reduce example verbosity by 40%

  🎯 Deduplicate frameworks (8 occurrences)
     Impact: -3,520 tokens (5.7%)
     Effort: 2 hours
     Frameworks: Kano, JTBD, Value Prop Canvas

  🎯 Optimize CLAUDE.md
     Impact: -680 tokens (10% of file)
     Effort: 2 hours
     Focus: Tone + redundancy

Total High-Impact: 10 hours, -9,000 tokens (14.5% reduction)

COMBINED POTENTIAL: 14 hours, -12,045 tokens (19.4% reduction)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
💰 COST IMPACT ESTIMATE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Current Monthly Cost:
  Sessions: 100 per month
  Context loads: 10 per session
  Total monthly tokens: 62,000,000
  Cost (Claude Opus $15/1M): $930/month

After Quick Wins:
  Optimized tokens: 58,955 per load
  Total monthly tokens: 58,955,000
  Cost: $884/month
  Savings: $46/month ($552/year)

After All Optimizations:
  Optimized tokens: 49,955 per load
  Total monthly tokens: 49,955,000
  Cost: $749/month
  Savings: $181/month ($2,172/year)

ROI Analysis:
  Quick Wins: 4 hours effort → $552/year = $138/hour ROI
  All Optimizations: 14 hours → $2,172/year = $155/hour ROI

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📈 TOKEN EFFICIENCY METRICS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Files by Efficiency:
  ✓ Excellent (< 2,000 tokens): 10 files (43%)
  ✓ Good (2,000-4,000 tokens): 7 files (30%)
  ⚠ Moderate (4,000-8,000 tokens): 3 files (13%)
  ⚠ High (8,000-12,000 tokens): 2 files (9%)
  🔴 Very High (> 12,000 tokens): 1 file (4%)

Optimization Priority:
  Priority 1: improvement-proposals SKILL.md (14,800 tokens)
  Priority 2: product-evolution-analysis SKILL.md (9,500 tokens)
  Priority 3: competitive-intelligence SKILL.md (8,200 tokens)

Token Density (tokens per concept):
  Skills avg: 5,263 tokens per skill (8 skills)
  Agents avg: 3,320 tokens per agent (5 agents)
  Commands avg: 350 tokens per command (8 commands)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🎯 RECOMMENDED ACTIONS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

This Week (Quick Wins - 4 hours):
  1. [1 hour] Deduplicate RICE framework → -870 tokens
  2. [1.5 hours] Remove conversational phrases → -525 tokens
  3. [1 hour] Deduplicate best practices → -1,200 tokens
  4. [30 min] Remove obvious context → -450 tokens

Next Week (High-Impact - 10 hours):
  5. [6 hours] Compress skill examples → -4,800 tokens
  6. [2 hours] Deduplicate frameworks → -3,520 tokens
  7. [2 hours] Optimize CLAUDE.md → -680 tokens

Expected Results:
  • Total savings: 12,045 tokens (19.4%)
  • Monthly cost reduction: $181 ($2,172/year)
  • Improved clarity and scannability
  • Reduced context load time

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🔧 NEXT STEPS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[ ] Review top 3 token consumers (files #1-3)
[ ] Apply quick wins this week (4 hours, $552/year ROI)
[ ] Schedule high-impact optimizations (10 hours)
[ ] Run /quick-instruction-audit on top 3 files
[ ] For comprehensive plan: /token-optimization-audit

Snapshot complete ✓ (Generated in 2 minutes)
Last snapshot: N/A (first run)
Next snapshot: Recommended monthly
```

## Snapshot Components

Every snapshot includes:

### 1. Total Token Usage
- Total tokens across all files
- Breakdown by category (skills, agents, etc.)
- File count and averages

### 2. Top 10 Consumers
- Ranked list of highest token files
- Percentage of total for each
- Quick optimization opportunity per file

### 3. Immediate Opportunities
- **Quick Wins**: < 2 hours, high ROI
- **High-Impact**: 10-15 hours, significant savings
- Effort and token savings estimates

### 4. Cost Impact
- Current monthly token cost
- Projected cost after optimizations
- ROI analysis (savings per hour effort)

### 5. Efficiency Metrics
- Files categorized by efficiency
- Optimization priorities ranked
- Token density analysis

### 6. Recommended Actions
- This week priorities (quick wins)
- Next week priorities (high-impact)
- Expected results

## Use Cases

### Monthly Token Review
```bash
# Check token usage monthly
/token-usage-snapshot

# Compare to last month
# Identify growing files
```

### Pre-Optimization Planning
```bash
# Get baseline before optimizing
/token-usage-snapshot

# Identify top targets
# Plan optimization sprint
```

### Post-Optimization Validation
```bash
# Measure improvements
/token-usage-snapshot

# Compare to baseline
# Calculate actual savings
```

### Cost Monitoring
```bash
# Track monthly API costs
/token-usage-snapshot

# Identify cost trends
# Justify optimization investments
```

## Efficiency Categories

### File Size Ratings
```
✓ Excellent: < 2,000 tokens (command-size)
✓ Good: 2,000-4,000 tokens (agent-size)
⚠ Moderate: 4,000-8,000 tokens (skill-size)
⚠ High: 8,000-12,000 tokens (large skill)
🔴 Very High: > 12,000 tokens (very large skill)
```

### Optimization Priority
```
Priority 1: Very High tokens + high optimization potential
Priority 2: High tokens + moderate optimization potential
Priority 3: Moderate tokens + optimization opportunities
```

## Cost Calculation

### Monthly Cost Formula
```
Monthly Cost = (Total Tokens × Context Loads × Sessions × $per1MTokens) / 1,000,000

Example:
  Total Tokens: 62,000
  Context Loads: 10 per session
  Sessions: 100 per month
  Cost: $15 per 1M tokens (Opus)

  Monthly Cost = (62,000 × 10 × 100 × $15) / 1,000,000
               = $930/month
```

### ROI Calculation
```
ROI = Annual Savings / Hours Effort

Example:
  Annual Savings: $2,172
  Hours Effort: 14 hours

  ROI = $2,172 / 14 = $155/hour
```

## Tracking Over Time

### Baseline Snapshot
```bash
# First run establishes baseline
/token-usage-snapshot

# Save results for comparison
```

### Monthly Snapshots
```bash
# Run monthly for trends
/token-usage-snapshot

# Compare to previous months
# Track optimization impact
```

### Before/After Optimization
```bash
# Before optimizing
/token-usage-snapshot > baseline.txt

# After optimizing
/token-usage-snapshot > optimized.txt

# Compare results
diff baseline.txt optimized.txt
```

## Tips for Better Snapshots

1. **Run monthly**: Track token usage trends
2. **Compare over time**: See if token usage growing
3. **Act on quick wins**: 4 hours = $500+/year ROI
4. **Prioritize by ROI**: Focus on high tokens/hour savings
5. **Track improvements**: Measure optimization impact

## Integration with Other Commands

- **token-usage-snapshot** - This command (quick overview)
- **quick-instruction-audit** - Audit specific high-token files
- **/token-optimization-audit** - Comprehensive token analysis + roadmap

---

**Remember**: Token snapshots provide fast overview for monitoring and prioritization. Use them monthly to track efficiency and identify optimization targets.
