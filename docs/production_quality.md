---
name: manufacture-masterclass-swtjkt2026
description: "Building production quality with CoCo."
---

## Purpose
Objective:

Your table will take one manufacturing decision, use synthetic data to analyse it, and create a prototype that a plant, supply-chain or operations team could act on.
1. Understand the operation.
2. Find the signal in the data.
3. Predict or explain an outcome.
4. Recommend an action.
5. Identify what is required to productionise it.
6. Create a viable prototype

Problem Statement:
1. Production quality: Which process conditions drive defects or low yield?

## Workflow
### Step 1: Prompt 0

Step 1: 
You are helping me build a fictional manufacturing analytics prototype for a workshop.
Use only synthetic data. Do not use or request real customer, employee, supplier or production data.
Before executing any SQL or code:
1. Inspect the current database and schema context.
2. Explain what you plan to create or change.
3. Prefer additive, reversible changes.
4. Do not drop or overwrite existing objects.
5. At the end of each step, show what was created and how to validate it.

Keep the solution small enough to complete in a workshop and explain assumptions clearly.
1. Ask discovery questions.
2. Classify requirements.
3. Recommend architecture options.
4. Confirm with the user before proceeding.

### Step 2: Prompt 1 - Synthetic Dataset

Step 2:
Create a fictional manufacturing dataset in a new scratch schema in my current Snowflake environment.

If you cannot create a schema, stop and tell me the exact privilege or object issue. Do not modify existing schemas.

Use a clearly named scratch schema such as COCO_MANUFACTURING_LAB_<MY_INITIALS> if naming is supported.

Create these related tables:
- PLANTS
- PRODUCTION_LINES
- ASSETS
- PRODUCTION_RUNS
- SENSOR_READINGS
- MAINTENANCE_EVENTS
- QUALITY_INSPECTIONS
- CUSTOMER_ORDERS
- INVENTORY
- SUPPLIERS
- SHIPMENTS

Generate realistic but fully synthetic data with:
- 3 plants
- 6 production lines
- 30 assets
- 12 months of history
- At least 10,000 production runs
- At least 50,000 sensor readings
- At least 2,000 customer orders
- Realistic timestamps, plant, line, asset, product and shift identifiers
- Seasonality, trends, correlations and operational anomalies
- 3–5% missing values in selected non-key fields
- A small number of duplicate or late-arriving records for data-quality analysis
- Enough signal to support predictive maintenance, quality analysis and demand/inventory forecasting

Include sensible primary-key-like identifiers and relationships. Add table and column comments where possible.

After creating the data, provide:
1. The schema name
2. A table-by-table data dictionary
3. Row counts for every table
4. The relationship map in text
5. Three recommended manufacturing AI use cases
6. Data-quality validation SQL

Do not invent results. Run the validation queries and report the actual results.

### Step 3: Prompt 2 - Validation
Step 3:
Validate the manufacturing lab environment before we build anything.

For every table in the scratch schema:
1. Return the row count.
2. Return the minimum and maximum event timestamp where applicable.
3. Check null rates for important fields.
4. Check duplicate business keys.
5. Check orphaned plant, line, asset, product, supplier and order references.
6. Check whether the date ranges are sufficient for the selected use case.

Create one DATA_QUALITY_SUMMARY table or view containing the results.
Do not change the source data. Flag any issue that could invalidate an analysis.


### Step 4: Problem 2
Step 4:
We selected production quality and yield.

Inspect the synthetic manufacturing schema and identify:
- Production runs
- Process conditions
- Quality inspections
- Yield, defect and scrap measures
- The time grain and join keys

Do not assume column names. Inspect the actual schema first.

Then produce:
1. A concise description of the quality signal.
2. The five most useful process or production features.
3. Yield and defect-rate definitions.
4. Any leakage, missing-data or sampling risks.
5. A proposed production-run analytical dataset for identifying high-risk runs.

Do not build the final model yet. First show the proposed logic and validation queries.


## Output

### Output 1: Prompt 5
Turn the selected analytical output into a lightweight operational experience.

First inspect what was actually created. Do not start from a blank application.

Create the simplest useful option available in the current environment:
- A dashboard or report for an operations manager, or
- A ranked action queue, or
- A natural-language question-and-answer interface over the result table.

The experience must answer:
1. What requires attention now?
2. Why is it being flagged?
3. What action is recommended?
4. Who should act?
5. What KPI should be monitored?

Use clear titles and business language. Include a last-refreshed timestamp and a note that the data is synthetic.
Explain how this could later be connected to production data and governed for wider use.

### Output 2: Prompt 6
Perform a final verification of the manufacturing prototype.

Check:
1. All referenced tables and views exist.
2. The output contains rows.
3. There are no obvious duplicate recommendations.
4. Joins do not multiply records unexpectedly.
5. Timestamps and time windows are valid.
6. Nulls are handled explicitly.
7. No real or sensitive data was used.
8. The headline KPI can be reproduced from the underlying data.

Return:
- A verification checklist with pass or flag status.
- The three most important assumptions.
- The one limitation we should disclose during the showback.

### Output 3: Prompt 7
Prepare a two-minute showback for this manufacturing prototype.

Use exactly this structure:
1. Operational problem - one sentence.
2. Data used - tables and time period.
3. Prototype built - one sentence.
4. Key finding - include one number from the actual result.
5. Recommended action - one sentence.
6. KPI to monitor - one metric.
7. Production next step - one data, integration or governance requirement.

Do not invent numbers. Use only results that were actually computed.

### Output 3: Prompt 8
Build streamlit in snowflake dashboard. Check and validate any error before deploy the dashboard. 
Ensure compatibility features & functions that is used with the SiS warehouse runtime version.
Fix for any error and re-deploy the dashboard
