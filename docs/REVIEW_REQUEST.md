# Request for Independent Review

We invite independent researchers, security analysts, and auditors to review the evidence presented in this repository.

## What you can verify:
1. **Data Integrity:** Verify the SHA-256 hashes in the `artifacts/sha256/` folder against the frozen datasets.
2. **Determinism:** Confirm that RUN007 and RUN008 produced identical outputs from the same frozen inputs.
3. **Statistical Validity:** Review the statistical methods (Randomization test p=0.0020, PEATH AUC 1.0, Spearman +0.5580) outlined in `VALIDATION.md`.

## What we are seeking:
We are looking for technical feedback on the reproducibility of our results. If you have questions regarding the frozen data or the output hashes, please open an Issue in this repository.

We do not provide access to the source code or internal algorithmic logic, as it remains a proprietary trade secret.
