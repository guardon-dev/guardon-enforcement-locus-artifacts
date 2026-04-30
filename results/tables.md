# Results Tables

This document summarizes the key experimental results corresponding to the evaluation section of the article.

---

## Table 1: Feedback Timing (RQ1)

**Definition:**  
Time from validation trigger to first visible feedback in the pull request interface.

- GuardOn: manifest render → annotation visible  
- CI/CD tools: PR trigger → annotation visible (includes scheduling)

| Tool              | Enforcement Locus | Median Time | P95 Time |
|-------------------|------------------|------------|----------|
| GuardOn           | Review-time      | 42 ms      | 110 ms   |
| OPA / Conftest    | CI/CD            | 38 s       | 74 s     |
| Kyverno CLI       | CI/CD            | 44 s       | 81 s     |
| Kube-Linter       | CI/CD            | 35 s       | 69 s     |

### Notes

- CI/CD measurements include:
  - job scheduling delay  
  - runner startup time  
  - execution + annotation propagation  

- Local CLI execution (without CI overhead) completes significantly faster (< 2 seconds) but does not represent **PR-visible feedback latency**.

- The observed difference is primarily due to **where evaluation occurs (enforcement locus)** rather than computational cost.

---

## Table 2: Detection Consistency (RQ2)

**Metrics:**
- Precision (P)
- Recall (R)
- F1 Score

**Dataset:** 160 manifests across four categories

| Category           | GuardOn (P) | GuardOn (R) | GuardOn (F1) | OPA (P) | OPA (R) | OPA (F1) |
|--------------------|-------------|-------------|--------------|--------|--------|----------|
| Resource Limits    | 0.97        | 0.95        | 0.96         | 0.96   | 0.97   | 0.97     |
| Security Context   | 0.94        | 0.93        | 0.94         | 0.95   | 0.95   | 0.95     |
| Deprecated APIs    | 1.00        | 0.94        | 0.97         | 0.98   | 0.91   | 0.95     |
| RBAC               | 0.91        | 0.78        | 0.84         | 0.93   | 0.93   | 0.93     |
| **Overall**        | **0.95**    | **0.90**    | **0.93**     | **0.96** | **0.94** | **0.95** |

### Notes

- GuardOn evaluates only **resource-local policies**
- RBAC differences arise due to:
  - exclusion of cross-resource rules
  - lack of live cluster context in client-side evaluation

- Results are **comparable for deterministic policy categories**

---

## Table 3: Workflow Impact (RQ3)

**Dataset:**
- 37 pull requests  
- 8 repositories  

| Metric | Value |
|--------|------|
| Total violations detected | 112 |
| Violations resolved before merge | 94 |
| Resolution rate | 84% |

### Baseline Context

- Historical CI data (same repositories, prior period):
  - ~61% of policy failures required additional commits after CI feedback

### Notes

- This comparison is:
  - **indicative**, not causal  
  - based on different PR sets and contributors  

- Results suggest that:
  - earlier visibility may improve remediation timing  
  - further controlled studies are required for causal claims  

---

## Summary

- Review-time enforcement provides **substantially lower feedback latency**
- Detection consistency is **comparable for applicable policy classes**
- Early evidence suggests **improved pre-merge resolution behavior**, within stated limitations