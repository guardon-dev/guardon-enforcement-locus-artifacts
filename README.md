# GuardOn Enforcement Locus Artifacts

This repository contains datasets, experimental summaries, and supporting evidence for the IEEE Software article:

**"Rethinking Policy-as-Code: Why Enforcement Timing Matters in Kubernetes"**

## Purpose

The purpose of this repository is to provide transparency and traceability for the empirical and observational claims made in the article. It enables reviewers and practitioners to inspect the dataset, evaluation summaries, and workflow observations supporting review-time Policy-as-Code enforcement.

## Scope

The artifacts support a practitioner-oriented study. Results should be interpreted as:

- Observations from controlled experiments
- Early-stage deployment evidence
- Not universal or benchmark claims

The evaluation focuses on **deterministic, resource-local policies** that can be evaluated without live cluster state.

## Repository Structure

### Datasets
- `datasets/manifests/` — 160 Kubernetes misconfiguration summaries
- `datasets/category_breakdown.csv` — distribution across categories
- `datasets/ground_truth.csv` — expected violation labels
- `datasets/pr-study/` — pull request workflow observations

### Experiments
- `experiments/latency/` — feedback timing measurements
- `experiments/detection_metrics.csv` — precision/recall/F1
- `experiments/confusion_matrix.csv` — classification breakdown
- `experiments/methodology.md` — evaluation details

### Evidence
- Usage screenshots (Chrome Web Store)
- GitHub metrics
- Conference participation
- Community mentions

## Dataset Summary

- Total manifests: **160**
- Categories:
  - Resource Limits
  - Security Context
  - Deprecated APIs
  - RBAC
  - Networking

These represent common Kubernetes misconfiguration patterns derived from:

- Public security benchmarks
- Open-source repositories (anonymized)
- Incident-driven examples

## Key Claims Supported

This repository supports:

1. Enforcement locus impacts feedback timing and developer workflow.
2. Review-time validation reduces feedback delay relative to CI/CD.
3. Detection consistency is comparable for context-free policies.
4. Review-time visibility improves pre-merge issue resolution.
5. Review-time enforcement is best used as an advisory layer.

## Limitations

- Dataset size is limited (160 manifests)
- PR study is observational (37 PRs)
- Client-side model excludes cluster-state-dependent policies
- Results may vary across environments

## Reproducibility

See: experiments/methodology.md

## Notes

- Raw manifests are not redistributed where licensing applies
- Results reflect controlled and early-stage usage conditions