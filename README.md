# BlackPearl — Public Validation Results

This repository publishes selected validation reports and reproducibility evidence for the BlackPearl deterministic engine. It is an evidence repository; it does **not** contain the engine source code or enough implementation detail to independently rerun the engine.

## Start here

1. Read the [validation overview](docs/VALIDATION.md) for task-scoped metrics, baselines, and caveats.
2. Follow the [results review guide](docs/RESULTS.md) for the recommended review sequence and interpretation boundaries.
3. See [methodology and provenance](docs/METHODOLOGY.md) and the [independent review request](docs/REVIEW_REQUEST.md).
4. Browse the [cybersecurity results index](results/cybersecurity/README.md).

## Published runs and reports

- [Executive summary](EXECUTIVE_SUMMARY.pdf)
- [RUN007 execution report](RUN007_report.pdf), [frozen manifest](artifacts/frozen-runs/RUN007/MANIFEST.md), and [SHA-256 list](artifacts/sha256/RUN007.sha256)
- [RUN008 execution report](RUN008_report.pdf), [frozen manifest](artifacts/frozen-runs/RUN008/MANIFEST.md), and [SHA-256 list](artifacts/sha256/RUN008.sha256)
- [RUN004 controlled benchmark report](results/cybersecurity/black_pearl_report_20261120T042752Z.md), [evidence JSON](results/cybersecurity/black_pearl_evidence_20261120T042752Z.json), [artifact status](results/cybersecurity/RUN004_MANIFEST.md), and [baseline/reproducibility review](results/cybersecurity/RUN004_REVIEW.md)
- [PEATH synthetic structural-path validation](results/cybersecurity/PEATH_validation.md) and [report](results/cybersecurity/PEATH_report.pdf)
- [Honeypot reports, artifacts, and observation-window caveat](results/cybersecurity/HONEYPOT_RESULTS.md)
- Additional [validation tables and supporting results](results/cybersecurity/)

## How to read the baseline comparisons

EPSS, CVSS, and Coherence are different scoring approaches and are not interchangeable measures of the engine's full capabilities.

In RUN004's specific task—distinguishing 299 CISA KEV-listed CVEs from 381 NVD-only CVEs—EPSS reports AUC **0.9825**, CVSS-only **0.7626**, 9_EF Coherence **0.6919**, and 10_EF Coherence **0.7051**. EPSS reports P@10/P@50/P@100 of **1.00/1.00/1.00**; Coherence reports **1.00/1.00/0.90** for 9_EF and **1.00/1.00/0.99** for 10_EF. Thus, EPSS leads by AUC and P@100 in this sample, while Coherence also reports perfect precision at the top 10 and top 50. This is a material result for this benchmark task—not a verdict on all structural-analysis or prioritization uses of the engine. The benchmark does not measure prediction of future exploitation.

A separate reported analysis on 3,000 non-KEV records gives Spearman correlation with EPSS of **+0.5580** for 9_EF and **+0.3661** for CVSS (difference **+0.1919**). This is greater rank association with EPSS in that separate analysis; it is not a 19-percentage-point improvement, an AUC result, or universal proof of prioritization superiority. The populations and metrics are different; see [the validation overview](docs/VALIDATION.md) and [RUN004 review](results/cybersecurity/RUN004_REVIEW.md).

## Structural validation and reproducibility

PEATH reports AUC **1.0000** on 300 synthetic scenarios whose declared chain structure defines ground truth. Its retrieval metrics are also reported: PEATH R@3/R@5/R@10 is **0.0200/0.0333/0.0667**, matching the sum-weight and finding-count baselines; MRR is 1.0000 for every listed method. This supports a result on the defined synthetic test, not real-world exploitation prediction or a universal advantage across metrics.

The PEATH report marks two displayed, **truncated** fingerprints as matching. RUN007/RUN008 manifests and checksum lists identify frozen artifacts, but artifact hashes alone do not prove repeated engine executions produce bit-for-bit identical outputs. The supplied RUN004 evidence contains no full repeat-run fingerprint. See [validation and reproducibility details](docs/VALIDATION.md).

## Artifact completeness and limits

- The RUN004 report and evidence JSON are published, but its population CSV (`black_pearl_population_20261120T042752Z.csv`) has not yet been committed. The RUN004 artifact manifest records this gap.
- Keep runs and hashes tied to their own run IDs. RUN007, RUN008, and RUN004 are distinct; do not attach one run's manifest or hashes to another.
- The two honeypot reports state 600-second durations, but their supplied timelines contain only two polls 10 seconds apart and one poll, respectively. Those timelines do not independently verify full 600-second polling coverage; the zero-event observation must be read with that limitation.
- Published metrics are repository-reported results, not an independent audit or a guarantee beyond the stated datasets and conditions. Sampling windows, NVD coverage, and the 10_EF `ransomware_flag` leakage risk are material caveats.
- The engine implementation and internal logic are proprietary and are not included here.

See the [upload checklist](UPLOAD_CHECKLIST.md) for outstanding publication and verification items. Review the [LICENSE](LICENSE): published materials are reserved for review and validation use; reuse requires permission from the rights holder.
