# Workflow Reference

Technical documentation for all automated workflows in the Sunny Acres Farm repository.

## Overview

This repository uses two types of workflows:

1. **Standard GitHub Actions** (`.yml` files) - Traditional scripted workflows
2. **Agentic Workflows** (`.md` files) - AI-powered adaptive workflows

## Standard Workflows

### Weekly Farm Reminder

**File:** `.github/workflows/weekly-reminder.yml`

**Trigger:**
- Schedule: Every Monday at 8:00 AM UTC
- Manual: workflow_dispatch

**Permissions:**
- `issues: write`

**What it does:**

1. Calculates current week number
2. Creates an Issue with weekly checklist
3. Applies labels: `routine`, `maintenance`
4. Includes sections for:
   - Equipment checks
   - Livestock monitoring
   - Crop/field scouting
   - Administrative tasks

**Customization:**

To modify the checklist, edit lines 37-63:

````yaml
body: `## Weekly Farm Checklist
- [ ] Your custom task here
`
````

**Schedule modification:**

Change the cron expression on line 13:

````yaml
- cron: '0 8 * * 1'  # minute hour day month day-of-week
````

**Common schedules:**
- `0 8 * * 1` - Monday 8 AM UTC
- `0 6 * * 1` - Monday 6 AM UTC  
- `0 8 * * 0` - Sunday 8 AM UTC
- `0 8 1 * *` - First day of month 8 AM UTC

---

### Dependabot Auto-Merge

**File:** `.github/workflows/dependabot-automerge.yml`

**Trigger:**
- pull_request_target: opened, synchronize, reopened

**Permissions:**
- `contents: write`
- `pull-requests: write`

**What it does:**

1. Detects Dependabot pull requests
2. Waits for CI checks to pass
3. Automatically approves the PR
4. Enables auto-merge
5. Merges when all checks pass

**Uses reusable workflow:**

````yaml
uses: zircote/.github/.github/workflows/reusable-dependabot-automerge.yml@main
````

**Security:**

- Only works for Dependabot PRs
- Requires CI checks to pass
- Respects branch protection rules
- Only merges patch/minor updates (configurable)

**Repository settings required:**

1. Enable "Allow auto-merge" in repository settings
2. Configure branch protection for main branch
3. Require status checks before merging

---

## Agentic Workflows

Agentic workflows use AI to understand context and make intelligent decisions. They are defined in Markdown files and compiled to `.lock.yml` files.

### Source and Compilation

**Source:** `githubnext/agentics/workflows/`

Each `.md` file includes:

````yaml
source: githubnext/agentics/workflows/<name>.md@<commit-hash>
````

**Compilation:**

After editing a `.md` workflow, recompile:

````bash
gh aw compile
````

This updates the corresponding `.lock.yml` file.

**Important:** Never edit `.lock.yml` files directly. They are auto-generated.

---

### Issue Triage

**File:** `.github/workflows/issue-triage.md`

**Trigger:**
- issues: opened
- workflow_dispatch

**Permissions:** read-all

**Safe outputs:**
- create-issue
- create-issue-comment
- Labels: `automation`

**Tools:**
- GitHub: all toolsets
- Bash: enabled

**Timeout:** 15 minutes

**What it does:**

1. Reads new Issue content
2. Analyzes title and description
3. Determines appropriate domain (crops, livestock, equipment, compliance)
4. Identifies type (maintenance, repair, inspection, etc.)
5. Assesses priority (urgent, routine, seasonal)
6. Suggests labels via comment
7. Can auto-apply labels if configured
8. May assign to team members based on area

**Customization:**

Edit the Job Description section in `issue-triage.md` to:
- Adjust label suggestions
- Modify assignment logic
- Add custom triage rules
- Change priority thresholds

**Example custom instruction:**

````markdown
## Custom Rules

- Always mark "water" issues as urgent
- Assign livestock issues to @farmmanager
- Tag seasonal issues with the current season
````

---

### Daily QA

**File:** `.github/workflows/daily-qa.md`

**Trigger:**
- schedule: Daily at 2:00 AM UTC
- workflow_dispatch

**Permissions:** read-all

**Safe outputs:**
- create-issue
- Labels: `automation`, `qa`

**Tools:**
- GitHub: all toolsets
- Web-fetch
- Bash: enabled

**Timeout:** 30 minutes

**What it does:**

