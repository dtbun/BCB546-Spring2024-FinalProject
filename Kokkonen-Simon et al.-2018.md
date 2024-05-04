# Introduction/summary to the original paper including the overview of results’ replication: 
 
# Reference: 
Kokkonen-Simon, K.M. et al. (2018) ‘Marked disparity of microrna modulation by cgmp-selective PDE5 versus PDE9 inhibitors in heart disease’, JCI Insight, 3(15). doi:10.1172/jci.insight.121739. 
 
# Background: 
MicroRNAs (miRs) are small ribonucleic acids that regulate gene expression by facilitating mRNA degradation, inhibiting protein translation, or degrading polypeptides. They have been found to be involved in heart disease and used as diagnostic and therapeutic agents. 
Hypothesis: miRs profiling could distinguish between two therapeutic interventions, PDE5-I and PDE9-I, which activate PKG by different cGMP pools.  
Findings: miRs profiles of these two drugs were dramatically different, with PDE5-I reducing a broad array of miRs associated with the disease state, while PDE9-I had virtually no impact. 
 
# Technical details of your replication of analyses: 

The paper originally used Bioconductor’s DESeq package (v1.26.0.) to identify differentially expressed genes while ANOVA was used to compare gene expression levels across multiple experimental conditions or treatments. But for all our analysis we used both R packages: DESeq2 and Limma to compare the outputs of both. Limma is tailored for microarray data but DESeq2 is particularly designed for RNAseq data. They did not mention anything about the threshold of FDR correction applied either but simply stated the significance level for ANOVA to be < 0.01.
The paper used Morpheus program for heatmap generation while we used pheatmap package in R studio itself.
Data preprocessing was done using both Python and R as suggested by the paper.
We went down from 1900 to 511 based on more than 50% of mice had reads for a given miRNA. Further, we were left with 376 after comparing miRNAs against the mouse miRNA record in Mus musculus miRgeneDB database. In the pre-processing, the scripts get to 370 miRNA due to 5 miRNA that have miRNA1 / miRNA2 format. These were matched manually with Excel and added back in manually to achieve 376 miRNA. Extra processing was needed for PO+PDE5 vs. PO analysis where we removed those data for which sum of rows for miRNA count was < 10 for PO+PDE5 samples to get rid of outliers.

DESeq analysis was done following the DESeq vignette:

