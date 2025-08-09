# Phishing Website Detection (Web Scraping + Machine Learning)

Predict whether a URL is **phishing** or **legitimate** using features engineered from the URL string and scraped HTML structure.

## Why
Phishing is a leading cause of credential theft. I see it as a perfect way to gain real-world experience with a Project that has inherent value to assist in security across the internet.
This project shows an **end-to-end DS pipeline**: 
Consisting of data sourcing → scraping → feature engineering → modeling → evaluation.

## Data Sources
- Phishing URLs: e.g., PhishTank / OpenPhish exports
- Legitimate domains: Tranco Top 1M (or similar)

## Method (high level plan)
1) Load lists of phishing and legitimate URLs  
2) Extract **URL features** (lengths, subdomains, entropy, https, suspicious chars)  
3) (Optional) Scrape HTML & extract **page features** (forms, iframes, external link ratio)  
4) Train models (Logistic Regression, Random Forest, XGBoost) with **stratified CV**  
5) Evaluate via **ROC-AUC**, **PR-AUC**, **Precision/Recall @ threshold**

## Tech Stack
Python, pandas, scikit-learn, XGBoost, BeautifulSoup, requests, matplotlib

## Reproducibility
- Notebooks in `/notebooks`
- Scripts in `/src`
- Data directories git-ignored; see notebook 01 for download instructions


## Results: TBD
- ROC-AUC:  
- PR-AUC:  
- Precision@0.95 Recall:  

## How to run
```bash
python -m venv .venv && source .venv/bin/activate   # (Windows: .venv\Scripts\activate)
pip install -r requirements.txt
jupyter lab
