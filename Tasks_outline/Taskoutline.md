Want to see effect of drugs on miRs. 
Testing inhibitors of phosphodiesters type 5 or type 9 (PDE5-I, PDE9-I) in regards to miRs.

Their (miRs) primary role is repressing gene expression by facilitating mRNA degradation, inhibiting protein translation, or degrading polypeptides through complementary binding to the 3′-UTR of target mRNAs. They appear to be based around controlling signaling pathways, however their expression is affected by disease and therapeutics.

However, growing evidence demonstrating their modification by intracellular and environmental signaling have led to their exploration as markers of disease therapy, of particular interest to the efforts to better personalize medical treatment (12, 13).



# Outline for the project

# First thing is first
* Read the article and take notes on what is happening (these notes can be put together for the article description and what we need to do)
* Break down the Methods into tasks on processing data, data analysis, figure generation, and extra figures we think might be good to have.
* https://doi.org/10.1172/jci.insight.121739

# Tasks from the assignment:
This should entail:
* Downloading, inspecting, and describing the data utilized in the study.
* Processing the data if necessary to format them for the analysis the group has chosen to reproduce.
* Rerunning the analysis described in the manuscript using your personal computers or ISU HPC resources.
* Providing visual summaries (e.g., ggplot figures) of your results.
The graded deliverables that each group will provide will include a GitHub Repository and an In-Class Presentation.

# Data
* add details about data
* miRs were filtered according to the following: more than 50% of mice had reads for a given miR, and the miR was present in the Mus musculus miRgeneDB database

# Figure 1
*  displays miR-seq results as volcano and heatmap plots for 3 group comparisons: PO+vehicle versus sham-control, PO+PDE5-I versus PO+vehicle, and PO+PDE9-I versus PO+vehicle.
    * Need to split the data by these 3 groups.
    * (A) Volcano plot of miRs altered in PO versus sham, with miRs relevant to cardiac hypertrophy/fibrosis labeled. (B) Volcano plot of miRs altered in PO+Sil versus PO. (C) Volcano plot of miRs altered in PO+PF-9613 versus PO.
    * Need to be able to differentially label volcano plot dots:
        * dark gray dots indicate differentially expressed miRs;
        * green triangles indicate miRs increased with PO, and decreased with drug treatment;
        * red triangles indicate miRs decreased with PO, and increased with drug treatment; and
        * pink diamonds indicate miRs labeled in panel
* (D) Heatmap of all miRs changed significantly with PO for all treatment groups, clustered by both rows (miRs) and columns (samples). Row labels (i.e., miR names) can be found in Supplemental Table 4.
