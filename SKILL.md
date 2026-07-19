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

**This is the highest-priority step.** Before generating anything, reconstruct the complete development history. The documentation must reflect the **full journey**, not just the final state.

**Sources to mine:**

| Source | How to access | What to extract |
|---|---|---|
| Conversation history | Read transcript logs from `<appDataDir>/brain/<conversation-id>/.system_generated/logs/transcript.jsonl` | Every prompt, response, iteration, pivot, and user feedback |
| Code changes | `list_dir`, `view_file`, `grep_search` across the project root | All source files, configs, scripts, tests — current state |
| Files created | Walk the full directory tree, note timestamps where available | Complete file inventory with purposes |
| Decisions made | Extract from conversation: "I chose X because Y", "Let's use Z" | Decision + rationale pairs |
| Errors encountered | Grep transcripts for error messages, stack traces, "fix", "bug", "broke" | Error description, root cause, context |
| Fixes applied | Track what changed after each error | Fix description, files modified, approach |
| User feedback | Filter transcript for `USER_INPUT` steps | Requests, corrections, approvals, rejections |

**Reconstruction process:**

1. **Read the conversation transcript** — scan `transcript.jsonl` for all `USER_INPUT` and `PLANNER_RESPONSE` steps. Build a chronological event list.
2. **Walk the codebase** — `list_dir` recursively from the project root. For every file, note path, size, and purpose.
3. **Extract decisions** — search the transcript for phrases like "chose", "decided", "because", "instead of", "better to", "let's use". Log each as a Decision record.
4. **Extract errors** — search for "error", "Error", "failed", "bug", "broke", "fix", "issue". Log each with context.
5. **Build a timeline** — order all events chronologically using timestamps from the transcript.
6. **Count metrics** — total files, languages, dependencies, iterations, bugs fixed.

---

### Step 2 — Generate Multiple Documentation Formats

Generate **all applicable** documents as artifacts:
- `README.md`
- `CHANGELOG.md`
- `CONTRIBUTING.md`
- `PROJECT_REPORT.md`
- `API_DOCUMENTATION.md`
- `USER_GUIDE.md`
- `DEPLOYMENT_GUIDE.md`

### Step 3 — Generate Development Log with Timeline
Create `<artifacts>/development_log.md` with timestamped development events and phases.

### Step 4 — Generate Technical Report
Create `<artifacts>/technical_report.md` with requirements, architecture, security, performance, and API specs.

### Step 5 — Generate Visual Documentation
Create `<artifacts>/visual_documentation.md` containing Mermaid.js diagrams (Architecture, Sequence, Component, Flowchart, Gantt).

### Step 6 — Capture AI Decisions
Create `<artifacts>/decision_log.md` logging architectural, technical, and process decisions with context and impact.

### Step 7 — Generate Project Metrics
Create `<artifacts>/project_metrics.md` tracking files, LOC estimates, prompt iterations, bug counts, and tools used.

### Step 8 — Generate Presentation Outline
Create `<artifacts>/presentation_outline.md` containing an 11-slide pitch deck outline with talking points.

### Step 9 — Generate Reflection & Retrospective
Create `<artifacts>/reflection.md` analyzing successes, improvements, postponed features, and future roadmap.

### Step 10 — Create Notion Workspace
Construct a 16-page hierarchical Notion workspace using Notion MCP API tools.

### Step 11 — Generate Summary Dashboard
Create `<artifacts>/project_dashboard.md` summarizing status and linking all artifacts and Notion pages.
