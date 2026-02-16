---
name: claude-instructions-optimization
description: Optimize CLAUDE.md files and agent definitions using 7-step framework including file discovery, token analysis, best practices audit, and implementation plan to achieve 20-40% token reduction while improving clarity
---

# Claude Instructions Optimization Skill

Analyze and optimize CLAUDE.md files, agent definitions, and skill instructions to reduce token usage, improve clarity, and eliminate ambiguity using data-driven optimization techniques.

## When to Use This Skill

Use this skill when you need to:
- Reduce token consumption in CLAUDE.md or agent definition files
- Improve clarity and reduce ambiguity in Claude instructions
- Audit instruction files for best practices compliance
- Eliminate redundancy and verbose phrasing
- Refactor instructions for better Claude understanding
- Measure and document optimization impact
- Create an implementation plan for instruction improvements

## 7-Step Claude Instructions Optimization Framework

### Step 1: File Discovery (5 min)

**Objective**: Identify all instruction files that consume Claude context

**Actions**:
1. **Find CLAUDE.md Files**:
   - Search for CLAUDE.md in root and subdirectories
   - Note file paths and sizes
   - Identify primary vs secondary instruction files
2. **Find Agent Definitions**:
   - Locate all agent definition files (typically `agents/*.md`)
   - Check frontmatter for agent names and descriptions
   - List all agent files with paths
3. **Find Skill Instructions**:
   - Locate all skill files (typically `skills/*/SKILL.md`)
   - Identify verbose or complex skills
   - Note skill names and purposes
4. **Find Command Instructions**:
   - Locate command files (typically `commands/*.md`)
   - Check for instruction redundancy across commands
5. **Calculate Baseline**:
   - Count total lines and estimate tokens for each file
   - Identify largest consumers (top 3-5 files)
   - Document current state for comparison

**Output Format**:
```markdown
## File Discovery

### Instruction Files Found

**CLAUDE.md Files**:
1. `/project-root/CLAUDE.md` (450 lines, ~6,800 tokens)
2. `/project-root/.claude/CLAUDE.md` (120 lines, ~1,800 tokens)

**Agent Definitions** (5 files):
1. `/agents/product-manager.md` (268 lines, ~4,100 tokens)
2. `/agents/financial-advisor.md` (195 lines, ~2,900 tokens)
3. `/agents/ai-specialist.md` (312 lines, ~4,700 tokens)
4. `/agents/test-engineer.md` (180 lines, ~2,700 tokens)
5. `/agents/security-auditor.md` (145 lines, ~2,200 tokens)

**Skills** (8 files, listing top 3):
1. `/skills/product-evolution-analysis/SKILL.md` (620 lines, ~9,500 tokens)
2. `/skills/improvement-proposals/SKILL.md` (978 lines, ~14,800 tokens)
3. `/skills/competitive-intelligence/SKILL.md` (540 lines, ~8,200 tokens)
[5 more skills...]

**Commands** (6 files):
[List all command files with token counts...]

### Token Consumption Baseline

**Total Tokens**: ~62,000 tokens
**Top Consumers**:
1. Improvement Proposals Skill: 14,800 tokens (24%)
2. Product Evolution Analysis Skill: 9,500 tokens (15%)
3. Competitive Intelligence Skill: 8,200 tokens (13%)
4. CLAUDE.md: 6,800 tokens (11%)
5. AI Specialist Agent: 4,700 tokens (8%)

**Hotspots**: Skills consume 68% of total tokens, main optimization target
```

---

### Step 2: Instruction Analysis (10 min)

**Objective**: Identify verbose, ambiguous, and conflicting instructions

**Actions**:
1. **Verbosity Detection**:
   - Search for wordy phrases: "you should", "it is important that", "please make sure"
   - Find redundant explanations (same concept repeated multiple times)
   - Identify conversational tone vs imperative directives
   - Flag long paragraphs (>100 words) that could be bullet lists
2. **Ambiguity Detection**:
   - Search for vague terms: "try to", "consider", "might want to", "generally"
   - Find missing constraints: "be concise" without defining length limits
   - Identify unclear success criteria: "improve quality" without metrics
   - Flag conditional instructions without clear conditions
3. **Conflict Detection**:
   - Find contradictory instructions across files
   - Identify inconsistent terminology (same concept, different names)
   - Check for conflicting priorities or approaches
4. **Redundancy Detection**:
   - Search for duplicated content across files
   - Find repeated examples or explanations
   - Identify information that could be referenced vs repeated
5. **Structure Issues**:
   - Long sections without subheadings (poor scannability)
   - Missing hierarchy (flat structure vs nested)
   - Unclear organization (related concepts scattered)

**Output Format**:
```markdown
## Instruction Analysis

### Verbosity Issues (12 found)

**Issue 1: Conversational Phrases** (CLAUDE.md, lines 45-60)
- Current: "You should always try to make sure that you read the file before editing it"
- Token cost: 16 tokens
- Problem: Conversational, uses "you should", "try to", "make sure"
- Impact: 3x longer than necessary

**Issue 2: Redundant Explanation** (product-manager.md, lines 110-135)
- Current: 26-line explanation of RICE scoring (repeated in multiple places)
- Token cost: ~400 tokens per occurrence (3 occurrences = 1,200 tokens)
- Problem: Full RICE explanation repeated in agent definition, skill, and command
- Impact: Could reference once, save 800 tokens

**Issue 3: Long Paragraph** (improvement-proposals SKILL.md, lines 272-295)
- Current: 24-line paragraph explaining impact assessment
- Token cost: ~370 tokens
- Problem: Wall of text, hard to scan, mixes multiple concepts
- Impact: Could be bullet list, 30% more scannable

[9 more verbosity issues...]

### Ambiguity Issues (8 found)

**Issue 1: Vague Constraint** (CLAUDE.md, line 89)
- Current: "Keep responses concise"
- Problem: "Concise" undefined (50 words? 200 words? 2 paragraphs?)
- Impact: Claude guesses, inconsistent behavior
- Context: Different agents interpret differently

**Issue 2: Unclear Success Criteria** (test-strategy-design SKILL.md, line 145)
- Current: "Ensure test coverage is good"
- Problem: "Good" unmeasured (70%? 90%? All critical paths?)
- Impact: No way to verify success
- Context: Step 5 output has no specific target

**Issue 3: Conditional Without Condition** (ai-specialist.md, line 203)
- Current: "Suggest optimizations when appropriate"
- Problem: "Appropriate" undefined (after every task? once per session? specific triggers?)
- Impact: Agent unsure when to act
- Context: Proactive monitoring section lacks trigger clarity

[5 more ambiguity issues...]

### Conflict Detection (3 found)

**Conflict 1: Response Length**
- CLAUDE.md line 89: "Keep responses concise"
- agent/product-manager.md line 145: "Provide comprehensive reports with detailed analysis"
- Problem: Conflicting guidance (concise vs comprehensive)
- Impact: Agent confused about expected detail level
- Resolution: Clarify context (concise for chat, comprehensive for reports)

**Conflict 2: Tool Usage**
- CLAUDE.md line 120: "Use Bash for file operations when needed"
- CLAUDE.md line 35: "Never use Bash for file operations, use Read/Write/Edit"
- Problem: Direct contradiction
- Impact: Agent unsure which to follow
- Resolution: Remove first instruction, keep specific guidance

[1 more conflict...]

### Redundancy Detection (6 found)

**Redundancy 1: RICE Framework** (Repeated 3 times)
- Locations:
  - `/agents/product-manager.md` lines 155-180 (26 lines, ~400 tokens)
  - `/skills/improvement-proposals/SKILL.md` lines 440-475 (36 lines, ~550 tokens)
  - `/commands/feature-impact-estimate.md` lines 12-35 (24 lines, ~370 tokens)
- Total: 1,320 tokens
- Opportunity: Define once, reference twice, save 900 tokens (68% reduction)

**Redundancy 2: Token Counting Explanation** (Repeated 4 times)
- Locations: [List files and line numbers]
- Total: 820 tokens
- Opportunity: Define once in shared location, save 615 tokens (75% reduction)

[4 more redundancies...]

### Structure Issues (5 found)

**Structure Issue 1: Flat Organization** (improvement-proposals SKILL.md)
- Lines 100-400: All step content at same level
- Problem: 300 lines without subheadings, hard to navigate
- Impact: Claude must read entire section to find relevant part
- Opportunity: Add H4 subheadings for each action, improve scannability 40%

[4 more structure issues...]
```

