# Customer & Product Clustering for the Online Retail Dataset.

# Project Overview
This project applies unsupervised learning to segment customers and cluster products using the Online Retail dataset from Kaggle, a transactional dataset containing purchases made at a UK-based online retailer.

# Project Structure
This repository contains three Jupyter notebooks:
- customer clustering.
- product clustering (considering only products with an associated customer ID).
- product clustering for products with missing customer IDs.

I split the product analysis into two parts because I wanted to incorporate customer information through a feature measuring the geographical dispersion of a product's customer base (country entropy). While retaining a variable indicating the number of unique customers who purchased a specific product would have been ideal, it was highly correlated with other relevant variables, so I decided to remove it.

# Pipeline & Methodology
The pipeline is similar across all three cases:
- creating the dataset with features relevant to the variable of interest.
- removing redundant variables based on the Spearman correlation matrix.
- robust standardization followed by visualization via PCA plots.
- removing outliers using MCD and transforming variables to better satisfy GMM assumptions.
- clustering using GMM, selecting the number of clusters based on BIC.
- examining the resulting clusters.
- analyzing the previously removed outliers.
I obtained 8 clusters for both product clustering scenarios: in the case with missing values, the BIC reached its minimum at 8; in the case with customer IDs present, the BIC showed only marginal improvements after 8, making a direct comparison between the two approaches easier.
For customer clustering, I chose 9 clusters because the BIC curve did not show significant improvement beyond that point, and a higher number of clusters resulted in excessive fragmentation without adding meaningful insight.

# What I Used
Python (Pandas, NumPy, Scikit-learn, SciPy)
Visualization (Matplotlib, Seaborn)
Dimensionality Reduction (PCA)
Clustering (Gaussian Mixture Models, BIC)

# Next Steps
As a potential next step, I would like to conduct a detailed comparison of the results from the two product clustering analyses.
