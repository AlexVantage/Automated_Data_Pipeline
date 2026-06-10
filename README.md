# Automated Data Pipeline

**A zero-touch Power Query ETL pipeline that replaces manual CSV formatting, un-pivoting, and cell scrubbing.**

Part of the [AlexVantage](https://alexvantage.com) Excel Asset Suite

---

## Problem
Operations teams waste hours every week manually un-pivoting columns, formatting dates, stripping whitespace, and scrubbing null values from server exports just to prepare their weekly performance reports. Because this relies on human intervention, it introduces formatting errors and inconsistent data typing that break downstream calculations.

## Approach
Built an automated extraction, transformation, and load (ETL) sequence using Microsoft Power Query and M-code. By establishing a strictly controlled local directory structure, the user simply drops the new CSV into a folder and clicks refresh. 

## What It Does
- **Explicit Data Typing:** Enforces text, currency, and date formats at the point of ingestion to prevent calculation breaks.
- **Delimiter Decomposition:** Programmatically splits compound string fields (like `PROD-SHIRT-RED-LRG` SKUs) into distinct category, color, and size columns.
- **Whitespace & Character Eradication:** Automatically trims trailing spaces, removes non-printable garbage bytes, and standardizes capitalization across all text fields.
- **Null Handling:** Scans numerical columns for blanks and safely injects zeroes to ensure downstream math functions run without failure.

## Tech Stack
- Microsoft Excel
- Power Query
- M-code Scripting

## Screenshots
![Directory Structure](screenshots/folder_structure.png)
*(Standardized local ingestion directories)*

![Applied Steps Logic](screenshots/applied_steps_panel.png)
*(The M-code transformation chain)*

## Impact
Turns a two-hour manual weekly formatting chore into a 5-second click-to-refresh action. Eliminates human error in the data prep phase, ensuring master tables are always structurally sound.

## Files
- `Automated_Data_Pipeline.xlsx` — The execution workbook.
- `/docs/pipeline.m` — Exported M-code for code review.
- `/sample_data/shopify_dump_dirty.csv` — Standardized dirty input file.
