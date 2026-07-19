# EEG-Based Seizure Prediction

**Capstone Project — Phase A**
Software Engineering Department, Braude College of Engineering
**Team Code:** 26-2-R-7

Epileptic Seizure Detection and Prediction using EEG.

## Overview

For people with drug-resistant epilepsy, the most disabling feature is the
unpredictability of seizure onset. This project builds on the **Complexity
Collapse** hypothesis — that a seizure is the brain becoming *simpler*, collapsing
from high-entropy neural diversity into a single, rigidly synchronized mode — and
re-engineers it from an offline description into a real-time predictor light enough
to run on a wearable.

Our contribution is **Ψ (Psi)**, a deterministic collapse operator that scores each
window of EEG along three axes, computed by streaming-friendly algorithms:

- **Informational** — Multiscale Lempel–Ziv Complexity (MLZC) over binarized streams
- **Coherence** — Phase-Locking Value (PLV) from phase-binarized bits
- **Topological** — three scalar summaries of a persistent-homology diagram

The three axes are fused into a single weighted score. A **Soft Fusion**
post-processing stage (rolling Top-K average) stabilizes alarms and suppresses
artifacts. At deployment, Ψ reduces to three multiplications and two additions per
window — no model inference, no GPU.

## Goal

Demonstrate that an interpretable, low-power, theoretically grounded operator can
reach clinically useful seizure-prediction performance under real wearable
constraints — not to beat deep-learning predictors on raw sensitivity.

## Dataset

[CHB-MIT Scalp EEG Database](https://physionet.org/content/chbmit/1.0.0/) — 22
subjects (23 cases), 664 EDF recordings, 198 annotated seizures, sampled at 256 Hz.
Evaluated under strict leave-one-subject-out cross-validation.

## Evaluation Metrics

- Event-Based F1
- False Prediction Rate per hour (FPR/h)
- Seizure Prediction Horizon / Seizure Occurrence Period (SPH / SOP)

## Efficiency (order-of-magnitude, per window)

| Axis | Reduction |
|---|---|
| MLZC | ~8× compute |
| PLV | ~100× compute |
| Persistent homology | ~30× retained size |
| Per-window memory | ~47× |

Exact wall-clock and energy figures are a Phase B deliverable.

## Documents

- [Phase A Report (PDF)](Capstone_Project_PhaseA_26-2-R-7.pdf)
- [Phase A Presentation (PPTX)](Seizure_Prediction_PhaseA_Ibrahim_Assad_Safa_Awad.pptx)

## Team

- Ibrahim Asad
- Safa Awad

**Advisor:** Dr. Samah Idrees Ghazawi

## Planned Tools (Phase B)

Python · NumPy / SciPy · MNE-Python / pyEDFlib · Ripser / GUDHI · scikit-learn ·
Matplotlib / pandas
