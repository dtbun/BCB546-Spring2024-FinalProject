# BCB546_final_project

# Daniel Bun, Ashmita Mainali, Manuela Chaves, Esther Jokodola and Vedika Desai

The following document describes the directory content for the final project of the EEOB 546
class. This project is based on the paper “Marked disparity of microRNA modulation by cGMP-
selective PDE5 versus PDE9 inhibitors in heart disease” from Kokkonen-Simon et al. (2018, DOI:
10.1172/jci.insight.121739).

This repository contains the following files:

## Description of Data folder:
This folder contains the raw count data "raw_mirna.txt", miRNAs filtered based on >50% of mice has the particular miRNA in "miRNA_filtered.txt", the final miRNAs after matching with MirGene database in "miRNA_filtered_final", metadata in "metadata.txt" including the list of mRNAs recorded in MirGene data base in "mirgene.txt". There is also the supplementary file from this paper "supplemental_jci.insight.pdf". Additionally, data used for each figures are included as "fig1a_data.txt" and so on.


## Description of Data processing folder:
This folder contains input files (mirbase.txt, miRNA.txt, raw_mirna.txt) and final filtered files generated from the R and Python scripts. The goal of these scripts is to replicate the filtering process by Kokkonen et al. 2018 performed. As such, we went from 1903 -> 511 -> 376 miRNA. In the pre-processing the scripts get to 370 miRNA due to 5 miRNA that have miRNA1 / miRNA2 format. These were matched manually with Excel and added back in manually to achieve 376 miRNA.


## Description of Figure 1a: 
Contains two sub-folders for each Limma and DeseQ analysis. Within each folder, respective R-markdown files(figure1a_limma/figure1c_deseq) contains codes for running the differential gene expression analysis and plotting volcano plots and heatmaps. The text files for filtered data are also provided as "mirna_filtered_final.txt" . Also the volcano plots and figures are included. The table for differential gene expression "deseq2_POvsSham.results" plus significantly expressed gene "deseq2_POvsSham.sign.results" with padj < 0.05 are attached for  DeseQ while the output file for Limma is provided as "limma_miRNA_DEA_fig1a.csv". 

## Description of Figure 1b:
Contains two sub-folders for each Limma and DeseQ analysis. Within each folder, respective R-markdown files(figure1b_limma/figure1b_deseq) contains codes for running the differential gene expression analysis and plotting volcano plots and heatmaps. The text files for filtered data are also provided as "mirna_filtered_final.txt" . Also the volcano plots and heatmap are included. The table for differential gene expression "deseq2_PO+PDE5vsPO.results" plus significantly expressed gene "deseq2_PO+PDE5vsPO.sign.results" with padj < 0.05 are attached for  DeseQ while the output file for Limma is provided as "limma_miRNA_DEA_fig1b.csv". 


## Description of Figure 1c:
Contains two sub-folders for each Limma and DeseQ analysis. Within each folder, respective R-markdown files(figure1c_limma/figure1c_deseq) contains codes for running the differential gene expression analysis and plotting volcano plots and heatmaps. The text files for filtered data are also provided as fig1c_data.txt .Also the volcano plots and heatmap are included. The table for differential gene expression "deseq2_PO+PDE9vsPO.results" plus significantly expressed gene "deseq2_PO+PDE5vsPO.sign.results" with padj < 0.05 are attached. As well "limma_miRNA_DEA_fig1c.csv" for differential gene expression is attached for  DeseQ while the output file for Limma is provided as "limma_miRNA_DEA_fig1c.csv". 


## Description of Figure 1d:
Contains two sub-folders for each Limma and DeseQ analysis. Within each folder, respective R-markdown files(figure1d_limma/figure1c_deseq) contains codes for running the differential gene expression analysis and plotting volcano plots and heatmaps. The text files for filtered data are also provided as fig1d_data.txt. Also the heatmap is included. The table for differential gene expression plus  "deseq2_multiplegroups.results" significantly expressed gene "deseq2_multiplegroups.sign.results" with padj < 0.05 are attached for DeseQ while the output file for Limma is provided as "limma_miRNA_DEA_fig1d.csv". 


## Description of Kokk0nen_et_al-2018.md file
This .md file introduces the original paper, explains the technical details of our replication of the analyses and summarizes our replication of the original results.
