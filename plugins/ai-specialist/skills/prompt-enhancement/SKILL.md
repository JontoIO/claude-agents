---
name: prompt-enhancement
description: Improve individual prompts for clarity, specificity, and token efficiency using 6-step framework including prompt analysis, rewrite strategies, and A/B testing recommendations
---

# Prompt Enhancement Skill

Analyze and improve individual prompts (user prompts, skill prompts, command prompts) for clarity, specificity, token efficiency, and better Claude responses.

## When to Use This Skill

Use this skill when you need to:
- Improve unclear or ambiguous prompts
- Reduce token usage in frequently-used prompts
- Enhance prompt specificity for better responses
- Optimize prompt structure for Claude comprehension
- Add constraints and success criteria to prompts
- Fix prompts that produce inconsistent results
- Design A/B tests for prompt variations

## 6-Step Prompt Enhancement Framework

### Step 1: Prompt Analysis (5 min)

**Objective**: Understand current prompt and identify issues

**Actions**:
1. Read prompt and expected outcome
2. Identify prompt type (open-ended, specific task, creative, analytical)
3. Check for clarity issues (ambiguity, vagueness, missing context)
4. Assess specificity (clear constraints, success criteria, examples)
5. Evaluate token efficiency (verbose, conversational, optimal)

**Output**: Prompt assessment with identified improvement areas

### Step 2: Clarity Enhancement (6 min)

**Objective**: Remove ambiguity and add specificity

**Actions**:
1. **Specify Intent**: What exactly do you want Claude to do?
2. **Add Constraints**: Length limits, format requirements, scope boundaries
3. **Define Success**: What does a good response look like?
4. **Provide Context**: Essential background for understanding task
5. **Include Examples**: Show desired output format or style

**Output**: Clarity improvement recommendations

### Step 3: Token Optimization (5 min)

**Objective**: Reduce token usage while preserving meaning

**Actions**:
1. Remove unnecessary words ("please", "I would like you to")
2. Use imperative tone ("Analyze" not "Can you analyze")
3. Eliminate redundant context (assume Claude knows basics)
4. Compress examples (keep essence, remove verbosity)
5. Front-load critical information

**Output**: Token-efficient prompt variations

### Step 4: Structure Optimization (6 min)

**Objective**: Organize prompt for better comprehension

**Actions**:
1. **Front-Load Request**: Lead with what you want
2. **Add Clear Sections**: Task, Context, Constraints, Output Format
3. **Use Formatting**: Bullets, numbers, headers for scannability
4. **Hierarchical Info**: Critical first, details later
5. **Progressive Disclosure**: Start simple, add complexity if needed

**Output**: Structurally optimized prompt

### Step 5: Rewrite Proposals (8 min)

**Objective**: Generate improved prompt variations

**Actions**:
1. Create 2-3 prompt variations
2. Show before/after token counts
3. Highlight key improvements (clarity, specificity, efficiency)
4. Explain trade-offs (if any)
5. Recommend best variation

**Output**: Multiple prompt options with analysis

### Step 6: Testing Recommendations (5 min)

**Objective**: Validate prompt improvements

**Actions**:
1. Design A/B test (original vs improved, measure quality)
2. Define success metrics (response quality, token usage, consistency)
3. Recommend test sample size (10-20 responses per variant)
4. Create evaluation rubric (clarity, completeness, accuracy)
5. Plan iteration based on results

**Output**: Testing and validation plan

---

## Example: Prompt Enhancement

### Original Prompt (85 tokens)
```
I would like you to please help me analyze this codebase and identify any potential issues or areas for improvement. Can you look through the files and let me know what you think? I'm particularly interested in code quality, performance, and maintainability, but feel free to point out anything else you notice. Thanks!
```

**Issues**:
- Conversational tone ("I would like", "please", "Thanks")
- Vague request ("identify any potential issues")
- No constraints (how many issues? what format?)
- No success criteria (what makes analysis good?)
- Inefficient structure (key request buried mid-prompt)

### Enhanced Prompt (42 tokens, 51% reduction)
```
Analyze codebase for issues.

**Focus Areas**: Code quality, performance, maintainability
**Output**: Top 5 issues, ranked by severity
**Format**: Issue, Location (file:line), Impact, Recommendation

Prioritize: Security vulnerabilities, performance bottlenecks, readability issues.
```

**Improvements**:
- Imperative tone ("Analyze" not "Can you analyze")
- Specific constraints (top 5 issues, ranked)
- Clear output format (issue, location, impact, recommendation)
- Front-loaded request (first line states intent)
- Added prioritization guidance
- 43 tokens saved (51% reduction)

### A/B Test Plan
- Run both prompts on 10 different codebases
- Measure: Response quality (1-10 scale), token usage, consistency
- Success criteria: Enhanced version ≥ original quality, <60% tokens
- Expected result: Enhanced version 20% better quality, 50% fewer tokens

---

## Quality Checklist

- [ ] Analyzed prompt for clarity, specificity, efficiency issues
- [ ] Enhanced clarity with constraints, success criteria, examples
- [ ] Optimized tokens (removed conversational tone, redundancy)
- [ ] Improved structure (front-loaded, formatted, hierarchical)
- [ ] Created multiple rewrite proposals with before/after analysis
- [ ] Designed testing plan to validate improvements

---

*Use this skill to enhance individual prompts for better Claude responses with fewer tokens.*
