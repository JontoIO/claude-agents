---
name: memory-efficiency-analysis
description: Optimize MEMORY.md and context management using 6-step framework to improve recall quality, reduce redundancy, and enhance Claude's cross-session understanding
---

# Memory Efficiency Analysis Skill

Analyze and optimize MEMORY.md files and memory management strategies to improve Claude's recall quality, reduce token waste, and enhance cross-session context understanding.

## When to Use This Skill

Use this skill when you need to:
- Optimize MEMORY.md files for better recall and efficiency
- Improve Claude's cross-session context retention
- Reduce redundant or outdated memory content
- Organize memory for faster scanning and comprehension
- Enhance memory quality through better structure
- Reduce memory token consumption
- Improve memory-based decision making

## 6-Step Memory Efficiency Analysis Framework

### Step 1: Memory Discovery & Baseline (5 min)

**Objective**: Understand current memory state and usage

**Actions**:
1. Locate all memory files (MEMORY.md, .claude/memory/, auto-memory/)
2. Calculate token counts and file sizes
3. Analyze memory structure (flat, hierarchical, topic-based)
4. Review memory content quality (specific vs vague, actionable vs commentary)
5. Identify when memory was last updated

**Output**: Memory inventory with baseline metrics

### Step 2: Content Quality Audit (10 min)

**Objective**: Assess memory content usefulness and accuracy

**Actions**:
1. **Relevance Check**: Is memory still applicable? Outdated info to remove?
2. **Specificity Check**: Vague statements vs specific actionable patterns
3. **Redundancy Check**: Duplicated information across memory files
4. **Accuracy Check**: Verify memory against current codebase state
5. **Utility Check**: Which memories are actually used? Which are ignored?

**Output**: Quality assessment with improvement opportunities

### Step 3: Organization Analysis (8 min)

**Objective**: Evaluate memory structure for scannability

**Actions**:
1. Assess current organization (chronological, topical, random)
2. Identify hard-to-find information (poor categorization)
3. Check memory hierarchy (sections, subsections, clear headers)
4. Evaluate length (too long for MEMORY.md = truncation risk)
5. Find opportunities for topic files (separate detailed notes)

**Output**: Structure recommendations for better organization

### Step 4: Token Efficiency Assessment (7 min)

**Objective**: Reduce memory token consumption

**Actions**:
1. Find verbose memory entries (unnecessary detail)
2. Identify redundant explanations (repeated patterns)
3. Locate obvious context (things Claude already knows)
4. Calculate token savings from compression
5. Balance brevity with specificity (don't lose useful detail)

**Output**: Token optimization opportunities with estimated savings

### Step 5: Recall Improvement Strategies (6 min)

**Objective**: Enhance Claude's ability to use memory effectively

**Actions**:
1. **Front-Load Critical Info**: Most important patterns first
2. **Use Clear Headers**: Enable quick scanning for relevant sections
3. **Add Context Triggers**: When to apply each memory pattern
4. **Include Examples**: Show concrete applications
5. **Link to Source**: Reference files/locations for verification

**Output**: Recall enhancement recommendations

### Step 6: Implementation Plan (4 min)

**Objective**: Create action plan for memory optimization

**Actions**:
1. Prioritize improvements (high-impact first)
2. Plan reorganization (topic files, hierarchy, front-loading)
3. Define update cadence (when to refresh memory)
4. Set quality standards (what belongs in memory vs docs)
5. Create maintenance checklist

**Output**: Prioritized implementation roadmap

---

## Example Output Summary

### Memory Efficiency Analysis Summary

**Baseline**: MEMORY.md (3,200 tokens), 4 topic files (1,800 tokens) = 5,000 tokens total

**Quality Issues**:
- 12 outdated entries (old patterns no longer used)
- 8 vague statements ("be careful with X" without specifics)
- 6 redundant entries (same pattern repeated)
- Poor organization (chronological, hard to find topics)

**Optimization Opportunities**:
- Remove outdated: -800 tokens
- Specify vague entries: +200 tokens (adds value)
- Deduplicate: -400 tokens
- Reorganize by topic: 0 tokens (structure improvement)
- Front-load critical info: 0 tokens (recall improvement)

**Net Impact**: -1,000 tokens (20% reduction), +40% recall quality

**Top Recommendations**:
1. Remove 12 outdated entries (30 min, -800 tokens)
2. Reorganize by topic with clear headers (45 min, +40% findability)
3. Specify 8 vague entries (30 min, +200 tokens but +60% usefulness)

---

## Quality Checklist

- [ ] Discovered all memory files and calculated baseline
- [ ] Audited content quality (relevance, specificity, accuracy)
- [ ] Analyzed organization and structure
- [ ] Identified token efficiency opportunities
- [ ] Designed recall improvement strategies
- [ ] Created prioritized implementation plan

---

*Use this skill to optimize memory management for better recall, efficiency, and cross-session understanding.*
