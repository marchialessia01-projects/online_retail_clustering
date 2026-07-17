# Customer & Product Clustering for the Online Retail Dataset

## Project Overview
The aim of this project is to apply unsupervised learning techniques to segment both customers and products based on purchasing behaviour using the **Online Retail** dataset from Kaggle, a transactional dataset containing purchases made at a UK-based online retailer.

## Dataset
Available on [Kaggle - Online Retail](https://www.kaggle.com/datasets/ulrikthygepedersen/online-retail-dataset)

## Project Structure
This repository contains three Jupyter notebooks:
- customer clustering.
- product clustering (considering only products with an associated customer ID).
- product clustering for products with missing customer IDs.
and a file requirements.txt

### Results

## Customer Clustering
The segmentation distinguished customers with different purchasing behaviours. The most valuable clusters were characterized by **high spending, recent purchases, and a broad variety of purchased products**, while the largest cluster consisted of **occasional customers** who typically made a single purchase and generated relatively low revenue. Smaller clusters were distinguished by higher return rates than the rest of the customer base.

## Product Clustering
Both product clustering analyses identified groups differentiated by **revenue, purchase frequency, recency, geographic distribution, and return behaviour**. The segmentation revealed **top-performing**, **standard**, **low-performing**, **niche/international**, and **high-return** products.

Including customer information through the **country entropy** feature produced a slightly richer segmentation, but the overall cluster structure remained similar even without customer-related features, allowing a direct comparison between the two approaches.

## Pipeline & Methodology
I split the product analysis into two parts because I wanted to incorporate customer information through a feature measuring the geographical dispersion of a product's customer base (country entropy). While retaining a variable indicating the number of unique customers who purchased a specific product would have been ideal, it was highly correlated with other relevant variables, so I decided to remove it.

The analysis followed a similar pipeline for all three notebooks:
- creating the dataset with features relevant to the variable of interest.
- removing redundant variables based on the Spearman correlation matrix.
- robust standardization followed by visualization via PCA plots.
- removing outliers using MCD and transforming variables to better satisfy GMM assumptions.
- clustering using GMM, selecting the number of clusters based on BIC.
- examining the resulting clusters.
- analyzing the previously removed outliers.

I chose Gaussian Mixture Models over K-Means for two main reasons: GMM provides probabilistic cluster assignments, allowing for uncertainty quantification, and it can identify clusters with ellipsoidal shapes rather than being restricted to spherical ones like K-Means.

I obtained 8 clusters for both product clustering scenarios: in the case with missing values, the BIC reached its minimum at 8; in the case with customer IDs present, the BIC showed only marginal improvements after 8, making a direct comparison between the two approaches easier.
For customer clustering, I chose 9 clusters because the BIC curve did not show significant improvement beyond that point, and a higher number of clusters resulted in excessive fragmentation without adding meaningful insight.

## Technologies
- Python
- Pandas
- NumPy
- Scikit-learn
- SciPy
- Matplotlib
- Seaborn

# Next Steps
As a potential next step, I would like to conduct a detailed comparison of the results from the two product clustering analyses.