1. **Documentation Checks:**
   - Validates all markdown files
   - Checks for broken links
   - Verifies file references
   - Ensures formatting consistency

2. **Data Quality Checks:**
   - Checks for required fields in records
   - Validates dates are in correct format
   - Ensures cross-references are accurate
   - Identifies missing metadata

3. **Compliance Checks:**
   - Flags approaching deadlines
   - Identifies expired certifications
   - Validates grant reporting dates
   - Checks required documentation exists

4. **Creates Issues:**
   - One Issue per problem found
   - Labels: `automation`, `qa`, and relevant domain
   - Includes fix suggestions
   - References affected files

**Customization:**

Add custom checks in the Job Description:

````markdown
## Custom QA Rules

- Verify planting dates are within season windows
- Check animal IDs follow format: [Type][Number] (e.g., BC001)
- Ensure equipment hours are incrementing
- Flag maintenance overdue by >30 days
````

---

### Update Docs

**File:** `.github/workflows/update-docs.md`

**Trigger:**
- push: branches [main]
- workflow_dispatch

**Permissions:** read-all

**Safe outputs:**
- create-pull-request
- Draft: true
- Labels: `automation`, `documentation`

**Tools:**
- GitHub: all toolsets
- Web-fetch
- Bash: enabled

**Timeout:** 15 minutes

**What it does:**

1. **Analyzes Changes:**
   - Detects files modified in last push
   - Identifies new functionality or data
   - Determines impact on documentation

2. **Identifies Documentation Gaps:**
   - Checks if related docs exist
   - Verifies docs are up-to-date
   - Identifies missing cross-references
   - Finds outdated examples

3. **Updates Documentation:**
   - Modifies affected documentation files
   - Adds new sections as needed
   - Updates cross-references
   - Maintains consistent style

4. **Creates Pull Request:**
   - Draft PR with documentation changes
   - Clear description of what was updated
   - Links to the original changes
   - Labels: `automation`, `documentation`

**Documentation Standards:**

The workflow follows:
- **Diátaxis framework:** Tutorials, how-to guides, reference, explanation
- **Google Developer Style Guide:** Clear, concise, active voice
- **Microsoft Writing Style Guide:** Accessibility and inclusivity
- **Progressive disclosure:** High-level first, details second

**Customization:**

Customize the Job Description section to:
- Add farm-specific documentation rules
- Define custom documentation structure
- Specify required sections
- Set style preferences

**Example:**

````markdown
## Farm Documentation Rules

- Always include field names in crop documentation
- Use YYYY-MM-DD date format
- Include animal IDs in livestock records
- Specify equipment model and serial numbers
````

---

### CI Doctor

**File:** `.github/workflows/ci-doctor.md`

**Trigger:**
- workflow_run: completed (on failure)
- workflow_dispatch

**Permissions:** read-all

**Safe outputs:**
- create-issue
- Labels: `automation`, `ci`

**Tools:**
- GitHub: all toolsets
- Bash: enabled

**Timeout:** 15 minutes

**What it does:**

1. **Detects Workflow Failures:**
   - Monitors all workflow runs
   - Triggers when any workflow fails
   - Retrieves failure logs

2. **Diagnoses Problems:**
   - Analyzes error messages
   - Identifies common issues:
     - Permission problems
     - Missing secrets
     - Syntax errors
     - Timeout issues
     - Dependency failures

3. **Suggests Fixes:**
   - Provides specific remediation steps
   - Links to relevant documentation
   - Offers configuration examples
   - Recommends preventive measures

4. **Creates Issues:**
   - One Issue per failing workflow
   - Labels: `automation`, `ci`
   - Includes error logs
   - Suggests fixes

**Common Issues Diagnosed:**

| Problem | Suggested Fix |
|---------|--------------|
| Permission denied | Update workflow permissions |
| Secret not found | Add secret in repository settings |
| Timeout | Increase timeout-minutes |
| Syntax error | Link to line with syntax problem |
| Dependency failure | Update dependency versions |

**Customization:**

Add farm-specific CI rules:

````markdown
## Custom CI Rules

- If weekly reminder fails, notify @farmmanager
- Timeout after 10 minutes for QA checks
- Retry failed workflows once before creating Issue
````

---

### Q (Query Assistant)

**File:** `.github/workflows/q.md`

