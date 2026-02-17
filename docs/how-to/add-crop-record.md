# How to Add a Crop Record

**Task:** Document a new crop planting or harvest event  
**Time:** 5 minutes  
**Prerequisites:** Repository access, basic GitHub knowledge

## When to Use This Guide

Use this guide when you need to:

- Record new planting dates
- Update crop rotation plans
- Document harvest information
- Add soil test results

## Steps

### 1. Determine Which File to Update

Navigate to the **crops/** directory and choose the appropriate file:

- **planting-schedule.md** — For recording planting dates
- **crop-rotation-plan.md** — For updating rotation strategy
- **soil-test-results.md** — For adding new soil analysis
- **README.md** — For updating current season status

### 2. Create a Branch

You cannot edit the main branch directly. Create a branch for your changes:

1. Navigate to the file you want to edit
2. Click the **pencil icon** (Edit this file)
3. GitHub will automatically create a branch, or you can name it yourself:
   - Use format: `crops/update-planting-schedule-YYYY-MM-DD`
   - Example: `crops/update-planting-schedule-2026-02-17`

### 3. Edit the File

**Example: Adding a planting record to planting-schedule.md**

Find the table for the relevant field and add a new row:

````markdown
| Field | Crop | Variety | Planting Date | Expected Harvest |
|-------|------|---------|---------------|------------------|
| North 40 | Corn | Pioneer P1197 | 2026-05-01 | 2026-10-15 |
| South Field | Soybeans | Asgrow AG24X9 | 2026-05-15 | 2026-10-20 |
| East Section | Wheat | WB-Grainfield | 2026-09-20 | 2027-07-10 |
| **West Field** | **Corn** | **DeKalb DKC62-54** | **2026-05-05** | **2026-10-18** |
````

**Format requirements:**

- Keep table alignment consistent (use pipes `|`)
- Use ISO date format (YYYY-MM-DD)
- Include all required columns
- Be specific about varieties when known

### 4. Write a Commit Message

At the bottom of the edit page, write a clear commit message:

**Good examples:**
- "Add corn planting date for West Field"
- "Update harvest dates for North 40 corn crop"
- "Add 2026 soil test results for South Field"

**Poor examples:**
- "Update" (too vague)
- "Fixed stuff" (unclear what changed)
- "asdfjkl" (meaningless)

### 5. Create a Pull Request

1. Click **Propose changes** (or **Commit changes**)
2. On the next page, click **Create pull request**
3. Fill in the PR template:
   - **Title:** Same as your commit message (or more descriptive)
   - **Description:** Explain what changed and why
     - Example: "Added planting date for West Field corn crop. Planting scheduled for May 5, 2026 using DeKalb DKC62-54 variety."
4. Add labels if appropriate:
   - **crops** (automatically added)
   - **planning** or **documentation**
5. Click **Create pull request**

### 6. Request Review (Optional)

If your farm has designated reviewers:

1. Click the gear icon next to **Reviewers** on the right sidebar
2. Select the appropriate reviewer
3. They'll be notified to review your changes

### 7. Merge the Pull Request

Once approved (or if no review is required):

1. Click **Merge pull request**
2. Confirm the merge
3. Delete the branch (GitHub will prompt you)

Your crop record is now updated!

## Special Cases

### Adding a New Field

If you're documenting a new field that doesn't exist in the schedule:

1. Follow steps 1-3 above
2. Add a new row at the appropriate location (alphabetically or by field layout)
3. Update the crops/README.md if needed to mention the new field

### Updating Historical Data

If correcting past records:

1. Make the edit clearly
2. In your commit message, note it's a correction: "Correct planting date for North 40 (was May 10, should be May 12)"
3. Consider adding a note in the description explaining the correction

### Bulk Updates

If updating multiple entries:

1. Make all changes in a single commit
2. List each change in your commit message:
   ```
   Update multiple crop records:
   - Add North 40 planting date
   - Update South Field harvest date
   - Correct West Field variety name
   ```

## Troubleshooting

**Problem:** "You don't have permission to edit this file"  
**Solution:** You may not have write access. Contact the repository administrator.

**Problem:** "Merge conflict detected"  
**Solution:** Someone else edited the same lines. You'll need to resolve the conflict manually or ask for help.

**Problem:** "Table formatting looks broken"  
**Solution:** Ensure each row has the same number of pipes (`|`) as the header row.

## Related Guides

- [Track Compliance Deadlines](./track-compliance-deadlines.md) — Link crop activities to compliance requirements
- [Use GitHub Issues Effectively](./use-github-issues.md) — Create issues for planting tasks

## Need Help?

- Open an issue with the **question** label
- Check [Getting Started Tutorial](../tutorials/getting-started.md)
- Review [File Naming Conventions](../reference/naming-conventions.md)
