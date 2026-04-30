# Methodology

This document describes the dataset construction, experimental setup, tool configuration, and measurement procedures used to evaluate GuardOn.

The evaluation is structured around three research questions:

- **RQ1:** Feedback timing  
- **RQ2:** Detection consistency  
- **RQ3:** Workflow impact  

All experiments were conducted on the same dataset under controlled conditions.

---

## 1. Dataset

### 1.1 Corpus Overview

The evaluation uses a corpus of **160 Kubernetes manifests** representing common misconfiguration patterns across five categories:

| Category | Count |
|----------|------|
| Resource Limits | 30 |
| Security Context | 40 |
| Deprecated APIs | 30 |
| RBAC | 30 |
| Networking | 30 |
| **Total** | **160** |

All manifests in the dataset represent **intentionally misconfigured examples**, and therefore the expected validation outcome for each instance is a policy violation.

---

### 1.2 Data Sources

Manifests were constructed from:

- publicly available misconfiguration studies  
- open-source repositories with known issues  
- documented Kubernetes configuration anti-patterns  

The dataset is included in this repository under `datasets/manifests/`.

---

### 1.3 Ground Truth

Ground truth labels were assigned via:

- manual inspection by the author  
- independent verification by two practitioners  

Inter-rater agreement was assessed using **Cohen’s κ ≈ 0.91** prior to reconciliation.

The mapping between manifests and expected outcomes is provided in:

```text
datasets/ground_truth.csv