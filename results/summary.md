# Results Summary

This section summarizes the key findings from the evaluation of GuardOn across feedback timing (RQ1), detection consistency (RQ2), and workflow impact (RQ3).

---

## 1. Feedback Timing (RQ1)

The evaluation shows a substantial difference in **PR-visible feedback latency** between review-time and CI/CD-based enforcement.

- GuardOn delivers feedback in **tens of milliseconds** (median: 42 ms)
- CI/CD-integrated tools require **tens of seconds** (median: 35–44 s)

This difference is primarily due to:
- CI job scheduling delays  
- runner startup overhead  
- asynchronous execution pipelines  

Importantly, the computational cost of policy evaluation itself is not the dominant factor. When executed locally, CLI tools complete in under a few seconds, indicating that **enforcement placement (locus)** governs user-perceived latency.

These findings support the argument that placing validation at review time enables significantly faster feedback cycles within pull request workflows.

---

## 2. Detection Consistency (RQ2)

Across a corpus of 160 Kubernetes manifests, GuardOn demonstrates **comparable detection performance** to established tools for policies that can be evaluated without external context.

- Overall F1 score: **0.93 (GuardOn) vs 0.95 (OPA/Conftest)**
- High agreement in:
  - resource limits  
  - security context validation  
  - deprecated API detection  

Differences are primarily observed in the RBAC category, where:
- some policies depend on **cross-resource relationships**
- client-side evaluation lacks access to live cluster state

When restricted to **deterministic, resource-local rules**, detection behavior remains broadly consistent across tools.

---

## 3. Workflow Impact (RQ3)

In a sample of 37 pull requests across 8 repositories:

- **112 violations** were identified
- **84% were resolved before merge**

This suggests that making policy feedback visible during code review:
- encourages earlier remediation  
- reduces reliance on post-CI correction cycles  

A baseline comparison using historical CI data indicates that:
- ~61% of violations required additional commits after CI feedback

However, this comparison is:
- not controlled  
- based on different PR populations  

As a result, findings should be interpreted as **indicative rather than causal**.

---

## 4. Key Observations

### Enforcement Locus Drives Feedback Experience
The timing of policy evaluation has a greater impact on user experience than the underlying evaluation cost. Review-time validation minimizes feedback delay by eliminating pipeline overhead.

### Review-Time Enforcement Complements Existing Approaches
GuardOn is not intended to replace CI/CD or admission control. Instead, it provides:
- a **fast feedback layer** for deterministic checks  
- improved visibility during collaborative review  

### Early Feedback May Improve Resolution Behavior
Preliminary evidence suggests that earlier visibility of violations correlates with higher pre-merge resolution rates, though further controlled studies are needed.

---

## 5. Limitations

The results should be interpreted with the following constraints:

- Dataset size and composition may not represent all production scenarios  
- Evaluation includes author involvement, introducing potential bias  
- Workflow study lacks a controlled experimental baseline  
- Client-side evaluation excludes policies requiring runtime or cluster context  

These limitations are consistent with the intended scope of the study and are discussed in detail in the accompanying documentation.

---

## 6. Conclusion

The evaluation demonstrates that:

- Review-time enforcement provides **substantially faster feedback**
- Detection consistency is **comparable for applicable policy classes**
- Early feedback visibility may contribute to **improved remediation timing**

Together, these findings support the role of **enforcement locus** as a meaningful design consideration in Policy-as-Code systems.