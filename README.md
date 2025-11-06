# Neoantigen Discovery Dataset (NDD)

> 📢 **Current public version: v0.2 (positive dataset only)**  
> This release contains **257 experimentally validated neoantigen peptides** across **25 cancer types** and **46 HLA class I alleles**.  
> For patient-level data and leaderboard participation, visit:  
> 👉 [https://huggingface.co/NeoDiscovery](https://huggingface.co/NeoDiscovery)

---

## Project Overview

Neoantigen prediction relies heavily on AI and machine learning models.  
The **Neoantigen Discovery Dataset (NDD)** v0.2 is designed to support such modeling efforts,  
providing a structured, high-quality collection of experimentally validated positive neoantigens.

Each entry includes standardized molecular annotations—covering mutation, HLA typing, peptide sequence,  
and detailed immunogenicity assay evidence—together with derived predictive features such as binding affinity,  
stability, anchor mutation, and expression context.

Unlike previous versions, **v0.2** focuses exclusively on experimentally confirmed **positive peptides**,  
ensuring clarity, reliability, and reproducibility for benchmarking and model development.  
All data have undergone manual curation, normalization, and cross-validation to ensure consistency.  
This dataset can serve both as a **machine learning training resource** and as a **verified reference set**  
for evaluating neoantigen prediction models.

---

## Data Curation and Standardization

- **Mutation Naming:** HGVS rules (e.g., *KRAS p.G12D*).  
  Mutation information is directly sourced from primary literature.  
  Due to variations in reference genome usage across publications (commonly *hg19* or *hg38*),  
  version differences may exist. NDD v0.2 preserves original reported coordinates and will continue  
  to harmonize reference genomes in future releases.

- **Cancer Type Classification:**  
  Cancer types were standardized through cross-referencing TCGA, IEDB, and literature-based definitions,  
  ensuring consistent nomenclature even for cancer types not covered by TCGA.

- **HLA Typing:**  
  Unified to four-digit resolution (e.g., *HLA-A02:01*), consolidating aliases and shorthand notations  
  into standardized nomenclature.

---

## Fields and Features

### Basic Fields
Core information directly extracted and standardized from literature, including gene, mutation, HLA, peptide,  
and assay evidence. These fields form the foundation of each dataset entry.  
See **Appendix Table 1 (Basic Fields)** or `docs/field-schema.md` for definitions.

### Predicted Features
Predicted or derived features are calculated using public tools and databases to describe  
binding, stability, anchor mutation, expression, and driver-related properties.  
These features follow the same field structure as **v0.1**,  
ensuring full compatibility and reproducibility across versions.  

> 💡 Note: The extended feature set (including eight machine learning–ready features)  
> used for training and leaderboard evaluation is hosted on Hugging Face.  
> The positive peptides provided here correspond to the **positive source subset**  
> of the Hugging Face training dataset (NDD v0.2).

Full feature definitions and sources are listed in **Appendix Table 2 (Predicted Features)**  
and `docs/predicted-features.md`.

### Patient-Level Metadata
NDD v0.2 includes patient-level metadata summarizing available HLA information,  
clinical context, and relevant reported identifiers.  
This information is provided in **Appendix Table 3 (Patient Metadata)**  
and `data/patient_metadata_v0.2.tsv`.

---

## Data Files & Format

- **Dataset format:** UTF-8 encoded TSV  
- **Main file:** `data/ndd_v0.2.tsv` — each row represents a peptide–HLA–mutation record  
- **Patient metadata:** `data/patient_metadata_v0.2.tsv` — patient-level information and HLA context  
- **Documentation:**  
  - `docs/field-schema.md`: basic field definitions  
  - `docs/predicted-features.md`: derived feature descriptions  
  - `CHANGELOG.md`: version update history

---

## Versioning & Updates

- **Current version: v0.2**  
  This release contains **257 curated positive neoantigen peptides**, covering **25 cancer types** and **46 unique HLA class I alleles**.  
  All entries are experimentally validated for immunogenicity and include harmonized molecular features such as binding rank, stability, anchor mutation, and expression context.  
  Peptide lengths range from **8–13 amino acids**, with **9-mers** remaining the most common.

- **Update strategy**  
  NDD v0.2 represents a focused, high-quality subset of experimentally confirmed positive neoantigens,  
  refined to support transparent benchmarking and community collaboration.  
  Future versions will expand by incorporating validated negatives, additional mutation types,  
  and extended clinical metadata to enable comprehensive model training and evaluation.

- **Changelog**  
  All modifications, new fields, and updates are documented in `CHANGELOG.md`,  
  including patient cohort adjustments and dataset schema consistency.

- **Reproducibility**  
  Historical drafts prior to v0.2 have been deprecated and are no longer public,  
  ensuring that analyses and benchmarks reference a single, consistent dataset release.

---

## Community and Contributions

NDD is an open community project.  
We welcome contributions and feedback from researchers, clinicians, and data scientists.  
If you discover missing annotations, new data sources, or wish to contribute improvements,  
please open an issue or pull request.  

Researchers are also invited to participate in the **NDD v0.2 leaderboard** on Hugging Face,  
where models can be benchmarked under standardized evaluation settings.  
👉 [https://huggingface.co/NeoDiscovery](https://huggingface.co/NeoDiscovery)

---

## Citation

If you use NDD in your work, please cite:

**Neoantigen Discovery Dataset (NDD) v0.2**  
NeoDiscovery Team, 2025.  
Hosted on Hugging Face: [https://huggingface.co/NeoDiscovery](https://huggingface.co/NeoDiscovery)

**Archived version (NDD v0.1)**  
NeoDiscovery Team, 2025.  
Available for reproducibility reference on GitHub: [https://github.com/NeoDiscovery/NDD](https://github.com/NeoDiscovery/NDD)

---

## License & Contact

- **Code and documentation:** MIT License  
- **Dataset:** CC BY 4.0 License  
- **Contact:** contact@neodiscovery.ai  
