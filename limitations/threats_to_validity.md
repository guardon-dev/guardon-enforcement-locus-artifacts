# Threats to Validity

This document outlines the key limitations and potential sources of bias in the evaluation of GuardOn, consistent with the scope of the study.

---

## 1. Internal Validity

The evaluation was conducted by the author, who is also the designer of GuardOn. This introduces potential **self-evaluation bias**.

Mitigation:
- Ground truth labels were independently verified by two practitioners with Kubernetes experience  
- Agreement was measured prior to reconciliation (Cohen’s κ reported in the article)

---

## 2. Dataset Representativeness

The evaluation corpus consists of **160 Kubernetes manifests** constructed from:
- public misconfiguration studies  
- open-source repositories  
- known configuration anti-patterns  

While diverse, this dataset may not fully represent:
- organization-specific policies  
- large-scale production configurations  
- complex multi-resource interactions  

---

## 3. Scope of Policy Evaluation

GuardOn evaluates only **deterministic, resource-local policies**.

Limitations include:
- no access to live cluster state  
- exclusion of cross-resource relationships  
- partial coverage of RBAC scenarios  

As a result, comparisons with tools supporting full cluster-context evaluation are **scope-constrained**.

---

## 4. Feedback Timing Measurement

Latency measurements for CI/CD tools include:
- job scheduling delays  
- runner startup time  
- pipeline execution overhead  

These reflect **PR-visible feedback latency**, not raw execution time.

Local CLI execution is faster but was not used as the primary comparison baseline, as it does not reflect typical collaborative workflows.

---

## 5. Workflow Impact Study

The workflow impact analysis is based on:
- 37 pull requests  
- 8 public repositories  

Limitations include:
- no controlled experimental baseline  
- different PR populations across comparison periods  
- potential selection bias toward early adopters  

The observed improvement in pre-merge resolution rate should be interpreted as **indicative, not causal**.

---

## 6. External Validity

Results were obtained under a specific environment:
- hardware: Apple M2  
- browser: Chrome  
- CI: GitHub-hosted runners  

Performance characteristics may vary:
- on lower-powered systems  
- across different CI providers  
- under varying repository sizes and workloads  

---

## 7. Reproducibility Constraints

While datasets and aggregate results are provided:
- exact CI latency reproduction may vary due to external factors  
- full replication of workflow behavior requires similar repository conditions  

This repository aims to provide **transparent and representative evidence**, rather than strict benchmark reproducibility.

---

## Summary

These limitations reflect the intended scope of the study:

- exploratory evaluation of enforcement placement  
- focus on deterministic policy validation  
- emphasis on practitioner-relevant workflows  

Future work may address:
- larger and more diverse datasets  
- controlled workflow experiments  
- integration with cluster-context-aware policies