# tb-bulk-rnaseq

Bulk RNA‑seq analysis of tuberculosis cohort GSE107994 using R in Quarto.

Singhania et al. profiled whole‑blood gene expression from humans with active tuberculosis, latent TB infection (LTBI), and uninfected controls across multiple cohorts, using microarrays and RNA‑seq. Their main goal was to identify an optimal reduced gene set to serve as a diagnostic biomarker for active TB that did not pick up other diseases. They showed that active TB is characterized by overabundance of type I interferon‑inducible transcripts and underabundance of IFNG/TBX21 and B‑/T‑cell–associated genes, and that some individuals with LTBI display “outlier” active‑TB‑like signatures, suggesting phenotypic heterogeneity and possible higher progression risk.

For this project intended to familiarize myself with bulk RNA-seq data, I focus first on a cross‑sectional baseline comparison between active TB, LTBI, and controls to reproduce key aspects of the transcriptional signature (e.g., interferon‑related changes), and then extend to longitudinal dynamics and heterogeneity within the LTBI and LTBI‑progressor groups.

> Singhania A, Verma R, Graham CM, Lee J et al. A modular transcriptional signature identifies phenotypic heterogeneity of human tuberculosis infection. Nat Commun 2018 Jun 19;9(1):2308. [PMID: 29921861](https://doi.org/10.1038/s41467-018-04579-w)

## Methods

- R environment and package dependencies managed with `renv`.
- Bulk RNA-seq counts and sample metadata downloaded from GEO (GSE107994).
- Lowly expressed genes filtered using `edgeR::filterByExpr`.
- Library size normalization with `edgeR` (TMM, trimmed mean of M-values).
- `voom` transformation to log2 counts-per-million with precision weights (limma-voom).
- Design matrix encoding baseline disease groups (Control, Active_TB, LTBI, LTBI_Progressor).
- Differential expression analysis with limma:
  - Linear models fitted per gene with `lmFit`.
  - Group contrasts (e.g. Active TB vs all recent contacts) defined with `makeContrasts`.
  - Empirical Bayes moderation and multiple testing correction (Benjamini–Hochberg).
- Exploratory PCA on voom-normalized expression to visualize sample structure.
- Targeted inspection of immune-related genes, including interferon-inducible markers and the 20-gene active TB signature reported by Singhania et al.

## Results

Reproduce the results report with:

```r
install.packages("renv")
renv::restore()
quarto::quarto_render("tb-bulk-rnaseq.qmd")
```

- PCA on voom-normalized expression shows separation of active TB from recent contacts at baseline.
- Limma-voom identifies >10,000 differentially expressed genes between active TB and recent contacts (FDR < 0.05).
- Interferon-inducible genes are upregulated and IFNG/TBX21 and B/T-cell marker genes are relatively downregulated in active TB, consistent with the modular signature of Singhania et al.

## Future Directions

This project served to familiarize myself with bulk RNA-seq data, including the standard limma-voom workflow. GSE107994 is a rich dataset capturing active TB cases, latent TB infection, and controls spanning both sexes, a range of ages, and multiple tuberculosis disease types. I intend to return to this dataset to practice additional study designs and analytical tools, such as:

- Gene set enrichment analysis
- Analysis 2 — Longitudinal view within LTBI
- Analysis 3 — Transcriptional differences among TB disease types
