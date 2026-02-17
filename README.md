# tb-bulk-rnaseq

Bulk RNA‑seq analysis of tuberculosis cohort GSE107994 using R and Quarto.

This is a personal project to get acquainted with bulk RNA-Seq data in relation to human disease. The R code for managing and analyzing the data will be stored and discussed within a Quarto document (.qmd) to serve as a walkthrough. The data were produced by expression profiling by high throughput sequencing of whole blood samples from *Homo sapiens*.

Data provided by ...
> Singhania A, Verma R, Graham CM, Lee J et al. A modular transcriptional signature identifies phenotypic heterogeneity of human tuberculosis infection. Nat Commun 2018 Jun 19;9(1):2308. PMID: 29921861

## Setup

```r
install.packages("renv")
renv::restore()
```

## Sections to include

- RNA-seq data cleaning and formatting
- Sample-level overview with PCA
- limma-voom
- DESeq2
- GSEA(?)
- Comparisons
- Summary
