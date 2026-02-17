# Data Dictionary

Technical reference for data fields used throughout the Sunny Acres farm repository.

## Overview

This document defines the structure, format, and validation rules for all data fields used in farm records.

## Standard Data Types

### Date Fields
- **Format:** ISO 8601 (YYYY-MM-DD)
- **Examples:** 2026-02-17, 2026-05-01, 2026-12-31
- **Validation:** Must be valid calendar date
- **Usage:** All date fields (planting dates, service dates, deadlines)

### Numeric Fields
- **Whole numbers:** No decimal point (e.g., 45, 320, 12)
- **Decimal numbers:** Use decimal point, 1-2 decimal places (e.g., 5.5, 123.75)
- **Currency:** USD format with 2 decimal places (e.g., $1,234.56)

### Text Fields
- **Short text:** Single line, max 100 characters
- **Long text:** Multi-line, max 1000 characters
- **Restricted text:** Must match specific values (see field definitions below)

## Crop Data Fields

### Planting Schedule (crops/planting-schedule.md)

| Field Name | Type | Required | Format | Example |
|------------|------|----------|--------|---------|
| Field | Short text | Yes | Field name from approved list | "North 40" |
| Crop | Short text | Yes | Crop type | "Corn", "Soybeans", "Wheat" |
| Variety | Short text | No | Specific cultivar/hybrid | "Pioneer P1197" |
| Planting Date | Date | Yes | YYYY-MM-DD | "2026-05-01" |
| Expected Harvest | Date | No | YYYY-MM-DD | "2026-10-15" |
| Acres | Decimal | No | Numeric, 1 decimal | "40.0" |
| Notes | Long text | No | Additional details | "Weather delayed" |

**Approved Field Names:**
- North 40
- South Field
- East Section
- West Field
- Home Pasture
- Back Pasture

**Approved Crop Types:**
- Corn
- Soybeans
- Wheat (Winter Wheat, Spring Wheat)
- Alfalfa
- Hay

### Crop Rotation Plan (crops/crop-rotation-plan.md)

| Field Name | Type | Required | Format | Example |
|------------|------|----------|--------|---------|
| Year | Numeric | Yes | YYYY | "2026" |
| Field | Short text | Yes | Field name | "North 40" |
| Planned Crop | Short text | Yes | Crop type | "Corn" |
| Previous Crop | Short text | No | Crop type | "Soybeans" |
| Rationale | Long text | No | Explanation | "Nitrogen fixation from previous soybeans" |

### Soil Test Results (crops/soil-test-results.md)

| Field Name | Type | Required | Format | Example |
|------------|------|----------|--------|---------|
| Field | Short text | Yes | Field name | "North 40" |
| Sample Date | Date | Yes | YYYY-MM-DD | "2026-03-15" |
| Lab | Short text | Yes | Testing lab name | "AgSource Laboratories" |
| pH | Decimal | Yes | 0.0-14.0, 1 decimal | "6.5" |
| Organic Matter % | Decimal | No | 0.0-100.0, 1 decimal | "3.8" |
| Nitrogen (ppm) | Numeric | No | Parts per million | "25" |
| Phosphorus (ppm) | Numeric | No | Parts per million | "45" |
| Potassium (ppm) | Numeric | No | Parts per million | "180" |
| Recommendations | Long text | No | Lab recommendations | "Apply 150 lbs/acre nitrogen" |

## Livestock Data Fields

### Health Records (livestock/health-records.md)

| Field Name | Type | Required | Format | Example |
|------------|------|----------|--------|---------|
| Animal ID | Short text | Yes | Unique identifier | "BC-045", "DC-03", "SH-12" |
| Animal Type | Short text | Yes | Species | "Beef Cattle", "Dairy Cow", "Sheep", "Horse" |
| Date | Date | Yes | YYYY-MM-DD | "2026-02-10" |
| Event Type | Short text | Yes | Health event category | "Vaccination", "Treatment", "Checkup" |
| Description | Long text | Yes | Details of event | "Annual vaccination - IBR, BVD, PI3" |
| Veterinarian | Short text | No | Vet name | "Dr. Sarah Johnson" |
| Cost | Currency | No | USD | "$125.00" |
| Next Due | Date | No | YYYY-MM-DD | "2027-02-10" |

**Animal ID Format:**
- Beef Cattle: BC-### (e.g., BC-001, BC-045)
- Dairy Cows: DC-## (e.g., DC-01, DC-12)
- Sheep: SH-## (e.g., SH-01, SH-28)
- Horses: H-# (e.g., H-1, H-2, H-3)

**Approved Event Types:**
- Vaccination
- Treatment
- Checkup
- Surgery
- Birth
- Weaning
- Observation

### Feeding Schedule (livestock/feeding-schedule.md)

| Field Name | Type | Required | Format | Example |
|------------|------|----------|--------|---------|
| Animal Group | Short text | Yes | Group designation | "Beef Cattle", "Dairy Herd" |
| Feed Time | Short text | Yes | Time of day | "6:00 AM", "2:00 PM" |
| Feed Type | Short text | Yes | Feed description | "Hay", "Grain Mix", "Silage" |
| Amount | Short text | Yes | Quantity | "50 lbs", "2 bales" |
| Frequency | Short text | Yes | How often | "Daily", "Twice daily" |
| Notes | Long text | No | Additional info | "Increase by 10% in winter" |

