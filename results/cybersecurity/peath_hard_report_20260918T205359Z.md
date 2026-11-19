# PEATH Hard Structural Path Validation

**Version:** V1.1
**Run ID:** PEATH-HARD-2026-09-18-RUN001
**Generated (UTC):** 2026-09-18T20:53:59.897590+00:00

## Design

- Both classes have the SAME length distribution (K ∈ {2,3,4} uniform).
- Both classes have the SAME severity distribution (uniform).
- Therefore, `finding_count`, `sum_weight`, `max_weight`, `max_cvss_like` are expected at ~0.5 (random).
- Only `PEATH_structural_coherence` should discriminate via structure.

- Scenarios: 300 (150 feasible / 150 infeasible)

## Metrics

| Method | AUC | 95% CI | MRR | R@3 | R@5 | R@10 |
|---|---|---|---|---|---|---|
| PEATH_structural_coherence | 0.9144 | [0.881, 0.943] | 1.0000 | 0.0200 | 0.0333 | 0.0667 |
| Baseline_max_weight | 0.4880 | [0.430, 0.550] | 0.5000 | 0.0067 | 0.0133 | 0.0400 |
| Baseline_sum_weight | 0.4808 | [0.416, 0.544] | 1.0000 | 0.0133 | 0.0267 | 0.0467 |
| Baseline_finding_count | 0.4888 | [0.427, 0.550] | 0.2500 | 0.0000 | 0.0067 | 0.0200 |
| Baseline_max_cvss_like | 0.4880 | [0.427, 0.547] | 0.5000 | 0.0067 | 0.0133 | 0.0400 |

## Determinism

- Fingerprint A: `00aec3ccd3cd9c6a83dd21d34b79dbc6…`
- Fingerprint B: `00aec3ccd3cd9c6a83dd21d34b79dbc6…`
- Match: **True**

## Interpretation

- Baselines near 0.5 confirm the confounds were removed.
- PEATH AUC reflects pure structural discrimination.
