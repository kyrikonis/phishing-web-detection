# Malicious URL Detection & Classification System

Utilised ML for detecting and classifying malicious URLs into four categories: benign, phishing, malware, and defacement attacks.

## 📊 Dataset Overview

The dataset contains **641,119 URLs** distributed across four categories:
- **Benign**: 428,080 URLs (66.8%)
- **Phishing**: 94,086 URLs (14.7%)
- **Defacement**: 95,308 URLs (14.9%)
- **Malware**: 23,645 URLs (3.7%)

## 🎯 Key Findings

### Statistical Analysis
- **Malicious URLs are longer on average**: 63.96 characters vs 57.68 for benign
- **Statistical significance**: T-test p-value < 0.001, Cohen's d = 0.140
- **95th percentile**: Malicious URLs reach 147 characters vs 125 for benign

### URL Characteristics by Type
- **Phishing URLs**: Often contain social engineering keywords like "secure", "account", "verify"
- **Malware URLs**: Frequently use obfuscation techniques and suspicious file extensions
- **Defacement URLs**: Show higher path depth (1.83 avg) and subdomain counts (0.87 avg)

## 🛠️ Feature Engineering

The system extracts over **40 comprehensive features** across 8 categories:
Some more may have been missed or added.

### URL Structure (6 features)
- URL length, path depth, subdomain count
- Query length, fragment length, parameter count

### Character Analysis (8 features)
- Special character count, digit count, entropy
- Character ratios and repetition patterns

### Word Analysis (3 features)
- Word count, average word length, longest word

### Security Indicators (6 features)
- IP address detection, suspicious TLDs
- URL shortener identification, brand impersonation

### Obfuscation Detection (4 features)
- Hex encoding, percent encoding
- Consecutive special characters

### Network Features (4 features)
- Domain entropy, HTTPS usage, port analysis

### Pattern Recognition (3 features)
- Date patterns, version patterns, redirect indicators

## Model Performance

Two machine learning models were trained and evaluated:

| Model | Test Accuracy | F1-Macro | F1-Weighted | ROC-AUC |
|-------|---------------|----------|-------------|---------|
| **XGBoost** | **96.34%** | **94.42%** | **96.27%** | **99.39%** |
| Random Forest | 94.03% | 92.13% | 94.16% | 99.05% |

### Per-Class Performance (XGBoost)
| Class | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| Benign | 97% | 99% | 98% | 85,616 |
| Phishing | 91% | 84% | 88% | 18,817 |
| Malware | 98% | 90% | 94% | 4,729 |
| Defacement | 97% | 99% | 98% | 19,062 |

## 🔍 Feature Importance

Top 5 most important features for classification:
1. **has_ip** (0.295) - Presence of IP address in URL
2. **path_depth** (0.138) - URL path complexity
3. **port_number** (0.066) - Non-standard ports
4. **is_https** (0.061) - HTTPS protocol usage
5. **subdomain_length** (0.044) - Subdomain characteristics

## 📈 Key Insights

### Domain Analysis
- **.com** domains dominate across all categories (52.5% phishing, 72.2% benign)
- **Suspicious TLDs** like .tk, .ml more prevalent in malicious URLs
- **Top malicious domains** include known bad actors and compromised sites

### Protocol Usage
- **HTTP vs HTTPS**: Benign URLs favor HTTPS, malicious often use HTTP
- **Suspicious patterns**: Date/version patterns indicate time-sensitive attacks

### Content Patterns
- **Phishing**: Heavy use of legitimate brand names and urgent language
- **Malware**: Technical obfuscation and file extension manipulation
- **Defacement**: Complex directory structures and CMS exploitation patterns

## 🚀 Usage

The trained XGBoost model can classify URLs with 96.34% accuracy and is particularly effective at:
- Detecting IP-based URLs (strongest predictor)
- Identifying suspicious domain structures
- Recognizing obfuscation techniques
- Flagging social engineering attempts

## 📁 Project Structure

```
├── notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_feature_screening.ipynb
│   └── 03_model_training.ipynb
├── data/
├── models/
│   ├── xgboost_model.pkl
│   └── random_forest_model.pkl
└── README.md
```

## 🔒 Security Applications

This system can be integrated into:
- Web browsers for real-time URL screening
- Email security systems for link validation
- Network security appliances
- Threat intelligence platforms
- Security awareness training systems

## 📊 Cross-Validation Results

- **XGBoost CV F1-Weighted**: 95.43% ± 0.17%
- **Random Forest CV F1-Weighted**: 93.43% ± 0.20%
- Consistent performance across different data splits

The XGBoost model performed better overall and will be the choice going forward upon project updates.