## Equipment Data Fields

### Maintenance Log (equipment/maintenance-log.md)

| Field Name | Type | Required | Format | Example |
|------------|------|----------|--------|---------|
| Equipment Name | Short text | Yes | Full equipment name | "John Deere 6120M Tractor" |
| Date | Date | Yes | YYYY-MM-DD | "2026-02-01" |
| Service Type | Short text | Yes | Maintenance category | "Oil Change", "Inspection", "Repair" |
| Hours | Numeric | No | Hour meter reading | "1250" |
| Description | Long text | Yes | Work performed | "50-hour service, oil and filter change" |
| Performed By | Short text | No | Person/company | "John's Equipment Service" |
| Cost | Currency | No | USD | "$285.50" |
| Next Service Due | Date or Numeric | No | Date or hours | "2026-04-01" or "1450" |

**Approved Service Types:**
- Oil Change
- Inspection
- Repair
- Tire Service
- Filter Replacement
- Calibration
- Annual Service

### Inventory (equipment/inventory.md)

| Field Name | Type | Required | Format | Example |
|------------|------|----------|--------|---------|
| Equipment Name | Short text | Yes | Full equipment name | "Case IH 7150 Combine" |
| Category | Short text | Yes | Equipment type | "Tractor", "Implement", "Tool" |
| Year | Numeric | Yes | YYYY | "2017" |
| Make | Short text | Yes | Manufacturer | "Case IH" |
| Model | Short text | Yes | Model designation | "7150" |
| Serial Number | Short text | No | Manufacturer S/N | "JJA0123456" |
| Current Hours | Numeric | No | Hour meter reading | "2450" |
| Status | Short text | Yes | Operational status | "Operational", "Repair Needed", "Winterized" |
| Location | Short text | No | Storage location | "Main Barn", "North Shed" |

**Approved Equipment Categories:**
- Tractor
- Combine
- Implement (Plow, Disc, Planter, etc.)
- Irrigation
- Tool
- Vehicle
- Attachment

**Approved Status Values:**
- Operational
- Repair Needed
- Under Repair
- Winterized
- Retired

## Compliance Data Fields

### Grant Tracker (compliance/grant-tracker.md)

| Field Name | Type | Required | Format | Example |
|------------|------|----------|--------|---------|
| Grant Name | Short text | Yes | Program name | "EQIP Conservation" |
| Agency | Short text | Yes | Funding agency | "USDA NRCS" |
| Status | Short text | Yes | Current status | "Active", "Pending", "Completed" |
| Start Date | Date | No | YYYY-MM-DD | "2025-01-01" |
| End Date | Date | No | YYYY-MM-DD | "2027-12-31" |
| Award Amount | Currency | No | USD | "$15,000.00" |
| Reporting Deadline | Date | No | YYYY-MM-DD | "2026-06-30" |
| Contact | Short text | No | Agency contact | "Mike Thompson, Conservation Planner" |

**Approved Status Values:**
- Active
- Pending
- Application Submitted
- Completed
- Denied
- Withdrawn

### Certifications (compliance/certifications.md)

| Field Name | Type | Required | Format | Example |
|------------|------|----------|--------|---------|
| Certification Name | Short text | Yes | Cert/license type | "Organic Certification" |
| Issuing Agency | Short text | Yes | Agency name | "State Ag Department" |
| Number | Short text | No | Cert/license number | "ORG-2024-12345" |
| Issue Date | Date | Yes | YYYY-MM-DD | "2024-01-15" |
| Expiration Date | Date | Yes | YYYY-MM-DD | "2027-01-14" |
| Status | Short text | Yes | Current status | "Active", "Pending Renewal" |
| Renewal Deadline | Date | No | YYYY-MM-DD | "2026-11-15" |
| Cost | Currency | No | USD | "$500.00" |

**Approved Status Values:**
- Active
- Pending
- Pending Renewal
- Expired
- Suspended
- Application Submitted

---

## Validation Rules

### Required vs. Optional Fields
- **Required:** Must have a value, cannot be empty
- **Optional:** May be left empty if information is not available

### Date Validation
All dates must:
- Use ISO 8601 format (YYYY-MM-DD)
- Represent valid calendar dates
- Be consistent (e.g., harvest date after planting date)

### Text Length Limits
- Short text: 100 characters maximum
- Long text: 1000 characters maximum
- Exceed limits only when absolutely necessary

### Numeric Validation
- Must be valid numbers
- No non-numeric characters (except decimal point or currency symbol)
- Negative numbers only where logically appropriate

---

## Need Help?

- Questions about field formats: See [Glossary](./glossary.md)
- Unsure what value to use: Open an issue with the **question** label
- Propose new fields: Create a pull request with documentation updates

**See also:**
- [File Naming Conventions](./naming-conventions.md)
- [Getting Started Tutorial](../tutorials/getting-started.md)
