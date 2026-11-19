# Methodology & Provenance

## Black-Box Reproducibility
We utilize a strict black-box validation protocol.
1. **Input (X)** is frozen and hashed (SHA-256).
2. **Output (Z)** is generated deterministically by the engine.
3. **Verification:** Anyone can verify that the input hash matches the manifest, and that the output hash matches the provided results.

## Data Provenance
All validation data is drawn from public, verifiable sources:
- CISA Known Exploited Vulnerabilities (KEV) Catalog (Frozen: 2026-09-16, SHA-256: `72b4e3489021d2ad50c4f9b8ddddd1608a9e6b87dd7beedc126f6341ea98f105`).
- NVD Enrichment (CVSS + CPE).
- Synthetic structural datasets (PEATH).

## Trade Secret Protection
The underlying code, weightings, and internal logic of the `BlackPearl-Deterministic-Core` are proprietary. This repository strictly publishes the *results* of the methodology, not the methodology itself.
