# Design Decisions & Rationale

This document captures key **architectural decisions** made in AutoDQCE and the reasoning behind them.

The goal is to make design intent explicit and traceable.

---

## Separation of Validation and Cleaning

### Decision
Validation and cleaning are implemented as **separate pipeline stages**.

### Rationale
- Prevents silent data modification
- Makes failures explicit
- Improves auditability

This separation avoids a common anti-pattern where detection and fixing are interleaved.

---

## Pipeline-Based Architecture

### Decision
AutoDQCE uses a **linear, stage-based pipeline**.

### Rationale
- Predictable execution flow
- Easier debugging and testing
- Clear responsibility boundaries

Each stage has a single responsibility.

---

## Configuration-Driven Behavior

### Decision
Behavior is driven by configuration rather than hard-coded logic.

### Rationale
- Improves reusability across datasets
- Avoids one-off scripts
- Enables controlled customization

This also supports future extensibility.

---

## Fail-Fast on Critical Violations

### Decision
Critical validation failures halt pipeline execution.

### Rationale
- Prevents corrupted data from propagating
- Makes failures visible early
- Encourages correct data contracts

Fail-fast behavior is essential for production systems.

---

## Explicit Outputs and Reporting

### Decision
All pipeline runs produce validation artifacts and reports.

### Rationale
- Enables auditing
- Supports debugging
- Builds trust in automated cleaning

Outputs are designed to be machine-readable and human-readable.

---

## Deterministic Execution

### Decision
AutoDQCE enforces deterministic behavior.

### Rationale
- Reproducibility
- Easier testing
- Reliable comparisons between runs

Same input and configuration always produce the same output.

---

## Summary

These design decisions prioritize **correctness, transparency, and long-term maintainability** over convenience or speed of initial implementation.
