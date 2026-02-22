---
name: user-story-discovery
description: Turn raw or solution-framed requirements into proper user story specs through a 4-step interactive discovery dialogue — intake, problem discovery, solution exploration, and full spec generation
---

# User Story Discovery Skill

Interactive framework for turning raw requirements into proper user story specs through structured problem discovery dialogue.

## Purpose

Stakeholders and users often present requirements as solutions ("add a search box") rather than problems ("users can't find their data"). This skill bridges the gap between what people ask for and what they actually need.

**Core principle**: Users propose solutions. PMs understand problems. When someone says "I want feature X," a good PM asks *why* — what are they really trying to accomplish? — before jumping to spec out that solution.

Use this skill when:
- A stakeholder brings a raw requirement or idea
- Someone says "write me a user story for this"
- A requirement is framed as a solution ("add X" or "build Y")
- You need to validate whether a proposed feature solves the right problem
- A CEO/customer request needs to be properly understood before speccing

**Time estimate**: 20-40 min (depending on dialogue rounds)

---

## IMPORTANT: Interactive Dialogue Required

**Do NOT generate the user story spec until you have completed Step 2 (Problem Discovery).**

This skill requires multiple message exchanges with the stakeholder. After each step that involves questions, **stop and wait for the user's response** before proceeding to the next step. Do not attempt to infer or assume answers — ask and wait.

---

## Step 1: Requirement Intake & Classification (2-3 min)

**Objective**: Understand what was given, classify it, and identify what is still unknown.

**Actions**:
1. **Read the requirement verbatim** — capture it exactly as stated
2. **Classify the framing**:
   - _Problem Statement_: Describes a pain point or gap ("users can't find items," "we lose customers because...")
   - _Solution Proposal_: Describes a specific implementation ("add a search box," "build a dashboard," "create an export button")
   - _Hybrid_: Has both ("users can't find items — we should add search")
3. **If solution-framed**: Flag internally. Do NOT assume the proposed solution is the correct or only solution. The proposed solution will be evaluated alongside alternatives in Step 3.
4. **Note implicit assumptions**:
   - Who is the user? (stated vs. assumed)
   - What is the scope? (one persona vs. all users)
   - What is the urgency? (now vs. eventually)
   - What is the context? (product area, workflow stage)
5. **Create internal summary** (not shown to user) of what is known vs. unknown

**Classification Output** (internal — do not show to user in this form):
```
Requirement: [verbatim]
Framing: [Problem / Solution / Hybrid]
Proposed solution (if any): [description]
Implicit assumptions: [list]
Unknown: [list of what needs to be discovered]
```

---

## Step 2: Problem Discovery (10-20 min, interactive)

**Objective**: Understand the underlying problem through clarifying questions. Do not design or evaluate solutions yet.

**Actions**:
1. **Acknowledge the requirement** — show you understood it
2. **Ask 3–5 clarifying questions** focused on the *problem*, not the solution
3. **Wait for answers** before proceeding to Step 3

**Question categories** — choose the most relevant 3–5, do not ask all of them:

| Category | Example Questions |
|----------|-------------------|
| **Who** | Which user persona or role experiences this? Is this affecting all users or a specific segment? |
| **What (current state)** | What do users do today when they face this problem? What is the workaround? |
| **What (goal)** | What are they ultimately trying to accomplish? What job are they trying to get done? |
| **When / How often** | How frequently does this problem occur? In which context or workflow stage? |
| **Why now** | What triggered this request? Has something changed (competitor, customer complaint, data)? |
| **Impact** | What is the cost of NOT solving this? (time lost, revenue, churn, support tickets, manual workarounds) |
| **Success** | How would the user/stakeholder know this problem is solved? What does "done" look like? |

**If the user proposed a specific solution**, also ask:
> "You've proposed [solution]. Is this the only approach you've considered, or are you open to evaluating alternatives?"

**Question format** — present questions clearly numbered, one block at a time:

```
I'd like to understand the problem more deeply before writing the spec.

A few questions:

1. [question]
2. [question]
3. [question]
[optional: 4-5 if needed]

(Take your time — the more context you share, the better the spec will be.)
```

**After receiving answers**: Synthesize what was learned. If critical unknowns remain, ask one focused follow-up round (max 2–3 additional questions). Then proceed to Step 3.

