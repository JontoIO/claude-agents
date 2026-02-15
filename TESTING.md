# Testing the Claude Agents Marketplace

This document provides steps to test the marketplace and plugins before deployment.

## Pre-deployment Checklist

### Structure Validation

- [x] `.claude-plugin/marketplace.json` exists and is valid JSON
- [x] Plugin directory structure follows requirements
- [x] All required files present (plugin.json, README.md, CHANGELOG.md)
- [x] Agent files have valid YAML frontmatter
- [x] Skill files have valid YAML frontmatter
- [x] Old directory structure removed (agents/, skills/, commands/)
- [x] Git tag created for old structure (v0.9.0-pre-marketplace)

### Documentation Validation

- [x] Root README.md updated for marketplace
- [x] CONTRIBUTING.md updated with plugin guidelines
- [x] docs/creating-plugins.md created
- [x] docs/marketplace-setup.md created
- [x] Plugin README.md is comprehensive
- [x] Plugin CHANGELOG.md documents v1.0.0

## Local Testing Steps

### Step 1: Validate JSON Files

```bash
# Validate marketplace manifest
python3 -m json.tool .claude-plugin/marketplace.json

# Validate plugin manifest
python3 -m json.tool plugins/financial-advisor/.claude-plugin/plugin.json
```

Expected: Both files should be valid JSON with no syntax errors.

### Step 2: Check File Structure

```bash
# List all plugin files
find plugins -type f

# Verify directory structure
tree plugins/ -L 3  # or use ls -R plugins/
```

Expected files:
- `plugins/financial-advisor/.claude-plugin/plugin.json`
- `plugins/financial-advisor/agents/financial-advisor.md`
- `plugins/financial-advisor/skills/cost-estimation/SKILL.md`
- `plugins/financial-advisor/skills/monetization-planning/SKILL.md`
- `plugins/financial-advisor/skills/financial-risk-assessment/SKILL.md`
- `plugins/financial-advisor/skills/roi-analysis/SKILL.md`
- `plugins/financial-advisor/commands/quick-cost-estimate.md`
- `plugins/financial-advisor/examples/saas-startup.md`
- `plugins/financial-advisor/README.md`
- `plugins/financial-advisor/CHANGELOG.md`

### Step 3: Validate YAML Frontmatter

```bash
# Check agent frontmatter
head -5 plugins/financial-advisor/agents/financial-advisor.md

# Check skill frontmatter
head -5 plugins/financial-advisor/skills/cost-estimation/SKILL.md
head -5 plugins/financial-advisor/skills/monetization-planning/SKILL.md
head -5 plugins/financial-advisor/skills/financial-risk-assessment/SKILL.md
head -5 plugins/financial-advisor/skills/roi-analysis/SKILL.md
```

Expected: Each file should have valid YAML frontmatter with `name` and `description` fields.

### Step 4: Test Marketplace Installation (Local)

**Note**: This requires Claude Code to be installed and working.

```bash
# From the repository root
/plugin marketplace add ./
```

Expected: Marketplace should be added successfully. Check with `/plugin`.

### Step 5: Test Plugin Installation (Local)

```bash
# Install the financial advisor plugin
/plugin install financial-advisor@jontoio-claude-agents
```

Expected: Plugin should install without errors.

### Step 6: Verify Components

```bash
# Check if plugin appears in list
/plugin

# Check if agent appears
/agents
```

Expected:
- Plugin shows as "Installed" or "Active" in `/plugin`
- `financial-advisor` agent appears in `/agents` list

### Step 7: Test Skills

```bash
# Test each skill
/financial-advisor:cost-estimation
/financial-advisor:monetization-planning
/financial-advisor:financial-risk-assessment
/financial-advisor:roi-analysis
```

Expected: Each skill should invoke successfully and Claude should follow the skill methodology.

### Step 8: Test Commands

```bash
# Test command
/financial-advisor:quick-cost-estimate Add AI chat feature

# Test command with parameters
/financial-advisor:quick-cost-estimate Add authentication --users 1000
```

Expected: Commands should execute and provide estimates.

### Step 9: Test Examples

Follow the example in `plugins/financial-advisor/examples/saas-startup.md` and verify the results match expectations.

## GitHub Testing Steps

After pushing to GitHub:

### Step 1: Test Remote Marketplace

```bash
# Add marketplace from GitHub
/plugin marketplace add jontoIO/claude-agents
```

Expected: Marketplace should be added from the GitHub repository.

### Step 2: Test Remote Installation

```bash
# Install plugin from GitHub
/plugin install financial-advisor@jontoio-claude-agents
```

Expected: Plugin should download and install from GitHub.

### Step 3: Verify All Components

