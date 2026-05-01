# Enforcement Locus Definition

## Overview

Policy-as-Code (PaC) systems are commonly evaluated based on:
- policy expressiveness  
- enforcement guarantees  
- integration with delivery pipelines  

This work introduces **enforcement locus** as an additional design dimension.

---

## Definition

**Enforcement locus** refers to the point in the software delivery lifecycle at which policy validation is applied.

Rather than treating policy enforcement as a fixed stage, enforcement locus frames it as a **design choice** that influences:

- feedback timing  
- visibility of policy decisions  
- developer experience  
- cost of remediation  

---

## Lifecycle Placement

Policy validation can occur at multiple stages:

| Locus | Description |
|------|------------|
| Edit-time | Validation in IDE during authoring |
| Commit-time | Validation before code is committed |
| Review-time | Validation during pull request review |
| Pipeline-time | Validation during CI/CD execution |
| Admission-time | Validation at cluster deployment boundary |

---

## Design Implications

Each enforcement locus introduces trade-offs:

- Earlier stages:
  - faster feedback  
  - limited visibility or coverage  

- Later stages:
  - stronger guarantees  
  - higher latency and remediation cost  

The review stage represents a unique position:
- collaborative decision point  
- shared visibility across contributors  
- opportunity for early correction before pipeline execution  

---

## GuardOn Context

GuardOn explores **review-time enforcement**, where:

- policy validation occurs directly in pull request interfaces  
- feedback is visible to both authors and reviewers  
- evaluation is performed client-side  

This model complements existing approaches rather than replacing them.

---

## Key Insight

The effectiveness of Policy-as-Code systems is influenced not only by:

- what policies enforce  
- how they enforce  

but also by:

> **when enforcement occurs within the development workflow**

Treating enforcement locus as a first-class design consideration enables more effective layering of governance mechanisms across the lifecycle.