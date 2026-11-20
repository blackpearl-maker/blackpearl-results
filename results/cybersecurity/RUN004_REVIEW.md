# RUN004: Interpretation, Baseline Comparison, and Reproducibility

**Run:** `BPV3-CISA-2026-09-15-RUN004` · **Version:** V3.4  
**Population stated in evidence:** 680 records (299 KEV positives, 381 NVD-only negatives)

EPSS, CVSS, and Coherence are different scoring approaches with different intended scopes. This benchmark compares their scores on one defined task; it is not a head-to-head evaluation of every use case of the Black Pearl engine.

## Reported results on this task

| Method | AUC (reported 95% CI) | P@10 | P@50 | P@100 |
|---|---:|---:|---:|---:|
| Random | 0.4709 [0.427, 0.516] | 0.10 | 0.42 | 0.39 |
| CVSS-only | 0.7626 [0.724, 0.799] | 0.50 | 0.68 | 0.68 |
| EPSS-only | **0.9825 [0.973, 0.991]** | **1.00** | **1.00** | **1.00** |
| 9_EF Coherence | 0.6919 [0.648, 0.733] | **1.00** | **1.00** | 0.90 |
| 10_EF Coherence | 0.7051 [0.661, 0.747] | **1.00** | **1.00** | 0.99 |

For this sample and label definition, EPSS has the highest AUC and perfect reported P@10/P@50/P@100. CVSS-only AUC is 0.7626. Coherence has perfect reported P@10/P@50, with lower AUC; P@100 is 0.90 for 9_EF and 0.99 for 10_EF. This is a material task-specific baseline result and is stated plainly. It does not show Coherence beating EPSS on this task, nor does it test the engine's full multi-domain structural-analysis and prioritization purposes.

The target is membership in CISA KEV: positives are KEV CVEs, negatives are NVD CVEs not in KEV. The report explicitly states that this is **not** prediction of future exploitation. The evidence also warns that the positive and negative publication windows may differ.

## Separate reported EPSS-correlation result

A separate validation summary reports a 3,000-record non-KEV comparison: Spearman correlation of 9_EF with EPSS is +0.5580 and CVSS with EPSS is +0.3661, difference +0.1919. This indicates greater rank association with EPSS for 9_EF in that comparison. It is not a 19-percentage-point improvement, not an AUC, and not a universal or end-to-end prioritization result. Do not combine it with RUN004's KEV-vs-NVD-only AUC table; they are different reported analyses/populations.

## Feature leakage and metric interpretation

- The 10_EF includes `ransomware_flag`, which the report says is non-zero only for KEV-listed ransomware CVEs. This risks target leakage in a KEV-vs-non-KEV test; interpret 10_EF as a flagged ablation, not clean generalization evidence. 9_EF excludes this field.
- P@k is precision among the top k in the tested sample. It is not a calibrated probability or, by itself, a guarantee of operational prioritization quality.
- The report notes that NVD CVSS coverage may be incomplete for recent CVEs and that independent replication is needed.

## Reproducibility confidence and integrity

The evidence includes 95% AUC intervals based on 2,000 resamples. These describe reported metric uncertainty under that resampling procedure; they do not verify bit-for-bit repeatability across engine executions. The supplied RUN004 evidence has no full output fingerprint or repeated-run match record, so this run's repeatability is **not established by the available RUN004 artifacts**. This does not mean the engine is nondeterministic; it marks the evidence boundary.

The evidence records SHA-256 `ad618e404a43d72ac6435b6e5a8d75000778b9245a6b70dbde46530152f2eef3` for the frozen CISA KEV snapshot. The report and evidence are committed, but their displayed GitHub blob IDs are SHA-1 object identifiers, not artifact SHA-256 checksums. The RUN004 population CSV was supplied in chat but is not yet committed, so the repository does not currently have a complete RUN004 artifact package or verified checksum for that CSV.

Keep RUN004 separate from the `...20261120T001020Z...` files: the accompanying report/evidence identifies RUN007, while the separately supplied manifest identifies RUN008. Those are not RUN004 artifacts.

## Bottom line

RUN004 favors EPSS by AUC and all three reported top-k precision cutoffs on this particular KEV-vs-NVD-only sample. Coherence nevertheless reports P@10/P@50 of 1.00 and a different score profile; this does not establish broad engine performance beyond this task. The separate 9_EF-versus-EPSS correlation result is a different analysis and should be described as rank association only. Assess structural prioritization with task-specific structural benchmarks, leakage controls, full untruncated repeat-run fingerprints, verified artifact hashes, and independent replication.
