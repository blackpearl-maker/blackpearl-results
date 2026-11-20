# Upload Checklist and Current Status

- [ ] Every frozen artifact has a corresponding SHA-256 hash that has been verified against the exact committed bytes. Existing manifests/checksum lists provide claimed hashes for named artifacts; RUN004 is incomplete, and the reconstructed first honeypot package's hashes need verification against original bytes.
- [ ] Every manifest lists inputs, outputs, and hashes. RUN007/RUN008 manifests do; RUN004 has only partial artifacts; honeypot manifests list outputs and hashes but no inputs.
- [x] Root README links to VALIDATION, RESULTS, METHODOLOGY, and REVIEW_REQUEST.
- [x] No engine source code is included in this repository's published result artifacts (RUN008 records a source fingerprint only).
- [x] No internal engine implementation or proprietary algorithm details are published in the result summaries.
- [ ] No equations included. Review repository documents/artifacts before marking complete; this checklist item has not been independently audited in this pass.
- [ ] No raw sensitive customer data included. Review all current and incoming artifacts before marking complete.
- [ ] Wording of all results and claims is strictly unmodified. Newly written navigation and interpretation notes are explicitly editorial; source reports remain separate, but the complete repository has not been audited for this item.

## Important publishing status

RUN004 report/evidence are present, but its population CSV and verified report/evidence/CSV SHA-256 values are missing. The first supplied honeypot package was reconstructed from chat text; verify its listed hashes against original files. The honeypot timelines show fewer polls than a full 600-second interval would imply, so the coverage caveat is retained in `results/cybersecurity/HONEYPOT_RESULTS.md`.
