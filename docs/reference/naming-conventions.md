# File Naming Conventions

Standards for naming files and directories in the Sunny Acres Farm repository.

## General Principles

### 1. Use Lowercase with Hyphens
**Format:** `word-word-word.md`

**Good:**
- `planting-schedule.md`
- `health-records.md`
- `maintenance-log.md`

**Bad:**
- `PlantingSchedule.md` (mixed case)
- `planting_schedule.md` (underscores)
- `plantingschedule.md` (no separators)

**Why:** Consistent, web-friendly, readable, no case-sensitivity issues.

### 2. Be Descriptive but Concise
**Aim for:** 2-4 words that clearly describe content

**Good:**
- `soil-test-results.md`
- `feeding-schedule.md`
- `grant-tracker.md`

**Bad:**
- `stuff.md` (too vague)
- `the-complete-and-comprehensive-livestock-feeding-schedule-for-all-animals.md` (too long)
- `doc1.md` (non-descriptive)

**Why:** Makes it easy to find files and understand content at a glance.

### 3. Use Plural for Collections
**When file contains multiple items**, use plural form.

**Examples:**
- `certifications.md` (list of multiple certifications)
- `health-records.md` (multiple health record entries)
- `soil-test-results.md` (multiple test results)

**But:**
- `crop-rotation-plan.md` (single plan document)
- `README.md` (single overview document)

### 4. Date Formats in Filenames
**When including dates**, use ISO 8601 format: `YYYY-MM-DD`

**Examples:**
- `soil-test-2026-03-15.md`
- `harvest-report-2026-10.md`
- `annual-summary-2026.md`

**Why:** Sorts correctly, unambiguous, international standard.

---

## Standard Filenames by Type

### Index/Overview Files

#### README.md
**Use for:** Directory overview, navigation aid, section introduction
**Location:** Root of any directory
**Content:** Description of directory contents, links to files, context

**Example structure:**
````markdown
# Section Name

Brief description of this section.

## Contents

| Document | Description |
|----------|-------------|
| [File Name](./filename.md) | What it contains |

## Additional Context

Any relevant information about this section.
````

### Record Files

#### Standard Names
Use these standard names when applicable:

**Crops:**
- `planting-schedule.md`
- `crop-rotation-plan.md`
- `soil-test-results.md`
- `harvest-records.md`
- `field-notes.md`

**Livestock:**
- `health-records.md`
- `feeding-schedule.md`
- `veterinary-log.md`
- `breeding-records.md`
- `birth-records.md`

**Equipment:**
- `maintenance-log.md`
- `safety-inspections.md`
- `inventory.md`
- `repair-history.md`
- `fuel-log.md`

**Compliance:**
- `grant-tracker.md`
- `certifications.md`
- `inspection-reports.md`
- `annual-reports.md`

### Temporary or Draft Files

**Format:** `draft-filename.md` or `temp-filename.md`

**Examples:**
- `draft-planting-plan-2027.md`
- `temp-soil-analysis.md`

**Important:** Delete or rename to final name once finalized.

### Archived Files

**Format:** `filename-archived-YYYY.md` or move to `archive/` subdirectory

**Examples:**
- `planting-schedule-archived-2025.md`
- `archive/2025/planting-schedule.md`

**Use for:** Historical records that are no longer active but should be preserved.

---

## Directory Naming

### Main Directories
**Use lowercase, plural, no hyphens for top-level directories:**

- `crops/`
- `livestock/`
- `equipment/`
- `compliance/`
- `docs/`

**Why:** Short, simple, standard practice for repository organization.

### Subdirectories
**Use lowercase with hyphens if needed:**

- `docs/tutorials/`
- `docs/how-to/`
- `docs/reference/`
- `docs/explanation/`

**Examples:**
- `crops/field-maps/`
- `equipment/service-manuals/`
- `livestock/breeding-records/`

---

## Special Cases

### GitHub-Specific Files

**Must use exact capitalization:**

- `README.md` (not readme.md or Readme.md)
- `LICENSE` (not license or license.txt)
- `CONTRIBUTING.md` (all caps)
- `CODE_OF_CONDUCT.md` (all caps)
- `SECURITY.md` (all caps)

**Why:** GitHub recognizes these names and displays them specially.

### Template Files

**Use `.md` extension, descriptive names:**

- `.github/ISSUE_TEMPLATE/equipment-maintenance.md`
- `.github/ISSUE_TEMPLATE/crop-issue-report.md`
- `.github/PULL_REQUEST_TEMPLATE.md`

### Workflow Files

**Agentic workflows use `.md` and `.lock.yml`:**

- `.github/workflows/issue-triage.md` (source)
- `.github/workflows/issue-triage.lock.yml` (compiled, auto-generated)

**Never edit `.lock.yml` files directly.**

---

## What NOT to Include in Filenames

### Avoid:
- ❌ Spaces: `planting schedule.md` → breaks in URLs and command line
- ❌ Special characters: `health&records.md`, `soil@test.md`
- ❌ Underscores: `planting_schedule.md` (use hyphens instead)
- ❌ Mixed case: `PlantingSchedule.md` (use all lowercase)
- ❌ Version numbers: `schedule-v2.md` (use git for versioning)
- ❌ Personal names: `johns-notes.md` (use descriptive names)
- ❌ Abbreviations only: `ps.md`, `hr.md` (spell out)

### Exception:
Some abbreviations are acceptable if widely understood:
- ✅ `usa.md`
- ✅ `faq.md`
- ✅ `api.md`

---

## Renaming Files

If you need to rename a file for consistency:

### Process:
1. Create an issue explaining why rename is needed
2. Create a pull request with the rename
3. Update all links pointing to the old filename
4. Note the old filename in the PR description

**Important:** Git tracks renames, so history is preserved.

### Finding Links to Update:
````bash
# Search for old filename references
grep -r "old-filename.md" .
````

---

## Checklist for New Files

Before creating a new file, verify:

- [ ] Filename is lowercase with hyphens
- [ ] Filename is descriptive (2-4 words)
- [ ] Extension is `.md` for markdown
- [ ] Doesn't conflict with existing file
- [ ] Follows standard naming pattern if applicable
- [ ] No spaces, special characters, or underscores
- [ ] Will make sense to others 6 months from now

---

## Examples by Scenario

### Adding a new livestock record type:
**Good:** `lambing-records.md`  
**Bad:** `Lambing.md`, `lambingRecords.md`, `lr.md`

### Creating a seasonal plan:
**Good:** `spring-planting-plan-2027.md`  
**Bad:** `SPP2027.md`, `plan.md`, `new plan.md`

### Documenting equipment service:
**Good:** `equipment/tractors/service-schedule.md`  
**Bad:** `equipment/Tractors/service.md`, `equipment/tractor_service.md`

### Creating documentation:
**Good:** `docs/how-to/update-crop-records.md`  
**Bad:** `docs/HowTo/updateCropRecords.md`, `docs/how to/update records.md`

---

## Questions?

- Unsure what to name a file? Open an issue with the **question** label
- See an inconsistently named file? Create a PR to fix it
- Want to propose a new naming standard? Start a discussion

---

**See also:**
- [Data Dictionary](./data-dictionary.md) — Field naming standards
- [Repository Design](../explanation/repository-design.md) — Overall structure
- [How to Add a Crop Record](../how-to/add-crop-record.md) — Creating new records
