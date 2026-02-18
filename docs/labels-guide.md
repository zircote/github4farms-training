# Labels Guide

Labels help organize and prioritize Issues and Pull Requests in the Sunny Acres Farm repository. This guide explains the label system and how to use labels effectively.

## Label Categories

Labels are organized into four categories:

### 1. Domain Labels (What area?)

Identify which area of the farm the issue relates to:

| Label | Color | Use When |
|-------|-------|----------|
| `crops` | 🟢 Green | Planting, harvesting, soil, field work |
| `livestock` | 🟤 Brown | Animals, feeding, health, breeding |
| `equipment` | ⚫ Dark Gray | Tractors, tools, machinery, implements |
| `compliance` | 🔵 Blue | Grants, certifications, regulations, reporting |

**Example:** An issue about corn planting would use the `crops` label.

### 2. Type Labels (What kind of task?)

Describe the nature of the work:

| Label | Color | Use When |
|-------|-------|----------|
| `maintenance` | 🟠 Orange | Routine upkeep and service |
| `repair` | 🔴 Red | Fixing broken equipment or systems |
| `inspection` | 🟡 Yellow | Safety checks, audits, evaluations |
| `planning` | 🟣 Purple | Strategy, scheduling, decision-making |
| `health` | 💗 Pink | Animal or plant health concerns |
| `documentation` | 📘 Blue | Record updates, reports, documentation |

**Example:** Scheduling an oil change would use `maintenance`.

### 3. Priority Labels (How urgent?)

Indicate the urgency level:

| Label | Color | Use When |
|-------|-------|----------|
| `urgent` | 🔴 Bright Red | Immediate attention required (safety, animal health) |
| `routine` | 🟢 Green | Normal operations, can be scheduled |
| `seasonal` | 🟡 Yellow | Time-sensitive but tied to season/weather |

**Example:** A broken water line in the livestock barn would be `urgent`.

### 4. Status Labels (What's the blocker?)

Track what's preventing progress:

| Label | Color | Use When |
|-------|-------|----------|
| `waiting-on-parts` | ⚫ Gray | Repair delayed by parts shipment |
| `waiting-on-weather` | 🌧️ Light Blue | Field work delayed by conditions |
| `waiting-on-vet` | 🩺 Light Pink | Veterinary consultation needed |
| `waiting-on-approval` | 📋 Beige | Decision or authorization pending |

**Example:** A tractor repair waiting for a fuel pump would use `waiting-on-parts`.

## Additional Labels

### Special Purpose Labels

| Label | Color | Purpose |
|-------|-------|---------|
| `automation` | 🤖 Light Gray | Created by automated workflows |
| `qa` | 🔍 Light Purple | Quality assurance and checks |
| `ci` | ⚙️ Dark Gray | Continuous integration workflow issues |
| `good first issue` | 💚 Bright Green | Great for newcomers |
| `help wanted` | 🙋 Orange | Extra assistance needed |
| `question` | ❓ Light Blue | Seeking information or clarification |

## How to Apply Labels

### When Creating an Issue

1. Click **New issue**
2. Choose a template (optional)
3. Fill in the issue details
4. On the right sidebar, click **Labels**
5. Select appropriate labels from each category
6. Submit the issue

**Tip:** Most issues should have at least 2-3 labels (domain + type + priority).

### When Creating a Pull Request

1. Create your PR
2. On the right sidebar, click **Labels**
3. Add labels that match the content:
   - Domain label for which area is affected
   - `documentation` if updating records
   - Priority if time-sensitive

### Updating Labels on Existing Issues

Anyone with write access can update labels:

1. Open the Issue or PR
2. Click **Labels** in the right sidebar
3. Add or remove labels as the situation changes
4. Comment to explain significant label changes

## Label Combinations

### Common Patterns

**Equipment repair waiting for parts:**
```
equipment, repair, routine, waiting-on-parts
```

**Urgent livestock health issue:**
```
livestock, health, urgent
```

