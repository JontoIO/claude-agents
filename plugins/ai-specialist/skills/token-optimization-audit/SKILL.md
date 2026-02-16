---
name: token-optimization-audit
description: Comprehensive token usage analysis using 7-step framework to identify compression opportunities, calculate savings, and create prioritized optimization roadmap for 20-40% token reduction
---

# Token Optimization Audit Skill

Conduct a comprehensive audit of token usage across Claude instruction files, identify optimization opportunities, calculate potential savings, and create a prioritized implementation roadmap.

## When to Use This Skill

Use this skill when you need to:
- Reduce Claude API costs through token optimization
- Analyze token consumption patterns across projects
- Identify highest token consumers and optimization opportunities
- Calculate ROI of token optimization efforts
- Create optimization roadmap with estimated savings
- Measure token efficiency improvements over time
- Justify token optimization investments

## 7-Step Token Optimization Audit Framework

### Step 1: Token Usage Discovery (5 min)

**Objective**: Identify all files consuming tokens and calculate baseline

**Actions**:
1. Find all instruction files (CLAUDE.md, agents, skills, commands)
2. Calculate token counts (use wc -w × 0.75 or tokenizer tool)
3. Rank files by token consumption
4. Calculate percentage of total for each file
5. Identify token usage patterns

**Output**: Baseline token inventory with top consumers identified

### Step 2: Hotspot Analysis (10 min)

**Objective**: Find highest token consumers and patterns

**Actions**:
1. Identify top 10 token-consuming files
2. Analyze why they consume so many tokens (verbosity, examples, redundancy)
3. Find repeated patterns across files (duplicated content, similar structures)
4. Calculate token density (tokens per concept/instruction)
5. Flag inefficient patterns (conversational tone, redundant explanations)

**Output**: Ranked list of optimization hotspots with root causes

### Step 3: Compression Opportunities (8 min)

**Objective**: Identify specific optimization strategies

**Actions**:
1. **Verbose → Concise**: Find wordy phrases, long sentences, conversational tone
2. **Repetition → Reference**: Find duplicated content that could be deduplicated
3. **Full Content → Summary**: Find detailed examples that could be compressed
4. **Explicit → Implicit**: Find obvious context Claude already knows
5. Calculate estimated savings for each opportunity

**Output**: Categorized compression opportunities with estimated token savings

### Step 4: Caching Strategies (5 min)

**Objective**: Identify content suitable for prompt caching

**Actions**:
1. Find static content loaded in every session (frameworks, examples, guidelines)
2. Find frequently accessed content (common agents, popular skills)
3. Estimate cache hit rates based on usage patterns
4. Calculate savings from caching (loaded once, used many times)
5. Recommend caching architecture

**Output**: Caching recommendations with estimated savings

### Step 5: Architecture Recommendations (7 min)

**Objective**: Suggest structural improvements for token efficiency

**Actions**:
1. **Hierarchical Context**: Load only relevant sections, not entire files
2. **Lazy Loading**: Load details on-demand, not upfront
3. **Shared References**: Extract common content to shared files
4. **Progressive Disclosure**: Start with summary, provide details if needed
5. Estimate implementation effort vs token savings

**Output**: Architecture improvements with effort/impact analysis

### Step 6: Savings Calculation (3 min)

**Objective**: Calculate total potential savings in tokens and cost

**Actions**:
1. Sum all optimization opportunities (conservative estimate)
2. Calculate percentage reduction from baseline
3. Estimate monthly token usage (sessions × context loads × tokens)
4. Calculate monthly cost savings (tokens × $/token)
5. Calculate annual savings and ROI

**Output**: Financial impact analysis with before/after projections

### Step 7: Implementation Roadmap (2 min)

**Objective**: Create prioritized action plan

**Actions**:
1. Prioritize optimizations by ROI (tokens saved per hour effort)
2. Group into phases (Quick Wins, High-Impact, Advanced)
3. Estimate timeline and resources
4. Define success metrics and tracking
5. Create implementation checklist

**Output**: Prioritized roadmap with timelines and milestones

---

## Example Output Summary

### Token Audit Executive Summary

**Baseline**: 62,000 tokens across all instruction files

**Optimization Potential**:
- Verbose → Concise: -8,500 tokens (14%)
- Repetition → Reference: -12,400 tokens (20%)
- Full → Summary: -6,200 tokens (10%)
- Caching: -15,000 effective tokens (24% through reuse)

**Total Savings**: 27,100 tokens baseline reduction + 15,000 through caching = **42,100 effective tokens saved (68% improvement)**

**Cost Impact**: $930/month → $410/month = **$520/month savings ($6,240/year)**

**Top Recommendations**:
1. Deduplicate frameworks (1 hour, -3,520 tokens, ROI: 3,520/hour)
2. Implement prompt caching (2 hours, -15,000 effective tokens, ROI: 7,500/hour)
3. Remove conversational phrases (1.5 hours, -525 tokens, ROI: 350/hour)

---

## Quality Checklist

- [ ] Discovered all instruction files and calculated baseline tokens
- [ ] Identified top 10 hotspots with root causes
- [ ] Categorized compression opportunities with estimates
- [ ] Evaluated caching strategies and potential
- [ ] Recommended architecture improvements
- [ ] Calculated financial savings (monthly and annual)
- [ ] Created prioritized roadmap with timeline

---

*Use this skill to conduct comprehensive token audits and create data-driven optimization strategies.*
