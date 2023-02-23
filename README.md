# Spatially Annotated Single-Cell Sequencing
We previously described spatially annotated single-cell sequencing, a method to spatially profile intratumor heterogeneity with deep scRNA-seq and single-cell resolution. Here, we have deposited all scripts required for analyzing the scRNA-seq data obtained using spatially annotated single-cell sequencing. 

More detailed information about the execution of the protocol and analysis of the results can be found in:

Smit, M.M. & Chien, M.-P. (2023). Protocol for profiling intratumor heterogeneity using spatially annotated single  cell sequencing. STAR Protocols (under review)

For complete details on the application of this protocol, please refer to: 

Smit, M. M., Feller, K. J., You, L., Storteboom, J., Begce, Y., Beerens, C., & Chien, M.-P. (2022). Spatially Annotated Single Cell Sequencing for Unraveling Intratumor Heterogeneity. Frontiers in Bioengineering and Biotechnology, 0, 62. https://doi.org/10.3389/FBIOE.2022.829509

The raw data and sample names files used in these scripts can be found at NCBI’s GEO DataSets site with accession number GSE196245.

## Workflow
### 1. Loading data
TSV files containing Poission-corrected transcript counts are loaded in a Seurat object using the SpatialFUNseq_SeuratObject__vGit.Rmd script. Sample names are loaded from Excel files and added to the Seurat object to allow data filtering & pre-processing. 

### 2. Pre-processing, dimensionality reduction & differential expression testing
Data pre-processing and standard scRNA-seq analysis is performed using the SpatialFUNseq_Analysis__vGit.Rmd script. Pre-processing involves several quality control checks to remove low-quality data, cell-cycle correction and an optional batch correction step. UMAP dimensionality reduction is then performed to visualize the scRNA-seq data, after which we identify differentially expressed genes using Seurat's findMarkers function. 

### 3. Pathway analysis
Using the identified differentially expressed genes, we then perform overrepresentation analysis and gene set enrichment analysis in the SpatialFUNseq_PathwayAnalaysis__vGit.Rmd script. These analyses can be performed using the Wikipathways, MSigDB, and Gene Ontology databases. 

### 4. Cell-cell interaction analysis
Enriched ligand-receptor interaction between the different cell populations are predicted using CellphoneDB (Efremova et al. Nat. Prot. 2022), more information on the execution of this analysis can be found at https://www.cellphonedb.org/. In principle, this entire analysis can be run using the package distributed by the authors. However, we visualized our results using a modified version of the author's dotplot function in the SpatialFUNseq_InteractionAnalysis__vGit.Rmd script. 
