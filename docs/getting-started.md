# Getting Started with Sunny Acres Farm Repository

Welcome to the Sunny Acres Farm repository! This guide helps you understand the repository structure and start contributing farm records.

## What This Repository Does

This repository organizes all farm operational records in one searchable, version-controlled location. Think of it as a digital filing cabinet that:

- Tracks changes over time
- Enables team collaboration
- Provides automated reminders and quality checks
- Creates audit trails for compliance

## Repository Structure

````
sunny-acres-farm/
├── crops/              # Crop planning and records
├── livestock/          # Animal health and feeding
├── equipment/          # Machinery maintenance
├── compliance/         # Grants and certifications
├── docs/              # This documentation
└── .github/           # Automation and templates
````

## Quick Start Tasks

### 1. Explore the Repository

Browse each directory to familiarize yourself with the content:

- **[Crops](../crops/)** - View planting schedules and soil data
- **[Livestock](../livestock/)** - Check feeding schedules and health records
- **[Equipment](../equipment/)** - Review maintenance logs
- **[Compliance](../compliance/)** - Track active grants and certifications

### 2. Understand Labels

Labels categorize Issues and Pull Requests. See the **[Labels Guide](./labels-guide.md)** for details.

Common labels include:

- **Domain:** `crops`, `livestock`, `equipment`, `compliance`
- **Type:** `maintenance`, `repair`, `inspection`, `planning`, `health`
- **Priority:** `urgent`, `routine`, `seasonal`

### 3. Create Your First Issue

To log a farm event or task:

1. Click **Issues** tab
2. Click **New issue**
3. Choose a template (crop, livestock, or equipment)
4. Fill in the details
5. Add appropriate labels
6. Submit

**Example:** Logging equipment maintenance

````markdown
Title: Oil change needed for John Deere 6120M

Labels: equipment, maintenance, routine

Body:
The tractor has reached 200 hours since the last oil change.
Need to schedule service this week.
````

### 4. Update Existing Records

To update a farm record file:

1. Navigate to the file (e.g., `equipment/maintenance-log.md`)
2. Click the **pencil icon** (Edit)
3. Make your changes
4. Scroll down to **Commit changes**
5. Write a clear commit message
6. Choose "Create a new branch" and start a pull request
7. Submit for review

### 5. Use Discussions for Questions

For general questions or discussions:

1. Click **Discussions** tab
2. Click **New discussion**
3. Choose a category
4. Ask your question or start a conversation

## Automated Features

This repository includes several automated workflows:

- **Weekly Reminders** - Creates a checklist every Monday
- **Issue Triage** - Categorizes and prioritizes new issues
- **Daily QA** - Checks for data quality issues
- **Documentation Updates** - Keeps docs synchronized with changes
- **CI Doctor** - Monitors workflow health

Learn more in the **[Automation Overview](./automation-overview.md)**.

## Common Workflows

### Recording Livestock Health Events

1. Create an Issue using the "Livestock Health Record" template
2. Add labels: `livestock`, `health`, and priority
3. Update the `livestock/health-records.md` file via Pull Request
4. Link the PR to the Issue

### Planning Crop Planting

1. Review `crops/planting-schedule.md`
2. Create an Issue with `crops`, `planning`, `seasonal` labels
3. Discuss timing in the Issue comments
4. Update the schedule via Pull Request when finalized

### Tracking Equipment Repairs

1. Create an Issue using the "Equipment Maintenance" template
2. Add labels: `equipment`, `repair`, and status (e.g., `waiting-on-parts`)
3. Log service in `equipment/maintenance-log.md`
4. Close the Issue when work is complete

## Best Practices

### Write Clear Commit Messages

**Good:**
- "Update planting dates for North Field corn"
- "Add vet visit for cow #42 - vaccination"
- "Mark tractor oil change complete - 200hr service"

**Avoid:**
- "Update"
- "Fix stuff"
- "Changes"

### Use Specific Details

Include:
- Field names or numbers
- Animal IDs or tag numbers
- Equipment model and serial numbers
- Dates in YYYY-MM-DD format
- Measurements with units

### Check Before Committing

- Verify dates and numbers
- Ensure no sensitive personal information
- Review for typos
- Confirm file is in the correct directory

## Getting Help

- **Create an Issue** with the `question` label
- **Start a Discussion** for open-ended questions
- **Check [SUPPORT.md](../SUPPORT.md)** for contact information
- **Review [CONTRIBUTING.md](../CONTRIBUTING.md)** for contribution guidelines

## Next Steps

1. ✅ Read this Getting Started guide
2. 📋 Review the [Labels Guide](./labels-guide.md)
3. 🤖 Understand [Automation Overview](./automation-overview.md)
4. 📝 Create your first Issue or update a record
5. 💬 Introduce yourself in Discussions

Welcome to the team! 🚜
