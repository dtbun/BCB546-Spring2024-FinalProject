# Outline for the project

* Read the article and take notes on what is happening (these notes can be put together for the article description and what we need to do)
* Break down the Methods into tasks on processing data, data analysis, figure generation, and extra figures we think might be good to have.
* DOI 10.1007/s13277-015-3576-y

# Data
* The phenotype including age at diagnosis, gender, and smoking history are also available from the public website (http://genome.cshlp.org/content/22/11/2109/suppl/
DC1).
* The transcriptome sequencing data from 68 lung adenocarcinoma patients with validated smoking status were downloaded from Gene Expression Omnibus (GEO) with accession number GSE40419.
* For validation of genes identified in nonsmoker group, independent RNA-seq data from six nonsmoker patients were downloaded from GEO with accession number GSE37765 [12].

# Methods tasks
* Figure 1 and Figure 2 are the figures we can complete. Volcano plot, heat map, etc
* Pair-end RNA-seq reads were aligned to human genome assembly Ensembl GRCh37 by Tophat. HTSeq was used to count the reads by genes (http://www-huber.embl.de/ users/anders/HTSeq/doc/tour.html#counting-reads-by-genes). We used R Bioconductor edgeR to perform the differential expression analysis, and we applied a general linear model: lung tissue expression∼smoking+smoking:patient+ smoking:tissue to accommodate the multifactor design of the experiment. This model incorporated the main effect for smoking plus interactions with patients and tissues, thus allowing us to identify genes differentially expressed in tumor versus normal tissue in nonsmoker or smoker patients, and genes that behave differently between smoker and nonsmoker patients. To make sure there were sufficient counts for each gene in the test, only tags that had at least 1 count per million (cpm) in at least half of the sample size were kept in the analysis. Genes with Benjamini-Hochberg adjusted FDR<0.05 and absolute values of logFC greater than 1 were reported as significant genes.
* Data filtering process: We applied a stringent filter on the data to remove the gene tags with sparse count data. Genes with at least 1 count per million (cpm) in at least half of the sample size were kept in the analysis. There are 62,069 gene tags in the raw data and 17,757 of them were kept in the analysis after the filter. The biological coefficient of variation (BCV) in the 136 RNA-seq samples was about 0.4, which indicates that a good quality of this dataset as a typical BCV value from a well-controlled experiment is 0.4 for human data [13].




