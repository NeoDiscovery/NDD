# Appendix Table 1. Basic Fields

| Field              | Category             | Description                                                                 |
|--------------------|----------------------|-----------------------------------------------------------------------------|
| pubmed_id          | data_source          | PubMed identifier of the reference                                          |
| reference_name     | data_source          | Title or short name of the reference                                        |
| patient_id         | sample_information   | Internal de-identified patient identifier                                   |
| tumor_tissue       | sample_information   | Tumor sample tissue                                                         |
| tumor_type_detail  | sample_information   | Original tumor type name reported in literature                             |
| gene               | mutation_information | Gene symbol                                                                 |
| mutation_type      | mutation_information | Mutation class                                                              |
| mutation           | mutation_information | Mutation description (HGVS format or amino acid change, e.g., p.G12D)       |
| position           | mutation_information | Mutation position within the peptide sequence (relative position in peptide)|
| chromosome         | mutation_information | Chromosome number (1–22, X, Y)                                              |
| genomic_coord      | mutation_information | Genomic coordinate                                                          |
| ref                | mutation_information | Reference allele                                                            |
| alt                | mutation_information | Alternative allele                                                          |
| mt_peptide         | peptide_information  | Mutated peptide (8–14mer)                                                   |
| wt_peptide         | peptide_information  | Corresponding wild-type peptide                                             |
| length             | peptide_information  | Peptide length                                                              |
| hla                | peptide_information  | Restricting HLA allele                                                      |
| response_type      | peptide_information  | Response category                                                           |
| assay_type         | assay_information    | Immunological assay type, harmonized from original literature into standardized categories. Multiple assay types may apply. |
| effector_origin    | assay_information    | Source of effector T cells as described in the original study               |
| stimulation_target | assay_information    | The target used to stimulate T cells, summarized from experimental description |
| presentation_method| assay_information    | Experimental method used to demonstrate peptide presentation                |
