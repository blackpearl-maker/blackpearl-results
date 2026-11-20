# BlackPearl — Public Validation Results

This repository publishes selected validation reports and reproducibility evidence for the BlackPearl deterministic engine. It is an evidence repository; it does **not** contain the engine source code.

## Start here

1. [Validation overview](docs/VALIDATION.md) — task-scoped metrics and caveats.
2. [Results review guide](docs/RESULTS.md) — how to interpret and navigate the runs.
3. [Methodology and provenance](docs/METHODOLOGY.md) and [independent review request](docs/REVIEW_REQUEST.md).
4. [Cybersecurity results index](results/cybersecurity/README.md).

## Selected reports and evidence

- [Executive summary](EXECUTIVE_SUMMARY.pdf)
- [RUN007 report](RUN007_report.pdf) and [frozen checksum list](artifacts/sha256/RUN007.sha256)
- [RUN008 report](RUN008_report.pdf) and [frozen checksum list](artifacts/sha256/RUN008.sha256)
- [RUN004 report](results/cybersecurity/black_pearl_report_20261120T042752Z.md), [evidence](results/cybersecurity/black_pearl_evidence_20261120T042752Z.json), and [interpretation/reproducibility review](results/cybersecurity/RUN004_REVIEW.md)
- [PEATH synthetic structural validation](results/cybersecurity/PEATH_validation.md)
- [Honeypot run results and observation-window caveat](results/cybersecurity/HONEYPOT_RESULTS.md)
- [Detailed results and caveats](docs/RESULTS.md)

EPSS, CVSS, and Coherence are not interchangeable. The RUN004 KEV-vs-NVD-only sample favors EPSS by AUC; that task-specific outcome does not evaluate every structural-analysis or prioritization capability of the engine. See the review guide before drawing broader conclusions.

## Important interpretation notes

- Published metrics are repository-reported results, not an independent audit or a performance guarantee beyond stated datasets and conditions.
- PEATH uses synthetic scenarios and does not establish real-world exploitation performance.
- Honeypot zero-event observations are bounded by the recorded timeline coverage.
- Run manifests and SHA-256 checksums must be tied to the correct run and exact artifact bytes.
- The engine implementation and internal logic are proprietary and not included here.

## Reproducibility and license

Reviewers can inspect published inputs, manifests, checksums, and reports. The repository does not include a public CLI or enough implementation detail to independently rerun the engine. See [LICENSE](LICENSE); published materials are reserved for review and validation use, and reuse requires rights-holder permission.
