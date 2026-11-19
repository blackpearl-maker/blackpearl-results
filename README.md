# BlackPearl — Public Validation Results

This repository publishes selected validation reports and reproducibility evidence for the BlackPearl deterministic engine. It is an evidence repository; it does **not** contain the engine's source code or provide a runnable software package.

## Start here

1. Read the [validation overview](docs/VALIDATION.md) for the reported tests, metrics, and scope.
2. Follow the [results review guide](docs/RESULTS.md) to inspect reports and supporting artifacts.
3. See [methodology and provenance](docs/METHODOLOGY.md) and the [independent review request](docs/REVIEW_REQUEST.md) for context on data and review boundaries.

## Evidence

The [`results/cybersecurity/`](results/cybersecurity/) directory contains validation reports, PDFs, CSV summaries, and JSON evidence. The [`artifacts/`](artifacts/) directory contains frozen-run materials and checksums. Consult manifests and scope notes alongside any reported result.

Selected reports:

- [RUN007 report](results/cybersecurity/RUN007_report.pdf)
- [PEATH report](results/cybersecurity/PEATH_report.pdf)
- [Executive summary](EXECUTIVE_SUMMARY.pdf)
- [Detailed results and caveats](docs/RESULTS.md)

Some reports may also exist as root-level or legacy copies. The links above point to the intended review locations where available; see the directory listings if a link is unavailable.

## Important interpretation notes

- Published metrics are repository-reported results, not an independent audit or a guarantee of performance beyond the stated datasets and test conditions.
- PEATH uses synthetic scenarios and does not establish real-world exploit prediction performance.
- A bounded honeypot observation should not be generalized beyond its stated monitoring window and conditions.
- The engine implementation and internal logic are proprietary and are not included here.

## Reproducibility and review

Reviewers can inspect the published inputs, manifests, checksums, and reports. This repository does not include a public command-line interface or enough implementation detail to rerun the engine itself. Please open an issue for questions or technical feedback; do not post sensitive data or proprietary code.

## License

See [LICENSE](LICENSE). The published materials are reserved for review and validation use; reuse requires permission from the rights holder.
