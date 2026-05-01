# Claims to Evidence Map

This document maps article claims to supporting artifacts.

---

## 1. Enforcement Locus Concept

**Claim:** Placement of policy validation impacts workflow and feedback timing.

**Evidence:**
- Figure 1 (paper)
- Table I (paper)

---

## 2. Dataset (160 Manifests)

**Claim:** Evaluation uses a 160-manifest corpus.

**Artifacts:**
- datasets/manifests/corpus-summary.csv
- datasets/category_breakdown.csv

---

## 3. Feedback Timing

**Claim:** Review-time validation provides faster feedback than CI/CD.

**Artifacts:**
- experiments/latency/latency-results.csv
- experiments/methodology.md

---

## 4. Detection Consistency

**Claim:** GuardOn aligns with existing tools for deterministic policies.

**Artifacts:**
- experiments/detection_metrics.csv
- experiments/confusion_matrix.csv

---

## 5. False Positive Rate

**Claim:** GuardOn produces a small number of false positives.

**Artifacts:**
- experiments/confusion_matrix.csv

---

## 6. Workflow Impact

**Claim:** 84% of violations resolved before merge.

**Artifacts:**
- datasets/pr-study/violation-resolution.csv
- experiments/workflow-impact/pr-analysis.md

---

## 7. Baseline Comparison

**Claim:** CI workflows require additional commits (~61%).

**Artifacts:**
- experiments/workflow-impact/baseline-comparison.md

**Note:** Observational comparison only.

---

## 8. Real-world Usage

**Claim:** GuardOn used by 200+ users.

**Artifacts:**
- evidence/usage/chrome-store.png

---

## 9. Limitations

**Claim:** Review-time enforcement is:

- Bypassable
- Limited to deterministic policies

**Artifacts:**
- experiments/methodology.md

---

## Final Note

All claims are supported by:

- Controlled experiments
- Observational workflow data
- Public evidence

These artifacts support transparency and reproducibility.