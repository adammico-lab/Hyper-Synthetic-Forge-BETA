## Quick Start

### Prerequisites

- [Claude Desktop](https://claude.ai/download) with agent mode enabled
- [Tableau MCP](https://github.com/tableau/tableau-mcp) installed and authenticated
- Access to a Tableau Cloud or Tableau Server site (for clone mode)

### Install

1. Clone or download this repository.
2. Copy the skill folder into your Claude skills directory.
3. Restart Claude Desktop.
4. Confirm Tableau MCP is connected (you should see your site's content when you ask Claude about it).

### Example Prompts

**Clone mode (mirror an existing datasource):**

```
Clone my "Sales Pipeline" datasource with 10,000 synthetic rows
```

```
Generate synthetic data that matches the schema and distributions of my Superstore datasource
```

**Description mode (build from scratch):**

```
I need fake e-commerce data: orders, customers, products, and returns. 50,000 rows, 2 years of history, with seasonal patterns.
```

```
Generate test data for a healthcare staffing dashboard. Include shifts, departments, employee roles, and overtime hours with realistic weekday patterns.
```

### What You Get

A synthetic dataset calibrated to match the statistical profile of your source (distributions, correlations, seasonality, null rates) or built to your spec from a description. Exported as CSV, with schema documentation and a validation summary showing how closely the output matches the target profile.
