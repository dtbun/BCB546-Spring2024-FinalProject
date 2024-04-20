# Outline for the project

# First thing is first
* Read the article and take notes on what is happening (these notes can be put together for the article description and what we need to do)
* Break down the Methods into tasks on processing data, data analysis, figure generation, and extra figures we think might be good to have.
* DOI 10.1007/s13277-015-3576-y

# Tasks from the assignment:
This should entail:
* Downloading, inspecting, and describing the data utilized in the study.
* Processing the data if necessary to format them for the analysis the group has chosen to reproduce.
* Rerunning the analysis described in the manuscript using your personal computers or ISU HPC resources.
* Providing visual summaries (e.g., ggplot figures) of your results.
The graded deliverables that each group will provide will include a GitHub Repository and an In-Class Presentation.

# Data
* The phenotype including age at diagnosis, gender, and smoking history are also available from the public website 
  (http://genome.cshlp.org/content/22/11/2109/suppl/DC1).
* The transcriptome sequencing data from 68 lung adenocarcinoma patients with validated smoking status were downloaded from Gene Expression Omnibus (GEO) with 
  accession number GSE40419. https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE40419
* For validation of genes identified in nonsmoker group, independent RNA-seq data from six nonsmoker patients were downloaded from GEO with accession number 
  GSE37765 [12].

# Methods tasks (WIP)
* Downloading, inspecting, and describing the data utilized in the study.
    * This will entail finding all of the data and downloading it. Then uploading it to Github or another resource so we all have it avaiable on the cloud 
      somewhere.
    * Inspecting the data and describing would probably be telling what characteristics of the data are. Probably file sizes, organization, what kind of data is in 
      these files, etc.
    * NOTE ON BAM FILES: Hufford recommends to use samtools in Unix to inspect the file as BAM files are not human readable like SAM files if using UNIX. Class 
      4/19/2024

* Figure 1 and Figure 2 are the figures we can complete. Volcano plot, heat map, etc. Tables should be simple to make actually so maybe we can do those too? idk
* Data Preparation
    * Need to process/filter the data: We applied a stringent filter on the data to remove the gene tags with sparse count data. Genes with at least 1 count per 
     million (cpm) in at least half of the sample size were kept in the analysis. There are 62,069 gene tags in the raw data and 17,757 of them were kept in the 
     analysis after the filter. The biological coefficient of variation (BCV) in the 136 RNA-seq samples was about 0.4, which indicates that a good quality of this 
     dataset as a typical BCV value from a well-controlled experiment is 0.4 for human data [13].
        1. Download the .gz file. Extract with 7-Zip or your favorite file processor for this. The file is too large to add to Github uncompressed.
        2. RNA-Seq data is 87 lung adenocarcinomas and 77 adjacent normal tissues, so need to split the data into 2 separate files for adenocarcinomas and norm?
        3. The file, RNA_seq.txt (uncompressed version) needs to be cleaned up. Remove _nor columns or separate _nor and cancer into separate files.
        4. Keep the gene column and the sample column.
        5. Can remove accession, chrom, start, end, strand?
        6. After cleaning up the RNA-seq data, we also need to append data on if that LC sample is a smoker/nonsmoker. Need to transpose one of the files to append 
        data to.
        7. Then apply filter to take only genes with at least 1 counter per million (cpm) in at least half of the sample size? There are 62,069 gene tags in the 
        raw data and 17,757 of them were kept in the analysis after the filter.- what does this mean? This needs to be done for Fig 2, but I'm not sure which data 
        this is referring to.

* Data processing/analysis
* Figure 1.
    * Use edgeR to identify genes differently expressed between tumor/normal and nonsmoker/smoker patients
    * CLuster plot (fig 1a) the 136 RNA-seq samples from 68 patients based on leading log-fold change
    * They filtered the data for plots b and onward as mentioned previously.
    * Plot B-C in Fig. 1 displays the average log-counts per million (logCPM) against log2-fold change (logFC) in nonsmoker and smoker group, respectively.
    * Plot D in Fig. 1 is a venn diagram for a total of 2273 and 3031 genes with FDR<0.05 and |logFC|>1 were identified in nonsmoker and smoker group, 
      respectively, and 1967 of them are shared in both groups (Fig. 1d, Supplementary 2). About 95 % of the genes identified in nonsmoking group are also detected 
      in smoking lung adenocarcinoma patients
    * Plot E in Fig. 1 is just bar graph for upregulated and downregulated separated by nonsmoker/smoker.
    * LITTLE EXTRA PROCESSING FOR FIG.1 E: We divided the genes with FDR<0.05 and |logFC|> 1 into five groups: (1) genes identified in only nonsmoker patients, (2) 
      genes identified in only smoker patients, (3) genes identified in both groups but with greater fold change in nonsmoker patients, (4) genes identified in 
      both group but with greater fold change in smoker patients, and (5) genes identified in both group with similar logFC value.
    * Then can do boxplot F in Fig 1. for logFC in these 5 groups.
    * Not sure what G in Fig 1 is.
* Figure 2.
    * Need to do the CPM analysis. Not sure which data that is referring to.
    * a Heatmap of normalized count per million (CPM) for genes that behave differently between two groups. Yellow and green bar denote normal and tumor tissues, 
      respectively. Nonsmoker group is on the left.
    * b Bar plot of CPM for genes. Left, nonsmoker patients; right, smoker patients. Red and green colors denote CPM from normal and tumor tissues, respectively
    * Pair-end RNA-seq reads were aligned to human genome assembly Ensembl GRCh37 by Tophat. HTSeq was used to count the reads by genes (http://www- 
     huber.embl.de/users/anders/HTSeq/doc/tour.html#counting-reads-by-genes). We used R Bioconductor edgeR to perform the differential expression analysis, and we 
      applied a general linear model: lung tissue expression∼smoking+smoking:patient+ smoking:tissue to accommodate the multifactor design of the experiment.







# Extra info
* Figure 1 b, c Volcano plots of signals from differential analysis in nonsmoker and smoker patients, respectively.




* Pair-end RNA-seq reads were aligned to human genome assembly Ensembl GRCh37 by Tophat. HTSeq was used to count the reads by genes (http://www-huber.embl.de/ users/anders/HTSeq/doc/tour.html#counting-reads-by-genes). We used R Bioconductor edgeR to perform the differential expression analysis, and we applied a general linear model: lung tissue expression∼smoking+smoking:patient+ smoking:tissue to accommodate the multifactor design of the experiment. This model incorporated the main effect for smoking plus interactions with patients and tissues, thus allowing us to identify genes differentially expressed in tumor versus normal tissue in nonsmoker or smoker patients, and genes that behave differently between smoker and nonsmoker patients. To make sure there were sufficient counts for each gene in the test, only tags that had at least 1 count per million (cpm) in at least half of the sample size were kept in the analysis. Genes with Benjamini-Hochberg adjusted FDR<0.05 and absolute values of logFC greater than 1 were reported as significant genes.
* Data filtering process: We applied a stringent filter on the data to remove the gene tags with sparse count data. Genes with at least 1 count per million (cpm) in at least half of the sample size were kept in the analysis. There are 62,069 gene tags in the raw data and 17,757 of them were kept in the analysis after the filter. The biological coefficient of variation (BCV) in the 136 RNA-seq samples was about 0.4, which indicates that a good quality of this dataset as a typical BCV value from a well-controlled experiment is 0.4 for human data [13].