Repeat Steps 6-8 from local testing to verify everything works from the remote repository.

## Troubleshooting

### Issue: Marketplace Won't Add

**Symptoms**: Error when running `/plugin marketplace add ./`

**Checks**:
1. Verify `.claude-plugin/marketplace.json` exists
2. Validate JSON syntax
3. Check file permissions
4. Verify Claude Code is up to date

### Issue: Plugin Won't Install

**Symptoms**: Error when installing plugin

**Checks**:
1. Verify `plugins/financial-advisor/.claude-plugin/plugin.json` exists
2. Validate plugin.json syntax
3. Check marketplace manifest includes the plugin
4. Verify all required files are present

### Issue: Agent Doesn't Appear

**Symptoms**: Agent not in `/agents` list

**Checks**:
1. Verify `plugins/financial-advisor/agents/financial-advisor.md` exists
2. Check YAML frontmatter syntax
3. Ensure frontmatter has `name` and `description` fields
4. Try reinstalling plugin

### Issue: Skills Don't Work

**Symptoms**: Skills can't be invoked

**Checks**:
1. Verify skill files named `SKILL.md` (uppercase)
2. Check YAML frontmatter syntax
3. Ensure files in correct location: `skills/skill-name/SKILL.md`
4. Verify plugin is installed

### Issue: Commands Not Found

**Symptoms**: Commands can't be executed

**Checks**:
1. Verify command files in `commands/` directory
2. Check file naming matches command name
3. Ensure proper namespace: `/financial-advisor:command-name`
4. Try reinstalling plugin

## Test Results Template

Use this template to document test results:

```markdown
## Test Results - [Date]

### Environment
- Claude Code Version: [version]
- Operating System: [OS]
- Installation Type: [Local/Remote]

### Marketplace Installation
- [ ] Marketplace added successfully
- [ ] Marketplace appears in `/plugin` list

### Plugin Installation
- [ ] Plugin installed successfully
- [ ] Plugin appears in `/plugin` list as installed

### Component Verification
- [ ] Agent appears in `/agents` list
- [ ] All 4 skills can be invoked
- [ ] Command executes successfully

### Functional Testing
- [ ] Cost estimation skill works end-to-end
- [ ] Monetization planning skill works end-to-end
- [ ] Financial risk assessment skill works end-to-end
- [ ] ROI analysis skill works end-to-end
- [ ] Quick cost estimate command works

### Documentation
- [ ] README instructions are accurate
- [ ] Examples work as documented
- [ ] All links in documentation work

### Issues Found
[List any issues discovered during testing]

### Notes
[Any additional observations]
```

## Automated Checks

Consider running these automated checks before deployment:

```bash
# Validate all JSON files
find . -name "*.json" -exec python3 -m json.tool {} \; > /dev/null

# Check for required files
test -f .claude-plugin/marketplace.json || echo "Missing marketplace.json"
test -f plugins/financial-advisor/.claude-plugin/plugin.json || echo "Missing plugin.json"
test -f plugins/financial-advisor/README.md || echo "Missing plugin README"
test -f plugins/financial-advisor/CHANGELOG.md || echo "Missing CHANGELOG"

# Check YAML frontmatter exists
grep -q "^---$" plugins/financial-advisor/agents/financial-advisor.md || echo "Missing agent frontmatter"
grep -q "^---$" plugins/financial-advisor/skills/cost-estimation/SKILL.md || echo "Missing skill frontmatter"

# Check for broken markdown links (requires markdown-link-check)
# npm install -g markdown-link-check
# find . -name "*.md" -exec markdown-link-check {} \;
```

## Deployment Checklist

Before pushing to production:

- [ ] All local tests pass
- [ ] Git tag created (v0.9.0-pre-marketplace)
- [ ] Old structure removed
- [ ] Documentation complete and accurate
- [ ] JSON files validated
- [ ] YAML frontmatter validated
- [ ] All components tested individually
- [ ] End-to-end workflows tested
- [ ] Examples verified
- [ ] Links in documentation checked
- [ ] CHANGELOG updated
- [ ] Version numbers consistent

## Post-Deployment Verification

After pushing to GitHub:

1. **Fresh Clone Test**: Clone repository to a new location and test
2. **Remote Installation Test**: Test installation from GitHub URL
3. **Documentation Review**: Verify all GitHub links work
4. **Community Testing**: Have another user test the installation

## Continuous Testing

Consider setting up automated testing:

- JSON validation in CI/CD
- Link checking in CI/CD
- Markdown linting
- YAML validation
- Integration tests for Claude Code plugin system

---

**Testing completed**: [Date]
**Tested by**: [Name]
**Result**: [Pass/Fail]