---

## Step 3: Solution Exploration (5-10 min)

**Objective**: Generate 2–4 alternative approaches to the discovered problem, including the user-proposed solution (if any), and confirm the direction to spec.

**Actions**:
1. **Summarize the problem** in 2–3 sentences based on what was discovered in Step 2
2. **Generate 2–4 solution alternatives**:
   - Include the user-proposed solution if one was given (evaluated without bias, as one option among many)
   - Include at least 1–2 non-obvious alternatives
   - Consider: build vs. integrate, minimal vs. comprehensive, synchronous vs. asynchronous approaches
3. **For each alternative, note**:
   - What it solves
   - Trade-offs (pros/cons)
   - Rough effort level (Low / Medium / High)
4. **Present to user** and ask which direction to spec (or provide a recommendation with rationale)

**Key principle**: The user's proposed solution may still be the best one — but it must be evaluated alongside alternatives, not defaulted to. If it is genuinely the best option, recommend it with clear reasoning.

**Output format**:
```
Based on our conversation, here's my understanding of the problem:

**Problem**: [2-3 sentence synthesis]

I've identified [N] potential approaches:

**Option A: [Name]**
- What it solves: [description]
- Trade-offs: [pros/cons]
- Effort: Low / Medium / High

**Option B: [Name]**
- What it solves: [description]
- Trade-offs: [pros/cons]
- Effort: Low / Medium / High

**Option C: [Name]** *(your proposed approach)*
- What it solves: [description]
- Trade-offs: [pros/cons]
- Effort: Low / Medium / High

**My recommendation**: [Option X] because [rationale]

Which approach would you like me to spec? (Or I can proceed with my recommendation.)
```

**Wait for confirmation** before proceeding to Step 4.

---

## Step 4: User Story Documentation (10-15 min)

**Objective**: Generate the full spec for the confirmed solution approach, in the same format used across all PM skills.

**Actions**:
1. Use all information gathered in Steps 1–3
2. Write the full proposal in the template below
3. Flag any open questions or gaps that remain unresolved

**Output format** — use the `Proposal N: [Name]` template consistent with the `improvement-proposals` skill:

---

### Proposal 1: [Feature Name]
**Origin: User Story Discovery | Priority: [P0/P1/P2 based on urgency/impact]**

#### Executive Summary
[2-3 sentences: what the feature is, the core problem it solves, and the expected outcome]