---

### Step 3: Best Practices Audit (8 min)

**Objective**: Check compliance with Claude instruction best practices

**Actions**:
1. **Tone Check**:
   - **Imperative vs Suggestive**: Count "do X" vs "you should consider X"
   - **Active vs Passive**: "Read the file" vs "The file should be read"
   - **Direct vs Conversational**: "Use Read tool" vs "You might want to use the Read tool"
   - **Target**: 90%+ imperative, active, direct
2. **Constraint Clarity**:
   - **Specific Limits**: "Max 3 recommendations" vs "Keep it brief"
   - **Measurable Outcomes**: "Reduce by 30%" vs "Improve efficiency"
   - **Clear Boundaries**: "Never use Bash for file reads" vs "Avoid Bash when possible"
   - **Target**: 80%+ constraints are specific and measurable
3. **Structure Quality**:
   - **Hierarchical Organization**: H1 > H2 > H3 > H4 > bullets
   - **Scannability**: Headers every 10-20 lines for navigation
   - **Front-Loading**: Most important info in first 1/3 of section
   - **Target**: Clear hierarchy, headers every 15 lines average
4. **Examples & Evidence**:
   - **Show Don't Tell**: Code examples vs verbal descriptions
   - **Before/After**: Comparisons for clarity
   - **Concrete**: Specific examples vs generic descriptions
   - **Target**: 1 example per 100 lines of instruction
5. **Success Criteria**:
   - **Measurable**: Can verify outcome objectively
   - **Observable**: Can see when complete
   - **Time-Bound**: Clear when to evaluate
   - **Target**: Every major task has success criteria

**Output Format**:
```markdown
## Best Practices Audit

### Tone Analysis

**Imperative vs Suggestive Tone**:
- Imperative (Good): 450 instances (65%)
- Suggestive (Improve): 240 instances (35%)
- Target: 90%+ imperative
- Gap: 25 percentage points (175 phrases to convert)

**Examples to Convert**:
- "You should try to use the Read tool" → "Use the Read tool"
- "It's important that you check for errors" → "Check for errors"
- "Please make sure to test" → "Test"
- "Consider using Grep to find files" → "Use Grep to find files"

**Impact**: Converting 175 phrases saves ~525 tokens (35% reduction in instructional overhead)

### Constraint Clarity

**Specific vs Vague Constraints**:
- Specific (Good): "Limit to 3 items", "Max 500 tokens", "Never use X"
  - Count: 85 instances (60%)
- Vague (Improve): "Be brief", "Keep it concise", "Avoid when possible"
  - Count: 57 instances (40%)
- Target: 80%+ specific
- Gap: 20 percentage points (28 constraints to specify)

**Vague Constraints to Improve**:
1. "Keep responses concise" → "Limit responses to 200 words (2-3 paragraphs)"
2. "Be thorough" → "Include: analysis, recommendations, metrics, timeline"
3. "Avoid unnecessary tools" → "Never use Bash for file operations (use Read/Write/Edit)"
4. "Improve test coverage" → "Achieve 80%+ line coverage, 100% critical path coverage"

**Measurable Outcomes**:
- Measurable (Good): 120 outcomes (70%)
- Unmeasurable (Improve): 52 outcomes (30%)
- Gap: "Optimize CLAUDE.md" → "Reduce CLAUDE.md tokens by 30% (6800 → 4760)"

### Structure Quality

**Hierarchical Organization**:
- Files with clear hierarchy (H1 > H2 > H3): 8/12 (67%)
- Files with flat structure: 4/12 (33%)
  - `/skills/prompt-enhancement/SKILL.md`: All H2, no H3/H4 breakdown
  - `/skills/memory-efficiency-analysis/SKILL.md`: Long sections without sub-sections

**Scannability (Header Frequency)**:
- Average lines between headers: 28 lines
- Target: 15 lines (current is 87% too sparse)
- Files exceeding 50 lines without headers: 6 files
  - `/agents/product-manager.md` lines 110-175 (65 lines, no headers)
  - `/skills/improvement-proposals/SKILL.md` lines 272-335 (63 lines, no headers)

**Front-Loading** (Critical info in first 1/3):
- Files front-loading well: 9/12 (75%)
- Files burying key info: 3/12 (25%)
  - `/skills/token-optimization-audit/SKILL.md`: Success metrics at end (should be step 1)

**Impact**: Adding 45 subheaders improves scannability by 40%, reduces read time 25%

### Examples & Evidence

**Example Density**:
- Total instruction lines: 4,200 lines
- Code examples: 38 examples
- Current ratio: 1 example per 110 lines
- Target ratio: 1 example per 100 lines
- Gap: Need 4 more examples

**Before/After Comparisons**:
- Files with before/after: 6/12 (50%)
- Files without: 6/12 (50%)
- Impact: Before/after increases clarity 60% (based on user feedback patterns)

**Concrete vs Abstract**:
- Concrete examples (Good): "RICE = (600 × 2 × 0.8) / 0.5 = 1920"
- Abstract descriptions (Improve): "Calculate RICE by multiplying reach, impact, confidence, then divide by effort"
- Ratio: 70% concrete, 30% abstract (target: 85% concrete)

### Success Criteria Analysis

**Tasks with Measurable Success Criteria**:
- Skills with clear success criteria: 5/8 (63%)
- Skills without: 3/8 (38%)
  - `/skills/prompt-enhancement/SKILL.md`: Step 6 "verify improvement" lacks metrics
  - `/skills/memory-efficiency-analysis/SKILL.md`: No definition of "efficient"

**Specificity**:
- Specific (Good): "Reduce tokens by 30%, improve recall by 20%"
- Vague (Improve): "Make it better", "Optimize performance"
- Current: 60% specific (target: 90%)

**Examples of Missing Success Criteria**:
1. Skill: claude-instructions-optimization
   - Missing: "How many tokens saved is successful?" (20%? 40%?)
   - Add: "Success: 20-40% token reduction, 90%+ instruction clarity score"

2. Skill: test-strategy-design
   - Missing: "What level of test coverage is sufficient?"
   - Add: "Success: 80% code coverage, 100% critical path coverage, 0 P0 bugs in production"

## Best Practices Compliance Summary

| Practice | Current | Target | Gap | Priority |
|----------|---------|--------|-----|----------|
| Imperative Tone | 65% | 90% | -25% | High |
| Specific Constraints | 60% | 80% | -20% | High |
| Measurable Outcomes | 70% | 90% | -20% | High |
| Header Frequency | 28 lines | 15 lines | -87% | Medium |
| Example Density | 1/110 lines | 1/100 lines | -10% | Low |
| Success Criteria | 63% | 90% | -27% | High |

**Overall Compliance**: 64% (target: 85%+)
**Improvement Needed**: 21 percentage points

```

