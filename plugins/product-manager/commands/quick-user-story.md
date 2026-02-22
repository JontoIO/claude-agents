# Quick User Story Command

Produces a condensed user story spec for well-defined requirements without going through a full discovery dialogue.

## Purpose

Get a structured user story spec quickly when:
- The problem is already well-understood (no ambiguity)
- The requirement comes from an internal/dev team with full context
- You've already done the discovery work and just need the spec written up
- Time is limited and the requirement is low-risk

**Time estimate**: 5-10 min

## When to Use

**Use quick-user-story when**:
- The requirement clearly states both the problem AND the affected user
- The context is internal (dev team, engineering backlog, sprint planning)
- Scope and persona are already defined
- You don't need to explore alternative solutions
- The requirement is straightforward and unambiguous

**Use the full user-story-discovery skill when**:
- A stakeholder or external user brought the requirement
- The requirement is solution-framed ("add X") without context
- You're not sure who the user is
- The problem isn't clearly articulated
- A CEO or customer request needs proper understanding before speccing
- You want to validate whether the proposed solution is the right one

## Command Format

```
/product-manager:quick-user-story [requirement description]
```

### Examples

```
/product-manager:quick-user-story Allow admins to export the user list as a CSV from the admin dashboard
/product-manager:quick-user-story Show a warning banner when a user's subscription is about to expire in the next 7 days
/product-manager:quick-user-story Add keyboard shortcut Cmd+K to open the global search
```

## Output Format

The command produces a condensed spec — faster to write and read than the full discovery output, but covering all essential spec elements.

```markdown
## User Story: [Feature Name]

### Problem
[1-2 sentences: the problem being solved and who experiences it]

### Solution
[What will be built, in 1-3 sentences]

### User Stories
1. As a [role], I want [feature], so that [benefit].
2. As a [role], I want [feature], so that [benefit].
3. As a [role], I want [feature], so that [benefit].

### Core Requirements
- [ ] [Requirement 1]
- [ ] [Requirement 2]
- [ ] [Requirement 3]
- [ ] [Requirement 4]

### Success Metrics
- **Primary**: [Key metric with target]
- **Secondary**: [Supporting metric]
- **Leading indicator**: [Early signal to track]

### Notes
- [Edge case, assumption, or open question if any]
```

## Example Output

**Input**:
```
/product-manager:quick-user-story Allow admins to export the user list as a CSV from the admin dashboard
```

**Output**:
```markdown
## User Story: Admin User List CSV Export

### Problem
Admins managing large user bases need to analyze user data outside the product (in Excel, BI tools, or for compliance audits) but currently have no way to extract the list — forcing manual data collection or engineering requests.

### Solution
Add a "Export as CSV" button to the admin user management dashboard that downloads the current filtered user list as a CSV file.

### User Stories
1. As an admin, I want to export the full user list as a CSV, so that I can analyze user data in external tools without requesting engineering help.
2. As an admin, I want the export to reflect my current filters and search, so that I can export specific user segments (e.g., inactive users, users on a specific plan).
3. As a compliance officer, I want a timestamped export of user data, so that I can fulfill audit and regulatory reporting requirements.

### Core Requirements
- [ ] Export button visible to admin roles only (not regular users)
- [ ] CSV includes: user ID, name, email, role, plan, created date, last login, status
- [ ] Export reflects current filters/search (not always the full list)
- [ ] File named with timestamp: `users_export_YYYY-MM-DD.csv`
- [ ] Handle large lists gracefully (pagination / async download for 10k+ users)

### Success Metrics
- **Primary**: Admin support tickets requesting user data exports drop by 80%
- **Secondary**: Feature adopted by 70% of admin users within 30 days of launch
- **Leading indicator**: Export button click rate tracked from day 1

### Notes
- Confirm which user fields are safe to export (PII / GDPR considerations)
- Consider rate-limiting exports to prevent abuse (e.g., 10 exports/day per admin)
- Phase 2: scheduled / automated exports via email
```

## When Quick User Story Is Not Sufficient

If during output generation you realize:
- The persona is unclear ("which users exactly?")
- The problem isn't actually stated ("add X" with no context)
- There are multiple valid interpretations of the requirement

**Switch to the full `user-story-discovery` skill** instead of guessing. A bad spec written quickly is worse than no spec. In this case, respond:

> "This requirement needs some discovery before I can write a solid spec. Let me switch to the full user-story-discovery skill and ask a few clarifying questions first."

## Integration with Other Skills

- **user-story-discovery**: Use for ambiguous or stakeholder-sourced requirements
- **improvement-proposals**: Use when the requirement is part of a larger roadmap initiative
- **feature-impact-estimate**: Use after speccing to get a RICE score and go/no-go recommendation
