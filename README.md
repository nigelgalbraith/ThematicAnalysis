# ThematicAnalysis

ThematicAnalysis is a structured qualitative analysis system that transforms raw text into organised, searchable, and visual insights.

Data begins in Excel, is transformed into structured JSON through Python, and is rendered dynamically through modular JavaScript components in a browser-based interface.

The goal is simple:

- Keep qualitative data structured
- Keep transformation logic modular
- Keep relationships explicit
- Keep rendering data-driven
- Avoid ambiguous category drift

---

## System Overview

ThematicAnalysis follows a layered architecture:

1. Content Layer (Excel Workbook)
2. Transformation Layer (Python Import + Cleaning Pipeline)
3. Web Layer (HTML + JavaScript + JSON)

Extracts (raw data) are linked to Factors (identified themes).
Factors are grouped into Groups, Sub-Groups, Categories, and Sub-Categories.

This hierarchy enables:

- Structured filtering
- Visualisations
- Risk modelling
- Search functionality
- Hierarchical exploration

---

## Core Data Structure

The system links:

- Extracts → Factors
- Factors → Groups
- Groups → Sub-Groups
- Factors → Categories
- Categories → Sub-Categories

This structured hierarchy ensures consistency between:

- Glossary definitions
- Search filtering
- Group analysis
- Risk models
- Web rendering

---

## Excel Workflow

### Step 1 — Enter Extracts and Identify Factors

Collect qualitative data (quotes, observations, feedback).

Each data point (Extract) is recorded in Excel.

Alongside each Extract:

- Identify recurring themes
- Record them as Factors

⚠ If editing factors manually:
- Switch mode to **Manual** to avoid duplication caused by macros
- After editing, switch back to **List** mode for dropdown consistency

---

### Step 2 — Review Identified Factors

Use the built-in Excel macro to:

- Consolidate all factors
- Detect spelling inconsistencies
- Identify duplicates
- Confirm completeness

This protects downstream structural integrity.

---

### Step 3 — Populate the Glossary Table

Assign each Factor to:

- A Group
- A Sub-Group

This builds the thematic hierarchy and connects lower-level ideas to broader concepts.

---

### Step 4 — Update Group and Sub-Group Values

Use the sheet buttons:

- **Update Group**
- **Update Sub Group**

These populate structured values from the Glossary.

Missing glossary entries are highlighted in red.

---

### Step 5 — Refresh Search Tool Dataset

Run the update function to:

- Copy finalised factors
- Transfer assignments into Search Tool Data sheet

This dataset powers:

- Dropdown filters
- Search logic
- Web filtering system

---

### Step 6 — Define Categories and Sub-Categories

Add or review:

- Category
- Sub-Category

Use automation buttons to fill values from the Glossary.

Add rows if new themes were introduced.

---

### Step 7 — Export for Web Use

Save the workbook as:

```
Thematic-Analysis-Complete.xlsm
```

Run:

```bash
python3 Python-Update-Webpage.py
```

If needed, adjust configuration inside:

- `IMPORT_CFG`
- `CLEAN_CFG`

The script:

- Converts Excel → JSON
- Cleans and restructures data
- Groups nested records
- Outputs raw JSON
- Outputs JavaScript-ready files
- Updates HTML files

---

## Full Transformation Pipeline

The update process performs:

- Excel → JSON conversion
- Structured record consolidation
- Data cleaning (character normalization)
- Nested field restructuring
- Group and category linking
- Multi-file merging
- JavaScript-ready wrapping
- HTML updates

Configuration-driven. No hardcoded paths.

---

## Web Architecture

Once exported:

- JSON files are loaded
- JavaScript modules process and render data
- Pages dynamically build analysis views

Key modules include:

- Group analysis logic
- Factor analysis logic
- Risk matrix modelling
- Search filtering controller
- Glossary viewer

All rendering is data-driven.

No thematic logic is embedded directly in HTML.

---

## Web Interface Features

### Search Tool

Users can:

- Filter by Category
- Filter by Sub-Category
- Filter by Group
- Filter by Sub-Group
- Browse glossary entries
- View full factor lists

---

### Thematic Overview Page

Displays:

- Groups
- Linked Factors
- Connected Extracts
- Frequency metrics (if enabled)
- Risk indicators (if defined)

---

### Group-Level Analysis

Shows:

- Relative size of each Group
- Spread across dataset
- Dominant themes

---

### Sub-Group Analysis

Displays focused clusters within broader Groups.

Useful for identifying niche issues.

---

### Factor-Level Analysis

Shows:

- Frequency of appearance
- Context usage
- Associated Extracts
- Cross-theme relationships

---

### Groupings Overview

Visual summary of thematic density.

Highlights pattern clusters and imbalances.

---

### Risk Model Creator

Allows users to:

- Define scenarios
- Assign risk weights
- Map grouped factors to risk outputs
- Build qualitative → quantitative insight bridges

---

## Architecture Principles

ThematicAnalysis is built around:

- Structured hierarchical data
- Explicit relationship mapping
- Configuration-controlled transformation
- Data-driven rendering
- Modular transformation stages
- No implicit thematic assumptions

Each layer performs a single responsibility.

---

## Conceptual Architecture

```
Excel Workbook
        ↓
Python Import Layer
        ↓
Raw JSON Data
        ↓
Cleaning & Structuring Layer
        ↓
JavaScript-Ready Data
        ↓
Dynamic Web Rendering
        ↓
Search + Analysis + Risk Models
```

Content, transformation, and presentation remain fully decoupled.

---

## Run

To serve locally:

```bash
python3 -m http.server
```

Then open:

```
http://localhost:8000
```

Or open the HTML files directly in a browser.