---

### Step 4: Token Efficiency Assessment (7 min)

**Objective**: Calculate token usage and identify compression opportunities

**Actions**:
1. **Token Counting**:
   - Count tokens for each file (use rough estimate: 1 token ≈ 0.75 words)
   - Calculate percentage of total for each file
   - Identify top 10 token consumers
2. **Compression Opportunity Analysis**:
   - **Verbose → Concise**: Identify wordy sections that could be shortened
   - **Repetition → Reference**: Find repeated content that could be deduplicated
   - **Full Content → Summary**: Long explanations that could be condensed
   - **Implicit → Explicit**: Remove redundant context that Claude infers
3. **Token Savings Calculation**:
   - Estimate savings for each opportunity (conservative)
   - Calculate total potential savings (tokens and %)
   - Prioritize by impact (savings per hour of effort)
4. **Cost Impact**:
   - Estimate monthly token usage (baseline × sessions)
   - Calculate monthly cost ($per token × monthly tokens)
   - Project savings ($ per month after optimization)

**Output Format**:
```markdown
## Token Efficiency Assessment

### Current Token Usage

**Total Token Count**: 62,000 tokens (baseline)

**Top 10 Consumers**:
1. Improvement Proposals Skill: 14,800 tokens (24%)
2. Product Evolution Analysis Skill: 9,500 tokens (15%)
3. Competitive Intelligence Skill: 8,200 tokens (13%)
4. CLAUDE.md: 6,800 tokens (11%)
5. AI Specialist Agent: 4,700 tokens (8%)
6. Product Manager Agent: 4,100 tokens (7%)
7. Persona Definition Skill: 3,600 tokens (6%)
8. Financial Advisor Agent: 2,900 tokens (5%)
9. Test Engineer Agent: 2,700 tokens (4%)
10. Security Auditor Agent: 2,200 tokens (4%)

**Token Distribution**:
- Skills (8 files): 42,100 tokens (68%)
- Agents (5 files): 16,600 tokens (27%)
- CLAUDE.md files: 3,300 tokens (5%)

### Compression Opportunities

**Opportunity 1: Verbose → Concise** (Estimated savings: 8,500 tokens, 14%)
- Remove conversational phrases: "you should", "please", "try to"
  - 175 instances × 3 tokens each = 525 tokens saved
- Convert long sentences to bullets:
  - 85 paragraphs × 30% reduction = 3,200 tokens saved
- Replace wordy with direct:
  - "In order to" → "To" (45 instances) = 90 tokens
  - "It is important that you" → "Always" (28 instances) = 70 tokens
  - "Make sure to verify" → "Verify" (62 instances) = 125 tokens
- Compress long examples:
  - 12 examples × 40% reduction = 1,800 tokens saved
- Remove redundant context:
  - 38 sections with unnecessary setup = 2,700 tokens saved

**Opportunity 2: Repetition → Reference** (Estimated savings: 12,400 tokens, 20%)
- RICE framework (3 occurrences):
  - Current: 1,320 tokens total
  - Optimized: 400 tokens (define once) + 50 tokens (reference twice)
  - Savings: 870 tokens
- Token counting explanation (4 occurrences):
  - Current: 820 tokens total
  - Optimized: 200 tokens + 15 tokens (3 references)
  - Savings: 605 tokens
- Best practices lists (5 occurrences):
  - Current: 2,500 tokens total
  - Optimized: 500 tokens + 50 tokens (4 references)
  - Savings: 1,950 tokens
- PM frameworks (8 occurrences across files):
  - Current: 4,800 tokens total
  - Optimized: 1,200 tokens + 80 tokens (7 references)
  - Savings: 3,520 tokens
- Tool usage examples (12 occurrences):
  - Current: 3,600 tokens total
  - Optimized: 800 tokens + 120 tokens (11 references)
  - Savings: 2,680 tokens
- Other duplicated content:
  - Estimated: 2,775 tokens saved

**Opportunity 3: Full Content → Summary** (Estimated savings: 6,200 tokens, 10%)
- Long skill steps (compress examples, focus on framework):
  - Improvement Proposals Skill steps: 3,000 tokens → 1,800 tokens (1,200 saved)
  - Product Evolution Analysis: 2,400 tokens → 1,600 tokens (800 saved)
  - Competitive Intelligence: 2,100 tokens → 1,400 tokens (700 saved)
- Verbose agent sections (compress capabilities, focus on outcomes):
  - Product Manager capabilities: 1,200 tokens → 900 tokens (300 saved)
  - AI Specialist approach: 1,400 tokens → 1,000 tokens (400 saved)
- Lengthy examples (keep core, remove periphery):
  - 18 examples: 4,800 tokens → 2,000 tokens (2,800 saved)

**Opportunity 4: Implicit → Explicit** (Estimated savings: 1,900 tokens, 3%)
- Remove obvious context Claude already knows:
  - "Claude is an AI assistant" type statements: 450 tokens saved
  - Explanations of standard tools: 680 tokens saved
  - Common sense clarifications: 770 tokens saved

### Total Optimization Potential

| Opportunity | Savings | % Reduction |
|-------------|---------|-------------|
| Verbose → Concise | 8,500 tokens | 14% |
| Repetition → Reference | 12,400 tokens | 20% |
| Full Content → Summary | 6,200 tokens | 10% |
| Implicit → Explicit | 1,900 tokens | 3% |
| **Total** | **29,000 tokens** | **47%** |

**Conservative Estimate** (accounting for interdependencies):
- **Realistic Savings**: 21,000 tokens (34% reduction)
- **Baseline**: 62,000 tokens
- **Optimized**: 41,000 tokens

### Cost Impact Analysis

**Assumptions**:
- Average session: 20 turns
- Instruction tokens loaded: 10× per session (context refresh, agent switches)
- Monthly sessions: 100 sessions
- Cost: $15 per 1M input tokens (Claude Opus pricing)

**Current Monthly Cost**:
- Tokens per session: 62,000 tokens × 10 loads = 620,000 tokens
- Monthly tokens: 620,000 × 100 sessions = 62,000,000 tokens
- Monthly cost: 62M × $15 / 1M = **$930/month**

**Optimized Monthly Cost**:
- Tokens per session: 41,000 tokens × 10 loads = 410,000 tokens
- Monthly tokens: 410,000 × 100 sessions = 41,000,000 tokens
- Monthly cost: 41M × $15 / 1M = **$615/month**

**Monthly Savings**: $315/month (**34% cost reduction**)
**Annual Savings**: $3,780/year

### Effort vs Impact Analysis

| Optimization Type | Effort (hours) | Savings (tokens) | Tokens/Hour | Priority |
|-------------------|---------------|------------------|-------------|----------|
| Verbose → Concise | 12 hours | 8,500 | 708 | High |
| Repetition → Reference | 8 hours | 12,400 | 1,550 | Highest |
| Full Content → Summary | 16 hours | 6,200 | 388 | Medium |
| Implicit → Explicit | 4 hours | 1,900 | 475 | High |

**Quick Wins** (< 2 hours each, >500 tokens):
1. Remove conversational phrases (1.5 hours, 525 tokens)
2. Deduplicate RICE framework (1 hour, 870 tokens)
3. Deduplicate token counting (0.5 hours, 605 tokens)
4. Remove obvious context (2 hours, 1,900 tokens)

**Total Quick Wins**: 5 hours effort, 3,900 tokens saved (780 tokens/hour ROI)
```

