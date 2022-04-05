# Research

<img src="https://github.com/viktormiok/viktormiok.me/blob/main/research/present.png" align="right" height="420" width="365">

Data stemming from complex cellular phenomena that have been characterized in many dimensions in order to understand interrelationships of the involved biomolecules and their functions, require developing novel methodology.

Together with many collaboration partners, my primary interest is in developing a statistical machine learning methodology and understanding the data in order to gain more profound insights into complex biological processes holistically, taking an integrative approach that combines multi-omics data where many cellular traits are interrogated simultaneously using the latest omics techniques. Developing the methodology that covers a wide spectrum of univariate and multivariate statistics, focusing both on steady-state and time-series data, while relying on Bayesian, frequentist, or a hybrid approach, depending on the nature of the problem at hand. 

Employing a developed methodology, borrowing knowledge from other fields, and combining it with available state-of-the-art tools allow me to analyze the data together with biomedical scientists addressing the problems in cancer or metabolism research. Lately, my research focuses more on the development and benchmarking of computational methods for integrative analysis of single-cell RNA sequencing data, while having generally interest in data visualization in order to strengthen new therapeutic concepts and identify biomarkers in the area of cardiometabolic diseases.

## Integrative Statistical Machine Learning

### Univariate Time-Series Statistics

<img src="https://github.com/viktormiok/viktormiok.me/blob/main/research/tigar.png" align="right" height="385" width="385">

  This theme focuses on developing a methodology for longitudinal (zero-inflated) counts and Gaussian multi-omics data in order to address the questions of:
 - [temporal integrative differential expression analysis.](https://bmcbioinformatics.biomedcentral.com/articles/10.1186/1471-2105-15-327) 
 - [reliable identification of miRNA targets to the mRNA levels.](https://www.mdpi.com/2072-6694/12/3/700/htm) 
 - [identifying cycling genes, while measuring crucial attributes of their rhythms including period, phase, and amplitude.](https://github.com/viktormiok/tigaRcycle) 
 
To do so, the following methodological issues arise: 
 - reproducibility problem due to the small number of samples. 
 - zero-inflation of counts data.
 - multi-parameter shrinkage due to the high-dimensional data.
 - accommodation of a variety of priors, including mixture, nonparametric and multivariate ones.
  
Hence, the proposed methodology describes temporal variation in gene expression by a generalized linear mixed model employing low-rank thin-plate splines, where the optimal numbers of knots for splines are determined using the deviance information criterion. Model parameters are estimated with an empirical Bayes procedure that exploits [integrated nested Laplace approximation](https://www.r-inla.org/) for fast computation. Iteratively, until converge posteriors of hyper-parameters and model parameters are re-estimated. The empirical Bayes procedure shrinks multiple dispersion-related parameters. Shrinkage leads to more stable estimates of the model parameters, better control of false positives, and improvement of reproducibility. In addition, to make estimates of the covariates (i.e. DNA copy number)  more stable, model parameters are also estimated in a multivariate way using triplets of features, imposing a spatial prior for the copy number effect. 

The proposed method  implemented in the [tigaR](https://bmcbioinformatics.biomedcentral.com/articles/10.1186/1471-2105-15-327) R-package available from [GitHub](https://github.com/viktormiok/tigaR), is compared to three well-known alternatives for significance analysis of time-course microarray data: [EDGE](https://www.pnas.org/doi/full/10.1073/pnas.0504609102), [timecourse](https://projecteuclid.org/journals/annals-of-statistics/volume-34/issue-5/A-multivariate-empirical-Bayes-statistic-for-replicated-microarray-time-course/10.1214/009053606000000759.full), [BATS](https://www.degruyter.com/document/doi/10.2202/1544-6115.1299/html) and outperforms them in terms of sensitivity, specificity, and reproducibility on two datasets.

### Network Multivariate Modelling of High-Dimensional Data

<img src="https://github.com/viktormiok/viktormiok.me/blob/main/research/VARX1.png" align="right" height="400" width="420">

In modern science Networks are ubiquitous. In many fields, network extraction has become a popular method for exploring a complex network of relations between entities of interest. Entities of interest to us are molecular features derived from omics studies. A challenge with omics-data is that they are often high-dimensional.

We approach network extraction for high-dimensional data through penalized graphical modeling. Conditional (in)dependence relations between random variables are expressed utilizing graphical models. In contrast to popular L1 approaches, we use L2 penalization to ensure that these models are estimable from high-dimensional data.

#### Time-Series Data

Dynamics of the gene expression levels within may be described by time-series chain graph suggests how molecular medicine could target the pathway. Time-series chain graph of (cross-)temporal and contemporaneous relations is obtained using the ridge penalized full maximum likelihood estimator of the vector autoregressive process. The methodology allows for:
 - incorporation of prior knowledge on the support of both temporal and contemporaneous interactions
 - memory efficient evaluation of the estimator is outlined
 - cross-validation is described to guide the choice of the penalty parameters.
 - several strategies (e.g. selection of interaction, mutual information, and path analysis) for down-stream exploitation

Method is comparison to [SCAD](https://academic.oup.com/biostatistics/article/14/3/586/260299), L1 based counterpart, in simulation study and indicate improvements in sensitivity and specificity of their edge selection. Methodology is further extended and implemented in [ragt2ridges](https://github.com/viktormiok/ragt2ridges) R-package to:
 - identify differences in the dynamics of particular molecular pathways between distinct groups/classes
 - assess the presence of dynamic dependencies over a longer time range
 - reconstruct temporal interaction form multiple molecular level

<img src="https://github.com/viktormiok/viktormiok.me/blob/main/research/coni.png" align="right" height="400" width="600">

#### Steady-State Data

As such network extraction is computationally intensive, it tends to concentrate on genes that act in concert. Employing partial correlations to build complex hypergraph-like networks allow us to:
 - extend to the all measured genes from the experiments
 - perform unsupervised integration of different omics steaady-state data
 - identify putative confounding variables(e.g. genes) for a set of paired dependent variables (e.g. metabolites)

Enabling to identify priority candidates such as locally controlling genes or comparing network structures dependent on different conditions.


## Integrative and Spatial Single-Cell Transcriptomics

### Brain Cellular Point Patterns for Spatial Single-Cell RNAseq

<img src="https://github.com/viktormiok/Csppa/blob/main/RandomForestClassifier.gif" align="right" height="400" width="300">

Understanding how the anatomical location of the cells and their spatial molecular distribution, determine the cellular response to a high caloric diet requires developing machine learning methods for analysis and visualization.
We developed both [Csppa](https://github.com/viktormiok/Csppa) R-package and [CsppaRshiny](https://github.com/viktormiok/CsppaRshiny) R-shiny app for machine learning analysis and visualisation of astrocyte spatial point patterns allow us to understand how hypercaloric diet triggers transient molecular rearrangements of astrocytes selectively in the arcuate nucleus.

Initially, we perform 2D and 3D for visualisations, allowing flexibility in order to represent the data and emphasize the question of interest. Allowing for performing overall and local significance analysis of spatial point pattern densities, employing several statistical approaches.
Further k-nearest neighbour and random forest classification algorithms are implemented to compare the grouping of the cells expressing different markers within and between the diets. On top of the, correlation and spatial auto-correlation of the cells expressing different markets can be compared using Mentel and Moran I test, respectively.

<img src="https://github.com/viktormiok/viktormiok.me/blob/main/research/spatial_opt.gif" align="left" height="250" width="250">

On the top of that, it is fundamentally challenging to study tissue organization and spatial gene expression patterns by using spatial information and single-cell transcriptomics data. Employing [novoSpaRc](https://pypi.org/project/novosparc/), a computational framework that probabilistically assigns cells to tissue locations, by incorporating spatial point pattern data analysis information as a prior knowledge, in order to improve reconstruction. At the core of this framework lies a structural correspondence hypothesis, that cells in physical proximity share similar gene expression profiles. Given scRNA-seq data, [novoSpaRc](https://pypi.org/project/novosparc/), and including information of [Csppa](https://github.com/viktormiok/Csppa) analysis we aim to spatially reconstructs cell organization and understand how hypercaloric diet triggers transient molecular rearrangements of astrocytes selectively in the arcuate nucleus.

### Characterization of Adipocytes Individual Cell Populations

<img src="https://github.com/viktormiok/viktormiok.me/blob/main/research/adypo-min.png" align="right" height="550" width="550">

The underlying cause of systemic insulin resistance and metabolic syndrome is pathological changes in adipose tissue. Due to an inability to identify and target dysfunctional adipocytes, the mechanisms underlying this functional impairment remain unclear. Our previous studies combined with ongoing projects in the laboratory suggest that both white and brown adipose tissues are functionally and developmentally diverse, and that differences between cell populations within these different depots can be detected at the cell surface.

Hence, the primary objective of this theme is to identify the individual cell populations and signaling pathways responsible for the initiation of local and subsequent systemic insulin resistance. [Single-cell transcriptomics pipeline](https://github.com/viktormiok/scRNAseq_AdipocyteSubtyping) is used to characterize individual cell populations in adolescent two and adult eight weeks mice, examining brown, perigonadal, and subcutaneous adipose depots.

Following publications and preparing articles address different aspects of this cell populations in our scRNA-seq data set, while on the [GitHub](https://github.com/viktormiok/scRNAseq_AdipocyteSubtyping) page, you can find the code and details about the analysis.
 - [Asc-1 regulates white versus beige adipocyte fate in a subcutaneous stromal cell population](https://doi.org/10.1038/s41467-021-21826-9)
 - [Identification and characterization of distinct brown adipocyte subtypes in C57BL/6J mice](https://www.life-science-alliance.org/content/4/1/e202000924)
 - [Characterization of individual imune cell population in white preadipocity and subcuteneous stromal cell populations](https://github.com/viktormiok/scRNAseq_AdipocyteSubtyping)
 - [Igf2 promoting factor of healthy expansion of white adipose tissue](https://github.com/viktormiok/scRNAseq_AdipocyteSubtyping)

Hence, our research aims at elucidating mechanisms that enable healthy adipose tissue expansion upon weight gain in order to prevent the development of insulin resistance and the metabolic syndrome.
