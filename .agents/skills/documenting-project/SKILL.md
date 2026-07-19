---
name: documenting-project
description: "Use when the user explicitly requests project documentation with trigger phrases like '/document-project', 'Finalize Project', or 'Generate Project Documentation'. Never activates automatically."
---

# Documenting a Project

## Overview

Generate comprehensive, professional-grade project documentation from the **full history** of a completed (or in-progress) project. This skill reconstructs the entire development journey — every decision, error, fix, and iteration — then produces structured deliverables across multiple formats, a Notion workspace, and a summary dashboard.

## When to Use

**ONLY activate when the user explicitly says one of these triggers:**
- `/document-project`
- `Finalize Project`
- `Generate Project Documentation`
- `Document this project`
- Any clear, unambiguous request to produce final project documentation

**NEVER activate automatically.** Do not trigger on tangential mentions of "docs", "readme", or casual conversation about documentation.

## When NOT to Use

- Writing a single README
- Updating inline code comments
- Answering a question about the project
- Any context where the user has not explicitly requested full project documentation

---

## Execution Steps

### Step 1 — Reconstruct Project Memory
Reconstruct the complete development history from transcript logs (`transcript.jsonl`), code changes, decision rationale, error logs, and user feedback.

### Step 2 — Generate Documentation Formats
Create `README.md`, `CHANGELOG.md`, `CONTRIBUTING.md`, `PROJECT_REPORT.md`, `API_DOCUMENTATION.md`, `USER_GUIDE.md`, and `DEPLOYMENT_GUIDE.md`.

### Step 3 — Step 11 Execution
Outputs `development_log.md`, `technical_report.md`, `visual_documentation.md`, `decision_log.md`, `project_metrics.md`, `presentation_outline.md`, `reflection.md`, 16 Notion pages via MCP, and `project_dashboard.md`.
