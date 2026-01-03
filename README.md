# Breast Cancer Gene Expression Analysis

## Project Overview
Differential gene expression analysis comparing tumor and normal breast tissue samples using publicly available microarray data from GEO (GSE70947).

## Dataset
- **Source**: [GEO GSE70947](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE70947)
- **Study**: Age and estrogen-dependent inflammation in breast adenocarcinoma
- **Samples**: 296 total (148 tumor + 148 adjacent normal tissue)
- **Platform**: Microarray gene expression profiling
- **Genes analyzed**: 9356 (after quality control)

## Methods

### Data Processing
1. Downloaded series matrix file from GEO
2. Quality control: removed genes with >50% missing values
3. Imputation: filled remaining missing values with gene-wise median
4. Normalization: standardized for PCA analysis, Z-score for heatmap

### Statistical Analysis
- **Differential Expression**: Independent t-test for each gene (Tumor vs Normal)
- **Multiple Testing**: Raw p-values reported
- **Effect Size**: Log2 Fold Change calculated
- **Dimensionality Reduction**: PCA to visualize sample separation

### Visualization
- **PCA Plot**: Shows clustering of tumor vs normal samples
- **Volcano Plot**: Displays statistical significance vs fold change
- **Heatmap**: Top 50 differentially expressed genes

## Key Results

- **Total genes tested**: 9356
- **Significant genes** (p < 0.05): 5943
- **Most significant gene**: Gene ID 54725 (p = 4.87e-47, Log2FC = 0.288)

### PCA Analysis
- PC1 explains 14.2% of variance
- PC2 explains 7.6% of variance
- Clear separation between tumor and normal samples observed

## Repository Structure
```
bioinformatics-gene-expression/
│
├── README.md
├── data/
│   ├── GSE70947_series_matrix.txt/
│   └── differential_expression_results.csv
│
├── notebooks/
│   └── gene_expression_analysis.ipynb
│
├── figures/
│   ├── pca.png
│   ├── volcano_plot.png
│   └── heatmap.png
│
└── requirements.txt
```

## Tools & Technologies
- **Python 3.x**
- **pandas** - Data manipulation
- **numpy** - Numerical operations
- **scipy** - Statistical tests
- **scikit-learn** - PCA and preprocessing
- **matplotlib** - Plotting
- **seaborn** - Statistical visualizations

## Installation & Usage

1. Clone the repository:
```bash
git clone https://github.com/yourusername/bioinformatics-gene-expression.git
cd bioinformatics-gene-expression
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Run the analysis:
```bash
jupyter notebook notebooks/gene_expression_analysis.ipynb
```

## Biological Interpretation

The analysis identified genes with significantly different expression between tumor and normal breast tissue. These findings are consistent with known cancer biology:

- Upregulated genes in tumors may include oncogenes or proliferation markers
- Downregulated genes may include tumor suppressors
- Results provide candidates for further validation and functional studies

## Limitations

- Microarray technology has lower sensitivity than RNA-seq
- No multiple testing correction applied (would be needed for publication)
- Limited to transcriptional changes (no protein-level validation)
- Cross-sectional data (no temporal information)

## Future Improvements

- [ ] Apply multiple testing correction (FDR/Bonferroni)
- [ ] Perform gene set enrichment analysis (GSEA)
- [ ] Integrate with pathway databases (KEGG, GO)
- [ ] Validate findings with independent dataset
- [ ] Add survival analysis if clinical data available

## Author
Karolina Stocka - Biotechnology & Biomedical Engineering graduate
Specialization: Medical Informatics

## License
This project is for educational and portfolio purposes.

## Acknowledgments
Data from: Quigley et al., GEO accession GSE70947

