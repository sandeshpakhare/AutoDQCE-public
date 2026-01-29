# Architecture Diagrams

This directory contains **visual representations of AutoDQCE’s system architecture**.

The diagrams are intended to complement the written documentation by providing
a clear, high-level understanding of how the system is structured and how data
moves through it.

They are **conceptual by design** and do not expose implementation details,
algorithms, or proprietary logic.

---

## Purpose of These Diagrams

The diagrams in this directory exist to:

- Communicate system design at a glance
- Clarify separation of responsibilities
- Support architectural reasoning and discussion
- Aid reviewers, recruiters, and collaborators in understanding the system

They are not meant to be execution diagrams or low-level flowcharts.

---

## Diagram Overview

### 1. System Overview (`system_overview.png`)

This diagram presents an **end-to-end view** of AutoDQCE.

It highlights:
- Major pipeline stages
- Clear boundaries between layers
- The progression from raw input to final output

This diagram answers the question:
> *“What are the main components of AutoDQCE, and how are they connected?”*

---

### 2. Data Flow (`data_flow.png`)

This diagram focuses on **how data moves through the system**.

It emphasizes:
- The sequential nature of the pipeline
- Validation occurring before cleaning
- Explicit output generation and reporting
- Fail-fast behavior on critical issues

This diagram answers the question:
> *“In what order does AutoDQCE process data, and where decisions are made?”*

---

### 3. Module Breakdown (`module_breakdown.png`)

This diagram illustrates **responsibility boundaries** between modules.

It shows:
- Which concerns belong to which module
- Clear separation between validation, cleaning, and reporting
- No overlap or hidden coupling between components

This diagram answers the question:
> *“What does each module own, and what does it not own?”*

---

## Static vs Interactive Diagrams

The diagrams stored here are **static images** to ensure:
- Consistent rendering on GitHub
- Easy embedding in documentation
- Low friction for reviewers

An **interactive HTML-based visualization** may exist elsewhere in the project
for presentation or walkthrough purposes, but static diagrams remain the
canonical architectural reference.

---

## How to Use These Diagrams

Recommended reading order:
1. Start with the **System Overview**
2. Move to the **Data Flow**
3. Use the **Module Breakdown** to understand responsibility boundaries

These diagrams are best read alongside:
- `docs/pipeline_design.md`
- `docs/design_decisions.md`
- `docs/validation_rules.md`

---

## Summary

The diagrams in this directory provide a **visual foundation** for understanding
AutoDQCE’s architecture.

They are intentionally simple, explicit, and stable—reflecting the system’s
design philosophy of clarity, correctness, and control.
