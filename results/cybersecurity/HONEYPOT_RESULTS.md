# Honeypot Results and Artifact Index

Two passive-listener runs are supplied and indexed separately:

| Run ID | Reported duration | Timeline polls provided | Events recorded | Artifacts |
|---|---:|---:|---:|---|
| `HONEYPOT-20261010-170811` | 600 s | 2 (elapsed 0–10 s) | 0 | Files ending `170828Z` in [`artifacts/frozen-runs/HONEYPOT/`](../../artifacts/frozen-runs/HONEYPOT/) |
| `HONEYPOT-20261010-170936` | 600 s | 1 (elapsed 0 s) | 0 | Files ending `170940Z` in [`artifacts/frozen-runs/HONEYPOT/`](../../artifacts/frozen-runs/HONEYPOT/) |

Each package has an evidence JSON, report, timeline CSV, and manifest. The manifests list `events_csv: null`. The corresponding SHA-256 values supplied in the manifests are catalogued in [`artifacts/sha256/HONEYPOT.sha256`](../../artifacts/sha256/HONEYPOT.sha256).

## Observation-window interpretation

Both reports state a duration of 600 seconds and describe passive listeners with no outgoing traffic. The supplied timeline evidence, however, records only two polls 10 seconds apart for the first run and one poll for the second. The timelines therefore do not independently document the full reported 600-second interval. This does not prove that the process ran for only 10 seconds; it means the artifacts provided here are insufficient to verify full-window polling coverage. The zero-event and zero-anomaly observations should be presented with that limitation, not generalized into a broad false-positive-rate or deployment-performance claim.

The first run's JSON/report/timeline were reconstructed from the text supplied in chat before publication. Their manifest SHA-256 values are retained as supplied but have not been independently recomputed against the committed bytes; verify against the original files before treating the checksums as confirmed. The second run's existing frozen artifacts and checksum list are preserved as-is.

These are published run artifacts, not independent verification of deployment configuration, monitoring coverage, or operational performance. Additional files can be indexed when supplied and verified against their run manifests.
