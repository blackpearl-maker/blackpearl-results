# Black Pearl V3 – Controlled Validation Benchmark

**Version:** V3.4
**Run ID:** BPV3-CISA-2026-09-15-RUN004
**Generated (UTC):** 2026-11-20T04:27:52.423847+00:00

## Population

- Total records: **680**
- Positives (KEV): **299**
- Negatives (NVD-only): **381**

## Validation notice

Positive class = CVE in CISA KEV. Negative class = CVE present in NVD but not in KEV. This evaluates discrimination between KEV-listed and non-KEV vulnerabilities. It does NOT measure prediction of future exploitation.

## Methodology

Coherence is an internal deterministic prioritisation score. It is not CVSS, a calibrated exploit probability, a breach probability, or measured detection accuracy.

## Feature sets

### 9-key EF

1. `cvss_base_norm`
2. `attack_vector_norm`
3. `attack_complexity_norm`
4. `privileges_required_norm`
5. `user_interaction_norm`
6. `impact_norm`
7. `exploitability_norm`
8. `vendor_criticality`
9. `recency_norm`

### 10-key EF

1. `cvss_base_norm`
2. `attack_vector_norm`
3. `attack_complexity_norm`
4. `privileges_required_norm`
5. `user_interaction_norm`
6. `impact_norm`
7. `exploitability_norm`
8. `vendor_criticality`
9. `recency_norm`
10. `ransomware_flag`

## Validation results

| Method          | AUC    | AUC 95% CI     | P@10   | P@50   | P@100  |
| --------------- | ------ | -------------- | ------ | ------ | ------ |
| Random          | 0.4709 | [0.427, 0.516] | 0.1000 | 0.4200 | 0.3900 |
| CVSS-only       | 0.7626 | [0.724, 0.799] | 0.5000 | 0.6800 | 0.6800 |
| EPSS-only       | 0.9825 | [0.973, 0.991] | 1.0000 | 1.0000 | 1.0000 |
| 9_EF Coherence  | 0.6919 | [0.648, 0.733] | 1.0000 | 1.0000 | 0.9000 |
| 10_EF Coherence | 0.7051 | [0.661, 0.747] | 1.0000 | 1.0000 | 0.9900 |

## Ablation: feature set × weights

| Config | Feature set | Weights | AUC | P@50 | P@100 |
|---|---|---|---|---|---|
| `9_EF_canonical` | 9_EF | 0.40/0.35/0.25 | 0.6919 | 1.0000 | 0.9000 |
| `9_EF_equal` | 9_EF | 0.33/0.33/0.33 | 0.6893 | 1.0000 | 0.9400 |
| `10_EF_canonical` | 10_EF | 0.40/0.35/0.25 | 0.7051 | 1.0000 | 0.9900 |
| `10_EF_equal` | 10_EF | 0.33/0.33/0.33 | 0.7109 | 1.0000 | 1.0000 |

## Limitations

- Positives (KEV) and negatives (NVD-only) may differ in publication windows.
- The 10-key EF includes `ransomware_flag`, which is only non-zero for KEV-listed ransomware CVEs. This creates target leakage in the KEV-vs-non-KEV task and is included as an ablation.
- Vendor criticality for non-KEV records defaults to 0.5.
- CVSS coverage from NVD may be incomplete for very recent CVEs.
- No operational telemetry, no endpoint events, no live IDS alerts.
- Results are preliminary and require independent replication.

## Next steps

1. Match positives and negatives to a common publication window.
2. Independent replication using the frozen KEV snapshot hash above.
3. Add EPSS historical trajectories as temporal features.
4. Technical review by a cybersecurity practitioner and a statistician.
