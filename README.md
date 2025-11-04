# Neoantigen Discovery Dataset (NDD)


> 📢 Current public version: **v0.1 (pruned)**  
> The latest full dataset (v0.2) with patient-level and generative negatives is available on Hugging Face:  
> [https://huggingface.co/NeoDiscoveryAdmin](https://huggingface.co/NeoDiscoveryAdmin)

---

## Overview

The Neoantigen Discovery Dataset (NDD) was developed with a clear focus on machine learning applications in neoantigen prediction. From the outset, NDD has been designed to support model development by systematically collecting a broad range of dimensions — including basic information, experimental labels, and ML-ready predictive features that can be directly used for training and validation.

In neoantigen research, different strategies serve complementary roles: threshold-based approaches are effective for filtering candidates using known rules, while deep learning methods require large-scale, standardized datasets to uncover complex patterns and improve generalization.

NDD addresses this need by providing a curated, standardized, and feature-rich dataset that enables the development, training, and benchmarking of new algorithms, while also facilitating integration with experimental evidence.

### Key highlights include

- Integration of data from literature reports and public resources such as IEDB, TCGA, and CEDAR.  
- Coverage of core experimental evidence alongside predicted features (binding affinity, stability, anchor mutations, driver status, etc.).  
- A structured design that supports both peptide-level predictions and patient-level cohort analyses.  
- Preservation of assay details to ensure reliable immunogenicity labels and reproducibility.  

NDD is not just a file collection, but a community resource for advancing model development, evaluation, and integration with experimental data. The current release, NDD v0.1, marks the starting point of an ongoing effort to expand data coverage, enrich feature annotations, and promote collaboration across the research community.

---

## Data Sources & Curation

NDD entries are primarily curated from original literature reports, manually reviewed and standardized for consistency. To ensure transparency and traceability, each record includes PMID/DOI identifiers, allowing users to directly access the corresponding publications.

In addition, we drew inspiration from previously published neoantigen datasets summarized by other research groups, building on their foundational efforts while extending the scope through broader standardization and feature integration.

The curation process draws on the frameworks established by public databases such as IEDB and CEDAR, while also integrating cross-references to resources like TCGA. This approach ensures that NDD combines the breadth of literature-derived evidence with the rigor of structured annotation.

### Standardization Principles

- Mutation nomenclature: Reported using HGVS format (e.g., KRAS p.G12D). Mutation descriptions are preserved as given in the original publications, which may reference different genome builds (commonly hg19 or hg38). In v0.1, all entries retain their original reporting style; future versions will unify genome references to improve comparability.  
- Cancer type classification: Manually normalized and mapped to widely used taxonomies such as IntOGen and TCGA, ensuring consistent categorization across diverse studies.  
- HLA typing: Harmonized to four-digit resolution (e.g., HLA-A02:01), with aliases and shorthand notations consolidated.  

### Quality Control

- Missing values are explicitly marked as NA.  
- Consistency checks combine manual review with automated scripts to validate key fields.  
- Future improvements will include automated QC pipelines to further minimize potential errors.  
- Source traceability is preserved for every entry, ensuring reproducibility and enabling direct comparison with original publications.  

Detailed documentation of the tools, versions, and parameters used for feature annotation is provided in `docs/predicted-features.md`.

---

## Fields & Features

NDD provides information at three levels: basic fields, predicted features, and patient-level metadata. Together, these dimensions make the dataset suitable for modeling and exploratory research.

- **Basic fields** capture essential information from original reports, including:  
  patient ID, tumor type, gene/mutation (HGVS), mutant and wild-type peptides, HLA allele, experimental method.  
  These fields form the foundation of each entry.  

- **Predicted features** extend each record with annotations widely used in neoantigen research, such as:  
  binding affinity and rank (NetMHCpan), stability (NetMHCstabpan), recognition likelihood (PRIME, BigMHC_IM), cleavage and transport scores (NetChop, NetCTLpan), differential agretopicity index (DAI), anchor mutation position, TCGA cancer expression (TPM median), and driver gene status (IntOGen).  
  These features make the dataset directly applicable to machine learning tasks.  

- **Patient-level metadata** (when available) include additional information such as extended HLA typing, clinical outcomes, or treatment details. In the current release these data are limited and not yet complete, but we recognize their importance and will continue to expand and refine this part of the dataset in future versions.  

**Field definitions and detailed documentation are provided in the `docs/` directory, including:**  
- `field-schema.md` — definitions of basic fields  
- `predicted-features.md` — list and description of predicted features  
- `patient-metadata.md` — definitions of patient-level metadata (when available)  

---

## Usage & Format

The dataset is released in tab-separated values (TSV, UTF-8 encoded) format.

- **Main file:** `data/ndd_v0.1.tsv`  
  Each row represents a mutation–HLA–peptide entry, combining both basic fields and predicted features.  

- **Patient-level metadata:** `data/patient_metadata.tsv`  
  Contains information at the patient dimension, such as extended HLA typing, clinical outcomes, and treatment details when available.  

*Note:* Patient IDs are anonymized to ensure privacy but remain consistent across files, enabling cohort-level analysis.  

### Limitations

- Patient-level metadata are currently limited in number and completeness, reflecting what is available in published sources.  
- Certain molecular features (e.g., RNA-seq coverage, expression levels, clonality, cancer cell fraction) are not yet integrated in this release. Only TCGA cancer expression (TPM median) is included.  
- Cancer type mapping to TCGA or IntOGen was performed internally during curation but is not included in the public dataset. Researchers may apply their own mapping according to their needs.  

These reflect the present scope of published evidence and curation coverage. Future versions will progressively expand molecular features and strengthen patient-level annotations.

---

## Versioning & Updates

- **Current version: v0.1**  
  This release contains 354 curated entries, covering 16 cancer types and 58 unique HLA alleles (MHC-I). All entries include experimental immunogenicity evidence. Peptide lengths range from 8–13 amino acids, with 9-mers being the most common.  

- **Update strategy**  
  Future releases will expand coverage by adding new literature sources, additional mutation types, and molecular features not yet included in v0.1. Patient-level metadata will also be progressively enriched as more information becomes available.  

- **Changelog**  
  All modifications and additions will be documented in `CHANGELOG.md`, including new data sources, field extensions, and corrections.  

- **Reproducibility**  
  Historical versions of the dataset will remain available in the repository, allowing users to reproduce analyses and compare results across versions.  

### Data Adjustment & Transition Notice (Nov 2025)

> **Data Adjustment (Nov 2025)**  
> To preserve the integrity and fairness of the upcoming Hugging Face leaderboard evaluation, we have **minimally pruned the GitHub-hosted NDD v0.1**.  
> Patients that are part of the **v0.2 closed test set** — along with all their corresponding positive peptides — have been removed from the public version.  
> The same patients have also been removed from the **patient-level metadata** file to prevent overlap or indirect reconstruction of the test cohort.  
> This adjustment affects only a small overlapping subset and does **not** alter the schema or usability of NDD v0.1 for research replication.  
> All field definitions, documentation, and feature descriptions remain unchanged. 

### Access NDD v0.2 and Join the Leaderboard

> **Access v0.2 Train & Leaderboard**  
> The **full NDD v0.2 training set** and official leaderboard instructions are hosted on Hugging Face:  
> 👉 [https://huggingface.co/datasets/NeoDiscovery/NDD-v0.2](https://huggingface.co/NeoDiscoveryAdmin/datasets)  
> You can download the full training dataset and follow the submission guide to benchmark your model on the leaderboard.  


---

## Community & Contributions

NDD is an open community project, and we warmly welcome participation from researchers, clinicians, and data scientists. There are several ways to get involved:

- **Feedback & suggestions**  
  Since the dataset has been curated largely through manual annotation and standardization, omissions or errors may remain. We sincerely welcome any feedback or corrections.  
  - Submit issues directly on GitHub Issues.  
  - Or contact us by email at neoantigendd@gmail.com.  

- **Data contributions**  
  You are encouraged to share new data sources, patient cohorts, or predictive features that could enrich future releases.  

- **Collaboration & discussion**  
  We invite contributions in areas such as data curation, feature development, or method benchmarking. Open discussions and new ideas are welcome.  

- **Pull requests (PRs)**  
  If you wish to directly improve documentation, metadata, or scripts, you can submit a pull request — a standard GitHub workflow for proposing changes. This allows us to review your edits and merge them into the main project.  

All contributions will be acknowledged in future version updates.  

---

## Citation

If you use NDD in your research, please cite as:

**Neoantigen Discovery Dataset (NDD) v0.2**  
NeoDiscovery Team, 2025.  
Hosted on Hugging Face: [https://huggingface.co/NeoDiscoveryAdmin](https://huggingface.co/NeoDiscoveryAdmin)

**Neoantigen Discovery Dataset (NDD), version 0.1**  
GitHub Repository: [https://github.com/NeoDiscovery/NDD-v0.1](https://github.com/NeoDiscovery/NDD-v0.1)  
Hugging Face Dataset: *to be released*  

For formal publications, you may include the following BibTeX entry:

```bibtex
@misc{ndd2025,
  title        = {Neoantigen Discovery Dataset (NDD), version 0.1},
  author       = {{Neoantigen Discovery Dataset (NDD) Contributors}},
  year         = {2025},
  howpublished = {\url{https://github.com/NeoDiscovery/NDD-v0.1}},
  note         = {Accessed: YYYY-MM-DD}
}
```

---

## License & Contact

### Acknowledgments

We thank the broader research community for making data and tools publicly available, which has greatly facilitated the development of NDD.  
We also appreciate earlier efforts to compile and share neoantigen-related datasets, which provided valuable references during our work.  

### License

- Code and scripts: released under the MIT License.  
- Dataset files (e.g., .tsv, .csv, .parquet): released under the Creative Commons Attribution 4.0 International License (CC BY 4.0).  
  Users are free to share and adapt the dataset with proper attribution, in accordance with the license terms.  

*Full license texts are available in the `LICENSE` and `DATA_LICENSE` files in this repository.*  

### Contact

For questions, feedback, or collaboration:  
- GitHub Issues (preferred): open an issue  
- Email: neoantigendd@gmail.com