#### Problem Statement
**User Pain Point**: [The underlying problem, framed from the user's perspective]

**Evidence from Discovery**:
- Who experiences it: [persona/segment]
- Current workaround: [what they do today]
- Frequency: [how often this occurs]
- Trigger: [what prompted this request]

**Business Impact**: [Cost of not solving this — time, revenue, churn, etc.]

#### Solution Overview
**What**: [What will be built — the chosen approach]

**Why this approach**: [Rationale for choosing this option over alternatives considered]

**Alternatives evaluated**:
- [Option A]: [1-line summary of why not chosen]
- [Option B]: [1-line summary of why not chosen]
- *(if user-proposed solution was not selected, explain why; if it was selected, note that it was evaluated alongside alternatives)*

#### Success Metrics
**Primary**:
- [Metric 1]: [current state] → [target]
- [Metric 2]: [current state] → [target]

**Secondary**:
- [Metric 3]
- [Metric 4]

**Leading Indicators** (track weekly):
- [Indicator 1]
- [Indicator 2]

#### Target Personas
- **Primary**: [Persona name] — [brief description of why they are the primary beneficiary]
- **Secondary**: [Persona name] — [brief description]

#### User Stories

*As a [role], I want [feature/capability], so that [benefit/outcome].*

1. As a [role], I want [feature], so that [benefit].
2. As a [role], I want [feature], so that [benefit].
3. As a [role], I want [feature], so that [benefit].
4. *(optional)* As a [role], I want [feature], so that [benefit].
5. *(optional)* As a [role], I want [feature], so that [benefit].

#### Feature Requirements

**Core / Must-Have (Phase 1)**:
- [ ] [Requirement 1]
- [ ] [Requirement 2]
- [ ] [Requirement 3]
- [ ] [Requirement 4]

**Enhanced / Phase 2**:
- [ ] [Enhancement 1]
- [ ] [Enhancement 2]
- [ ] [Enhancement 3]

#### Technical Requirements
- [Technical constraint or requirement 1]
- [Technical constraint or requirement 2]
- [Performance / security / scalability considerations]

#### User Experience Notes
- [UX consideration 1 — e.g., where this fits in the existing flow]
- [UX consideration 2 — e.g., edge cases, error states]
- [Accessibility or mobile considerations if relevant]

#### Risk Assessment

**Risk 1: [Name]**
- Likelihood: Low / Medium / High
- Impact: Low / Medium / High
- Mitigation: [how to address]

**Risk 2: [Name]**
- Likelihood: Low / Medium / High
- Impact: Low / Medium / High
- Mitigation: [how to address]

#### Open Questions
- [ ] [Unresolved question 1 — e.g., needs validation, needs engineering input]
- [ ] [Unresolved question 2]

#### Dependencies
- [Dependency 1 — e.g., another feature, third-party service, infrastructure change]
- [Dependency 2]

#### Timeline Estimate
**Development Time**: [N weeks]
- [Breakdown: design, build, QA, launch]

**Resources**:
- [Role 1]: [time estimate]
- [Role 2]: [time estimate]

**Complexity**: Low / Medium / High — [brief explanation]

#### Go/No-Go Recommendation
**[✅ GO / ⚠️ GO with conditions / ❌ NO-GO] — [one-line verdict]**

**Rationale**:
- [Reason 1]
- [Reason 2]
- [Reason 3]

**Decision**: [Recommended priority and timing]

---

## Quality Checklist

Before delivering the spec, verify:

- [ ] The spec addresses the *problem* discovered in Step 2 — not just the initially proposed solution
- [ ] At least 2 alternatives were evaluated and documented
- [ ] User stories follow the format: "As a [role], I want [feature], so that [benefit]"
- [ ] Success metrics include at least one primary, one secondary, and one leading indicator
- [ ] Open questions are documented (not hidden or glossed over)
- [ ] If the user's originally proposed solution was chosen, the rationale is explicit (not implied)
- [ ] If the user's originally proposed solution was NOT chosen, the explanation is respectful and evidence-based

---

## Example Dialogue Flow

**Stakeholder**: "I want to add a PDF export button."

**Step 1 classification** (internal): Solution Proposal. The underlying problem is unknown. Implicit assumption: users want to share or archive content.

**Step 2 questions** (shown to user):
> I'd like to understand the problem before writing the spec.
>
> 1. Who is asking for this — which users or teams?
> 2. What are they trying to do when they want to export a PDF? (Share with external stakeholders? Archive a record? Print it?)
> 3. What do they do today when this need arises? (Copy-paste? Screenshot? Something else?)
> 4. How often does this come up? Is there urgency?
> 5. You've proposed PDF export — are you open to evaluating other approaches too?

**Stakeholder answers**: Sales team exports proposals to share with clients who don't have accounts. Currently copying text into Word. Several deals lost because format looks unprofessional. Happens 5-10x per day per salesperson. Open to alternatives.

**Step 3 alternatives** (shown to user):
> **Option A: PDF Export** (your proposed approach) — direct download. Solves the formatting problem. Medium effort. Doesn't require client to have an account.
>
> **Option B: Shareable Read-Only Link** — generate a public link clients can view in-browser without an account. Low effort, no formatting issues. Doesn't work offline.
>
> **Option C: Email Delivery** — send formatted proposal directly via email. Low-medium effort. Keeps client in their email workflow.
>
> **Recommendation**: Option B (shareable link) solves the core problem (sharing with external stakeholders without an account) with less effort and better mobile experience. PDF adds value as Phase 2 for clients who explicitly need offline/archival copies.

**Step 4**: Generate full spec for shareable read-only link, with PDF export documented as Phase 2 enhancement.

---

## Integration with Other Skills

- **improvement-proposals**: If the discovery reveals a systemic problem affecting many users, escalate to improvement-proposals for full prioritization and roadmap placement
- **persona-definition**: If the persona is unclear or undocumented, use persona-definition to properly define who this is for
- **competitive-intelligence**: If alternatives depend on competitive context ("does any competitor do this better?"), pull in competitive-intelligence data