**Trigger:**
- issues: opened (with `/q` command)
- issue_comment: created (with `/q` command)
- workflow_dispatch

**Permissions:** read-all

**Safe outputs:**
- create-issue-comment
- Labels: `automation`

**Tools:**
- GitHub: all toolsets
- Web-fetch
- Bash: enabled

**Timeout:** 10 minutes

**What it does:**

1. **Responds to Queries:**
   - Detects `/q` command in Issues or comments
   - Understands natural language questions
   - Searches repository for relevant information
   - Provides helpful answers

2. **Use Cases:**
   - "What's the planting schedule for North Field?"
   - "When was the last oil change for the tractor?"
   - "Who is responsible for livestock health records?"
   - "What grants are due this month?"

3. **Provides Context:**
   - Links to relevant files
   - Cites specific lines or sections
   - Offers related documentation
   - Suggests next steps

**Using Q:**

In any Issue or comment, type:

````markdown
/q When is the next vet visit scheduled?
````

Q will respond with:

````markdown
Based on `livestock/veterinary-log.md`, the next scheduled vet visit is:

**Date:** 2026-03-15
**Purpose:** Spring vaccinations for cattle herd
**Veterinarian:** Dr. Sarah Johnson

See [veterinary-log.md](../livestock/veterinary-log.md#line-42) for details.
````

**Customization:**

Add farm-specific knowledge:

````markdown
## Q Knowledge Base

- Tractor mechanic: Mike's Repair, (555) 123-4567
- Preferred vet: Dr. Johnson, (555) 234-5678
- Seed supplier: County Farm Supply
- Parts vendor: AgriParts Direct
````

---

## Workflow Configuration Reference

### Common Settings

#### Network Access

````yaml
network: defaults
````

Options:
- `defaults` - Standard GitHub Actions network
- `none` - No network access
- `full` - Unrestricted (not recommended)

#### Timeout

````yaml
timeout-minutes: 15
````

Recommended timeouts:
- Simple checks: 5-10 minutes
- Quality assurance: 15-30 minutes
- Complex analysis: 30-60 minutes

#### Tools Configuration

````yaml
tools:
  github:
    toolsets: [all]  # or [repos, issues, pull_requests, etc.]
  web-fetch:
  bash: true
````

Available GitHub toolsets:
- `repos` - Repository operations
- `issues` - Issue management
- `pull_requests` - PR operations
- `actions` - Workflow management
- `all` - Everything

#### Safe Outputs

````yaml
safe-outputs:
  create-pull-request:
    draft: true
    labels: [automation, documentation]
  create-issue:
    labels: [automation, qa]
````

Available safe outputs:
- `create-pull-request`
- `create-issue`
- `create-issue-comment`
- `noop` (status message)

---

## Workflow Labels

All automated workflows apply these labels:

| Label | Applied By | Purpose |
|-------|-----------|---------|
| `automation` | All workflows | Identifies automated creation |
| `documentation` | Update Docs | Documentation changes |
| `qa` | Daily QA | Quality assurance Issues |
| `ci` | CI Doctor | Workflow health Issues |
| `dependencies` | Dependabot | Dependency updates |

---

## Troubleshooting Workflows

### Workflow Won't Run

**Check:**

1. **Is it enabled?**
   - Actions tab → Select workflow → Check if disabled

2. **Are permissions correct?**
   - Verify workflow file permissions block
   - Check repository settings → Actions → General

3. **Is trigger correct?**
   - Verify trigger event matches expectations
   - Check if conditions are met (e.g., specific branch)

4. **Repository settings:**
   - Actions tab → Settings → Allow all actions

### Workflow Fails

**Debugging steps:**

1. **View logs:**
   - Actions tab → Failed run → Click job → Expand steps

2. **Check error message:**
   - Look for red X icons
   - Read error output
   - Note the failing step

3. **Common fixes:**

   **Permission denied:**
   ````yaml
   permissions:
     issues: write  # Add missing permission
   ````

   **Timeout:**
   ````yaml
   timeout-minutes: 30  # Increase from 15
   ````

   **Missing secret:**
   - Settings → Secrets and variables → Actions → New secret

4. **Re-run workflow:**
   - Actions tab → Failed run → Re-run jobs

### Agentic Workflow Issues

**Compilation errors:**

````bash
# Validate markdown syntax
gh aw validate

# Recompile all workflows
gh aw compile

# Compile specific workflow
gh aw compile .github/workflows/update-docs.md
````

**Runtime issues:**

1. Check `.lock.yml` file is up-to-date
2. Verify source reference is valid
3. Test with workflow_dispatch trigger
4. Review job logs for AI decisions

---

## Modifying Workflows

### Editing Standard Workflows

1. Create a branch: `git checkout -b workflow/update-weekly-reminder`
2. Edit the `.yml` file
3. Test with workflow_dispatch
4. Create Pull Request
5. Review and merge

### Editing Agentic Workflows

1. Create a branch: `git checkout -b workflow/update-issue-triage`
2. Edit the `.md` file (NOT the `.lock.yml`)
3. Compile: `gh aw compile`
4. Commit both `.md` and updated `.lock.yml`
5. Test with workflow_dispatch
6. Create Pull Request
7. Review and merge

**Important:** Always commit both the `.md` source and compiled `.lock.yml` file.

---

## Workflow Best Practices

### Do:

✅ **Test changes** with workflow_dispatch before merging  
✅ **Use descriptive names** for workflow files  
✅ **Set appropriate timeouts** to avoid hanging  
✅ **Include error handling** in custom scripts  
✅ **Document customizations** in comments  
✅ **Version control workflows** with pull requests  

### Don't:

❌ **Edit `.lock.yml` directly** - Edit `.md` and recompile  
❌ **Use overly broad permissions** - Grant minimum required  
❌ **Skip testing** - Always test workflow changes  
❌ **Hardcode secrets** - Use repository secrets  
❌ **Set excessive timeouts** - Keep under 60 minutes  
❌ **Ignore failed workflows** - Investigate and fix  

---

## Advanced Customization

### Adding Custom Workflow

1. **Choose type:**
   - Standard for simple, scripted logic
   - Agentic for context-aware, adaptive behavior

2. **Create file:**
   - `.github/workflows/my-workflow.yml` (standard)
   - `.github/workflows/my-workflow.md` (agentic)

3. **Define trigger and permissions**

4. **Write job logic**

5. **Test thoroughly**

6. **Document in this reference**

### Workflow Composition

Combine multiple workflows for complex automation:

````yaml
jobs:
  call-qa:
    uses: ./.github/workflows/daily-qa.md
  
  call-docs:
    uses: ./.github/workflows/update-docs.md
    needs: call-qa
````

---

## Security Considerations

### Permissions

Always use minimum required permissions:

````yaml
permissions:
  contents: read    # Default: read-only
  issues: write     # Only if creating/updating Issues
  pull-requests: write  # Only if creating/updating PRs
````

### Secrets

Never hardcode sensitive data:

````yaml
# ❌ Wrong
env:
  API_KEY: "abc123secret"

# ✅ Correct
env:
  API_KEY: ${{ secrets.API_KEY }}
````

### Third-party Actions

Agentic workflows use trusted sources:

````yaml
source: githubnext/agentics/workflows/update-docs.md@<commit-hash>
````

Always pin to specific commit hash, not branch.

---

## Monitoring and Maintenance

### Weekly Checks

- Review Actions tab for failed workflows
- Check for CI Doctor Issues
- Verify scheduled workflows are running
- Review automated PRs and Issues

### Monthly Maintenance

- Update workflow dependencies
- Review and update schedules
- Assess automation effectiveness
- Update documentation
- Archive resolved automation Issues

### Quarterly Reviews

- Evaluate workflow performance
- Gather user feedback
- Identify improvement opportunities
- Update workflow configurations
- Train team on new features

---

## Getting Help

### Workflow Issues

- Create Issue labeled `automation`, `question`
- Include workflow name and run ID
- Attach error logs
- Describe expected vs. actual behavior

### Enhancement Requests

- Start a Discussion
- Describe desired automation
- Explain use case
- Suggest implementation approach

### Documentation

- [GitHub Actions Documentation](https://docs.github.com/actions)
- [Workflow Syntax Reference](https://docs.github.com/actions/using-workflows/workflow-syntax-for-github-actions)
- [Agentic Workflows Documentation](https://githubnext.com/projects/agentic-workflows)

---

## Related Documentation

- [Automation Overview](./automation-overview.md) - User-friendly automation guide
- [Getting Started](./getting-started.md) - Repository basics
- [Labels Guide](./labels-guide.md) - Label system reference