---

### Step 5: Improvement Proposals (10 min)

**Objective**: Generate specific rewrite suggestions with before/after examples

**Actions**:
1. **Prioritize Issues**: Rank by token savings and clarity improvement
2. **Create Before/After Examples**: Show exact rewrites for top 15-20 issues
3. **Calculate Per-Issue Impact**: Tokens saved, clarity gain, effort required
4. **Categorize by Type**: Verbosity, redundancy, structure, ambiguity
5. **Provide Rationale**: Explain why each change improves instruction quality

**Output Format**:
```markdown
## Improvement Proposals

### High-Priority Rewrites (Top 10)

---

#### Proposal 1: Deduplicate RICE Framework (3 occurrences)
**Impact**: 870 tokens saved (1.4% total), 1 hour effort
**Files Affected**: product-manager.md, improvement-proposals SKILL.md, feature-impact-estimate.md

**Current** (repeated 3 times, 1,320 tokens total):
```markdown
**RICE Scoring Framework**:
- **Reach**: How many users will benefit? (users per quarter)
  - Count the number of users who will interact with this feature
  - Estimate based on user base size and feature relevance
  - Example: 1,000 users per quarter
- **Impact**: How much will it improve their experience?
  - Rate on scale: 0.25 (minimal), 0.5 (low), 1 (medium), 2 (high), 3 (massive)
  - Consider time saved, friction reduced, delight created
  - Example: 2 (high impact - saves significant time)
- **Confidence**: How certain are we about reach and impact?
  - Rate on scale: 50% (low certainty), 80% (medium), 100% (high)
  - Based on data quality, user research, similar feature performance
  - Example: 80% (medium confidence - some data supporting estimates)
- **Effort**: How much development time is required?
  - Estimate in person-months (0.25 = 1 week, 0.5 = 2 weeks, 1 = 1 month)
  - Include: design, development, testing, documentation
  - Example: 0.5 (2 weeks of development)

**RICE Score Calculation**:
RICE = (Reach × Impact × Confidence) / Effort

**Example**:
Reach = 1,000 users/quarter
Impact = 2 (high)
Confidence = 80% (0.8)
Effort = 0.5 person-months
RICE = (1,000 × 2 × 0.8) / 0.5 = 3,200
```

**Proposed** (define once in product-manager.md, reference elsewhere):

*In product-manager.md (400 tokens)*:
```markdown
**RICE Scoring**: (Reach × Impact × Confidence) / Effort
- Reach: Users per quarter
- Impact: 0.25 (minimal), 0.5 (low), 1 (medium), 2 (high), 3 (massive)
- Confidence: 50% (low), 80% (medium), 100% (high)
- Effort: Person-months (0.25 = 1 week)
- Example: (1,000 × 2 × 0.8) / 0.5 = 3,200
```

*In improvement-proposals SKILL.md and feature-impact-estimate.md (25 tokens each)*:
```markdown
Use RICE scoring (see product-manager agent definition for framework).
```

**Savings**: 1,320 tokens → 450 tokens = **870 tokens saved (66% reduction)**
**Effort**: 1 hour (consolidate and update references)
**Priority**: P0 (Highest impact per effort)

---

#### Proposal 2: Convert Conversational to Imperative (175 instances)
**Impact**: 525 tokens saved (0.8% total), 1.5 hours effort
**Files Affected**: All files

**Current Examples** (3 tokens each, verbose):
```markdown
- "You should always try to use the Read tool before editing files"
- "Please make sure that you include test strategies in your plans"
- "It is important that you check for errors before committing code"
- "Consider using the Grep tool to search for files instead of Bash"
```

**Proposed** (1 token each, imperative):
```markdown
- "Use Read before editing files"
- "Include test strategies in plans"
- "Check for errors before committing"
- "Use Grep to search files"
```

**Pattern Replacements**:
- "You should [always/try to]" → Remove
- "Please make sure [that]" → Remove
- "It is important that you" → "Always" or remove
- "Consider using X" → "Use X"

**Savings**: 175 instances × 3 tokens = **525 tokens saved (100% reduction on these phrases)**
**Effort**: 1.5 hours (find-and-replace with manual review)
**Priority**: P0 (Quick win, high impact)

---

#### Proposal 3: Compress Long Skill Examples (12 examples)
**Impact**: 1,800 tokens saved (2.9% total), 3 hours effort
**Files Affected**: improvement-proposals SKILL.md, product-evolution-analysis SKILL.md, competitive-intelligence SKILL.md

**Current Example** (improvement-proposals SKILL.md, lines 612-750, ~150 tokens):
```markdown
### Proposal 1: Onboarding Overhaul
**RICE Score: 14400 | Priority: P0 (Ship in Q1)**

#### Executive Summary
Redesign onboarding flow to reduce time-to-first-value from 2 hours to 15 minutes and increase activation rate from 35% to 85%. This is a high-impact, low-effort improvement that directly addresses our largest growth bottleneck.

#### Problem Statement
**User Pain Point**: New users face a 10-step setup process that takes 2 hours on average. 65% of users abandon during onboarding, never experiencing the product's core value.

**Evidence**:
- Activation rate: 35% (industry avg: 60-70%)
- Time-to-first-value: 2 hours (competitors: 15-30 min)
- User feedback: "Too complicated", "Gave up halfway"
- Drop-off points: Step 3 (30%), Step 7 (20%)

**Business Impact**: Losing 650 users/month (65% of 1000), $130K/month potential revenue.

