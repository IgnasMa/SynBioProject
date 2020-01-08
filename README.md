# SynBioProject
Final project for Synthetic Biology programming course


Data: gene expression cancer RNA-Seq Data Set
Taken from: https://archive.ics.uci.edu/ml/datasets/gene+expression+cancer+RNA-Seq
Source: Samuele Fiorini, samuele.fiorini '@' dibris.unige.it, University of Genoa, redistributed under Creative Commons license (http://creativecommons.org/licenses/by/3.0/legalcode) from https://www.synapse.org/#!Synapse:syn4301332.

The dataset is composed of 801 instances and 20531 attributes. Adittionally there is a data file for cancer type for each sample names "labels"

Data has N/A missing values, however it's know that technical biases for gene caprutes and sequencing might arrise, which can lead to "0" expression values. 
Imputation of data could be performed after clustering

Before analysis, the data was explored descriptively. Due to large number of features in the data set a Principal Component Analysis was performed to explore the data. Data formed 5 clusters according to the cancer type. 
![alt text](https://github.com/IgnasMa/SynBioProject/blob/master/Graphs/PCA_analysis.png)

2020/01/06
Before doing clustering on the data, a distribution of sum of counts for each sample was plotted. This showed that the count number for each sample is similar: 132287.85 +- 3183.43 and the data counts are already normalized.
![alt text](https://github.com/IgnasMa/SynBioProject/blob/master/Graphs/sum_counts.png)


Variability of each gene's expression was inspected by ploting log10(1 + gene expression fano_f) againt log10(1+mean gene expression).
![alt text](https://github.com/IgnasMa/SynBioProject/blob/master/Graphs/Dispersion_vs_mean-expression.png)


The data was stored in AnnData object, labeled with Cancer type labels.
Data leiden clustering was performed using different number of princial components - 10; 20; 30; 40; 50.

10 Principal components
![alt text](https://github.com/IgnasMa/SynBioProject/blob/master/Graphs/clustering_10PCs.png)

20 Principal components
![alt text](https://github.com/IgnasMa/SynBioProject/blob/master/Graphs/clustering_20PCs.png)


2020/01/08

The data was count normalized - even though all the samples had a similar count coverage, total counts were normalized to 130k per sample.
Highly variable genes were detected in the sample to make the clustering easier.
Data was clustered using 10, 20, 30, 40, 50 PCs.
Using more then 30 PCs yields similar results.
Differential gene expression analysis was performed. It showed that BRCA sample single population segregation into two clusters yields no significant  expression fold change. 
Visual inspection of gene expression in this topology ielded, that majority of genes are equally expressed in both clusters
Based on this, clustering with 30 PCs was used (granularity, that merges one of the BRCA populations into single cluster). 
Differential gene expression was performed and will by analyzed later.
30 Principal components
![alt text](https://github.com/IgnasMa/SynBioProject/blob/master/Graphs/clustering_30PCs.png)

40 Principal components
![alt text](https://github.com/IgnasMa/SynBioProject/blob/master/Graphs/clustering_40PCs.png)

50 Principal components
![alt text](https://github.com/IgnasMa/SynBioProject/blob/master/Graphs/clustering_50PCs.png)

1. Data, clustered with 30 and 50 PCs look the most correct, as the granuality of clustering matches the labels of cancer types (single type cancer samples (except BRCA cancer sample) are clustered into one cluster in gene expression space).
2. BRCA cancer sample seems to form two populations and it clustered into two groups.
3. Differential gene expression analysis must be carried out to understand if clustering inside single cancer type provides any additional information.
