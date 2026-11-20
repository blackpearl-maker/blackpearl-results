# Validation & Statistical Evidence

This page summarizes reported tests and identifies what each can support. Results are repository-reported; they are not an independent audit.

## 1. Deterministic reproducibility and fingerprints

The supplied PEATH structural report displays two matching **truncated** fingerprints beginning `07776c4d8496554fb67552bc6ce2d90f...` and marks `Match: True`. This is evidence that the report claims a match for that test, but the shortened values do not allow an independent full-hash comparison here. RUN007 and RUN008 have frozen artifact manifests and SHA-256 lists, which support integrity checking of those named artifacts; artifact hashes alone do not prove repeated engine runs produced identical outputs. The RUN004 evidence provided here does not include a repeated-run fingerprint or match record.

## 2. KEV/ransomware statistical test

The published validation summary reports 1,766 CISA KEV records, ransomware correlation `r = +0.090`, and a randomization test with 1,000 shuffles and `p = 0.0020`. These figures describe the stated dataset/test; they do not establish causal association or future exploitation prediction.

## 3. EPSS correlation comparison (separate population/task)

For a reported population of 3,000 non-KEV records, the summary gives Spearman correlation `+0.5580` between 9_EF and EPSS and `+0.3661` between CVSS and EPSS, a difference of `+0.1919`. This means 9_EF had greater rank association with EPSS than CVSS did in that reported comparison. It is not a 19-percentage-point gain, does not compare AUC, and does not establish universal or end-to-end prioritization superiority. EPSS and Coherence represent different measures and intended uses.

## 4. RUN004: KEV versus NVD-only benchmark

RUN004 reports 680 records (299 KEV positives and 381 NVD-only negatives). Its scope is discrimination between those classes in this sample; it explicitly does **not** measure future-exploitation prediction.

| Method | AUC (reported 95% CI) | P@10 | P@50 | P@100 |
|---|---:|---:|---:|---:|
| Random | 0.4709 [0.427, 0.516] | 0.10 | 0.42 | 0.39 |
| CVSS-only | 0.7626 [0.724, 0.799] | 0.50 | 0.68 | 0.68 |
| EPSS-only | 0.9825 [0.973, 0.991] | 1.00 | 1.00 | 1.00 |
| 9_EF Coherence | 0.6919 [0.648, 0.733] | 1.00 | 1.00 | 0.90 |
| 10_EF Coherence | 0.7051 [0.661, 0.747] | 1.00 | 1.00 | 0.99 |

For this benchmark task, EPSS has the highest reported overall AUC and perfect reported top-k precision; Coherence has perfect P@10/P@50, with lower AUC and lower P@100 for 9_EF (10_EF P@100 is 0.99). This task-specific result does not test all broader structural-analysis or prioritization use cases of the engine. Positive/negative publication windows may differ. The 10_EF `ransomware_flag` is non-zero only for some KEV-listed ransomware CVEs and creates target-leakage risk; treat it as an ablation, not clean generalization evidence. Detailed discussion and artifact status: [`RUN004_REVIEW.md`](../results/cybersecurity/RUN004_REVIEW.md).

## 5. PEATH synthetic structural-path test

PEATH reports 300 synthetic labeled scenarios (150 feasible and 150 infeasible), seed 42. The ground truth is the declared chain structure; this is not a real-world exploitation prediction test.

| Method | AUC (95% CI) | MRR | R@3 | R@5 | R@10 |
|---|---:|---:|---:|---:|---:|
| PEATH structural coherence | 1.0000 [1.000, 1.000] | 1.0000 | 0.0200 | 0.0333 | 0.0667 |
| Baseline max weight | 0.6622 [0.609, 0.712] | 1.0000 | 0.0200 | 0.0267 | 0.0600 |
| Baseline sum weight | 0.9603 [0.940, 0.978] | 1.0000 | 0.0200 | 0.0333 | 0.0667 |
| Baseline finding count | 0.9716 [0.957, 0.985] | 1.0000 | 0.0200 | 0.0333 | 0.0667 |
| Baseline max CVSS-like | 0.6622 [0.610, 0.715] | 1.0000 | 0.0200 | 0.0267 | 0.0600 |

The perfect reported AUC supports discrimination on this defined synthetic dataset. Retrieval metrics are also shown: MRR is 1.0 for all methods, and PEATH R@3/R@5/R@10 equals the sum-weight and finding-count baselines. Interpret each metric rather than inferring a universal advantage from AUC alone. Full report: [`PEATH_validation.md`](../results/cybersecurity/PEATH_validation.md).

## 6. Honeypot

Two passive-listener reports state 600-second duration and zero events. The timelines supplied for `HONEYPOT-20261010-170811` and `HONEYPOT-20261010-170936` contain only two polls 10 seconds apart and one poll, respectively. They do not independently establish a continuous 600-second observation. Zero events in these records is not a broad false-positive-rate estimate. See [`HONEYPOT_RESULTS.md`](../results/cybersecurity/HONEYPOT_RESULTS.md).

## 7. Integrity, limitations, and next review

SHA-256 values in frozen manifests/checksum lists identify specific artifacts and should be checked against the exact bytes. The RUN004 report/evidence are published, but its supplied population CSV is not yet committed; the RUN004 manifest documents this gap and distinguishes Git blob IDs from SHA-256. Keep run files and hashes attached to their own run IDs. Independent replication, matched publication windows, full fingerprints, leakage-controlled ablations, and task-specific baselines remain appropriate review steps.
