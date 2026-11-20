# RUN004: Interpretation, Baseline Comparison, and Reproducibility

**Run:** `BPV3-CISA-2026-09-15-RUN004` · **Version:** V3.4  
**Population stated in evidence:** 680 records (299 KEV positives, 381 NVD-only negatives)

This review is about what this run measures and what it does not. EPSS, CVSS, and Coherence are not interchangeable products. The RUN004 comparison uses them as scoring methods in one specified KEV-vs-NVD-only discrimination task; it is not a general evaluation of every use case of the Black Pearl engine.

## Results in the stated task

| Method | AUC (reported 95% CI) | P@10 | P@50 | P@100 |
|---|---:|---:|---:|---:|
| Random | 0.4709 [0.427, 0.516] | 0.10 | 0.42 | 0.39 |
| CVSS-only | 0.7626 [0.724, 0.799] | 0.50 | 0.68 | 0.68 |
| EPSS-only | **0.9825 [0.973, 0.991]** | **1.00** | **1.00** | **1.00** |
| 9_EF Coherence | 0.6919 [0.648, 0.733] | **1.00** | **1.00** | 0.90 |
| 10_EF Coherence | 0.7051 [0.661, 0.747] | **1.00** | **1.00** | 0.99 |

In this run and task, EPSS has the strongest reported overall discrimination by AUC and perfect reported precision at the top 10, 50, and 100. CVSS-only AUC is 0.7626. Coherence has lower AUC than both baselines here, while its reported top-10 and top-50 precision is 1.00 for both feature sets; at top 100, 9_EF is 0.90 and 10_EF is 0.99. These are meaningful but different metric profiles. They do **not** show that Coherence beats EPSS on this task, and they do **not** establish that EPSS covers the broader structural analysis or prioritization purposes for which the engine is intended.

**Scope boundary:** the benchmark labels positives as CVEs listed in CISA KEV and negatives as CVEs present in NVD but not in KEV. It measures discrimination between those groups in this sampled population. The report explicitly says it does not measure prediction of future exploitation. It also does not test the engine's full multi-domain capabilities, operational outcomes, or all prioritization workflows. Therefore, the AUC result should be stated plainly for this task, without turning it into a claim that one system is universally superior or that the systems perform the same function.

## Important interpretation and caveats

- The evidence says the sample has 299 KEV positives and 381 NVD-only negatives. It notes that positive and negative publication windows may differ; this can affect the comparison.
- The 10_EF feature set includes `ransomware_flag`. The report says this flag is non-zero only for KEV-listed ransomware CVEs, creating target leakage risk for a KEV-vs-non-KEV task. Treat the 10_EF results as an explicitly flagged ablation, not clean evidence of generalization. The 9_EF result excludes that flag.
- Reported P@k is precision among the top k ranked records in this run. It is not, on its own, a probability calibration result or a general guarantee of operational prioritization quality.
- The report notes incomplete NVD CVSS coverage may affect recent CVEs, and that results are preliminary and require independent replication.
- The stated deterministic scoring methodology is not the same as independently verified reproducibility of this particular run. The available RUN004 evidence supplies bootstrap AUC confidence intervals based on 2,000 resamples; those intervals describe reported metric uncertainty under that procedure. They do **not** establish bit-for-bit repeatability across repeated engine executions.
- No RUN004 output fingerprint or repeated-run match record was supplied in the RUN004 evidence shown here. Accordingly, RUN004's independent reproducibility status is **not established by the available artifacts**. This is not a claim that the engine is nondeterministic; it is a boundary on what this run's published evidence verifies.

## Integrity and artifact status

- The evidence records SHA-256 `ad618e404a43d72ac6435b6e5a8d75000778b9245a6b70dbde46530152f2eef3` for the frozen CISA KEV snapshot.
- The report and evidence are in the repository. Their listed GitHub blob IDs are SHA-1 object identifiers, not artifact SHA-256 checksums.
- The RUN004 population CSV was supplied in chat but is not yet committed in the repository. Its byte size and SHA-256 therefore remain unverified here.
- Keep RUN004 separate from the `...20261120T001020Z...` material: the accompanying report/evidence identify RUN007, whereas the separate supplied manifest identifies RUN008. These are not RUN004 files.

## Bottom line

RUN004 reports perfect EPSS top-k precision and higher AUC than either Coherence variant for this particular KEV-vs-NVD-only sample. It also reports perfect Coherence precision at top 10 and top 50, with lower AUC and a top-100 difference between 9_EF and 10_EF. The result is a task-bounded comparison, not a verdict on the whole engine or on structural prioritization in other domains. The structural question needs benchmarks designed around those intended tasks, with matched populations, leakage controls, explicit repeat-run fingerprints, and independent replication.