**Seasonal crop planning:**
```
crops, planning, seasonal
```

**Routine equipment inspection:**
```
equipment, inspection, routine
```

**Compliance documentation update:**
```
compliance, documentation, routine
```

### Status Label Workflow

Status labels help track blockers:

1. Issue created → No status label
2. Blocker identified → Add appropriate `waiting-on-*` label
3. Blocker resolved → Remove `waiting-on-*` label
4. Work completed → Close issue

**Example Timeline:**

- **Day 1:** Create issue: `equipment, repair, urgent`
- **Day 2:** Parts ordered: Add `waiting-on-parts`
- **Day 5:** Parts arrive: Remove `waiting-on-parts`
- **Day 6:** Repair complete: Close issue

## Searching by Labels

### Find All Issues in a Category

Use the Labels tab or search:

- All crop issues: Click `crops` label or search `label:crops`
- All urgent tasks: Search `label:urgent is:open`
- Equipment waiting on parts: Search `label:equipment label:waiting-on-parts is:open`

### Filter Multiple Labels

Combine labels for precise searches:

```
label:livestock label:health label:urgent is:open
```

This finds all open, urgent livestock health issues.

### Exclude Labels

Find issues without a certain label:

```
label:equipment -label:waiting-on-parts is:open
```

This finds equipment issues NOT waiting on parts.

## Label Best Practices

### Do:

✅ **Apply multiple labels** - Use domain + type + priority minimum  
✅ **Update labels** - Change status labels as situations evolve  
✅ **Be specific** - Choose the most accurate labels  
✅ **Use status labels** - Track blockers transparently  
✅ **Comment on changes** - Explain why labels changed  

### Don't:

❌ **Over-label** - Avoid adding every possible label  
❌ **Leave unlabeled** - Every issue should have at least one label  
❌ **Forget status updates** - Remove `waiting-on-*` when unblocked  
❌ **Contradict priority** - Don't mark routine work as urgent  

## Automated Labeling

Some workflows automatically add labels:

- **Issue Triage Workflow:** Suggests labels based on issue content
- **Update Docs Workflow:** Adds `automation` + `documentation`
- **Daily QA Workflow:** Adds `automation` + `qa`
- **CI Doctor Workflow:** Adds `automation` + `ci`

You can modify automated labels if they're incorrect.

## Creating New Labels

Need a label that doesn't exist?

1. Go to **Issues** → **Labels**
2. Click **New label**
3. Propose the new label in a Discussion first
4. Discuss naming, color, and use case
5. Repository maintainers will create if approved

**Before creating:** Check if an existing label works.

## Quick Reference

### Minimal Labeling

Every issue should have at minimum:

1. **One domain label:** crops, livestock, equipment, or compliance
2. **One type label:** maintenance, repair, inspection, planning, health, or documentation
3. **One priority label:** urgent, routine, or seasonal

### Status Labels (Optional)

Add when blocked:
- `waiting-on-parts`
- `waiting-on-weather`
- `waiting-on-vet`
- `waiting-on-approval`

### Example Labels for Common Scenarios

| Scenario | Labels |
|----------|--------|
| Schedule corn planting | `crops`, `planning`, `seasonal` |
| Broken tractor hydraulic line | `equipment`, `repair`, `urgent` |
| Annual safety inspection | `equipment`, `inspection`, `routine` |
| Cow vaccination record | `livestock`, `health`, `routine` |
| EQIP grant report due | `compliance`, `documentation`, `routine` |
| Field flooded, can't plant | `crops`, `planning`, `waiting-on-weather` |

## Questions?

- Create an Issue with the `question` label
- Start a Discussion
- See [SUPPORT.md](../SUPPORT.md) for help

## Related Documentation

- [Getting Started Guide](./getting-started.md) - Repository basics
- [Automation Overview](./automation-overview.md) - Automated workflows
- [Labels Configuration](../.github/labels.yml) - Complete label definitions
