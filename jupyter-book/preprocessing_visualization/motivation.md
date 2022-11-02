# Motivation

Single-cell RNA-seq datasets have two important properties that one should have in mind when performing an analysis.
Firstly, scRNA-seq are drop-out meaning that there is an excessive number of zeros in the data due to limiting mRNA.
Secondly, the potential for correcting the data and performing quality control might be limited as the data may be confounded with biology.
It is therefore crucial to select preprocessing methods that are suited to the underlying data without overcorrecting or removing biological effects.

This chapter will guide you through the steps of data preprocessing and visualization.
The set of tools for the analysis of single-cell RNA-sequencing data is evolving fast due to new sequencing technologies and a growing number of captured cells, measured genes and identified cell populations {cite}`zappia_over_2021`.
Many of these tools are dedicated to preprocessing which aims to address the following analysis steps: doublet detection, quality control, normalization, feature selection, and dimensionality reduction.
The tools selected throughout this chapter can heavily affect downstream analysis and interpretation of the data.
For example, if you filter out too many cells during quality control, you might lose rare cell subpopulations and miss insight into interesting cell biology.
Whereas if you are too permissive, you might have a hard time annotating your cells if you did not exclude poor quality cells in your preprocessing pipeline.
Therefore, it is important to select tools that provide a best practice and that proved to outperform other tools with respect to downstream tasks.
In many cases, you will still have to re-assess your preprocessing analysis and change, for example, the filtering strategy.
This is common and the daily struggle of every computational biologist.

The starting point of this notebook is single-cell data that has been processed as previously described in the raw processing chapter.
The data was aligned to obtain matrices of molecular counts, the so-called count matrices, or read counts (read matrices).
The difference between count and read matrices depends on whether unique molecular identifiers (UMIs) were included in the single-cell library construction protocol.
Read and count matrices have the dimension number of barcodes x number of transcripts.
It is important to note that the term "barcode" is used here instead of "cell" as a barcode might wrongly have tagged multiple cells (doublet) or might have not tagged any cell (empty droplet/well).
We will elaborate more on this in the next section "Doublet detection".

## References

```{bibliography}
:filter: docname in docnames
```