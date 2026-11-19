# PEATH Structural Path Validation

**Version:** V1.0
**Run ID:** PEATH-STRUCT-2026-09-18-RUN001
**Generated (UTC):** 2026-09-18T20:38:05.054061+00:00

## Scope

Controlled structural test on synthetic labeled findings. Ground truth = declared chain structure. This does NOT measure real-world exploitation prediction.

## Design

- Synthetic labeled dataset, seed `42`
- 300 scenarios (150 feasible / 150 infeasible)
- Feasible = consecutive attack stages starting at recon.
- Infeasible = single, same-stage cluster, or stage gap (1→3).

## Metrics

| Method | AUC | 95% CI | MRR | R@3 | R@5 | R@10 |
|---|---|---|---|---|---|---|
| PEATH_structural_coherence | 1.0000 | [1.000, 1.000] | 1.0000 | 0.0200 | 0.0333 | 0.0667 |
| Baseline_max_weight | 0.6622 | [0.609, 0.712] | 1.0000 | 0.0200 | 0.0267 | 0.0600 |
| Baseline_sum_weight | 0.9603 | [0.940, 0.978] | 1.0000 | 0.0200 | 0.0333 | 0.0667 |
| Baseline_finding_count | 0.9716 | [0.957, 0.985] | 1.0000 | 0.0200 | 0.0333 | 0.0667 |
| Baseline_max_cvss_like | 0.6622 | [0.610, 0.715] | 1.0000 | 0.0200 | 0.0267 | 0.0600 |

## Determinism

- Fingerprint A: `07776c4d8496554fb67552bc6ce2d90f…`
- Fingerprint B: `07776c4d8496554fb67552bc6ce2d90f…`
- Match: **True**
