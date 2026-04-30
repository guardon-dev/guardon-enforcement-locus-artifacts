# Dataset Notes

This dataset contains a corpus of 160 Kubernetes manifest examples used to evaluate GuardOn for review-time Policy-as-Code validation.

## Corpus Composition

The corpus is organized into five categories:

| Category | Count | Description |
|---|---:|---|
| resource_limits | 30 | Missing or under-specified CPU/memory requests and limits |
| security_context | 40 | Privileged containers, root execution, privilege escalation, and related security context issues |
| deprecated_apis | 30 | Deprecated, removed, invalid, or unsupported Kubernetes API versions |
| rbac | 30 | Overly broad or risky Role/ClusterRole permissions |
| networking | 30 | Service exposure, port configuration, ingress, and network policy issues |
| **Total** | **160** | Full evaluation corpus |

## Dataset Organization

Manifest files are grouped by category under `datasets/manifests/`.

The category folder is used as the primary source for assigning the `category` value in `ground_truth.csv`.

## Ground Truth Labeling

Each manifest represents an intentionally misconfigured Kubernetes example. Therefore, the expected validation outcome for each row in `ground_truth.csv` is `fail`.

The `violation_type` field is inferred from the filename and category structure. It is intended to describe the primary misconfiguration represented by the manifest.

## Use in Experiments

All experiments in the `experiments/` directory are based on this 160-manifest corpus unless otherwise noted.

The dataset is used for:

- latency evaluation
- detection consistency analysis
- false positive / false negative review
- workflow-impact interpretation

## Scope

This corpus focuses on deterministic, resource-local policy checks that can be evaluated without requiring live cluster state.

Examples of out-of-scope checks include:

- policies requiring runtime cluster state
- admission-time mutation or generation
- complex cross-resource dependencies
- organization-specific policy exceptions

## Important Note

The current corpus includes a `networking` category. If the associated paper describes only four categories, the paper should be updated to reflect the five-category corpus used in this repository.