# Automation Overview

The Sunny Acres Farm repository includes several automated workflows that help manage farm operations, maintain data quality, and streamline collaboration. This guide explains what automation exists and how it helps.

## Why Automation?

Farm management involves repetitive tasks, routine checks, and timely reminders. Automation helps by:

- **Reducing manual overhead** - Automatic reminders and checks
- **Ensuring consistency** - Standard processes every time
- **Catching issues early** - Quality checks on every change
- **Saving time** - Less time on administration, more on farming

## Automated Workflows

### 1. Weekly Farm Reminder

**Purpose:** Creates a weekly checklist every Monday morning

**What it does:**
- Runs every Monday at 8:00 AM UTC
- Creates an Issue with a farm task checklist
- Labels it `routine` and `maintenance`
- Includes equipment, livestock, crops, and administrative checks

**How to use it:**
1. Check for the weekly Issue each Monday
2. Work through the checklist
3. Check off items as completed
4. Close the Issue when done or roll tasks to next week

**Example Issue:**
````markdown
Title: Weekly Farm Check - Week 7

Labels: routine, maintenance

## Weekly Farm Checklist
- [ ] Check fluid levels on all tractors
- [ ] Verify all water sources are working
- [ ] Scout fields for pest or disease signs
- [ ] Review any open issues from last week
````

**Triggering manually:**
- Go to **Actions** tab
- Select "Weekly Farm Reminder"
- Click **Run workflow**

---

### 2. Issue Triage

**Purpose:** Automatically categorizes and prioritizes new Issues

**What it does:**
- Runs when a new Issue is created
- Analyzes the Issue title and description
- Suggests appropriate labels (domain, type, priority)
- Adds helpful comments with guidance
- Can assign Issues to team members based on area

**How it helps:**
- Ensures Issues are properly labeled
- Routes Issues to the right people
- Identifies urgent matters quickly
- Maintains organization automatically

**What you'll see:**
After creating an Issue, the bot may add:
- Suggested labels
- A comment explaining the triage
- Assignment to a relevant team member

**Note:** You can modify the automated suggestions if they're incorrect.

---

### 3. Daily QA (Quality Assurance)

**Purpose:** Performs nightly data quality checks

**What it does:**
- Runs daily at 2:00 AM UTC
- Checks for common issues:
  - Broken links in documentation
  - Missing required fields in records
  - Outdated information (e.g., expired certifications)
  - Inconsistent formatting
  - Missing cross-references
- Creates Issues for problems found
- Labels them `automation` and `qa`

**How it helps:**
- Catches data drift before it becomes a problem
- Maintains documentation accuracy
- Flags outdated compliance records
- Ensures file integrity

**What you'll see:**
Issues created by Daily QA might look like:
````markdown
Title: [QA] Broken link in equipment/maintenance-log.md

Labels: automation, qa, equipment, documentation

The link to the parts vendor catalog is broken.
Please update or remove it.
````

**Responding to QA Issues:**
1. Review the identified problem
2. Fix the issue
3. Close the QA Issue
4. The next nightly run will verify the fix

---

### 4. Update Docs

**Purpose:** Keeps documentation synchronized with repository changes

**What it does:**
- Runs on every push to the main branch
- Analyzes what changed
- Identifies documentation that needs updates
- Creates a Pull Request with suggested documentation changes
- Labels PRs as `automation` and `documentation`

**How it helps:**
- Documentation stays current
- Reduces manual documentation work
- Ensures changes are reflected in guides
- Maintains single source of truth

**What you'll see:**
After merging changes, you may see a draft PR:
````markdown
Title: Update docs to reflect new planting schedule structure

Labels: automation, documentation

## Changes
- Updated crops/README.md to reflect new schedule format
- Added section to getting-started.md about scheduling
- Cross-referenced new fields in planting-schedule.md
````

**Responding to doc updates:**
1. Review the suggested changes
2. Make any needed adjustments
3. Mark the PR as "Ready for review"
4. Merge when approved

---

### 5. CI Doctor

**Purpose:** Monitors the health of automated workflows themselves