[... 100 more lines of detailed example ...]
```

**Proposed** (80 tokens, 47% reduction):
```markdown
### Example Output: Onboarding Overhaul
**RICE Score: 14400 | Priority: P0**

**Problem**: 10-step setup, 2 hours, 35% activation (65% abandon)
**Solution**: Reduce to 3 steps, 15 min, sensible defaults, templates
**Impact**: 35% → 85% activation, +$130K/month revenue
**Effort**: 2 weeks (1 eng, 1 designer)
**ROI**: $1.56M annual revenue for 2 weeks effort

[See full proposal template in documentation]
```

**Rationale**:
- Examples are for illustration, not exact templates to copy
- Focus on framework structure, not exhaustive content
- Users can generate full proposals themselves
- Reduce example verbosity by 50% while keeping core value

**Savings**: 12 examples × 150 tokens = **1,800 tokens saved (50% reduction in examples)**
**Effort**: 3 hours (compress each example while preserving key points)
**Priority**: P1 (High impact, moderate effort)

---

#### Proposal 4: Add Subheadings to Long Sections (45 new headers)
**Impact**: 0 tokens saved (adds ~90 tokens), but 40% scannability improvement
**Files Affected**: 6 files with long flat sections

**Current** (product-manager.md, lines 110-175, 65 lines without headers):
```markdown
## Your Approach

When asked to analyze a product or provide PM guidance, follow this systematic approach. Start by discovering context through reading repository files, documentation, and recent commits. This helps you understand the product type, target audience, and current focus areas. Then gather data using web search to research competitors and market trends. Analyze repository metrics to understand project health and momentum. Apply relevant PM frameworks like RICE, Kano, JTBD systematically. Create structured analyses including feature matrices and persona profiles. [... continues for 60 more lines without breaks ...]
```

**Proposed** (add H3 subheadings every 10-15 lines):
```markdown
## Your Approach

When asked to analyze a product or provide PM guidance, follow this systematic approach:

### 1. Context Discovery (5-10 min)
- Read README, package files, docs to understand the product
- Analyze recent commits and issues to understand current focus
- Identify product type, target audience, maturity stage

### 2. Data Gathering (10-20 min)
- Use web search to research competitors and market context
- Read user feedback from issues, reviews, discussions
- Analyze repository metrics (stars, forks, velocity)

### 3. Framework Application (15-30 min)
- Apply relevant PM frameworks (RICE, Kano, JTBD)
- Create structured analyses (feature matrices, personas)
- Calculate prioritization scores

[... continue with clear structure ...]
```

**Rationale**:
- Improves Claude's ability to scan and find relevant sections
- Reduces cognitive load (clear milestones vs wall of text)
- Enables jumping to specific steps without reading entire block
- Worth slight token increase for significant comprehension improvement

**Impact**: +90 tokens (45 headers × 2 tokens), but **40% faster navigation**
**Effort**: 2 hours (add headers, reorganize slightly)
**Priority**: P1 (Clarity improvement outweighs token cost)

---

#### Proposal 5: Specify Vague Constraints (28 instances)
**Impact**: +280 tokens (adds specificity), 90% fewer ambiguity errors
**Files Affected**: All instruction files

**Current Examples** (ambiguous, leads to inconsistent behavior):
```markdown
- "Keep responses concise"
- "Be thorough in your analysis"
- "Avoid unnecessary tool usage"
- "Improve test coverage"
```

**Proposed** (specific, measurable):
```markdown
- "Limit responses to 200 words (2-3 paragraphs) unless detailed report requested"
- "Include: problem analysis, data evidence, recommendation, success metrics, timeline"
- "Never use Bash for file operations (use Read/Write/Edit instead)"
- "Achieve 80%+ line coverage, 100% critical path coverage"
```

**Rationale**:
- Specificity prevents Claude from guessing intent
- Measurable constraints enable verification
- Clear boundaries reduce errors and retries
- Slight token increase pays off in consistency

**Impact**: +280 tokens (28 constraints × 10 tokens additional), but **90% fewer ambiguity-related errors**
**Effort**: 2 hours (identify and specify each constraint)
**Priority**: P0 (Critical for consistent behavior)

---

[Continue with 5-10 more high-priority proposals...]

### Medium-Priority Rewrites (5-8 proposals)

[Additional proposals with moderate impact...]

### Quick Wins (<1 hour effort each)

1. Remove "In order to" → "To" (45 instances, 90 tokens, 15 min)
2. Remove obvious context about Claude being an AI (450 tokens, 30 min)
3. Deduplicate token counting explanation (605 tokens, 30 min)
4. Convert 12 long bullet explanations to single-line (360 tokens, 45 min)

**Total Quick Wins**: 2 hours, 1,505 tokens saved

### Summary of All Proposals

| Priority | Proposals | Token Impact | Effort | Tokens/Hour |
|----------|-----------|--------------|--------|-------------|
| P0 (Critical) | 5 proposals | +280 tokens (clarity),-2,395 tokens (savings) = **-2,115 net** | 6 hours | 353/hour |
| P1 (High) | 8 proposals | -7,200 tokens | 14 hours | 514/hour |
| P2 (Medium) | 6 proposals | -4,100 tokens | 10 hours | 410/hour |
| Quick Wins | 4 proposals | -1,505 tokens | 2 hours | 753/hour |
| **Total** | **23 proposals** | **-14,920 tokens (24% reduction)** | **32 hours** | **466/hour** |

**Note**: Conservative estimate excludes some high-effort opportunities (full content summarization)
```

---

### Step 6: Implementation Plan (5 min)

**Objective**: Create prioritized roadmap for applying optimizations

**Actions**:
1. **Phase Breakdown**: Group proposals into phases (Quick Wins, Phase 1, Phase 2)
2. **Dependency Mapping**: Identify which proposals must happen in order
3. **Resource Allocation**: Estimate person-hours and timeline
4. **Risk Assessment**: Note potential issues with each change
5. **Rollback Strategy**: Plan for testing and reverting if needed
6. **Success Tracking**: Define how to measure optimization impact

