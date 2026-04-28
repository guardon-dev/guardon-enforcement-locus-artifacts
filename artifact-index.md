# Artifact Index

This document provides a structured overview of all artifacts included in this repository and their purpose in supporting the IEEE Software article:

**"Rethinking Policy-as-Code: Why Enforcement Timing Matters in Kubernetes"**

---

## Overview

The artifacts are organized into five main categories:

1. Datasets
2. Experiments
3. Evidence
4. Documentation
5. Reproducibility

Each section below describes the contents and how they relate to the claims made in the paper.

---

## 1. Datasets

### `datasets/manifests/`
Contains summaries of the Kubernetes misconfiguration corpus used in evaluation.

- `corpus-summary.csv`  
  List of all 160 manifests with metadata (category, source type, resource kind).

- `categories-breakdown.csv`  
  Distribution of manifests across misconfiguration categories:
  - Resource limits
  - Security context
  - Deprecated APIs
  - RBAC

- `README.md`  
  Description of dataset construction and limitations.

---

### `datasets/policies/`
Contains summaries of policy rules used in evaluation.

- `policy-summary.csv`  
  Overview of policy rules mapped to evaluation categories.

- `README.md`  
  Description of rule alignment across tools (GuardOn, OPA, Kyverno, Kube-Linter).

---

### `datasets/pr-study/`
Contains anonymized pull request workflow data.

- `pr-summary.csv`  
  Overview of 37 pull requests analyzed (repo type, manifest count, violations).

- `violation-resolution.csv`  
  Resolution statistics for detected violations (pre-merge fixes).

- `README.md`  
  Description of sampling methodology and limitations.

---

## 2. Experiments

### `experiments/latency/`
Supports RQ1 (Feedback Timing).

- `latency-results.csv`  
  Median and P95 latency for GuardOn and CI/CD tools.

- `methodology.md`  
  Measurement approach, environment, and interpretation notes.

---

### `experiments/detection/`
Supports RQ2 (Detection Consistency).

- `precision-recall-results.csv`  
  Precision, recall, and F1 scores by category and tool.

- `false-positives.csv`  
  List and explanation of observed false positives.

- `methodology.md`  
  Ground truth construction, rule alignment, and evaluation procedure.

---

### `experiments/workflow-impact/`
Supports RQ3 (Workflow Impact).

- `pr-analysis.md`  
  Analysis of violation resolution during code review.

- `baseline-comparison.md`  
  Observational comparison with CI-based workflows.

---

## 3. Evidence

### `evidence/usage/`
- `chrome-store.png`  
  Screenshot showing install count.

- `installs-timestamp.txt`  
  Timestamp of usage snapshot.

---

### `evidence/github/`
- `stars.png`  
  Repository popularity indicators.

- `contributors.png`  
  Contributor information.

---

### `evidence/conferences/`
- Screenshots of conference presentations (DeveloperWeek, SCaLE, etc.)

---

### `evidence/community/`
- Public mentions:
  - LinkedIn
  - Reddit
  - YouTube
  - X (Twitter)

---

## 4. Documentation

- `README.md`  
  Repository overview and usage guidance.

- `claims-to-evidence-map.md`  
  Direct mapping from article claims to artifacts.

- `artifact-index.md` (this file)  
  High-level navigation for reviewers.

---

## 5. Reproducibility

### `scripts/`

- `reproduction-guide.md`  
  Instructions for:
  - Re-running evaluation
  - Interpreting results
  - Understanding limitations

---

## How to Use This Repository

For reviewers:
1. Start with `claims-to-evidence-map.md`
2. Use this index to locate supporting artifacts
3. Inspect datasets and experiment summaries as needed

For practitioners:
- Focus on:
  - latency results
  - workflow impact
  - policy coverage

For researchers:
- Examine:
  - dataset composition
  - methodology files
  - evaluation assumptions

---

## Notes

- All datasets are summaries; raw manifests are not redistributed where licensing or ownership constraints apply.
- Results reflect controlled experiments and early usage observations.
- Observations should not be interpreted as universal performance guarantees.
