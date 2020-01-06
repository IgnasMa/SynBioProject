# SynBioProject
Final project for Synthetic Biology programming course


Data: gene expression cancer RNA-Seq Data Set
Taken from: https://archive.ics.uci.edu/ml/datasets/gene+expression+cancer+RNA-Seq
Source: Samuele Fiorini, samuele.fiorini '@' dibris.unige.it, University of Genoa, redistributed under Creative Commons license (http://creativecommons.org/licenses/by/3.0/legalcode) from https://www.synapse.org/#!Synapse:syn4301332.

The dataset is composed of 801 instances and 20531 attributes. Adittionally there is a data file for cancer type for each sample names "labels"

Data has N/A missing values, however it's know that technical biases for gene caprutes and sequencing might arrise, which can lead to "0" expression values. 
Imputation of data could be performed after clustering

Before analysis, the data was explored descriptively. Due to large number of features in the data set a Principal Component Analysis was performed to explore the data. Data formed 5 clusters according to the cancer type. 

2020/01/06
Before doing clustering on the data, a distribution of sum of counts for each sample was plotted. This showed that the count number for each sample is similar: 132287.85 +- 3183.43 and the data counts are already normalized.

Variability of each gene's expression was inspected by ploting log10(1 + gene expression fano_f) againt log10(1+mean gene expression).

The data was stored in AnnData object, labeled with Cancer type labels.
Data leiden clustering was performed using different number of princial components - 10; 20; 30; 40; 50.

1. Data, clustered with 30 and 50 PCs look the most correct, as the granuality of clustering matches the labels of cancer types (single type cancer samples (except BRCA cancer sample) are clustered into one cluster in gene expression space).
2. BRCA cancer sample seems to form two populations and it clustered into two groups.
3. Differential gene expression analysis must be carried out to understand if clustering inside single cancer type provides any additional information.