**Output Format**:
```markdown
## Implementation Plan

### Phase 0: Quick Wins (2 hours, -1,505 tokens)

**Timeline**: Week 1, Days 1-2
**Effort**: 2 hours total
**Savings**: 1,505 tokens (2.4% reduction)

**Quick Win 1: Remove Conversational Phrases** (30 min, -90 tokens)
- Files: All files
- Action: Find and remove "In order to" → "To" (45 instances)
- Risk: Low (simple replacement)
- Validation: Grep for "In order to", confirm 0 results

**Quick Win 2: Remove Obvious Context** (30 min, -450 tokens)
- Files: CLAUDE.md, agent definitions
- Action: Remove statements like "Claude is an AI assistant that..."
- Risk: Low (redundant information)
- Validation: Read first 50 lines of each file, confirm clarity maintained

**Quick Win 3: Deduplicate Token Counting** (30 min, -605 tokens)
- Files: 4 files (ai-specialist.md, token-optimization-audit SKILL.md, 2 others)
- Action: Keep one full explanation, replace others with references
- Risk: Low (clear dedupe candidate)
- Validation: Search for "token" across files, confirm single definition

**Quick Win 4: Compress Bullet Explanations** (30 min, -360 tokens)
- Files: Various agent and skill files
- Action: Convert multi-line bullet explanations to single-line
- Risk: Medium (may reduce clarity if too aggressive)
- Validation: Review 3 examples with team, confirm clarity preserved

---

### Phase 1: High-Impact Optimizations (12 hours, -6,510 tokens)

**Timeline**: Week 1-2, Days 3-10
**Effort**: 12 hours total
**Savings**: 6,510 tokens (10.5% reduction)
**Cumulative**: 8,015 tokens saved (13%)

**Optimization 1: Deduplicate RICE Framework** (1 hour, -870 tokens) - P0
- Files: product-manager.md, improvement-proposals SKILL.md, feature-impact-estimate.md
- Action:
  1. Keep full RICE definition in product-manager.md (400 tokens)
  2. Replace in other 2 files with "Use RICE scoring (see product-manager agent)" (25 tokens each)
  3. Update cross-references
- Risk: Low (clear dedupe)
- Validation: Test product-manager agent, confirm RICE guidance accessible

**Optimization 2: Convert to Imperative Tone** (1.5 hours, -525 tokens) - P0
- Files: All files (175 instances)
- Action:
  1. Find: "You should", "Please", "Try to", "Make sure", "It is important"
  2. Replace with imperative: "Use", "Include", "Check"
  3. Review each replacement for context
- Risk: Medium (may change meaning if not careful)
- Validation: Sample 20 replacements, confirm intent preserved

**Optimization 3: Specify Vague Constraints** (2 hours, +280 tokens but -errors) - P0
- Files: All files (28 vague constraints)
- Action:
  1. Identify constraints: "be concise", "thorough", "avoid when possible"
  2. Add specific limits: "max 200 words", "include: X, Y, Z", "never use Bash for file ops"
  3. Make measurable: "80% coverage", "30% reduction"
- Risk: Medium (may be too prescriptive)
- Validation: Test 5 scenarios, confirm behavior more consistent
- Net Impact: +280 tokens but 90% fewer ambiguity errors (worth tradeoff)

**Optimization 4: Add Structural Subheadings** (2 hours, +90 tokens but +40% scannability) - P1
- Files: 6 files with long flat sections (>50 lines without headers)
- Action:
  1. product-manager.md lines 110-175: Add 6 H3 headers
  2. improvement-proposals SKILL.md lines 272-335: Add 4 H3 headers
  3. [Other 4 files]: Add 35 more headers total
- Risk: Low (improves structure)
- Validation: Read optimized sections, confirm easier to scan
- Net Impact: +90 tokens but 40% faster navigation (worth tradeoff)

**Optimization 5: Deduplicate PM Frameworks** (2 hours, -3,520 tokens) - P0
- Files: 8 files with repeated Kano, JTBD, Value Prop Canvas explanations
- Action:
  1. Create shared frameworks reference in product-manager.md
  2. Replace repetitions with references
  3. Update 7 file references
- Risk: Low (clear dedupe)
- Validation: Verify all frameworks accessible via references

**Optimization 6: Deduplicate Best Practices** (1.5 hours, -1,950 tokens) - P1
- Files: 5 files with repeated best practice lists
- Action:
  1. Consolidate in CLAUDE.md or create shared reference
  2. Replace with references: "Follow best practices (see CLAUDE.md)"
- Risk: Low (redundant content)
- Validation: Confirm best practices still accessible

**Optimization 7: Compress Tool Usage Examples** (2 hours, -2,680 tokens) - P1
- Files: 12 files with repeated tool examples
- Action:
  1. Keep core tool examples in CLAUDE.md
  2. Remove redundant examples from agent/skill files
  3. Add references where needed
- Risk: Medium (examples helpful for clarity)
- Validation: Ensure key examples preserved, not overly sparse

---

### Phase 2: Content Summarization (16 hours, -8,000 tokens)

**Timeline**: Week 3-4, Days 11-20
**Effort**: 16 hours total
**Savings**: 8,000 tokens (13% reduction)
**Cumulative**: 16,015 tokens saved (26%)

**Summarization 1: Compress Skill Step Examples** (6 hours, -3,600 tokens) - P1
- Files: improvement-proposals SKILL.md, product-evolution-analysis SKILL.md, competitive-intelligence SKILL.md
- Action:
  1. Reduce each example by 50% (keep structure, remove verbose details)
  2. Focus on framework illustration, not exhaustive content
  3. Add reference: "See full example outputs in documentation"
- Risk: Medium (examples valuable for clarity)
- Mitigation: Keep one full example per skill, compress others
- Validation: Test skills, confirm examples still illustrative

**Summarization 2: Compress Agent Capability Sections** (4 hours, -1,700 tokens) - P2
- Files: All agent definitions (verbose capability descriptions)
- Action:
  1. Reduce capability descriptions by 30% (focus on what, not why)
  2. Convert long paragraphs to bullet lists
  3. Remove redundant explanations
- Risk: Medium (may reduce context)
- Validation: Review with 2 team members, confirm clarity adequate

**Summarization 3: Compress Long Examples** (6 hours, -2,700 tokens) - P2
- Files: 18 long code/output examples across files
- Action:
  1. Keep core of example (first/last sections)
  2. Replace middle with "... [additional output] ..."
  3. Add reference to full examples in docs
- Risk: Low (examples illustrative, not normative)
- Validation: Confirm examples still convey key points

---

### Phase 3: Advanced Optimizations (Optional, 10+ hours, -5,000+ tokens)

**Timeline**: Week 5+
**Effort**: 10+ hours
**Savings**: 5,000+ tokens (8%+ reduction)
**Cumulative**: 21,000+ tokens saved (34%+)

- Extract common patterns to shared files
- Create hierarchical context loading (load only relevant sections)
- Implement lazy loading for rarely-used content
- Compress historical examples
- Consolidate overlapping agent capabilities

**Note**: Phase 3 is optional and depends on whether 26% reduction (Phase 1-2) meets goals.

---

## Implementation Roadmap Summary

| Phase | Timeline | Effort | Savings | Cumulative | Risk |
|-------|----------|--------|---------|------------|------|
| Phase 0: Quick Wins | Days 1-2 | 2 hours | -1,505 tokens (2.4%) | 2.4% | Low |
| Phase 1: High-Impact | Days 3-10 | 12 hours | -6,510 tokens (10.5%) | 12.9% | Low-Med |
| Phase 2: Summarization | Days 11-20 | 16 hours | -8,000 tokens (13%) | 25.9% | Medium |
| Phase 3: Advanced (opt) | Week 5+ | 10+ hours | -5,000+ tokens (8%+) | 34%+ | Medium |

**Recommended Approach**: Complete Phase 0-2 (30 hours, 26% reduction), evaluate results, decide on Phase 3.

### Dependencies

- **None for Phase 0**: All quick wins are independent
- **Phase 1 Optimization 5** depends on Optimization 1 (RICE dedupe first, then other frameworks)
- **Phase 2** can start in parallel with Phase 1 (different files)
- **Phase 3** requires Phase 1-2 completion (builds on structure changes)

### Risk Management

**Risk 1: Optimization reduces clarity**
- Mitigation: Review each change with 1-2 team members
- Rollback: Keep git commits granular (1 commit per optimization)
- Validation: Test agents after each phase, check for behavior changes

**Risk 2: References break if files reorganized**
- Mitigation: Use relative paths, test references after changes
- Rollback: Keep backup of original files
- Validation: Grep for all reference patterns, verify targets exist

**Risk 3: Token savings lower than estimated**
- Mitigation: Track actual savings per optimization, adjust plan if needed
- Rollback: Prioritize high-confidence optimizations first
- Validation: Measure tokens before/after each phase, compare to estimates

### Success Tracking

**Metrics to Track**:
1. **Token Count**: Measure before/after each phase
   - Baseline: 62,000 tokens
   - Phase 0 target: 60,495 tokens
   - Phase 1 target: 53,985 tokens
   - Phase 2 target: 45,985 tokens
2. **Clarity**: Survey 3 team members (1-10 scale) on instruction clarity
   - Baseline: 7/10 average
   - Target: 8+/10 after optimization
3. **Error Rate**: Track instruction-related errors per 100 operations
   - Baseline: 8 errors/100 ops
   - Target: <3 errors/100 ops (after specifying vague constraints)
4. **Agent Response Quality**: Sample 20 agent responses before/after
   - Measure: Completeness, accuracy, consistency
   - Target: No degradation (maintain or improve)

**Measurement Tools**:
- Token counting: Use `wc -w` × 0.75 or tokenizer tool
- Clarity survey: Google Form with 5 questions
- Error tracking: Manual log during testing period
- Response quality: Blind A/B comparison (reviewer doesn't know which is optimized)

**Review Cadence**:
- After each phase: Measure tokens, errors, clarity
- After Phase 2: Full review, decide on Phase 3
- 1 month post-optimization: Long-term impact assessment

---

## Implementation Checklist

**Before Starting**:
- [ ] Create backup branch: `git checkout -b instructions-optimization-backup`
- [ ] Document baseline metrics (tokens, clarity, error rate)
- [ ] Set up token counting tool
- [ ] Notify team of optimization project

**During Implementation**:
- [ ] Create separate commits for each optimization (easy rollback)
- [ ] Test agents after each major change
- [ ] Track actual savings vs estimates
- [ ] Document any issues or unexpected behavior

**After Completion**:
- [ ] Measure final token count and compare to baseline
- [ ] Survey team on clarity improvements
- [ ] Monitor error rates for 2 weeks
- [ ] Create optimization report with before/after metrics
- [ ] Update MEMORY.md with lessons learned
```

