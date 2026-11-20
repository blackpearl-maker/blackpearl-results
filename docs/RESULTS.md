# Public Results & Evidence

This page is the navigation and interpretation guide for the repository's published benchmark runs. Results are reported for distinct tasks and samples; the scores should not be collapsed into a single system-wide ranking.

## Review sequence

1. [Executive summary](../EXECUTIVE_SUMMARY.pdf) — high-level claims; read alongside the scoped evidence below.
2. [RUN007 execution report](../RUN007_report.pdf), [frozen manifest](../artifacts/frozen-runs/RUN007/MANIFEST.md), and [SHA-256 list](../artifacts/sha256/RUN007.sha256).
3. [RUN008 execution report](../RUN008_report.pdf), [frozen manifest](../artifacts/frozen-runs/RUN008/MANIFEST.md), and [SHA-256 list](../artifacts/sha256/RUN008.sha256).
4. [RUN004 benchmark report](../results/cybersecurity/black_pearl_report_20261120T042752Z.md), [evidence JSON](../results/cybersecurity/black_pearl_evidence_20261120T042752Z.json), [artifact status](../results/cybersecurity/RUN004_MANIFEST.md), and [interpretation/baseline review](../results/cybersecurity/RUN004_REVIEW.md).
5. [PEATH structural validation](../results/cybersecurity/PEATH_validation.md) and [PEATH report](../results/cybersecurity/PEATH_report.pdf); these are controlled synthetic tests, not real-world exploitation tests.
6. [Honeypot results and limitations](../results/cybersecurity/HONEYPOT_RESULTS.md) and frozen run files under [`artifacts/frozen-runs/HONEYPOT/`](../artifacts/frozen-runs/HONEYPOT/).
7. Supporting CSVs and reports in [`results/cybersecurity/`](../results/cybersecurity/).

## What the different results measure

### EPSS/CVSS baseline comparison is task-specific

RUN004 labels 299 records as CISA KEV positives and 381 NVD-only records as negatives. It measures discrimination between those labels in that sample; the report explicitly says it does not measure prediction of future exploitation. In this task, EPSS has the highest reported AUC (0.9825; 95% CI 0.973–0.991), followed by CVSS-only (0.7626; 0.724–0.799), 10_EF Coherence (0.7051; 0.661–0.747), and 9_EF Coherence (0.6919; 0.648–0.733). Reported P@10/P@50/P@100 are respectively 1.00/1.00/1.00 for EPSS, 0.50/0.68/0.68 for CVSS, 1.00/1.00/0.90 for 9_EF, and 1.00/1.00/0.99 for 10_EF. These metrics describe this sample and task only; they neither make EPSS and Coherence equivalent products nor test all intended engine domains.

A separate validation summary reports Spearman correlation with EPSS of +0.5580 for 9_EF and +0.3661 for CVSS, a difference of +0.1919. This is greater rank-association with EPSS in that separate 3,000-record non-KEV population, not a 19-percentage-point improvement, not an AUC comparison, and not proof of superior performance on every prioritization objective. See [`VALIDATION.md`](VALIDATION.md) for scope.

### Structural validation

PEATH reports AUC 1.0000 (95% CI [1.000, 1.000]) on 300 synthetic labeled scenarios, where the declared chain structure defines ground truth. The same report lists R@3/R@5/R@10 of 0.0200/0.0333/0.0667 for PEATH, equal to the sum-weight and finding-count baselines; MRR is 1.0000 for every listed method. Thus the AUC result is strong within that controlled classification test, while the retrieval metrics do not show a corresponding separation from those baselines. This does not establish real-world exploit prediction.

### Reproducibility and fingerprints

PEATH documentation reports matching truncated fingerprints (`07776c4d8496554fb67552bc6ce2d90f...`) and marks the match true. Because the displayed fingerprints are truncated, the full values cannot be independently compared from that text alone. RUN007/RUN008 manifests and checksum lists provide artifact integrity identifiers for their named files; artifact hashes are not, by themselves, evidence of repeated identical engine executions. RUN004's supplied evidence contains bootstrap AUC intervals but no repeated-run fingerprint record. See [`RUN004_REVIEW.md`](../results/cybersecurity/RUN004_REVIEW.md).

### Honeypot observation

Two honeypot reports state 600-second runs and zero events. The supplied timelines record two polls 10 seconds apart in run `HONEYPOT-20261010-170811` and one poll in run `HONEYPOT-20261010-170936`. The timelines therefore do not independently document a complete 600-second observation window. Interpret the zero-event result only within the recorded evidence; do not treat it as a broad false-positive-rate estimate. See [`HONEYPOT_RESULTS.md`](../results/cybersecurity/HONEYPOT_RESULTS.md).

## Limits and provenance

These are repository-reported results, not an independent audit or a guarantee of performance outside the stated datasets and conditions. Publication-window differences, NVD coverage, sample design, and the 10_EF `ransomware_flag` leakage risk are material caveats. The engine's source and internal algorithmic logic are not included here. Run identities and artifact provenance must remain separate; in particular, RUN007, RUN008, and RUN004 are distinct runs.
