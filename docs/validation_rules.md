# Validation Rules Philosophy

This document describes the **validation philosophy** used by AutoDQCE.

It intentionally focuses on **how validation is structured and categorized**, not on specific rule implementations or proprietary heuristics.

---

## Purpose of Validation in AutoDQCE

Validation in AutoDQCE exists to **detect data quality issues early and explicitly**, before any data modification occurs.

The validation layer is responsible for:
- Identifying structural and logical issues
- Classifying severity of violations
- Producing auditable validation artifacts

Validation **never mutates data**.

---

## Rule Categories

AutoDQCE validation rules are conceptually grouped into the following categories.

### 1. Structural Rules
Structural rules verify the basic shape of the dataset.

Examples:
- Expected columns are present
- Column order or naming consistency (where applicable)
- Dataset is non-empty
- File-level integrity checks

Structural violations are typically **critical**.

---

### 2. Schema Rules
Schema rules enforce expected data types and formats.

Examples:
- Numeric vs categorical type enforcement
- Date and timestamp format validation
- Boolean coercion feasibility

Schema violations may be critical or recoverable depending on configuration.

---

### 3. Null & Missing Value Rules
These rules detect missing or undefined values.

Examples:
- Null presence thresholds
- Mandatory field enforcement
- Missing value distribution analysis

Detection is separated from any imputation decision.

---

### 4. Range & Constraint Rules
Constraint rules validate logical and statistical boundaries.

Examples:
- Numeric range checks
- Non-negative constraints
- Upper/lower bounds derived from domain knowledge

Violations are reported explicitly and may block execution.

---

### 5. Consistency & Integrity Rules
These rules verify internal consistency.

Examples:
- Cross-column dependencies
- Cardinality expectations
- Duplicate detection

These rules help surface silent data corruption.

---

## Severity Classification

Validation results are classified by severity:

- **Critical:** Pipeline execution should halt
- **Warning:** Issue is surfaced but may be cleaned
- **Informational:** Diagnostic insight only

Severity classification is explicit and configurable.

---

## Design Guarantees

The validation system guarantees that:
- All checks are deterministic
- No silent fixes occur
- All violations are reported
- Validation always precedes cleaning

---

## Summary

AutoDQCE treats validation as a **first-class system component**, not a pre-processing step.

By isolating validation from cleaning and enforcing explicit severity handling, the system avoids silent failures and improves trust in downstream data usage.