(http://bioconductor.org/packages/devel/bioc/vignettes/DESeq2/inst/doc/DESeq2.html#heatmap-of-the-count-matrix).

Limma analysis was done following limma vignettes:

https://bioconductor.org/packages/devel/workflows/vignettes/RNAseq123/inst/doc/limmaWorkflow.html
https://ucdavis-bioinformatics-training.github.io/2018-June-RNA-Seq-Workshop/thursday/DE.html 

# Figure 1a:
The original figure displayed 111 significantly regulated miRNAs between pressure overloaded PO versus negative control (Sham). Most of the miRNAs were upregulated after surgery at the left ventricular atrium of heart including miRNAs involved in hypertrophy and fibrosis like mmu-miR-208b-3p, mmu-miR-34c-5p, mmu-miR-199a-3p/mmu-miR-199b-3p, mmu-miR-21a-3p and mmu-miR-21a-3p.

DESeq2

In our analysis, after FDR correction was applied, there were only 96 significantly regulated miRNAs and most of them were upregulated including those involved in hypertrophy. The volcano plot was plot drawn which showed similar trend as that of paper leaning towards significant upregulation.

Limma

In our analysis, we normalized the data using trimmed mean of M-values (TMM), removed heteroscedascity from the count data, fit into 2 different linear models, smoothed out errors with Empircal Bayes smoothing, performed differential expression analysis, and used Benjamini-Hochbnerg method to adjust p-values. It was found that there 81 significantly regulated miRNAs and similarly most of them were upregulated including those involved in hypertrophy. The volcano plot was plot drawn which showed similar trend as that of paper leaning towards significant upregulation.


# Figure 1b:
The original figure displayed 142 significantly regulated miRNAs between pressure overloaded PO + PDE5 versus PO. Most of the miRNAs were downregulated after the injection of PDE5 to the mice undergone surgery which is kind of reversing the effect of pressure overload.

DESeq2

From this analysis, 97 miRNAs were found significantly expressed. The volcano plot was drawn which showed similar trend as that of paper leaning towards significant downregulation.
We tried attempting to create a heatmap out of curiosity for the top microRNAs with p-adjusted < 0.05. The clustering was done considering columns only. As can be seen in the figure, significant downregulation of miRNAs after the injection of PED5 was evident.

Limma

From this analysis, 208 miRNAs were found significantly expressed, which is very different from the article. This is due to lack of extra filtering as seen in the DESeq2 analysis with extra pre-processing. The volcano plot was drawn which showed similar trend as that of paper leaning towards significant downregulation.
We also attempted to create a heatmap using limma out of curiosity for the top microRNAs with p-adjusted < 0.05. The clustering was done with rows and columns. As can be seen in the figure, significant downregulation of miRNAs after the injection of PED5 was evident.


# Figure 1c:
The figure displayed the volcano plot for miRNAs between PO+PDE9I (PO+PF-9613) vs PO. The paper showed only 9 differentially expressed miRNAs which is not profound in comparison to PO+PDE5.

DESeq2

Using DESeq in R, we got only 3 differentially expressed miRNAs, out of which only one matched the differentially expressed miRNAs list from the paper. We also had to use the ‘p-value <0.05’ to get the differentially expressed miRs and not the ‘padj <0.05’ (adjusted p values to exclude the false positives) as we were getting zero differentially expressed miRNAs with the latter. The volcano plot in the paper and the volcano plot developed by us look similar but do not meet the number of differentially expressed miRNA details. However, the conclusion that the PDE9-I drug has a curing effect like PDE5-I but doesn’t cause any alteration at the miRs level, unlike PDE5-I, which influences miRs, matches our conclusion. 

Limma

Using the Limma package in R, we were able to obtain four significantly differentially expressed miRNAs: Mmu-miR-501-3p, Mmu-miR-376b-3p, Mmu-miR-3061-3p and Mmu-miR-222-5p. Interestingly, only Mmu-miR-501-3p matched with the paper’s data, as well as with the reproduced DESeq2 data. However, the data from both analyses performed by us (DESeq2 and Limma) had a match of 3 out of 4 miRNAs, being Mmu-miR-376b-3p the only one excluded. The most interesting feature of this analysis, was that once set the adjustable method “BH”, our dataset with Differentially Expressed miRNAs became empty, meaning that no DEGs were found with a p-value <0.05. Therefore, we were forced to apply the statistics on the raw p-value <0.05, without any adjustment, thus obtainingthe four significant miRNAs mentioned above. 
With the Limma approach, we were able to obtain the same shape of distribution of miRNAs along the volcano plot. However, the X axis, which represents the Log2 Fold Change values, is widely spread in contrast to the paper and DESeq2 results. 

# Figure 1d:
The original figure displayed 111 significantly regulated miRNAs among PO versus sham, PO + PDE5 and PO+PDE9 from an independent multigroup testing using ANOVA. They have plotted a heatmap for this analysis after that.
PO + PDE5 versus PO.

DESeq2

We used DESeQ2 package in R instead and found 39 number of differentially expressed miRNAs instead. We tried plotting our data using pheatmap package of R itself. It could be due to improper grouping of multiple groups in R. Sadly, we did not have time to troubleshoot and publish but we plan to figure that out later out of curiosity even after the submission deadline. 

Limma

We used limma package in R instead and found 0 differentially expressed miRNAs when using p-adjusted < 0.05. When removing the adjustment method, it was found that there are 64 differentially expressed miRNA that have p-value < 0.05. This could be due to improper grouping as suspected in the DESeq analysis as well as missing an extra filtering step in the miRNA data. 


