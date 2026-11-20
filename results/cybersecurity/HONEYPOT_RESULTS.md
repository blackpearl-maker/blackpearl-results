# Honeypot Results and Artifact Index

Two passive-listener runs are currently documented:

| Run ID | Reported duration | Polls recorded | Events | Package |
|---|---:|---:|---:|---|
| `HONEYPOT-20261010-170811` | 600 s | 2 | 0 | [`artifacts/frozen-runs/HONEYPOT/`](../../artifacts/frozen-runs/HONEYPOT/) — files ending `170828Z` |
| `HONEYPOT-20261010-170936` | 600 s | 1 | 0 | [`artifacts/frozen-runs/HONEYPOT/`](../../artifacts/frozen-runs/HONEYPOT/) — files ending `170940Z` |

Each package has an evidence JSON, report, timeline CSV, and manifest. The SHA-256 entries for the six report/evidence/timeline artifacts are in [`artifacts/sha256/HONEYPOT.sha256`](../../artifacts/sha256/HONEYPOT.sha256). The manifests state `events_csv: null` for both runs; no events CSV was supplied.

## Important observation-window caveat

The reports/manifests state a 600-second duration, but the supplied timelines record only two polls 10 seconds apart for the `170828Z` run and one poll for the `170940Z` run. Those timelines do not demonstrate continuous 600-second observation. The zero-event finding must therefore be interpreted as limited to the recorded polling data; do not present these artifacts as evidence of a fully observed 10-minute window unless additional logs substantiate it.

These are repository-published artifacts, not independent verification of the honeypot deployment or its monitoring coverage. Additional files may be added when supplied and checked against the run manifests.