**What it does:**
- Runs when workflows fail
- Diagnoses common workflow problems
- Suggests fixes for failures
- Creates Issues for recurring problems
- Labels them `automation` and `ci`

**How it helps:**
- Keeps automation working smoothly
- Identifies configuration problems
- Provides troubleshooting guidance
- Maintains workflow reliability

**What you'll see:**
Issues from CI Doctor look like:
````markdown
Title: [CI] Weekly Reminder workflow failed

Labels: automation, ci

The weekly reminder workflow failed due to permissions.
Suggested fix: Update workflow permissions in .github/workflows/weekly-reminder.yml
````

**Responding to CI issues:**
- Repository maintainers will typically handle these
- You may be asked to re-run a failed workflow
- Report repeated failures in Discussions

---

### 6. Dependabot Auto-Merge

**Purpose:** Automatically updates and merges dependency updates

**What it does:**
- Monitors for security updates
- Automatically approves and merges safe updates
- Requires CI checks to pass first
- Focuses on patch and minor version updates

**How it helps:**
- Keeps dependencies secure
- Reduces manual update burden
- Maintains compatibility
- Prevents security vulnerabilities

**What you'll see:**
Dependabot may create PRs like:
````markdown
Title: Bump actions/checkout from 3.5.0 to 3.5.2

Labels: dependencies

Automatically merged after CI passed.
````

**When it won't auto-merge:**
- Major version updates (require manual review)
- Breaking changes detected
- CI checks fail
- Conflicts with other changes

---

## Workflow Labels

Automated workflows use specific labels:

| Label | Applied By | Meaning |
|-------|-----------|---------|
| `automation` | All workflows | Created by automation |
| `documentation` | Update Docs | Documentation changes |
| `qa` | Daily QA | Quality assurance issue |
| `ci` | CI Doctor | Workflow health issue |
| `dependencies` | Dependabot | Dependency update |

**Tip:** Filter Issues by `label:automation` to see all automated activity.

## Viewing Workflow Runs

### See Recent Workflow Activity

1. Go to the **Actions** tab
2. View all recent workflow runs
3. Click any run for detailed logs
4. Check status: ✅ Success, ❌ Failed, 🔄 In Progress

### Check a Specific Workflow

1. **Actions** tab → Left sidebar
2. Select workflow (e.g., "Weekly Farm Reminder")
3. View run history
4. See success rate and timing

### Manually Trigger Workflows

Some workflows can be run manually:

1. **Actions** tab
2. Select the workflow
3. Click **Run workflow** button
4. Choose branch (usually `main`)
5. Click **Run workflow**

**Manually triggerable workflows:**
- Weekly Farm Reminder
- Daily QA
- Update Docs

## Understanding Workflow Files

Workflows are defined in `.github/workflows/`:

| File | Type | Purpose |
|------|------|---------|
| `weekly-reminder.yml` | Standard | Creates weekly checklists |
| `dependabot-automerge.yml` | Standard | Auto-merges dependencies |
| `issue-triage.md` | Agentic | AI-powered issue categorization |
| `daily-qa.md` | Agentic | Intelligent quality checks |
| `update-docs.md` | Agentic | Smart documentation updates |
| `ci-doctor.md` | Agentic | Workflow health diagnostics |
| `q.md` | Agentic | General query and assistance |

### Standard vs. Agentic Workflows

**Standard workflows** (`.yml` files):
- Traditional GitHub Actions
- Follow scripted logic
- Predictable behavior
- Fast execution

**Agentic workflows** (`.md` files):
- AI-powered automation
- Understand context and intent
- Adaptive responses
- More intelligent decisions

## Workflow Schedule

| Workflow | When it Runs |
|----------|-------------|
| Weekly Reminder | Every Monday, 8:00 AM UTC |
| Daily QA | Every day, 2:00 AM UTC |
| Issue Triage | On new Issue creation |
| Update Docs | On push to main branch |
| CI Doctor | When workflows fail |
| Dependabot | Weekly, or when updates available |

## Customizing Automation

### Adjusting the Weekly Checklist

