# Getting Started with AnnData (scverse)

## Overview

This repository contains a structured implementation and exploration of the **AnnData data structure** from the **scverse ecosystem**, based on the official tutorial:

👉 https://scverse-tutorials.readthedocs.io/en/latest/notebooks/anndata_getting_started.html

The goal of this work is to understand how single-cell data is represented, manipulated, and analyzed using `AnnData`, which is a core data structure in modern single-cell bioinformatics workflows (e.g., Scanpy, scverse tools).

---

##  Objectives

The main objectives of this practical assignment are:

- Understand the structure of the `AnnData` object
- Explore how single-cell data is stored (cells × genes matrix)
- Learn how to use:
  - `obs` (cell metadata)
  - `var` (gene metadata)
  - `obsm` / `varm` (multi-dimensional annotations)
  - `obsp` / `varp` (pairwise relationships)
- Perform subsetting and slicing of AnnData objects
- Understand the difference between **views vs copies**
- Work with real single-cell RNA-seq–like datasets

---

##  Key Concepts Covered

### 1. AnnData Structure

`AnnData` is a container for annotated data matrices:

- Rows → Cells (observations)
- Columns → Genes (variables)
- `.X` → Main expression matrix

---

### 2. Metadata Storage

| Component | Description |
|----------|-------------|
| `obs` | Cell-level metadata (clusters, QC, etc.) |
| `var` | Gene-level metadata (gene names, IDs) |
| `uns` | Unstructured annotations (plots, parameters) |

---

### 3. Multi-dimensional Annotations

- `obsm`: embeddings (e.g., PCA, UMAP)
- `varm`: gene-level embeddings
- `obsp`: cell-cell relationships (e.g., distance matrix)
- `varp`: gene-gene relationships

---

### 4. Data Subsetting

AnnData supports flexible indexing:

- By gene/cell names
- By numeric indexing
- By boolean masks

Example:

```python
adata_subset = adata[:5, ["GeneA", "GeneB"]]
```
## 5. Views vs Copies

- **View** → Lightweight reference to original data  
- **Copy** → Independent dataset  

### Important behavior:
- Modifying a view may trigger conversion into a full copy  

---

## 6. Layers in AnnData

Layers allow storage of multiple versions of the same data:

- Raw counts  
- Normalized counts  
- Log-transformed values  

### Example:

```python
adata.layers["counts"] = adata.X.copy()
```
##  Dataset Used

The tutorial uses a **PBMC single-cell RNA-seq dataset**, commonly used for:

- Immune cell classification  
- Gene expression analysis  
- Dimensionality reduction workflows  

---

##  Tools & Libraries Used

- Python 3.x  
- `anndata`  
- `scanpy`  
- `numpy`  
- `pandas`  
- `matplotlib`  
- `pooch`  
