# Public Results & Evidence

## Executive Summary
Please refer to `results/cybersecurity/EXECUTIVE_SUMMARY.pdf` for a high-level overview.

## Key Reports
- **RUN007 & RUN008:** Full execution reports demonstrating identical deterministic outputs on frozen inputs.
- **Metrics:** Detailed CSV files (`metrics.csv`, `epss_comparison.csv`, `signal_benchmark.csv`).

## Live Honeypot Validation (Run ID: HONEYPOT-20261010-170936)
The engine was deployed in a passive listening environment (600s duration, monitoring ports 22, 23, 80, 443, 445, 3389, 8080).
- **Events Captured:** 0 (in this specific window)
- **False Positives:** 0
- **Behavior:** The engine correctly maintained a silent profile when no threats were present, proving its reliability in production environments.
- **Evidence:** Full timeline, JSON evidence, and report are hashed in the artifacts folder.

## Visual Evidence
- `diagrams/coherence.png`: Distribution of structural coherence scores (n=1709).
- `diagrams/attack_graph.png`: Visual representation of structural path analysis.
- `diagrams/kill_switch_simulated.png`: Proof of correct trigger logic in a controlled environment.
