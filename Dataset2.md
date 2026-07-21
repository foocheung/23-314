# 23-314 Frase Fostamatinib D5 Analysis

## Datasets

### 210127_0187_gustaf_scRNA-Seq Samples

- Fosta007_d5
- Fosta007_pre_SP
- Fosta08_d5
- Fosta09_d5_SP
- Fosta10_d5
- Fosta10_pre_SP
- Fosta007_d5_SP
- Fosta008_pre
- Fosta08_d5_SP
- Fosta09_pre
- Fosta10_d5_SP
- Fosta007_pre
- Fosta008_pre_SP
- Fosta09_d5
- Fosta09_pre_SP
- Fosta10_pre

### 201221_0167_gustaf_scRNA-Seq Samples

- PBMC_covid01_pre
- PBMC_Fosta002_d5_SP
- PBMC_covid01_d5
- PBMC_covid01_pre_SP
- PBMC_Fosta002_pre
- PBMC_covid01_d5_SP
- PBMC_Fosta002_d5
- PBMC_Fosta002_pre_SP

## Analysis Workflow

1. CellRanger pipeline for FASTQ files provided by collaborators
2. Basic quality control and data integration
3. Cell type identification via Azimuth
4. Differential expression analysis (Placebo vs. Fostamatinib)

## CellRanger Run Summary

- Samples ending in `_SP` showed major quality issues, including poor transcriptome mapping and low gene detection per cell.
- Most samples from `210127_0187_gustaf_scRNA-Seq` were of poor quality. The only samples with acceptable metrics (although still showing relatively low transcriptome mapping of ~70%) were `Fosta007_pre`, `Fosta10_d5`, and `Fosta10_pre`.
- `PBMC_Fosta002_d5`, `PBMC_Fosta002_pre`, `PBMC_covid01_d5`, and `PBMC_covid01_pre` were of good quality and suitable for downstream analyses.

The following samples were initially identified as suitable for downstream analyses.

### Day 0

- Fosta007_pre
- Fosta10_pre
- PBMC_Fosta002_pre *(shallow sequencing; ~12,000 reads per cell)*
- PBMC_covid01_pre

### Day 5

- Fosta10_d5
- PBMC_Fosta002_d5
- PBMC_covid01_d5

## CITE-seq Processing Notes

- The `_SP` samples correspond to ADT libraries from the CITE-seq experiments.
- Processing the ADT data requires the feature list, which was not provided.
- For differential expression analysis, the ADT data were excluded, and only the gene expression (GEX) data were analyzed.
- Reprocessing from the raw, unfiltered 10x files did not substantially improve the quality of the poorly performing samples.

## Final Datasets Used for Analysis

### Placebo

| Timepoint | Sample |
|-----------|--------|
| Day 0 | `PBMC_covid01_pre` |
| Day 5 | `PBMC_covid01_d5` |

### Fostamatinib

| Timepoint | Sample |
|-----------|--------|
| Day 0 | `PBMC_Fosta002_pre` |
| Day 5 | `PBMC_Fosta002_d5` |

The samples `Fosta007_pre`, `Fosta10_pre`, and `Fosta10_d5` were excluded after further review because they remained of suboptimal quality.
