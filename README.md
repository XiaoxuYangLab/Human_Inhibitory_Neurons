# Human Inhibitory Neuron
This repository contains codes and pipelines, as well as data used in the analysis of human inhibitory and excitatory neuronal clonal dynamics and lineage relationships, with cell-type-specific mosaic variant barcoding analysis (cMVBA). WGS, MPAS, snMPAS, snRNA-seq data are available from multiple neurotypical postmortem donors. Raw WGS, MPAS, snMPAS, snRNAseq sequences from cortical regions, subregions from ID01, ID05, ID06, ID07, and ID08 are available at the NDA website under [accession number 919](https://nda.nih.gov/study.html?id=919) and SRA under accession numbers [PRJNA736951](https://trace.ncbi.nlm.nih.gov/Traces/study/?acc=PRJNA736951&o=acc_s%3Aa) and [PRJNA799597](https://trace.ncbi.nlm.nih.gov/Traces/study/?acc=PRJNA799597&o=acc_s%3Aa). WGS panel of normal data is available [here](https://trace.ncbi.nlm.nih.gov/Traces/study/?acc=PRJNA660493&o=acc_s%3Aa).

-----------------------------------

### 1. Pipelines for the process of whole-genome sequencing data

#### 1.1 Pipelines for WGS data process

WGS data processing is following [this pipeline](https://github.com/shishenyxx/Human_Inhibitory_Neurons/tree/main/Pipelines/Alignment).

Germline heterozygous variants are called with HaplotypeCaller following [this pipeline](https://github.com/shishenyxx/Sperm_control_cohort_mosaicism/tree/master/Pipelines/Preprocessing/Haplocaller).

#### 1.2 Pipelines for mosaic SNV/indel calling and variant annotations

Sample-unique variant calling with Mutect2 and Strelka paired mode is carried out following [this pipeline](https://github.com/shishenyxx/Adult_brain_somatic_mosaicism/tree/master/pipelines/WGS_SNV_indel_calling_pipeline/Mutect2_PM_Strelka2).

Sample-specific variant calling is first carried with [this pipeline](https://github.com/shishenyxx/Adult_brain_somatic_mosaicism/tree/master/pipelines/WGS_SNV_indel_calling_pipeline/Mutect2_single_mode) using Mutect2 single mode (full panel of normal). Followed with DeepMosaic is carried out following the [official guidelines](https://github.com/Virginiaxu/DeepMosaic) and MosaicForecast using [this pipeline](https://github.com/shishenyxx/Adult_brain_somatic_mosaicism/tree/master/pipelines/WGS_SNV_indel_calling_pipeline/MosaicForecast_pipeline).

Sample-unique and sample-specific variants are further called without control using MosaicHunter following [this pipeline](https://github.com/shishenyxx/Adult_brain_somatic_mosaicism/tree/master/pipelines/WGS_SNV_indel_calling_pipeline/MosaicHunter_single_mode_pipeline) and the 300x properties file.

Variants were further combined and annotations were performed using [this pipeline](https://github.com/shishenyxx/PASM/tree/master/Snakemake_pipeline). 

#### 1.3 Pipelines for single nucleus transcriptome sequencing analysis

Single nucleus transcriptome sequencing analysis with ResolveOME RNA seq pipeline is provided [here](https://github.com/shishenyxx/Human_Inhibitory_Neurons/tree/main/Pipelines/scRNAseq/ResolveOME).

Single nucleus transcriptome sequencing analysis with a 10x Genomics RNA seq pipeline is provided [here](https://github.com/shishenyxx/Human_Inhibitory_Neurons/blob/main/Analyses/20221223_7669_Ampliseq_QC/Bioskryb/Bioskryb_celltype_identificationV2_with_ref-Copy1.ipynb).

Cell identity was determined as described [here](https://github.com/shishenyxx/Human_Inhibitory_Neurons/blob/main/Analyses/20221223_7669_Ampliseq_QC/Bioskryb/Bioskryb_celltype_identificationV2.ipynb).
     
-----------------------------------

### 2. Pipelines for the process of Massive Parallel Amplicon Sequencing (MPAS) and single-nuclei Massive Parallel Amplicon Sequencing (snMPAS)

#### 2.1 Pipelines for MPAS and snMPAS data alignment and processing

Alignment and processing of MPAS and snMPAS were carried out following [this pipeline](https://github.com/shishenyxx/Adult_brain_somatic_mosaicism/tree/master/pipelines/MPAS_and_snMPAS_processing_pipeline)

#### 2.2 Pipelines for AF quantification and variant annotations

After alignment, candidate variants were further combined and genotyped using [this pipeline](https://github.com/shishenyxx/PASM/tree/master/Snakemake_pipeline) in every sample detected with MPAS and snMPAS. 

Quality control were carried out for WGS and MPAS MAFs measured in [ID01](https://github.com/shishenyxx/Human_Inhibitory_Neurons/blob/main/Analyses/20230114_7614_Ampliseq_QC/7614_interneuron_Ampliseq_QC_Rscript-Copy1.ipynb) and [ID05](https://github.com/shishenyxx/Human_Inhibitory_Neurons/blob/main/Analyses/20221223_7669_Ampliseq_QC/20230101_QC/7669_interneuron_Ampliseq_QC_Rscript.ipynb).


-----------------------------------

### 3. Identification the cell types by using whole-genome bisulfite sequencing analysis

#### 3.1 [Pipelines](https://github.com/shishenyxx/Human_Inhibitory_Neurons/tree/main/Pipelines/Methylome) for methylome analysis using BisMark

#### 3.2 [Statical analysis](https://github.com/shishenyxx/Human_Inhibitory_Neurons/blob/main/Methylome/plots/Human_Interneuron_Methylome_Plots.ipynb) combining published standards to identify the cell types

-----------------------------------

### 4. Computational and statistical analyses for human neuronal clonal distribution patterns

#### 4.1 Pipelines for mosaic variant determination, annotations, and plotting

Variant annotation for [ID01](https://github.com/shishenyxx/Human_Inhibitory_Neurons/blob/main/Analyses/20230114_7614_Ampliseq_QC/annotation/7614_Ampliseq_Annotation.ipynb) and [ID05](https://github.com/shishenyxx/Human_Inhibitory_Neurons/blob/main/Analyses/20221223_7669_Ampliseq_QC/20230105_annotation/7669_Ampliseq_Annotation.ipynb) are provided separately.

UpSet plot for [ID01](https://github.com/shishenyxx/Human_Inhibitory_Neurons/blob/main/Analyses/20230114_7614_Ampliseq_QC/variant_annotation/7614_Upset_plot.ipynb) and [ID05](https://github.com/shishenyxx/Human_Inhibitory_Neurons/blob/main/Analyses/20221223_7669_Ampliseq_QC/variant_annotation/7669_upset_plot.ipynb) variants.

#### 4.2 Pipelines for statistical analysis, and the related plotting

Fig.1 Single-nucleus RNA sequencing results for [cell type identification of sorted nuclei](https://github.com/shishenyxx/Human_Inhibitory_Neurons/blob/main/Analyses/20230913_Changuk_10X_interneuron_IGM/Cell_type_identification_for_sorted_nuclei.ipynb), Number of MVs categorized by location detected in each donor [ID01](Analyses/20230114_7614_Ampliseq_QC/variant_annotation/7614_variant_annotation.ipynb) or [ID05](Analyses/20221223_7669_Ampliseq_QC/variant_annotation/7669_variant_annotation.ipynb)

Fig.2 Heatmaps, dendrograms, and contour plots with kernel density estimation plots for strong Hippocampal lineage restriction: [ID01](Analyses/20230114_7614_Ampliseq_QC/CTX_BG_HIP/7614_CTX_BG_HIP.ipynb), [ID05](https://github.com/shishenyxx/Human_Inhibitory_Neurons/blob/main/Analyses/20221223_7669_Ampliseq_QC/CTX_BG_HIP/7669_CTX_BG_HIP.ipynb)

Fig.3 Bootstraps, AF Heatmaps and dendrograms and for sorted cortical excitatory and inhibitory neuronal pools: [ID01](Analyses/20230114_7614_Ampliseq_QC/Basic_correlation/7614_variant_by_sample_heatmap.ipynb), [ID05](Analyses/20221223_7669_Ampliseq_QC/Basic_characteristics_of_variants/7669_variant_by_sample_heatmap.ipynb)

Fig.4 ResolveOME analysis: [Cell type identification](Analyses/20221223_7669_Ampliseq_QC/Bioskryb/Bioskryb_celltype_identificationV2_with_ref.ipynb), [oncoplot](Analyses/20221223_7669_Ampliseq_QC/Bioskryb/DNA2/ResolveOME_DNA2_3_oncoplot.ipynb), [Peudobulk analysis](Analyses/20221223_7669_Ampliseq_QC/Bioskryb/DNA2/ResolveOME_DNA2_4_pseudobulk.ipynb), [Permutation test](Analyses/20221223_7669_Ampliseq_QC/Bioskryb/DNA2/ResolveOME_DNA2_6_permutation.ipynb), [DEG analysis between InN1 and InN2](Analyses/20221223_7669_Ampliseq_QC/Bioskryb/Asterisk_Marked_InN_DEG.csv)

Fig.5 AF Heatmap, dendrogram, contour plots with kernel density estimation plots for restricted clonal spread in a parietal lobe of ID05 is [here](Analyses/20221223_7669_Ampliseq_QC/Lobe/7669_R_P_1to17_varxsample_heatmap.ipynb)

Pearson correlation analysis for [ID01](https://github.com/shishenyxx/Human_Inhibitory_Neurons/blob/main/Analyses/20230114_7614_Ampliseq_QC/Basic_correlation/7614_var_by_var_corr_heatmap.ipynb) and [ID05](https://github.com/shishenyxx/Human_Inhibitory_Neurons/blob/main/Analyses/20221223_7669_Ampliseq_QC/Basic_characteristics_of_variants/7669_var_by_var_corr_umap.ipynb)

Lolliplot and geoclones for [ID01](https://github.com/shishenyxx/Human_Inhibitory_Neurons/blob/main/Analyses/20230114_7614_Ampliseq_QC/Rolliplot/7614_lolliplot.ipynb); [ID05 lollipolt](https://github.com/shishenyxx/Human_Inhibitory_Neurons/blob/main/Analyses/20221223_7669_Ampliseq_QC/Lolliplot/7669_lolliplot.ipynb) and [geoclones](https://github.com/shishenyxx/Human_Inhibitory_Neurons/blob/main/Analyses/20221223_7669_Ampliseq_QC/Basic_characteristics_of_variants/7669_geoclones.ipynb).

UMAP for variant AF for [ID01](Analyses/20230114_7614_Ampliseq_QC/UMAP/7614_UMAP.ipynb) and [ID05](Analyses/20221223_7669_Ampliseq_QC/UMAP/7669_UMAP.ipynb).
Simulated contamination and deconvolution for [ID01](Analyses/20230114_7614_Ampliseq_QC/Basic_correlation/7614_variant_by_sample_heatmap_ContC-T.ipynb), [ID05_contamination](Analyses/20221223_7669_Ampliseq_QC/Basic_characteristics_of_variants/7669_concolved_virtual_75COUPT2n25TBR1_heatmap.ipynb), [ID05 deconvolution](Analyses/20221223_7669_Ampliseq_QC/Basic_characteristics_of_variants/7669_deconvolved_DLX1_heatmap.ipynb).
Estimating the contribution of dorsal and ventral origin for DLX1+ inhibitory neurons for [ID01](Analyses/20230114_7614_Ampliseq_QC/Basic_correlation/7614_beta.ipynb) and [ID05](Analyses/20221223_7669_Ampliseq_QC/Basic_characteristics_of_variants/7669_beta.ipynb)

-----------------------------------

### 5. Contact:

:email: Changuk Chung: [chchung@health.ucsd.edu](mailto:chchung@health.ucsd.edu)

:email: Xiaoxu Yang: [xiaoxu.yang@genetics.utah.edu](xiaoxu.yang@genetics.utah.edu), or the Yang Lab [xiaoxuyanglab@gmail.com](mailto:xiaoxuyanglab@gmail.com)

:email: Joseph Gleeson: [jogleeson@health.ucsd.edu](mailto:jogleeson@health.ucsd.edu), or the Gleeson lab [gleesonlab@health.ucsd.edu](gleesonlab@health.ucsd.edu)

-----------------------------------

### 6. Cite the data and codes:
Chung C, Yang X, et al., Gleeson JG. Cell-type-resolved mosaicism reveals clonal dynamics of the human forebrain. 2024. (Nature, [DOI: 10.1038/s41586-024-07292-5](https://www.nature.com/articles/s41586-024-07292-5), [PMID: 38600385](https://pubmed.ncbi.nlm.nih.gov/38600385/) )


