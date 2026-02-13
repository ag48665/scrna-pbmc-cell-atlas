# Single-cell RNA-seq Cell Atlas of Human PBMCs

## Overview

This project presents a complete single-cell RNA sequencing (scRNA-seq) analysis of human peripheral blood mononuclear cells (PBMCs). The aim of the study was to identify distinct immune cell populations and determine the genes that define them using an unsupervised computational workflow.

Single-cell transcriptomics enables gene expression profiling at cellular resolution, allowing detection of heterogeneous cell types that cannot be resolved using bulk RNA sequencing. In this project, I analysed a publicly available PBMC dataset and reconstructed immune cell composition using the Scanpy framework in Python.

---

## Objectives

* Perform quality control and filtering of single-cell RNA-seq data
* Normalize and preprocess gene expression counts
* Identify highly variable genes
* Reduce dimensionality using PCA and UMAP
* Perform unsupervised clustering (Leiden algorithm)
* Identify marker genes using differential expression analysis
* Assign biological cell types based on known immune markers

---

## Dataset

The dataset was obtained from the Scanpy built-in dataset:

`sc.datasets.pbmc3k()`

It contains ~2,700 human peripheral blood mononuclear cells generated using droplet-based single-cell RNA sequencing technology.

---

## Computational Workflow

The analysis pipeline consisted of the following steps:

1. Data loading
2. Quality control filtering

   * Remove cells with <200 detected genes
   * Remove cells with >2500 detected genes (potential doublets)
   * Remove cells with >5% mitochondrial RNA
3. Library size normalization (10,000 counts per cell)
4. Log transformation
5. Selection of ~2000 highly variable genes
6. Principal Component Analysis (PCA)
7. k-nearest neighbor graph construction
8. UMAP visualization
9. Leiden clustering (resolution = 0.5)
10. Marker gene identification (Wilcoxon rank-sum test)
11. Cell type annotation

---

## Identified Cell Types

The analysis successfully identified major immune cell populations:

* CD4 T cells (IL7R, CD3D)
* B cells (MS4A1, CD79A)
* Natural Killer (NK) cells (NKG7, GNLY)
* Monocytes (LYZ, S100A8, S100A9)
* Dendritic cells (FCER1A, CST3)
* Platelets (PPBP)

The agreement between clustering results and known biological markers validates the computational workflow.

---

## Results

Key findings:

* 2638 high-quality cells remained after filtering
* Unsupervised clustering revealed 10 transcriptionally distinct populations
* Marker gene analysis confirmed known immune cell identities
* Differential expression analysis demonstrated unique transcriptional signatures for each cell type

Figures generated:

* Quality control violin plots
* UMAP cluster visualization
* Annotated cell atlas
* Marker gene dotplot
* Differential expression heatmap

---

## Requirements

Software used:

* Python 3.10
* Scanpy
* Anndata
* NumPy
* Pandas
* Matplotlib
* Seaborn
* Leidenalg
* igraph
* JupyterLab

---

## How to Reproduce the Analysis

```bash
conda env create -f environment.yml
conda activate scrna-pbmc
jupyter lab
```

Open:

```
notebooks/01_pbmc_cell_atlas.ipynb
```

Run all cells sequentially.

---

## Biological Interpretation

The results demonstrate that transcriptional profiles alone are sufficient to distinguish immune cell populations without prior labeling. Cells cluster according to biological function, indicating that gene expression patterns strongly correlate with cellular identity.

This project highlights the power of single-cell RNA sequencing to study immune heterogeneity and provides a reproducible workflow for analysing high-dimensional transcriptomic data.

---

## Limitations

* Dropout events and sparse gene expression matrices
* Technical noise from sequencing
* Possible doublets
* Batch effects (not present in single dataset)
* Lack of spatial information

---

## References

Key references are listed in the accompanying report PDF.
