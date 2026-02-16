# Salesforce -> ClickUp SF ID Sync

This script pulls Salesforce Account Number values from **Closed Won** Opportunities and stores them in a ClickUp custom field ("SF ID") on tasks whose names match the Salesforce **Account Name**.

## What It Does
- Reads credentials from `.env`
- Queries Salesforce for Closed Won Opportunities
- Matches ClickUp tasks by **exact task name = Account Name**
- Updates the ClickUp **SF ID** custom field **only if blank**
- Verifies the updated value via the ClickUp API

## Requirements
- Python 3.10+
- Salesforce username/password/security token
- ClickUp API token
- ClickUp List ID + Custom Field ID

## Setup
1. Install dependencies:
   ```bash
   python3 -m pip install simple-salesforce requests
   ```

2. Create your `.env` file:
   ```bash
   cp .env.template .env
   ```

3. Fill in `.env` with your values.

## Run
```bash
python3 step2.py
```

## Notes
- The script **does not** write anything back to Salesforce.
- It will skip tasks if:
  - The SF ID field already has a value
  - The task name doesn’t match an Account Name
  - There are multiple ClickUp tasks with the same name

## Files
- `step2.py` — main script
- `.env.template` — env template (safe to commit)
- `.env` — secrets (do not commit)