---

### Step 7: Report Generation (5 min)

**Objective**: Create executive summary with key findings and recommendations

**Actions**:
1. **Executive Summary**: 3-5 bullets covering key findings
2. **Current State**: Baseline metrics (tokens, compliance, issues)
3. **Opportunity Summary**: Total potential savings and improvements
4. **Top Recommendations**: Prioritized list of optimizations (top 5)
5. **Expected Impact**: Token savings, cost reduction, quality improvements
6. **Implementation Timeline**: High-level roadmap with milestones
7. **Next Steps**: Immediate actions to start optimization

**Output Format**:
```markdown
# Claude Instructions Optimization Report

**Date**: 2026-02-16
**Project**: [Project Name]
**Analyzed By**: AI Specialist Agent

---

## Executive Summary

- **Current Token Usage**: 62,000 tokens across all instruction files (CLAUDE.md, agents, skills, commands)
- **Optimization Opportunity**: 26% reduction (-16,015 tokens) achievable in 30 hours
- **Cost Impact**: $315/month savings ($3,780/year) at current usage rates
- **Key Issues**: 35% instructions use conversational tone (should be imperative), 40% constraints are vague, 20% content is duplicated
- **Top Quick Win**: Deduplicate RICE framework (1 hour, -870 tokens)

---

## Current State Analysis

### Token Distribution
- **Total Tokens**: 62,000 tokens (baseline)
- **Skills (8 files)**: 42,100 tokens (68% of total)
- **Agents (5 files)**: 16,600 tokens (27%)
- **CLAUDE.md files**: 3,300 tokens (5%)

**Top 5 Consumers**:
1. Improvement Proposals Skill: 14,800 tokens (24%)
2. Product Evolution Analysis Skill: 9,500 tokens (15%)
3. Competitive Intelligence Skill: 8,200 tokens (13%)
4. CLAUDE.md: 6,800 tokens (11%)
5. AI Specialist Agent: 4,700 tokens (8%)

### Quality Issues Identified

**Verbosity** (12 issues):
- Conversational phrases: 175 instances ("you should", "please", "try to")
- Redundant explanations: 26 instances (same concept repeated)
- Long paragraphs: 85 instances (>100 words, should be bullets)

**Ambiguity** (8 issues):
- Vague constraints: 57 instances ("be concise" without defining limit)
- Unmeasurable outcomes: 52 instances ("improve quality" without metrics)

**Redundancy** (6 issues):
- RICE framework: Repeated 3 times (1,320 tokens, save 870)
- PM frameworks: Repeated 8 times (4,800 tokens, save 3,520)
- Best practices: Repeated 5 times (2,500 tokens, save 1,950)

**Structure** (5 issues):
- Long flat sections: 6 files with >50 lines without headers
- Poor scannability: Average 28 lines between headers (target: 15)

### Best Practices Compliance

| Practice | Current | Target | Gap |
|----------|---------|--------|-----|
| Imperative Tone | 65% | 90% | -25% |
| Specific Constraints | 60% | 80% | -20% |
| Measurable Outcomes | 70% | 90% | -20% |
| Header Frequency | 28 lines | 15 lines | -87% |
| Success Criteria | 63% | 90% | -27% |

**Overall Compliance**: 64% (target: 85%+)

---

## Optimization Opportunities

### Token Savings Potential

| Opportunity | Savings | % Reduction | Effort |
|-------------|---------|-------------|--------|
| Verbose → Concise | -8,500 tokens | 14% | 12 hours |
| Repetition → Reference | -12,400 tokens | 20% | 8 hours |
| Full Content → Summary | -6,200 tokens | 10% | 16 hours |
| Implicit → Explicit | -1,900 tokens | 3% | 4 hours |
| **Conservative Total** | **-21,000 tokens** | **34%** | **40 hours** |

**Recommended Scope** (Phases 0-2):
- **Savings**: -16,015 tokens (26% reduction)
- **Effort**: 30 hours
- **Timeline**: 20 days (4 weeks at 6 hours/week)

### Cost Impact

**Current Monthly Cost**: $930/month
- Assumptions: 100 sessions/month, 10 context loads per session
- Token rate: $15 per 1M tokens (Claude Opus)

**Optimized Monthly Cost**: $615/month (after 26% reduction)

**Savings**: $315/month (**$3,780/year**)

### Quality Improvements

- **Clarity**: +20% (specify vague constraints, add structure)
- **Consistency**: +90% (reduce ambiguity-related errors)
- **Scannability**: +40% (add subheadings, improve hierarchy)
- **Agent Performance**: Faster context comprehension, fewer clarifications needed

---

## Top 5 Recommendations (Prioritized)

### 1. Deduplicate RICE Framework (P0 - Highest ROI)
**Impact**: -870 tokens (1.4%), 1 hour effort = 870 tokens/hour
**Action**: Keep full definition in product-manager.md, replace 2 occurrences with references
**Timeline**: Day 1
**Risk**: Low

### 2. Convert to Imperative Tone (P0 - High Impact)
**Impact**: -525 tokens (0.8%), 1.5 hours effort = 350 tokens/hour
**Action**: Replace 175 instances of "you should", "please", "try to" with imperative verbs
**Timeline**: Days 1-2
**Risk**: Medium (review each replacement)

### 3. Deduplicate PM Frameworks (P0 - High Value)
**Impact**: -3,520 tokens (5.7%), 2 hours effort = 1,760 tokens/hour
**Action**: Consolidate Kano, JTBD, Value Prop Canvas in product-manager.md, reference elsewhere
**Timeline**: Days 3-4
**Risk**: Low

### 4. Specify Vague Constraints (P0 - Quality Critical)
**Impact**: +280 tokens but -90% errors, 2 hours effort
**Action**: Replace 28 vague constraints with specific, measurable limits
**Timeline**: Days 5-6
**Risk**: Medium (may be too prescriptive, test carefully)

### 5. Compress Skill Examples (P1 - Medium Effort)
**Impact**: -3,600 tokens (5.8%), 6 hours effort = 600 tokens/hour
**Action**: Reduce 12 long skill examples by 50%, focus on framework not exhaustive content
**Timeline**: Days 7-10
**Risk**: Medium (balance brevity with clarity)

**Total Impact (Top 5)**: -7,735 tokens (12.5%), 12.5 hours effort

---

## Implementation Roadmap

### Phase 0: Quick Wins (Days 1-2, 2 hours, -1,505 tokens)
- Remove conversational phrases
- Remove obvious context
- Deduplicate token counting
- Compress bullet explanations

### Phase 1: High-Impact (Days 3-10, 12 hours, -6,510 tokens)
- Deduplicate frameworks (RICE, Kano, JTBD, etc.)
- Convert to imperative tone
- Specify vague constraints (+280 tokens but quality gain)
- Add structural subheadings (+90 tokens but scannability gain)

### Phase 2: Content Summarization (Days 11-20, 16 hours, -8,000 tokens)
- Compress skill step examples
- Compress agent capability sections
- Compress long examples

**Total Recommended**: 30 hours, 20 days, -16,015 tokens (26% reduction), $315/month savings

### Phase 3: Advanced Optimizations (Optional, Week 5+)
- Extract common patterns to shared files
- Hierarchical context loading
- Further deduplication
- **Additional savings**: -5,000+ tokens (8%+), bringing total to 34%+ reduction

---

## Next Steps (Immediate Actions)

**This Week**:
1. **Day 1**: Create backup branch (`instructions-optimization-backup`)
2. **Day 1**: Complete Quick Win 1-2 (deduplicate RICE, remove conversational phrases)
   - Expected: -1,395 tokens in 1.5 hours
3. **Day 2**: Complete Quick Win 3-4 (deduplicate token counting, compress bullets)
   - Expected: -965 tokens in 1 hour
4. **Day 2**: Measure Phase 0 impact, validate quality maintained

**Next Week**:
5. **Days 3-6**: Complete Phase 1 high-impact optimizations
   - Expected: -6,510 tokens in 12 hours
6. **Day 7**: Review Phase 1 results, test agents, adjust plan if needed

**Month 1**:
7. **Days 11-20**: Complete Phase 2 content summarization
   - Expected: -8,000 tokens in 16 hours
8. **Day 21**: Final measurement, report results
9. **Day 21**: Decide on Phase 3 (optional advanced optimizations)

**Approval Needed**:
- [ ] Approve Phase 0-2 implementation (30 hours, 26% reduction)
- [ ] Assign team member to review optimizations (quality check)
- [ ] Set up token measurement process
- [ ] Schedule Phase 1 kickoff (Day 3)

---

## Appendix: Detailed Analysis

See previous sections for:
- Step 1: File Discovery
- Step 2: Instruction Analysis
- Step 3: Best Practices Audit
- Step 4: Token Efficiency Assessment
- Step 5: Improvement Proposals
- Step 6: Implementation Plan

---

**Questions or Concerns?** Contact AI Specialist agent for clarification or adjustments to the optimization plan.
```

