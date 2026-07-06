# Hyper Synthetic Forge

**Tableau-Aware Synthetic Data Generator | v3.0**

---

## What It Does

Hyper Synthetic Forge generates production-quality synthetic datasets by cloning the schema and statistical distributions of your Tableau datasources — or building from scratch via natural language. The output is statistically faithful, correlation-aware, temporally realistic, privacy-safe, and ready to connect in Tableau via native .hyper extract format.

---

## Two Modes

| Mode | Input | Output |
|------|-------|--------|
| **Tableau Clone** | A published datasource name or LUID | Synthetic data matching real schema + profiled distributions + correlations + temporal patterns |
| **From Description** | "I need e-commerce data with 10K rows" | Synthetic data using domain-aware templates with built-in seasonality and growth curves |

---

## How to Trigger

Say any of:
- "Hyper Synthetic Forge"
- "Generate test data"
- "Clone this datasource"
- "I need mock data / fake data / sample data"
- "Forge me some data"

If you ask generically, the skill will offer to scan your Tableau datasources for schema inspiration.

---

## Workflow (7 Phases)

| Phase | What Happens |
|-------|--------------|
| 1. Source Identification | Resolves datasource by URL, name, or LUID. Handles permission errors gracefully. |
| 2. Schema Analysis & Profiling | Classifies fields, profiles distributions, detects nulls, identifies calculated fields, profiles numeric correlations, detects temporal patterns (trend, seasonality, day-of-week). |
| 3. Schema Proposal & Preview | Presents full schema table with strategies, correlation matrix, temporal patterns, and a 5-row preview for approval. |
| 4. Full Generation | Generates data with calibrated distributions, correlation-aware field ordering, temporal pattern application, and multi-attempt calibration with escape hatches. |
| 4B. Anomaly Injection (optional) | Injects controlled spikes, dips, outliers, regime changes, or flatlines for testing alerts and insight detection. |
| 4C. Data Imperfection Mode (optional) | Injects realistic messiness (inconsistent casing, typos, near-duplicates, format inconsistency) for testing data quality workflows. |
| 5. Post-Generation Validation | Mandatory checks — statistical accuracy, categorical distributions, correlation direction, temporal pattern adherence, cross-field consistency, privacy. |
| 6. Export | Delivers in user's chosen format: .hyper (recommended), CSV, JSON, Excel, or SQL. |
| 7. Schema Save & Reuse | Serializes the full profile to JSON so future runs skip profiling entirely. |

---

## What's New in v3.0

**Numeric Correlation Profiling** — Profiles the statistical relationships between numeric measures (Sales↔Profit, Discount↔Profit) using quartile-binned proxy queries. Generates correlated fields together instead of independently, so cross-tabbing the output produces realistic patterns rather than random noise.

**Time-Series Pattern Detection** — Detects year-over-year growth trends, monthly seasonality curves (holiday spikes, seasonal dips), and day-of-week volume patterns. Applies them multiplicatively during generation so synthetic time-series data actually behaves like real business data.

**Anomaly & Event Injection** — Insert controlled spikes (Black Friday 3x), dips (supply shortage 0.3x), scattered outliers, permanent regime changes, event clusters, or flatlines (outage simulation) into specific date windows. Designed for testing alerting systems, Tableau Pulse sensitivity, and anomaly visualizations.

**Data Imperfection Mode** — Generates intentionally messy data at Light/Medium/Heavy severity: inconsistent casing, trailing spaces, typos, near-duplicates, mixed date formats, phantom categories, and encoding artifacts. Includes an optional answer key CSV mapping every imperfection to its original clean value. Built for testing Tableau Prep flows and data quality pipelines.

**Native .hyper Export** — The recommended export format for Tableau users. Uses the pantab library to generate Tableau Hyper extracts that drop directly into Tableau Desktop or publish to Tableau Cloud with no intermediate connection step.

**Schema Save & Reuse** — After a successful run, save the complete profile (distributions, correlations, temporal patterns, cross-field rules) as a JSON file. Future runs reference the saved schema by name, skipping Phases 1–3 entirely and jumping straight to generation.

---

## Key Capabilities

- Resolves Tableau datasource references by URL, name, or LUID — handles permission errors with fallback suggestions
- Profiles field distributions, cardinality, null rates, and cross-field relationships from live datasources
- Detects and applies numeric correlations between measures (positive, negative, or independent)
- Models temporal behavior: YoY growth, monthly seasonality, weekday/weekend weighting
- Calibrates numeric fields to within 10% of profiled averages using a 3-attempt algorithm with user-facing escape hatch
- Enforces cross-field consistency: geographic hierarchies, date ordering, ID-date synchronization, state-region mappings
- Computes calculated fields per-row from base fields using Tableau formula logic
- Generates multi-table datasets with referential integrity (parent → child FK validation)
- Supports controlled anomaly injection with configurable type, magnitude, and date targeting
- Injects realistic data imperfections at three severity levels with optional answer key
- Exports as .hyper (native Tableau extract), CSV, JSON, Excel, or SQL (multiple dialects)
- Saves and loads schema profiles for instant repeat generation
- Validates privacy: no real name + address + contact combinations; fully synthetic PII

---

## Export Formats

| Format | Best For | Notes |
|--------|----------|-------|
| **.hyper** | Tableau Desktop, Server, Cloud | Native extract format. No connection step needed. Recommended. |
| **CSV** | Universal compatibility, large datasets | UTF-8, ISO 8601 dates, one file per table |
| **JSON** | APIs, web applications | Pretty-printed, array of objects |
| **Excel (.xlsx)** | Sharing with non-technical stakeholders | Multi-sheet, formatted headers, frozen panes |
| **SQL** | Database seeding | CREATE TABLE + INSERT. PostgreSQL, MySQL, or SQL Server dialect. |

---

## Domain Templates (Description-Based Mode)

When generating without a Tableau source, built-in templates provide realistic defaults:

- **E-Commerce** — Orders, customers, products. Q4 holiday spikes, log-normal amounts, Pareto product popularity.
- **Healthcare** — Patients, visits, providers. Age skew, flu seasonality, chronic condition repeats.
- **Financial Services** — Accounts, transactions. Weekday-heavy, log-normal amounts, account-type balance ranges.
- **SaaS/B2B** — Companies, users, usage. ARR correlated with company size, power-user segmentation.
- **Supply Chain** — Suppliers, shipments, inventory. Regional lead times, seasonal demand, capacity utilization.
- **HR/People** — Employees, departments, reviews. Tenure distributions, salary bands by level, performance curves.

---

## Use Cases

**Dashboard prototyping** — Generate realistic data matching a production schema so you can build and demo dashboards without exposing real data. The .hyper export connects instantly.

**Testing Tableau Pulse and alerting** — Inject anomalies at known dates and magnitudes to validate that your Pulse metrics detect the right signals at the right sensitivity.

**Data quality pipeline testing** — Use Data Imperfection Mode to generate messy inputs for Tableau Prep flows, then validate against the answer key that your cleaning logic catches every issue.

**Training and enablement** — Create safe, realistic datasets for workshops and certifications without privacy risk. Schema save/reuse means you can regenerate fresh data for each cohort.

**Statistical method validation** — The correlation-aware and temporally-patterned output lets you verify that analytical models (forecasting, clustering, regression) respond correctly to known data characteristics.

**Load and performance testing** — Generate 100K+ rows calibrated to production distributions to stress-test dashboard rendering, extract refresh, and query performance.

