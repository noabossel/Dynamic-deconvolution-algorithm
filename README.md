# Dynamic-deconvolution-algorithm
Dynamic deconvolution algorithm to infer cell type composition and infection-induced states from bulk measurements of complex mixture of immune cell types

System requirements: MATLAB (tested on R2018a)

The code_algorithm.zip contains the following files:
README.txt
deconvolution_algorithm.m
cell_types_marker_genes_from_sc_data.mat
small_dataset_to_demo.mat
bulk_WT_TLR10_T0_log2_data.mat
bulk_WT_TLR10_T4_log2_data.mat
bulk_WT_TLR10_T8_log2_data.mat

Instructions: 
Unzip the dynamic_deconvolution_algorithm.zip file and run the Matlab script from this directory. 

Running the code:
The function deconvolution_algorithm.m get as input the name of the .mat file with the bulk RNA-seq data.
The function outputs the estimators of each cell type frequency (k) and cell type infection-induced states (s) for each bulk RNA-seq sample. 
Example to run the code:  [k_cell_type_freq,s_cell_type_inf_induced_state]=deconvolution_algorithm('bulk_WT_TLR10_T0_log2_data');

The .mat file with the bulk RNA-seq data should contain 3 variables - 
1) exp_data: matrix with the log2 normalized expression data (row for each gene and column for each sample; size: #genes x #samples)
2) exp_genes: cell array with the name of the genes (gene symbols; size: #genes x 1)
2) exp_samples: cell array with the name of the samples (size: #samples x 1)

The code generates two output files: 
1) cell_type_freq.txt
2) cell_type_activation.txt

To run the code on a small dataset as demo:
Run the deconvolution_algorithm.m script with the input file small_dataset_to_demo.mat, or write as input ‘demo’ instead of the .mat file name.
e.g. [k_cell_type_freq,s_cell_type_inf_induced_state]=deconvolution_algorithm('demo') ;


To reproduced the data presented at the manuscript:
Run the deconvolution_algorithm.m script with the following input files:
1) bulk_WT_TLR10_T0_log2_data - bulk RNA-seq data of the 8 individuals before infection (t=0)
2) bulk_WT_TLR10_T4_log2_data - bulk RNA-seq data of the 8 individuals 4 hours post-infection (t=4h)
3) bulk_WT_TLR10_T8_log2_data - bulk RNA-seq data of the 8 individuals 8 hours post-infection (t=8h)


