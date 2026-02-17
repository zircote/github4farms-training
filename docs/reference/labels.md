# Label Reference

Complete guide to GitHub labels used in the Sunny Acres Farm repository.

## Overview

Labels are colored tags that categorize issues and pull requests. They help organize work, prioritize tasks, and filter information.

## How to Use Labels

### Viewing Issues by Label
1. Go to the **Issues** tab
2. Click any label to see all issues with that label
3. Or click **Labels** to see all available labels

### Adding Labels
1. Open an issue or pull request
2. Look for **Labels** in the right sidebar
3. Click the gear icon
4. Select appropriate labels

**Pro tip:** Most labels are automatically applied by issue templates.

---

## Label Categories

### Domain Labels
**What part of the farm is this about?**

#### 🌾 crops
- **Color:** Green (#0E8A16)
- **Use for:** Crop planting, harvest, soil tests, field work
- **Examples:**
  - "Update planting schedule for North 40"
  - "Soil test results for South Field"
  - "Corn harvest progress"

#### 🐄 livestock
- **Color:** Brown (#CD7F32)
- **Use for:** Animal health, feeding, breeding, veterinary care
- **Examples:**
  - "Vaccination due for beef cattle"
  - "Calf birth in North pasture"
  - "Update feeding schedule for winter"

#### 🚜 equipment
- **Color:** Blue (#0052CC)
- **Use for:** Machinery maintenance, repairs, purchases, safety
- **Examples:**
  - "Oil change for John Deere tractor"
  - "Combine needs tire repair"
  - "Annual safety inspection due"

#### 📋 compliance
- **Color:** Purple (#5319E7)
- **Use for:** Grants, certifications, regulations, reporting
- **Examples:**
  - "EQIP report due June 30"
  - "Renew organic certification"
  - "Grant application for new irrigation"

---

### Type Labels
**What kind of task is this?**

#### 🔧 maintenance
- **Color:** Dark Blue (#1D76DB)
- **Use for:** Routine service, preventive care, scheduled tasks
- **Examples:**
  - "500-hour service on tractor"
  - "Clean and calibrate planter"
  - "Quarterly fence inspection"

#### 🛠️ repair
- **Color:** Red (#B60205)
- **Use for:** Fixing broken equipment, addressing problems
- **Examples:**
  - "Hydraulic leak on combine"
  - "Replace broken fence post"
  - "Fix barn door latch"

#### 📝 planning
- **Color:** Light Blue (#BFD4F2)
- **Use for:** Future planning, strategy, decision-making
- **Examples:**
  - "Plan 2027 crop rotation"
  - "Decide on fall fertilizer application"
  - "Budget for equipment purchases"

#### 👁️ inspection
- **Color:** Orange (#D93F0B)
- **Use for:** Safety checks, quality reviews, assessments
- **Examples:**
  - "Annual equipment safety inspection"
  - "Fence line inspection"
  - "Grain storage quality check"

#### 💊 health
- **Color:** Pink (#E99695)
- **Use for:** Animal health, veterinary care, wellness
- **Examples:**
  - "Cow limping in south pasture"
  - "Schedule annual sheep vaccinations"
  - "Monitor sick calf"

---

### Priority Labels
**How urgent is this?**

#### 🚨 urgent
- **Color:** Bright Red (#D93F0B)
- **Use for:** Immediate action required, safety issues, emergencies
- **Examples:**
  - "Fence down, cattle at risk"
  - "Equipment broken during harvest"
  - "Animal injury requiring vet"

**Expected response:** Same day or within hours.

#### 🔄 routine
- **Color:** Gray (#CCCCCC)
- **Use for:** Regular tasks, normal priority, scheduled work
- **Examples:**
  - "Weekly feeding schedule update"
  - "Routine oil change"
  - "Regular pasture rotation"

**Expected response:** Within normal schedule (days to weeks).

#### 🌱 seasonal
- **Color:** Yellow (#FBCA04)
- **Use for:** Tasks tied to specific seasons or weather
- **Examples:**
  - "Spring planting preparation"
  - "Winterize irrigation system"
  - "Fall equipment storage"

**Expected response:** Before season ends or deadline passes.

---

### Status Labels
**What's blocking this task?**

#### ⏳ waiting-on-parts
- **Color:** Light Gray (#EDEDED)
- **Use for:** Work delayed pending parts delivery
- **Examples:**
  - "Tractor repair awaiting hydraulic hose"
  - "Planter needs replacement disc blades"

#### ☁️ waiting-on-weather
- **Color:** Cyan (#C2E0C6)
- **Use for:** Field work dependent on weather conditions
- **Examples:**
  - "Field too wet to plant"
  - "Rain delaying harvest"
  - "Waiting for ground to freeze"

#### 🏥 waiting-on-vet
- **Color:** Light Pink (#FFC0CB)
- **Use for:** Animal care pending veterinary visit
- **Examples:**
  - "Scheduled vet visit next Tuesday"
  - "Waiting for test results"
  - "Pregnancy check scheduled"

---

### Special Labels

#### ❓ question
- **Color:** Light Purple (#D876E3)
- **Use for:** Questions, requests for information or clarification
- **Examples:**
  - "What fertilizer rate for North 40?"
  - "Which vet do we use for sheep?"
  - "How to log equipment hours?"

#### 📚 documentation
- **Color:** Teal (#0075CA)
- **Use for:** Updates to documentation, instructions, guides
- **Examples:**
  - "Add new field to README"
  - "Update equipment manual link"
  - "Create how-to guide"

#### 🤖 automation
- **Color:** Dark Gray (#666666)
- **Use for:** Automated processes, workflows, bots
- **Examples:**
  - "Weekly backup reminder"
  - "Automated compliance deadline notification"

#### 🆕 enhancement
- **Color:** Bright Green (#84B6EB)
- **Use for:** Improvements, new features, suggestions
- **Examples:**
  - "Add photos to equipment inventory"
  - "Create seasonal calendar document"
  - "Improve issue template"

#### 🐛 bug
- **Color:** Dark Red (#D73A4A)
- **Use for:** Problems with repository, broken links, errors
- **Examples:**
  - "Broken link in README"
  - "Template not working correctly"
  - "Formatting error in table"

---

## Label Combinations

Use multiple labels together for precise categorization:

### Common Combinations

**Equipment + Maintenance + Routine**
- Regular scheduled equipment service
- Example: "200-hour service on tractor"

**Livestock + Health + Urgent**
- Emergency animal health situation
- Example: "Cow down, vet needed immediately"

**Crops + Planning + Seasonal**
- Seasonal crop planning task
- Example: "Finalize spring planting schedule"

**Compliance + Documentation + Waiting-on-**
- Compliance task with dependency
- Example: "Submit EQIP report (waiting for soil test results)"

### Suggested Patterns

| Task | Labels |
|------|--------|
| Broken tractor needs repair | equipment, repair, urgent |
| Plan next year's crops | crops, planning, seasonal |
| Annual vet visit scheduled | livestock, health, routine |
| Grant report due soon | compliance, documentation, seasonal |
| Field too wet to plant | crops, waiting-on-weather, seasonal |
| Fix fence before cattle arrive | equipment, repair, urgent |
| Update equipment manual | documentation, equipment, routine |

---

## Label Best Practices

### Do:
- ✅ Use multiple labels for better organization
- ✅ Apply domain label (crops/livestock/equipment/compliance)
- ✅ Apply type label (maintenance/repair/planning/etc.)
- ✅ Apply priority if relevant (urgent/routine/seasonal)
- ✅ Update labels as status changes
- ✅ Remove labels when no longer applicable

### Don't:
- ❌ Over-label (too many labels = confusion)
- ❌ Use conflicting labels (e.g., urgent + routine)
- ❌ Forget to label issues
- ❌ Create new labels without discussion

---

## Requesting New Labels

If you need a label that doesn't exist:

1. Open an issue with **question** label
2. Describe what label you need and why
3. Suggest a name and color
4. Explain what it would be used for

Repository administrators will review and create if appropriate.

---

## Related Resources

- [How to Use GitHub Issues Effectively](../how-to/use-github-issues.md)
- [Getting Started Tutorial](../tutorials/getting-started.md)
- [Data Dictionary](./data-dictionary.md)

---

**See all labels:** [GitHub Labels Page](https://github.com/zircote/github4farms-training/labels)
