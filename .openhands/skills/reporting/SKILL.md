---
triggers:
  - report
  - write up
  - summary
  - generate document
  - create report
---

# Professional Reporting

When asked to generate a report, follow this structural standard. Do not output raw markdown in the chat unless asked; prefer creating a file (e.g., `REPORT.md`).

## Report Structure

### 1. Executive Summary
* A 3-5 sentence overview of the task, the data analyzed, and the main conclusion.
* Target audience: Management (non-technical).

### 2. Methodology
* Briefly describe the tools used (e.g., "Analyzed 500MB log file using RLM method", "Scraped data using Selenium").
* List sources (filenames, URLs).

### 3. Findings
* Use bullet points for clarity.
* Include data evidence (numbers, percentages).
* **Embed Images:** If you generated charts in a previous step, embed them here using Markdown: `![Description](path/to/image.png)`.

### 4. Recommendations / Next Steps
* Actionable advice based on the findings.

## Formatting Guidelines
* Use Headers (`#`, `##`) strictly for hierarchy.
* Use **bold** for key metrics.
* Use `code blocks` for technical logs or specific commands referenced.
