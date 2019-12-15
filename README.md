# TDimpute 
TDimpute is designed to impute missing gene expression data from DNA methylation data by using transfer learning based neural network.
The method is still on progress and the preprint could be found at [here](https://doi.org/10.1101/803692). For any questions about the code or original datasets, please contact zhoux85@mail2.sysu.edu.cn

# Requirements
tensorflow 1.11.0, python 3.6.5, preprocessCore 1.48.0

# Data preparation
RNA-seq data (UNC IlluminaHiSeq_RNASeqV2_RSEM), DNA methylation data (JHU-USC HumanMethylation450), downloaded from TCGA.

We use the Wilms tumor dataset from TARGET cancer project as a example for imputing RNA-seq data using DNA methylation data. Note that the RNA-seq data should be quantified as RSEM estimated read counts, since we pretrained the neural network with the RNA-seq data of RNASeqV2_RSEM. The pretrained model with other quantification, such as readcounts, TPM, will be provided later.

# Usage
### quantile normalization
quantile_normalization_process.R is used to remove technical variabilities between TCGA and the dataset you want to impute: specifically, the TCGA data is considered as reference to normalize the your dataset into the same distribution.  
"reference_distribution_DNA_TCGA.RData" and "reference_distribution_RNA_TCGA.RData" are two processed files using funciton "normalize.quantiles.determine.target" in R package "preprocessCore". They can be loaded directly as reference distribution of DNA methylation and RNA-seq data from TCGA.

### To run script and sample dataset:
python TDimpute_without_transfer.py GPU_index cancer_name full_dataset_path imputed_dataset_path

In the script TDimpute.py, RNA_DNA_combine.csv is a 33-cancer dataset downloaded from TCGA including gene expression and DNA methylation data.



