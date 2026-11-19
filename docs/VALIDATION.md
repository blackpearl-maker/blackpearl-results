# Validation & Statistical Evidence

## 1. Deterministic Reproducibility & Fingerprinting
The BlackPearl Engine has been executed across multiple identical runs using frozen datasets.
- **Output Fingerprints:**
  - Fingerprint A: `07776c4d8496554fb67552bc6ce2d90f...`
  - Fingerprint B: `07776c4d8496554fb67552bc6ce2d90f...`
  - **Match: True**
- The output hashes are bit-for-bit identical across all executions.
- Input datasets are frozen and secured with SHA-256.

## 2. Statistical Significance (Ransomware Correlation)
In a dataset of 1,766 records (CISA KEV catalog), the engine's structural coherence score demonstrated a non-random correlation with ransomware presence:
- **Observed Correlation (r):** +0.090
- **Randomization Test:** 1,000 shuffles.
- **p-value:** 0.0020 (Statistically significant, outside the null distribution).

## 3. Baseline Comparison (EPSS Correlation)
In a population of 3,000 non-KEV records, the engine's feature set (9_EF) demonstrated a significantly higher correlation with EPSS compared to standard CVSS:
- **Spearman (9_EF, EPSS):** +0.5580
- **Spearman (CVSS, EPSS):** +0.3661
- **Delta:** +0.1919 (indicating superior prioritization capability).

## 4. Synthetic Structural Path Validation (PEATH)
The engine was tested on 300 synthetic labeled scenarios (150 feasible / 150 infeasible).
- **PEATH AUC:** 1.0000 (95% CI: [1.000, 1.000])
- **Scope Notice:** This controlled test measures structural coherence logic, not real-world exploitation.
- Full report: `PEATH_validation.md`.

## 5. Mathematical Foundation: Structural Discrimination
The engine's core equation (C) was tested against standard time-series signals to prove its ability to differentiate between structural coherence and stochastic noise.
- **Deterministic Structure (`sine`):** Mean C = 0.5022 (Highest coherence).
- **Pure Stochastic Noise (`white_noise`):** Mean C = 0.3857 (Lowest coherence).
- **Noise Indicator (`K`):** Correctly spikes for `random_walk` (0.2579) and `white_noise` (0.2180), while remaining low for `sine` (0.1171).
This confirms the engine does not suffer from "noise hallucination" and can reliably filter out random artifacts from genuine structural patterns.
