# Berlin Marathon Pacing Strategies: A Comparative Analysis of PCA and MDS

**Statistical Data Analysis – Academic Project**

**Authors:** Weronika Zacłona and Mikołaj Szmid

## Project Overview

This project investigates pacing strategies among participants in the Berlin Marathon between 1999 and 2019 using multivariate statistical methods.

The main objective is to explore how runners distribute their effort throughout a marathon and to compare two dimensionality reduction approaches: **Principal Component Analysis (PCA)** and **Multidimensional Scaling (MDS)**.

Rather than focusing exclusively on finishing times, the analysis examines relative pacing patterns across consecutive race segments. This allows runners with different performance levels to be compared based on their pacing strategies.

## Research Objectives

The project addresses the following questions:

1. What are the main dimensions underlying differences in marathon pacing strategies?
2. How effectively can high-dimensional pacing profiles be represented in two dimensions?
3. To what extent do PCA and MDS produce similar configurations of runners?
4. How do classical and non-metric MDS differ in their ability to preserve relationships between observations?
5. What are the main advantages, limitations, and practical differences between PCA and MDS?

## Dataset

The analysis uses publicly available Berlin Marathon results from **1999–2019**, originally obtained from the [marathon-results repository](https://github.com/AndrewMillerOnline/marathon-results).

The dataset includes finishing times, intermediate split times, gender, nationality, and race year.

- **Original dataset:** 678,711 observations
- **Final cleaned dataset:** 632,183 observations
- **Study period:** 1999–2019
- **Race distance:** 42.195 km

Records with missing, invalid, or non-chronological split times were excluded from analyses requiring complete pacing profiles.

Pacing variables were calculated from split times and expressed relative to each runner's individual average pace over the first 40 kilometres.

## Methodology

### 1. Data Preparation and Exploratory Data Analysis

The initial stage includes:

- Integration and validation of annual marathon datasets.
- Assessment of missing values and potentially invalid observations.
- Calculation of pace and pacing variability indicators.
- Identification of positive and negative splits.
- Examination of pacing patterns by gender, finishing time, nationality, and race year.
- Investigation of variable distributions, correlations, and outliers.

### 2. Principal Component Analysis (PCA)

PCA is applied to standardised relative pacing variables to identify the main dimensions of pacing variability.

The analysis includes:

- Correlation matrix examination.
- Kaiser–Meyer–Olkin (KMO) measure and Bartlett's test of sphericity.
- Eigenvalue analysis, Kaiser's criterion, and scree plot.
- Explained variance and component loadings.
- Interpretation of principal component scores.
- Assessment of variable representation quality using squared loadings (cos²).
- Sensitivity analysis excluding the 1% most extreme pacing profiles.

**Main PCA findings:**

| Indicator | Result |
|---|---:|
| KMO | 0.863 |
| Variance explained by PC1 | 61.24% |
| Variance explained by PC2 | 19.48% |
| Total variance explained | 80.72% |
| Total after outlier sensitivity analysis | 81.27% |

The first component primarily captures the contrast between early and later pacing, while the second reflects additional variation in the middle stages of the race.

### 3. Multidimensional Scaling (MDS)

The MDS analysis compares two approaches:

**Classical MDS (cMDS)**

Classical MDS represents pairwise Euclidean distances between runners in a lower-dimensional space. Its relationship to PCA is examined using the same observations and standardised variables.

**Non-metric MDS (NMDS)**

Non-metric MDS focuses on preserving the rank ordering of pairwise dissimilarities rather than their exact numerical values. Multiple initialisations and goodness-of-fit diagnostics are used to evaluate solution quality.

### 4. Comparison of PCA and MDS

The methods are compared using:

- Two-dimensional configurations of the same runners.
- Explained variance and MDS goodness-of-fit diagnostics.
- Stress-1 and Shepard diagrams.
- Pearson and Spearman correlations of pairwise distances.
- Procrustes analysis.
- Stability, computational requirements, and interpretability.

The comparison distinguishes between the geometric equivalence of PCA and classical Euclidean MDS and the different optimisation objective of non-metric MDS.

## Technologies

- Python
- pandas and NumPy
- SciPy
- scikit-learn
- Matplotlib and Seaborn
- Quarto
- Jupyter

## Reproducibility

The analysis is implemented in a reproducible Quarto report combining Python code, statistical results, figures, and methodological interpretation.

To generate the HTML report, install the required Python dependencies, configure the Python environment and Quarto Jupyter kernel, and run:

```bash
quarto render raport.qmd --to html
```

The rendered report is saved in the `output/` directory.

## Limitations

The study is subject to several limitations:

- Complete split-time data are not available for every marathon edition, particularly 2003.
- PCA focuses on selected relative pacing variables from the first 40 km.
- The construction of relative pacing variables introduces dependencies between race segments.
- Computational constraints require a smaller sample for standard MDS implementations.
- The analysis is descriptive and exploratory and does not establish causal relationships.

## Authors

**Weronika Zacłona**  
**Mikołaj Szmid**

AGH University of Krakow  
Faculty of Management  
Statistical Data Analysis – Academic Project

## License and Data Attribution

The underlying marathon results originate from the publicly available *marathon-results* dataset. Source attribution and any applicable dataset usage conditions should be respected.

This repository was created for educational and academic purposes.
