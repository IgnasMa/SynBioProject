# SynBioProject
Final project for Synthetic Biology programming course


Data: gene expression cancer RNA-Seq Data Set
Taken from: https://archive.ics.uci.edu/ml/datasets/gene+expression+cancer+RNA-Seq
Source: Samuele Fiorini, samuele.fiorini '@' dibris.unige.it, University of Genoa, redistributed under Creative Commons license (http://creativecommons.org/licenses/by/3.0/legalcode) from https://www.synapse.org/#!Synapse:syn4301332.

The dataset is composed of 801 instances and 20531 attributes. Adittionally there is a data file for cancer type for each sample names "labels"

Data has N/A missing values, however it's know that technical biases for gene caprutes and sequencing might arrise, which can lead to "0" expression values. 
Imputation of data could be performed after clustering

Before analysis, the data was explored descriptively. Due to large number of features in the data set a Principal Component Analysis was performed to explore the data. Data formed 5 clusters according to the cancer type. 
