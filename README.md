# Finding Hidden Binders in Virtual Chemical Space

**How causal discovery reveals therapeutic molecules that traditional screening dismisses.**

## Live Demo

[**Explore the interactive explainer →**](https://diego-carriellopez.github.io/causal-discovery-series/drug-discovery.html)

## The Problem

High-throughput screening dismisses molecules with weak apparent signal. But weak signal doesn't mean weak binding — confounding properties like poor solubility can mask genuine affinity. Entire scaffold families get filed under "inactive" when their binding is real but invisible to the assay.

## The Approach

Causal discovery algorithms reconstruct the directed acyclic graph (DAG) of cause-and-effect relationships between molecular descriptors and assay outcomes. This separates two distinct pathways to apparent signal:

- **True binding path:** Scaffold → H-bond donors → Pocket fit → Affinity → Signal
- **Confounder path:** Scaffold → LogP → Solubility → Effective concentration → Signal

By deconfounding solubility from affinity, we rescue dismissed families and navigate virtual chemical space toward analogs with corrected properties.

## What the Demo Shows

**Five scaffold families** screened against a kinase target. Families C (Indazoles) and E (Thiazolopyrimidines) are dismissed as noise — until causal discovery reveals solubility is masking their true affinity.

| Family | Apparent Signal | True Affinity (deconfounded) | Delta |
|--------|----------------|------------------------------|-------|
| C — Indazoles | 18% | **72%** | +54% |
| E — Thiazolopyrimidines | 8% | **52%** | +44% |

### Interactive Features

- **Chemical Space Map** — UMAP-style scatter plot of physical library vs virtual space. Reveal hidden binders, then explore virtual candidates.
- **Causal Graph** — Run causal discovery to light up the true binding path (green) vs confounder path (red).
- **Deconfounding Chart** — Before/after bar chart showing the dramatic affinity jumps for masked families.
- **Virtual Screening Table** — Top candidates with specific R-group modifications (morpholino, piperazine, glycol chains) that fix solubility while preserving binding.

## Key Results

- Traditional ML hit rate (trained on apparent signal): **~8%**
- Causal-guided virtual screening hit rate: **~38%**
- Rescued scaffold families: **2 out of 5** (previously dismissed as inactive)

## Tech

Pure HTML/CSS/JavaScript — no frameworks, no dependencies. All simulations run client-side using the Canvas API. Designed as a static site for GitHub Pages.

## Background

This work draws on a theoretical result by Chevalley, Mehrjou & Schwab showing that the false-negative rate (FNR) of causal discovery **concentrates** as the number of variables grows. In drug discovery, your variables are molecular descriptors — and modern cheminformatics gives you hundreds per molecule. High dimensionality works in your favor.

Your existing SAR (structure-activity relationship) workflow already generates the interventional data these algorithms need. Every R-group modification is a `do(X=x)` in the causal graph.

## Practical Entry Points

- **Causal discovery:** gCastle, CausalDiscoveryToolbox, NOTEARS, DoWhy
- **Molecular descriptors:** RDKit (200+ descriptors, Morgan fingerprints, MACCS keys)
- **Validation:** Generate testable predictions — "Family C analogs with LogP < 3.0 should show strong binding" — then synthesize and check

## Author

**Diego Carriello-Lopez** — PhD Biochemistry / Structural Biology (CEA Grenoble), M.Sc. Data Science & AI (DSTI Paris)

## License

MIT
