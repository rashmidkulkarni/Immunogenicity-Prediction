
# 🧬 Immunogenicity-Prediction
This project explores machine learning models for predicting human immunogenicity to therapeutic biologics (e.g., Humira, Erenumab, Herceptin) by leveraging HLA allele information and both ex-vivo and in-silico datasets.
#  Overview
Predicting immunogenicity is a critical challenge in biologics and vaccine development. Individual variability in HLA class II alleles influences whether the immune system recognizes therapeutic proteins as foreign, leading to T-cell proliferation and adverse responses.
This project combines:
Ex-vivo proliferation assay data from human donors
In-silico binding predictions (NetMHCIIpan, IEDB, Tepitope) filtered by strong binders (Percentile Rank < 1%)
to train machine learning classifiers that can predict whether a given allele–drug combination is likely to induce a positive immune response.
# Data Sources
Ex-vivo data:
Proliferation assays for donors with known HLA profiles and SI (stimulation index) values across drugs.
In-silico data:
HLA–peptide binding predictions (percentile ranks, IC50 values). Strong binders were used as synthetic positive examples to enrich the dataset.
# Methods
Feature Engineering
One-hot encoding of HLA class II alleles (e.g., DRB1*03, DRB1*15)
Drug indicator variables (Drug_Humira, Drug_Erenumab, Drug_Herceptin)
Zygosity encoding
Synthetic rows from in-silico predictions integrated with ex-vivo donor data
Models Used
Random Forest (baseline)
XGBoost
LightGBM (best performing)
Evaluation Metrics
Precision, Recall, F1-score
Confusion matrix analysis
Threshold tuning to prioritize recall (catching as many true positives as possible)
# Results
Without in-silico augmentation:
Recall on positives ~0.75, accuracy ~0.86
With in-silico augmentation (<1% strong binders):
Recall on positives improved to ~0.88–0.94
Overall accuracy ~0.92
Key Insight: Integrating strong in-silico binders significantly improves the model’s ability to detect immunogenic responses.
# Tech Stack
Python (Pandas, NumPy, Scikit-learn)
LightGBM, XGBoost, RandomForest
Matplotlib/Seaborn for visualization
Excel/CSV datasets from ex-vivo assays and NetMHCIIpan/IEDB predictions

# ✨ This project demonstrates how combining wet-lab data with computational predictions can accelerate understanding of immunogenicity in biologics.
