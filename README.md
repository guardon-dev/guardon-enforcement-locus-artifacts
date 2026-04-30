# GuardOn Enforcement Locus Artifacts

This repository provides supporting datasets, experimental results, and methodology for the article:

**“Rethinking Policy-as-Code: Why Enforcement Timing Matters in Kubernetes”**

The work introduces **enforcement locus** as a design dimension in Policy-as-Code (PaC) systems and evaluates a **review-time enforcement model** using GuardOn, a browser-based policy engine for Kubernetes manifests.

---

## Purpose

The goal of this repository is to:

- Provide transparency into the experimental setup and evaluation  
- Support key findings related to feedback timing, detection consistency, and workflow impact  
- Enable partial reproducibility of results presented in the article  

This repository is intended as a **supporting artifact**, not a full benchmark suite.

---

## Repository Structure

```text
guardon-enforcement-locus-artifacts/
├── enforcement_locus/     # Concept definition and trade-offs
├── dataset/               # 160-manifest corpus and ground truth
├── experiments/           # Methodology and raw results (RQ1, RQ2, RQ3)
├── results/               # Tables and summarized findings
└── limitations/           # Threats to validity and constraints