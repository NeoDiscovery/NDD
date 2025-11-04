# Changelog

All notable changes to this project will be documented in this file.  
This project follows semantic versioning where possible.

---
## [v0.2] — November 2025

### Overview
This release introduces **patient-level architecture**, **generative negative peptides**, and **a balanced train/test split** designed for leaderboard benchmarking.  
It represents a major upgrade from v0.1, which contained only experimentally reported positive peptides.

### Key Updates
- **Generative Negative Data**  
  Added high-quality synthetic negative peptides generated under HLA- and sequence-matched constraints to support balanced model training.
- **Patient-level Cohort Structure**  
  Each record now links to a unique `patient_id`.  
  Patients are split into **training** and **test** cohorts for fair evaluation.
- **Feature Set Redefinition**  
  Eight core derived features are provided for direct machine learning use:
  1. `seq_len`  
  2. `mutant_rank_netMHCpan`  
  3. `mutant_rank`  
  4. `mutant_rank_PRIME`  
  5. `mut_Rank_Stab`  
  6. `TAP_score`  
  7. `mut_netchop_score_ct`  
  8. `mutant_other_significant_alleles`
- **Leaderboard Preparation**  
  The full v0.2 training set and evaluation instructions are hosted on Hugging Face:  
  [https://huggingface.co/NeoDiscoveryAdmin](https://huggingface.co/NeoDiscoveryAdmin)
- **Public Version Adjustment**  
  To prevent data overlap, the GitHub-hosted v0.1 has been minimally pruned — removing patients that are part of the v0.2 test set, along with corresponding metadata.
- **Backward Compatibility**  
  Schema and field definitions remain consistent with v0.1, ensuring reproducibility and smooth model migration.

### Files
- `ndd_v0.2.train.tsv` — Full training set (available on Hugging Face)
- `patient_split_v0.2.tsv` — Train/test partition by patient
- `docs/predicted-features.md` — Updated feature definitions
- `docs/field-schema.md` — No structural changes


## [v0.1] - 2025-09-24
### Added
- Initial public release of the **Neoantigen Discovery Dataset (NDD)**.
- Main dataset file `ndd_v0.1.tsv` containing curated **basic fields** and **predicted features**.
- Patient-level metadata file `patient_metadata.tsv` with limited cohort information.
- Documentation under `docs/`:
  - `field-schema.md` — definitions of basic fields
  - `predicted-features.md` — descriptions of predicted features and tools
  - `patient-metadata.md` — patient-level metadata definitions
- Dual license:
  - **MIT** for code/scripts
  - **CC-BY 4.0** for dataset files

---