Edit `.github/workflows/weekly-reminder.yml`:

1. Create a branch
2. Edit the `body:` section (lines 37-63)
3. Add, remove, or modify checklist items
4. Submit a Pull Request
5. Test the changes

### Changing Workflow Schedules

Edit the `cron:` line in workflow files:

````yaml
schedule:
  - cron: '0 8 * * 1'  # Monday at 8 AM UTC
````

**Cron format:** `minute hour day-of-month month day-of-week`

**Examples:**
- `0 8 * * 1` - Every Monday at 8 AM
- `0 2 * * *` - Every day at 2 AM
- `0 0 * * 0` - Every Sunday at midnight

**Important:** Use UTC time zone.

### Disabling a Workflow

To temporarily disable:

1. Go to **Actions** tab
2. Select the workflow
3. Click **⋯** (three dots)
4. Click **Disable workflow**

Re-enable the same way.

## Best Practices

### Do:

✅ **Review automated Issues** - Don't ignore them  
✅ **Close Issues when resolved** - Keep things tidy  
✅ **Provide feedback** - Comment if automation is wrong  
✅ **Check Actions tab** - Monitor workflow health  
✅ **Update templates** - Keep checklists relevant  

### Don't:

❌ **Auto-close automation Issues** - Review them first  
❌ **Ignore failed workflows** - They may need attention  
❌ **Delete automated PRs** - Review and merge or decline  
❌ **Disable workflows permanently** - Discuss alternatives first  

## Troubleshooting

### Workflow Didn't Run

**Check:**
1. Is the workflow enabled? (Actions tab)
2. Was the trigger condition met? (e.g., Monday for weekly reminder)
3. Are there permission issues? (Check CI Doctor)
4. Is the repository active? (Disabled on inactive repos)

### Automated Issue is Wrong

**If automation mislabeled an Issue:**
1. Correct the labels manually
2. Add a comment explaining why
3. The workflow learns from corrections

**If automation created a duplicate:**
1. Close the duplicate
2. Reference the original
3. Report in Discussions if it recurs

### Workflow Failed

**Steps:**
1. Check the **Actions** tab for error details
2. Look for CI Doctor Issues with guidance
3. Try re-running the workflow
4. Report persistent failures in Discussions

## Privacy and Security

**Workflows cannot:**
- Access private files without permissions
- Modify files outside the repository
- Access sensitive credentials
- Make destructive changes without review

**All automated changes:**
- Are visible in Pull Requests
- Require review before merging (documentation updates)
- Can be reverted like any commit
- Are logged in workflow runs

## Learning More

### Workflow Documentation Files

Each agentic workflow has detailed documentation:

- `.github/workflows/issue-triage.md`
- `.github/workflows/daily-qa.md`
- `.github/workflows/update-docs.md`
- `.github/workflows/ci-doctor.md`
- `.github/workflows/q.md`

### GitHub Actions Documentation

- [GitHub Actions overview](https://docs.github.com/actions)
- [Workflow syntax](https://docs.github.com/actions/using-workflows/workflow-syntax-for-github-actions)
- [Scheduled workflows](https://docs.github.com/actions/using-workflows/events-that-trigger-workflows#schedule)

### Getting Help

- Create an Issue labeled `question` and `automation`
- Start a Discussion about workflow behavior
- Check [SUPPORT.md](../SUPPORT.md) for contacts

## Summary

Automation in this repository:

1. **Reduces manual work** with weekly reminders and automatic checks
2. **Maintains quality** through daily QA and documentation updates
3. **Improves organization** with automatic issue triage
4. **Keeps systems healthy** with CI Doctor monitoring
5. **Enhances security** with automatic dependency updates

**Key takeaway:** Automation handles routine tasks so you can focus on farming. Review automated Issues and PRs, but trust the system to maintain quality and consistency.

## Related Documentation

- [Getting Started Guide](./getting-started.md) - Repository basics
- [Labels Guide](./labels-guide.md) - Understanding labels used by automation
- [Workflow Reference](./workflow-reference.md) - Technical workflow details
