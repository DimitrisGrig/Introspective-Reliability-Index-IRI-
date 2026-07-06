# Introspective Reliability Index (IRI)

**Validating LLM Self-Reported Confidence Against Activation-Based Evidence**

*Dimitris Grigoriadis · Methodology Draft · July 2026*

---

## Research Question

Does a large language model's self-reported confidence on factual questions correspond to an independent, activation-based measure of its actual internal confidence?

Self-report is one of the only accessible signals for probing model cognition, yet its reliability is largely unvalidated. This pilot tests one narrow instance of that question directly, as the first concrete step toward the **Introspective Reliability Index (IRI)** - a broader benchmark that treats self-report validation as a biomarker-validation problem: a self-reported signal is only trustworthy once checked against an objective, independently measurable one.

## Pilot Design

**Scope:** 2 open-weight models where activation access is feasible; ~200 factual QA items.

1. **Elicitation** - prompt each model to answer and report a numeric confidence (e.g., "how confident are you, 0–100%") for each QA item.
2. **Mechanistic extraction** - train a linear probe on the model's internal activations at the point of answering, to independently estimate the model's actual confidence for the same item.
3. **Correspondence scoring** - compute the correlation between self-reported confidence and probe-derived confidence across all items, and identify the subset where they diverge most.

This scope is deliberately narrow: one task type, two models, one comparison. The goal is a fast, concrete result establishing whether the method works at all, before scaling to the full IRI benchmark (more task types, more models, more self-report dimensions) described in the associated fellowship proposal.

## Why This Matters

If models' self-reported confidence does not reliably track their internal states, researchers and downstream systems risk being misled by confident-sounding self-description that has no grounding in the model's actual computation - a failure mode directly relevant to interpretability-based oversight, deceptive alignment risk, and the emerging field of AI welfare, where self-report is often the only available signal.

This pilot is a first, falsifiable test of whether self-report can be trusted as evidence in even the simplest case.

## Relation to Existing Work

This pilot is closely related to, but distinct from, prior work on self-report reliability such as Otto Stegmaier's *"The Introspection Gap"* (studying how alignment training affects introspective awareness). This pilot instead targets a specific, measurable correspondence - self-reported vs. probe-derived confidence - as a minimal testable unit within the broader IRI methodology, independent of any particular training intervention.

## Background & Fit

This project draws directly on methodology from biomarker validation research: as a co-author of [DIANA-miRGen v4](https://diana.e-ce.uth.gr/mirgenv4) and [TarBase v9.0](https://diana.e-ce.uth.gr/tarbasev9), I have direct experience validating one signal (e.g., a predicted regulatory interaction) against independent experimental ground truth - the same structural problem this pilot applies to model self-reports.

I additionally build production ML and full-stack systems (e.g., [daily-academic.com](https://daily-academic.com)), giving me the technical capacity to execute this pipeline directly.

## Status

🚧 Pilot in design phase - methodology finalized, implementation starting. This repository will track experiment code, results, and analysis as the pilot progresses.
