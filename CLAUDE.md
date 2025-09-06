# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an R-based bioinformatics analysis repository focused on XRN1 knockout vs wild-type differential expression analysis in HepG2 cells. The project performs DESeq2-based differential gene expression analysis, pathway enrichment analysis using clusterProfiler and reactomePA, and generates visualizations including volcano plots.

## Development Commands

-   **Render Quarto documents**: `quarto render R/filename.qmd` (analyses are written as .qmd files)
-   **Open R Project**: Open `senko_xrn1_analysis.Rproj` in RStudio
-   **Execute from root**: All scripts should be run from the repository root directory to ensure proper relative paths

## Repository Structure

```         
├── R/                          # Analysis scripts (Quarto .qmd files)
│   ├── 01_KO_vs_WT_DEA_volcano.qmd    # Volcano plot generation
│   ├── 02_35_B18R_vs_35_DEA_viz.qmd   # Additional visualization analysis  
│   └── 03_ko_vs_wt_dea_rna_metabolism.qmd  # RNA metabolism focused analysis
├── read/                       # Input data files
│   ├── gene_count_*.csv       # Gene count matrices
│   ├── metadata.csv           # Sample metadata (WT vs KO, replicates 1-3)
│   └── *.tsv                  # Pre-computed differential expression results
├── write/                     # Output directory
│   ├── figures/               # Generated plots (PDFs)
│   └── tables/                # Results tables (CSV)
└── checkpoints/               # Intermediate analysis checkpoints
```

## Key Analysis Components

-   **Sample Design**: 3 WT replicates vs 3 XRN1 KO replicates in HepG2 cells
-   **Differential Expression**: DESeq2 pipeline with replicate-aware design
-   **Visualization**: Volcano plots, feature plots, dotplots for pathway enrichment
-   **Pathway Analysis**: GO biological processes, GSEA analysis on differentially expressed genes
-   **Output Format**: HTML reports with darkly theme, self-contained files

## R Package Dependencies

Based on analysis files, key packages include: - DESeq2 (differential expression) - tidyverse (data manipulation) - clusterProfiler, reactomePA (pathway enrichment) - conflicted (namespace conflict resolution)

## Analysis Workflow

1.  Data import from `read/` directory using relative paths from project root
2.  DESeq2 analysis with factor levels: group (WT, KO), replicate (1,2,3)
3.  Visualization generation saved to `write/figures/`
4.  Results tables saved to `write/tables/`
5.  All scripts expect execution from repository root for correct relative paths