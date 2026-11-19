# BlackPearl Deterministic Engine: Public Validation Results

This repository publishes validation reports, frozen run artifacts, and cryptographic integrity evidence for the BlackPearl Engine V3.6. It is an evidence repository; the engine's source code and internal logic are not published.

## Review the reports in order

The four PDF files currently visible in the repository root are:

1. [Executive summary — currently named `EXECUTIVE_SUMMRY.pdf` (filename typo)](EXECUTIVE_SUMMRY.pdf)
2. [RUN007 execution report](RUN007_report.pdf)
3. [RUN008 execution report — currently named `RUN008.pdf`](RUN008.pdf)
4. [PEATH structural validation report](PEATH_report.pdf)

For a clean presentation, please download these PDFs and re-upload them under `results/cybersecurity/` with the intended names `EXECUTIVE_SUMMARY.pdf`, `RUN007_report.pdf`, `RUN008_report.pdf`, and `PEATH_report.pdf`. The binary files are currently in the root, so the intended folder links are not active yet. See [`results/cybersecurity/README.md`](results/cybersecurity/README.md) for the upload steps and validation caveats.

## Supporting evidence

- [Validation claims and scope](docs/VALIDATION.md)
- [Results and reviewer guidance](docs/RESULTS.md)
- [Methodology and provenance](docs/METHODOLOGY.md)
- [Independent review request](docs/REVIEW_REQUEST.md)
- Frozen run artifacts and checksums under [`artifacts/`](artifacts/)

## Important scope notes

The published values are claims reported by the repository, not an independent audit or a guarantee beyond the described test conditions. The PEATH evaluation uses synthetic scenarios and is not a real-world exploitation prediction test. The honeypot summary describes one 600-second observation window. No `diagrams/` directory or visual assets are currently present in this repository; references to those images should be treated as unavailable until the actual files are added.

For technical questions or review feedback, open an issue. Do not upload sensitive customer data or proprietary engine code.
