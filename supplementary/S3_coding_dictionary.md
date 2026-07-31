# Supplementary File S3 — Coding dictionary and operational definitions

All charting was performed on **title and abstract metadata**, not on full texts. Every
variable below is therefore an indicator of what a record *states in its abstract*, not a
verified property of the study. This is the central limitation of the map and is stated
as such in the manuscript.

## Units of analysis
| Unit | n |
|---|---|
| Records included in the map | 186 |
| Primary studies | 179 |
| Review articles | 7 |

Maturity indicators are reported over the **179 primary studies**. Review articles are
retained for narrative context and citation chasing only, and are excluded from every
maturity denominator.

## Variables

**record_type** — single-label. `review article` if the title matches a secondary-literature
pattern (systematic/scoping/narrative review, meta-analysis, overview, editorial,
commentary, perspective, roadmap); otherwise `primary study`.

**themes** — **multi-label**. A record may be counted under several themes, so theme counts
sum to more than the number of records. Assignment is by regular-expression match on
title and abstract. `Datasets/benchmarks` means the abstract *mentions* a named dataset,
benchmark or annotation effort — it does **not** mean the record released data.

**architecture_families** — **multi-label**, so counts sum to more than the number of
records. Records naming no family receive the explicit value
`Family not specified in abstract`. Categories are deliberately *not* mutually exclusive
and are *not* hierarchical: ResNet is a CNN, and an ensemble may contain a YOLO detector.
The chart reports how often each family is *named*, not a partition of the corpus.

Counts over the 179 primary studies:
  - CNN (generic term): 61
  - Family not specified in abstract: 56
  - YOLO family: 44
  - Other named backbone: 21
  - Ensemble / distillation: 17
  - ResNet: 13
  - Transformer / ViT: 11
  - U-Net: 9
  - R-CNN family: 7
  - GAN: 5
  - LSTM / RNN: 3

**human_material_flag** — abstract refers to human samples or a human clinical context.

**validation_flag** — abstract mentions external validation, multi-centre design,
independent test set, cross-clinic generalisation, or prospective evaluation. These are
**collapsed into one indicator**, which the peer review correctly identifies as a
limitation: a prospective single-centre study is not external validation. The flag should
be read as "any signal of validation beyond an internal random split", nothing stronger.

**code_or_data_flag** — abstract refers to released code or data (GitHub, Zenodo, "source
code", "publicly available", "open-source"). Links were **not** opened or verified, and
code, model weights, annotations and raw data are **not** distinguished.

**crossref_verified** — the DOI resolved against Crossref and full metadata were retrieved.
This verifies bibliographic metadata only; it is not eligibility validation.

## Screening rules
Two automated stages, both on title and abstract:
1. Title/abstract screen — domain terms present, method terms present, sperm/semen not
   merely incidental, species filter, imaging-vs-omics filter.
2. Eligibility assessment — an identifiable deep-learning architecture, an image/video/
   signal-based task, sperm as the analytic target; oocyte/embryo-only, classical-ML-only
   and term-collision records removed.

Rules were developed iteratively and inspected manually against samples of both included
and excluded records. **No formal calibration statistics (sensitivity, precision,
inter-rater agreement) were computed, and screening was performed by a single reviewer.**
One systematic failure was detected and corrected: records ingested without abstracts were
being rejected by the method rule, which was fixed by the Europe PMC back-fill and the
pipeline re-run from the beginning.

## Retraction screening
Crossref `update-to` relations and title prefixes were checked for all records with a
resolvable DOI (167 of 186).
Records without a resolvable DOI were **not** screened for retraction.