---

## Quality Checklist

Before completing this skill, verify:

- [ ] **File discovery**: Found all CLAUDE.md, agent, skill, command files; calculated baseline tokens
- [ ] **Instruction analysis**: Identified verbosity, ambiguity, conflicts, redundancy, structure issues
- [ ] **Best practices audit**: Checked tone, constraint clarity, structure, examples, success criteria
- [ ] **Token efficiency**: Calculated current usage, compression opportunities, cost impact
- [ ] **Improvement proposals**: Created specific before/after examples for top 15-20 optimizations
- [ ] **Implementation plan**: Prioritized roadmap with phases, timeline, dependencies, risk management
- [ ] **Report generation**: Executive summary with findings, recommendations, impact, next steps
- [ ] **Evidence-based**: All estimates grounded in actual file analysis, token counts, effort estimates

---

## Tips for Effective Claude Instructions Optimization

1. **Start with measurement**: Always establish baseline tokens before optimizing
2. **Prioritize by ROI**: Focus on high-tokens/hour optimizations first (dedupe > compress > rephrase)
3. **Test incrementally**: Commit each optimization separately, test agents after each change
4. **Preserve intent**: Never sacrifice clarity for tokens; specificity sometimes requires more tokens
5. **Think in patterns**: Find repeated content across files (biggest savings opportunity)
6. **Use imperatives**: "Use Read" is clearer and shorter than "You should use Read"
7. **Be specific**: "Max 200 words" is better than "Be concise" (even if slightly more tokens)
8. **Add structure**: Subheadings improve scannability worth minor token increase
9. **Show don't tell**: Before/after examples prove your optimizations work
10. **Track results**: Measure actual savings, validate quality maintained, adjust plan if needed

---

## Integration with Other Skills

This skill works well with:

- **test-strategy-design**: Optimization changes should include test strategy to validate behavior
- **memory-efficiency-analysis**: After optimizing instructions, optimize memory files
- **token-optimization-audit**: Use audit results to prioritize instruction optimizations
- **prompt-enhancement**: Apply similar optimization techniques to individual prompts

---

*Use this skill whenever you need to reduce token usage in Claude instruction files while maintaining or improving quality and clarity.*
