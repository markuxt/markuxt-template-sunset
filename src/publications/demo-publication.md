---
# ============================================================
# Demo Publication — a VISIBLE example so the Publications page
# renders out of the box. Copy this file, rename it (e.g.
# doe2025-title.md), replace the fields below, then delete this
# demo once you have real publications.
# ============================================================

# title [Required]: Full publication title.
title: Decentralized Coordination of Autonomous Drone Swarms

# authors [Required]: Author list. Use "LastName, FirstName" so the
# page can format "F. LastName" and sort/group correctly.
authors:
  - Doe, John
  - Smith, Jane
  - Lee, Min

# authors_orcid [Optional]: ORCID iD per author, PARALLEL to `authors` (use
# null where an author has none). An ORCID matching a member's `orcid` links
# them: the member appears as a site-author on this publication's page, and
# this publication appears on the member's page. Below, the first author is
# linked to the demo member (src/members/staff/demo-member.md).
authors_orcid:
  - 0000-0000-0000-0000

# year [Required]: Publication year. Drives the "grouped by year"
# listing on the Publications page.
year: 2025

# doi [Optional]: Link to the publisher / DOI. Renders as a button
# on the detail page.
doi: https://doi.org/10.1000/example

# venue [Optional]: Journal or conference name.
venue: IEEE Transactions on Robotics

# keywords [Optional]: Tag list. Filterable / displayed as chips.
keywords:
  - control systems
  - multi-agent
  - UAV
---

## Abstract

This is a **demo publication** so the Publications page renders out of the box. Replace it with your real papers — one Markdown file per publication. The abstract is shown on the detail page.

## Key Contributions

We introduce a decentralized planner whose convergence can be characterized by the Lyapunov function below.

## Methodology

Markuxt renders LaTeX math via KaTeX (`remark-math` + `rehype-katex`, configured in the layer):

The candidate Lyapunov function is

$$V(x) = \frac{1}{2} \sum_{i=1}^{n} \| x_i - x_i^* \|^2$$

and its time derivative satisfies $\dot{V}(x) \le 0$ along closed-loop trajectories.

## Results

- 30% reduction in inter-agent collisions versus the centralized baseline.
- Scales linearly to 50 agents in simulation.

## Conclusion

The proposed decentralized scheme achieves near-centralized performance with only local communication.
