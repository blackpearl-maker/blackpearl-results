# Public Results & Evidence

## Recommended review sequence

Review the material in this order so the summary is followed by the underlying runs and then the scope and supporting evidence:

1. **Executive summary:** [`results/cybersecurity/EXECUTIVE_SUMMARY.pdf`](../results/cybersecurity/EXECUTIVE_SUMMARY.pdf). If the PDF is not uploaded yet, start with [`VALIDATION.md`](VALIDATION.md).
2. **RUN007:** [`results/cybersecurity/RUN007_report.pdf`](../results/cybersecurity/RUN007_report.pdf), then compare the [RUN007 manifest](../artifacts/frozen-runs/RUN007/MANIFEST.md) and [checksums](../artifacts/sha256/RUN007.sha256).
3. **RUN008:** [`results/cybersecurity/RUN008_report.pdf`](../results/cybersecurity/RUN008_report.pdf), then inspect the [RUN008 manifest](../artifacts/frozen-runs/RUN008/manifest.json) and [checksums](../artifacts/sha256/RUN008.sha256).
4. **PEATH:** [`results/cybersecurity/PEATH_report.pdf`](../results/cybersecurity/PEATH_report.pdf), alongside the [detailed validation](../results/cybersecurity/PEATH_validation.md) and [frozen manifest](../artifacts/frozen-runs/PEATH/manifest.json). This is a controlled synthetic test, not a real-world exploitation prediction evaluation.
5. **Supporting results:** [Non-KEV validation](../results/cybersecurity/NONKEV_validation.md), `metrics.csv`, `epss_comparison.csv`, and `signal_benchmark.csv` in [`results/cybersecurity/`](../results/cybersecurity/).
6. **Honeypot:** review the one-window summary below and the frozen report, timeline, manifest, and checksums under [`artifacts/frozen-runs/HONEYPOT/`](../artifacts/frozen-runs/HONEYPOT/) and [`artifacts/sha256/HONEYPOT.sha256`](../artifacts/sha256/HONEYPOT.sha256).

The PDFs are intended to be the first, human-readable layer; manifests, hashes, CSVs, and JSON provide supporting evidence. If a PDF link is unavailable, that PDF has not yet been uploaded, and the linked Markdown evidence should be used instead.

## Reported validation results

- **Determinism:** The reports state matching output fingerprints for repeated runs on frozen inputs. Review the run manifests and hashes to assess the evidence for those specific executions.
- **KEV statistical test:** The validation summary reports a randomization-test p-value of 0.0020 on 1,766 CISA KEV records and a ransomware correlation of +0.090.
- **Non-KEV comparison:** The report gives Spearman correlations of +0.5580 for the engine's 9_EF feature and +0.3661 for CVSS against EPSS (difference +0.1919). This is a correlation comparison, not a measured percentage improvement in operational outcomes.
- **PEATH:** The reported AUC of 1.0000 is from 300 synthetic, labeled scenarios. The report explicitly says this does not measure real-world exploitation prediction.
- **Honeypot:** The published run reports zero events and zero false positives during one 600-second passive monitoring window. This is a bounded observation, not evidence for all production conditions.

These are repository-reported results, not an independent audit or a guarantee of performance outside the described datasets and test conditions. The source code and internal algorithmic logic are not published.
