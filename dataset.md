# Analysis Plan

The analysis is performed independently for each predicted cell type (`predicted.celltype.l1`) using an RNA pseudobulk differential expression workflow.

## Workflow

1. Filter cells
   - Retain singlet droplets only.
   - Remove cells with missing subject, treatment, LPS condition, or cell type annotations.

2. Standardize metadata
   - Treatment: Placebo or Fostamatinib
   - LPS condition: LPSm or LPSp
   - Create four experimental groups:
     - Placebo_LPSm
     - Placebo_LPSp
     - Fostamatinib_LPSm
     - Fostamatinib_LPSp

3. Generate pseudobulk samples
   - Aggregate RNA counts by **Subject × LPS condition** within each cell type.
   - Require at least **20 cells** to create a pseudobulk sample.

4. Quality control
   - Require at least **2 biological samples** in each experimental group before testing.
   - Skip cell types that do not satisfy the minimum sample requirements.

5. Differential expression analysis
   - Perform pseudobulk differential expression using **edgeR** and **limma-voom**.
   - Model subjects as biological replicates with repeated measurements across LPS conditions.

6. Identify significant genes
   - False discovery rate (FDR) < **0.05**
   - Absolute log2 fold change ≥ **0.5**

7. Pathway enrichment
   - Perform Reactome over-representation analysis (ORA) using significant DEGs.
   - Report the top enriched Reactome pathways for each contrast and cell type.

8. Export results
   - Differential expression tables
   - Significant DEG tables
   - Reactome enrichment tables
   - Reactome pathway plots
   - Summary figures and quality-control outputs
