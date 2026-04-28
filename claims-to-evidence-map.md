# Claims to Evidence Map

This document maps each major claim in the IEEE Software article:

**"Rethinking Policy-as-Code: Why Enforcement Timing Matters in Kubernetes"**

to the corresponding datasets, experimental results, and supporting evidence in this repository.

The goal is to make all claims traceable, inspectable, and reproducible.

---

## 1. Conceptual Claim: Enforcement Locus Matters

**Claim:**  
The placement of policy evaluation (enforcement locus) impacts feedback timing, visibility, and developer workflow.

**Evidence:**
- Figure 1 (in paper): lifecycle diagram
- Table I (in paper): structural trade-offs
- Section III (conceptual analysis)

**Artifacts:**
- `artifact-index.md` (concept overview)
- `experiments/latency/methodology.md` (timing interpretation)

---

## 2. Dataset: 160 Kubernetes Manifests

**Claim:**  
Evaluation is based on a corpus of 160 manifests covering common misconfiguration patterns.

**Evidence (paper):**
- Section V-A: corpus construction
- Category breakdown (resource limits, security context, APIs, RBAC)

**Artifacts:**
- `datasets/manifests/corpus-summary.csv`
- `datasets/manifests/categories-breakdown.csv`
- `datasets/manifests/README.md`

---

## 3. Tool Comparison

**Claim:**  
GuardOn is compared with:
- Open Policy Agent (OPA)/Conftest
- Kyverno CLI
- Kube-Linter

**Artifacts:**
- `experiments/detection/precision-recall-results.csv`
- `experiments/detection/methodology.md`

**Notes:**
- Rule alignment is described in methodology
- Non-equivalent policies are excluded for fairness

---

## 4. Feedback Timing (RQ1)

**Claim:**  
Review-time validation provides near-instant feedback compared to CI/CD-integrated tools due to elimination of scheduling overhead.

**Evidence (paper):**
- Table II (median and P95 latency)

**Artifacts:**
- `experiments/latency/latency-results.csv`
- `experiments/latency/methodology.md`

**Important Interpretation Note:**
Latency differences include CI scheduling and runner startup time, not just evaluation cost.

---

## 5. Detection Consistency (RQ2)

**Claim:**  
GuardOn achieves detection results broadly consistent with established tools for policies that do not require external context.

**Evidence (paper):**
- Table III (precision, recall, F1)
- Section V-C

**Artifacts:**
- `experiments/detection/precision-recall-results.csv`
- `experiments/detection/methodology.md`

---

## 6. False Positive Rate

**Claim:**  
GuardOn produced a small number of false positives (~4.4%) in the evaluation corpus.

**Evidence (paper):**
- Section V-C (False Positive Rate discussion)

**Artifacts:**
- `experiments/detection/false-positives.csv`

**Notes:**
- Root cause of false positives documented in file
- Policy correction applied after observation

---

## 7. Workflow Impact (RQ3)

**Claim:**  
A majority of detected violations were resolved before merge when surfaced during code review.

**Evidence (paper):**
- Section V-D
- 84% resolution rate (94 out of 112 violations)

**Artifacts:**
- `datasets/pr-study/violation-resolution.csv`
- `datasets/pr-study/pr-summary.csv`
- `experiments/workflow-impact/pr-analysis.md`

---

## 8. Baseline Comparison (Pre-GuardOn)

**Claim:**  
CI-based workflows required additional commits for policy failures (~61% of cases in observed repositories).

**Evidence (paper):**
- Section V-D (Baseline Context)

**Artifacts:**
- `experiments/workflow-impact/baseline-comparison.md`

**Important Note:**
- This comparison is observational
- Different PR populations and time windows
- Not a controlled experiment

---

## 9. Real-World Deployment

**Claim:**  
GuardOn has been deployed in real-world workflows and used by 200+ users.

**Evidence (paper):**
- Section V-D

**Artifacts:**
- `evidence/usage/chrome-store.png`
- `evidence/usage/installs-timestamp.txt`
- `evidence/github/stars.png`

---

## 10. Review-Time vs CI Annotation Tools

**Claim:**  
CI-based PR annotation tools (e.g., Checkov, Datree) provide review visibility but still incur scheduling delay.

**Evidence (paper):**
- Section II-B
- Section V-B discussion

**Artifacts:**
- `experiments/latency/latency-results.csv`
- `experiments/latency/methodology.md`

---

## 11. Limitations of Review-Time Enforcement

**Claim:**  
Review-time enforcement:
- is bypassable
- cannot evaluate cluster-state-dependent policies
- should be treated as an advisory layer

**Evidence (paper):**
- Section IV-B (Security and Trust Model)
- Section V-E (Threats to Validity)
- Section VI (Lessons)

**Artifacts:**
- `experiments/detection/methodology.md`
- `experiments/workflow-impact/pr-analysis.md`

---

## 12. Threats to Validity

**Claim:**  
Evaluation results are subject to:
- self-evaluation bias
- corpus representativeness limits
- deployment sample bias
- hardware/environment variability

**Evidence (paper):**
- Section V-E

**Artifacts:**
- `experiments/detection/methodology.md`
- `experiments/workflow-impact/baseline-comparison.md`

---

## Final Note

All claims in the associated article are supported by:
- controlled experimental summaries
- anonymized workflow observations
- publicly verifiable usage evidence

These artifacts are intended to support transparency and reproducibility, not to establish universal performance guarantees.
