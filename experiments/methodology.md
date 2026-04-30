# Methodology

This document describes the experimental setup, dataset construction, tool configuration, and measurement procedures used to evaluate GuardOn across three research questions:

- RQ1: Feedback timing
- RQ2: Detection consistency
- RQ3: Workflow impact

The goal is to ensure transparency and enable partial reproducibility of results reported in the article.

---

## 1. Experimental Overview

GuardOn was evaluated along three dimensions:

| Research Question | Objective |
|------------------|----------|
| RQ1 | Compare feedback latency between review-time and CI/CD-based validation |
| RQ2 | Assess detection consistency with established tools |
| RQ3 | Observe workflow impact during pull request review |

All experiments were conducted using the same dataset and aligned policy categories where applicable.

---

## 2. Dataset Construction

### 2.1 Manifest Corpus

A corpus of **160 Kubernetes manifests** was constructed to represent common misconfiguration patterns across four categories:

| Category | Count |
|----------|------|
| Resource limits (missing/incorrect) | 38 |
| Security context (privilege issues) | 42 |
| Deprecated/invalid APIs | 35 |
| RBAC misconfigurations | 45 |

### 2.2 Data Sources

Manifests were derived from:
- Public Kubernetes misconfiguration studies
- Open-source repositories with known issues
- Documented configuration anti-patterns

Each manifest was reviewed and labeled manually to establish ground truth.

---

## 3. Ground Truth Validation

Ground truth labels were assigned through:

- Manual inspection by the author
- Independent verification by two practitioners with Kubernetes experience

Agreement between reviewers was assessed using **Cohen’s kappa (κ = 0.91)** prior to reconciliation.

---

## 4. Tools and Configuration

The following tools were used for comparison:

| Tool | Version | Execution Mode |
|------|--------|----------------|
| GuardOn | Browser extension (local) | Review-time |
| OPA / Conftest | v0.49 | CLI (CI/CD simulation) |
| Kyverno CLI | v1.11 | CLI (CI/CD simulation) |
| Kube-Linter | v0.6.8 | CLI (CI/CD simulation) |

### Policy Alignment

- Policies were mapped across tools to a **common taxonomy**
- Only **deterministic, resource-local rules** were included
- Policies requiring external cluster state were excluded

---

## 5. Experimental Environment

Experiments were conducted under controlled conditions:

- Hardware: Apple M2, 16 GB RAM
- OS: macOS
- Browser: Chrome (version aligned with testing period)
- CI Simulation: GitHub-hosted runner (2 vCPU, Ubuntu 22.04)

All tools were executed against the same dataset.

---

## 6. RQ1: Feedback Timing

### Measurement Definition

- **GuardOn:** Time from manifest rendering in PR view → first annotation visible
- **CLI tools:** Time from execution start → output available
- **CI/CD tools:** Includes job scheduling and runner startup overhead

### Procedure

1. Each manifest evaluated across all tools
2. Latency recorded per run
3. Median and P95 values computed

### Notes

- Local CLI execution is faster but excluded from main comparison
- CI/CD measurements reflect **PR-visible latency**, not raw execution time

---

## 7. RQ2: Detection Consistency

### Metrics

- Precision
- Recall
- F1 Score

### Procedure

1. Each manifest evaluated across tools
2. Results classified as:
   - True Positive
   - False Positive
   - False Negative
3. Metrics computed per category and overall

### Scope Limitation

- GuardOn evaluates only **resource-local policies**
- Cross-resource RBAC rules requiring cluster context were excluded

---

## 8. RQ3: Workflow Impact

### Dataset

- **37 pull requests**
- Drawn from **8 public repositories**
- Each repository contains ≥10 Kubernetes manifests

### Procedure

1. GuardOn used during PR review
2. Violations recorded
3. Resolution tracked via subsequent commits

### Metric

- % of violations resolved before merge

### Baseline Comparison

- Historical CI policy failure data from same repositories
- Compared at aggregate level (not matched PRs)

---

## 9. Data Aggregation

- All experiments executed under consistent conditions
- Results aggregated across full dataset (160 manifests)
- No sampling or filtering applied post hoc

---

## 10. Limitations

- Dataset may not fully represent production diversity
- Self-evaluation bias is present
- Workflow study lacks controlled baseline
- Client-side evaluation excludes policies requiring runtime context

These limitations are discussed in detail in the article.

---

## 11. Reproducibility Notes

- Dataset and result files are included in this repository
- Tool versions and configurations are documented above
- Exact replication of CI latency may vary due to external scheduling factors

The goal of this repository is to provide **transparent, representative evidence**, not strict benchmark reproducibility.
