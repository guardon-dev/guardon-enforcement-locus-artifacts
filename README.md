# GuardOn Enforcement Locus Artifacts

This repository provides supporting datasets, experimental results, and methodology for the article:

**“Rethinking Policy-as-Code: Why Enforcement Timing Matters in Kubernetes”**

The article introduces **enforcement locus** as a design dimension in Policy-as-Code (PaC) systems and evaluates a **review-time enforcement model** using GuardOn, a browser-based policy engine for Kubernetes manifests.

---

## Purpose

This repository serves as a **supporting artifact** for the article by:

- Providing transparency into the evaluation methodology  
- Making datasets and aggregate results available  
- Supporting key findings related to feedback timing, detection consistency, and workflow impact  

The repository is intended to provide **representative and reproducible evidence**, not a full benchmark framework.

---

## Repository Structure

```text
guardon-enforcement-locus-artifacts/
├── enforcement_locus/     # Concept definition and trade-offs
├── datasets/              # Manifest corpus and summaries
├── experiments/           # Methodology and evaluation data
├── results/               # Tables and summarized findings
└── limitations/           # Threats to validity and constraints