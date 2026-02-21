# tb-bulk-rnaseq

Bulk RNA‑seq analysis of tuberculosis cohort GSE107994 using R and Quarto.

Singhania et al. profiled whole‑blood gene expression from humans with active tuberculosis, latent TB infection (LTBI), and uninfected controls across multiple cohorts, using microarrays and RNA‑seq. Their main goal was to identify an optimal reduced gene set to serve as a diagnostic biomarker for active TB that did not pick up other diseases. They showed that active TB is characterized by overabundance of type I interferon‑inducible transcripts and underabundance of IFNG/TBX21 and B‑/T‑cell–associated genes, and that some individuals with LTBI display “outlier” active‑TB‑like signatures, suggesting phenotypic heterogeneity and possible higher progression risk.

For this project intended to familiarize myself with bulk RNA-seq data, I focus first on a cross‑sectional baseline comparison between active TB, LTBI, and controls to reproduce key aspects of the transcriptional signature (e.g., interferon‑related changes), and then extend to longitudinal dynamics and heterogeneity within the LTBI and LTBI‑progressor groups.

> Singhania A, Verma R, Graham CM, Lee J et al. A modular transcriptional signature identifies phenotypic heterogeneity of human tuberculosis infection. Nat Commun 2018 Jun 19;9(1):2308. [PMID: 29921861](https://pubmed.ncbi.nlm.nih.gov/29921861/)

## Setup

```r
install.packages("renv")
renv::restore()
```
