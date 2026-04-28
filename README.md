# GuardOn Enforcement Locus Artifacts

This repository contains datasets, experimental summaries, methodology notes, and supporting evidence for the IEEE Software article:

**Rethinking Policy-as-Code: Why Enforcement Timing Matters in Kubernetes**

## Purpose

The purpose of this repository is to provide traceability between the claims made in the article and the supporting artifacts used to evaluate GuardOn, a browser-based review-time Policy-as-Code system for Kubernetes manifests.

The repository is organized so that reviewers, practitioners, and researchers can inspect the evidence behind the article’s claims, including the manifest corpus, policy evaluation summaries, latency measurements, detection consistency results, pull request workflow observations, and public usage evidence.

## Scope

These artifacts support a practitioner-oriented article. The results should be interpreted as observations from controlled experiments and early usage, not as universal benchmark claims.

The evaluation focuses on review-time validation of Kubernetes manifests using deterministic, resource-local policies. Policies requiring live cluster state, external API access, cross-resource reasoning, mutation, or generation are outside the primary scope of this artifact package.

## Repository Contents

| Path | Description |
|---|---|
| `claims-to-evidence-map.md` | Maps article claims to supporting artifacts |
| `artifact-index.md` | High-level inventory of all artifacts |
| `datasets/manifests/` | Summary of the 160-manifest misconfiguration corpus |
| `datasets/policies/` | Summary of policy rules used in evaluation |
| `datasets/pr-study/` | Pull request workflow study summaries |
| `experiments/latency/` | Feedback timing measurements and methodology |
| `experiments/detection/` | Detection consistency, precision/recall, and false positive analysis |
| `experiments/workflow-impact/` | Pull request resolution and baseline comparison notes |
| `evidence/usage/` | Public usage evidence such as Chrome Web Store screenshots |
| `evidence/github/` | GitHub repository visibility evidence |
| `evidence/conferences/` | Conference presentation evidence |
| `evidence/community/` | Public community mention evidence |
| `scripts/` | Reproduction and verification guidance |

## Main Article Claims Supported

This repository supports the following article claims:

1. Enforcement locus is a useful design dimension for Policy-as-Code systems.
2. Review-time validation can provide faster feedback than CI/CD-integrated validation because it avoids pipeline scheduling overhead.
3. GuardOn can evaluate deterministic, resource-local Kubernetes policies inside pull request workflows.
4. GuardOn’s detection behavior is broadly consistent with established tools for policies that do not require external context.
5. Review-time feedback can help developers resolve policy violations before merge.
6. Review-time enforcement should be used as a complementary advisory layer, not as a replacement for CI/CD or admission-time enforcement.

## Interpretation Guidance

The artifacts should be read with the following limitations in mind:

- The manifest corpus contains 160 Kubernetes examples and may not represent all production misconfiguration patterns.
- The pull request study includes 37 pull requests and should be interpreted as early usage evidence.
- The workflow comparison is observational and does not establish causal impact.
- Client-side review-time validation is bypassable and does not provide non-bypassable enforcement guarantees.
- Results may vary depending on browser version, hardware, repository size, and policy set.

## Related Repositories

- GuardOn source code: `https://github.com/guardon-dev/guardon`
- Evaluation corpus: add link once published
- Article manuscript: add link or DOI once available

## Citation

If you use this artifact package, please cite the associated article once published.

## License

Unless otherwise noted, dataset summaries and documentation in this repository are released under the license specified in `LICENSE`.
