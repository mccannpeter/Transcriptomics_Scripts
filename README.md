# Transcriptomics Pipelines

This repository contains two complementary pipelines for RNA-seq data:

1. **HPC pipeline** (`hpc_pipeline.txt`)  
   - Bash scripts for cluster/HPC environments.  
   - Steps:  
     - Read trimming (Trimmomatic)  
     - Quality control (FastQC)  
     - Reference build + alignment (HISAT2)  
     - SAM→BAM conversion (samtools)  
     - Transcript assembly & quantification (StringTie)  
     - Count matrix generation (prepDE.py)  

2. **DESeq2 pipeline** (`deseq_pipeline.txt`)  
   - R workflow for downstream RNA-seq analysis.  
   - Steps:  
     - Import counts + metadata  
     - Prefiltering (zero-count and Wilcoxon)  
     - Differential expression (DESeq2 LRT and Wald tests)  
     - QC & exploratory plots (PCA, dispersion, MA, volcano, clustering)  
     - Heatmaps of top DEGs  
     - Export of per-condition gene lists for enrichment tools  

## Requirements
- HPC pipeline: Linux + cluster scheduler, modules for `trimmomatic`, `fastqc`, `hisat2`, `samtools`, `stringtie`, Python 2.7 (for prepDE).  
- R pipeline: R ≥ 4.0 with packages: `DESeq2`, `ggplot2`, `pheatmap`, `EnhancedVolcano`, `clusterProfiler`, `fgsea`, `msigdbr`, `WGCNA`, `reshape2`.  

## Usage
- Run the **HPC pipeline** to preprocess raw FASTQs into aligned, quantified counts.  
- Use the **DESeq2 pipeline** for statistical testing, visualization, and functional analysis.  

---