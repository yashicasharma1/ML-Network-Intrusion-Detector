# ML Network Intrusion Detector

**IBM SkillsBuild Cyber Security BootCamp 2026 | BharatCares**
**Author:** Yashica Sharma

## Project Description

This project is a machine learning based Network Intrusion Detection System (IDS). It looks at records of network connections (things like how many bytes were sent, which service was used, how many errors happened) and decides whether each connection is **normal** traffic or an **attack**. The model is trained with scikit-learn on the public NSL-KDD dataset, and two models are compared: a Decision Tree and a Random Forest.

## Dataset

- **Name:** NSL-KDD
- **Official source:** https://www.unb.ca/cic/datasets/nsl.html
- **Kaggle:** https://www.kaggle.com/datasets/hassan06/nslkdd
- **Files used:** `KDDTrain+.txt` (125,973 rows) and `KDDTest+.txt` (22,544 rows)

You don't need to download anything by hand. If the two files aren't next to the notebook, it loads them automatically from this public GitHub mirror: https://github.com/defcom17/NSL_KDD

## Technologies Used

- Python 3
- Jupyter Notebook / Google Colab
- pandas and NumPy (loading and handling the data)
- scikit-learn (encoding, scaling, Decision Tree, Random Forest, evaluation metrics)
- matplotlib (charts and confusion matrices)

## Project Files

| File | What it is |
|---|---|
| `YashicaSharma_NetworkIntrusionDetector.ipynb` | The full project code |
| `requirements.txt` | Python libraries needed to run it |
| `YashicaSharma_ProjectReport.docx` | Full project report |
| `README.md` | This file |

## How to Run

**Option 1: Google Colab (easiest)**
1. Go to https://colab.research.google.com and upload `YashicaSharma_NetworkIntrusionDetector.ipynb`.
2. Click **Runtime → Run all**. The dataset downloads by itself, and everything runs in about a minute.

**Option 2: On your own computer**
```bash
pip install -r requirements.txt
jupyter notebook YashicaSharma_NetworkIntrusionDetector.ipynb
```
Then run all the cells from top to bottom.

## How It Works

1. **Load** the training and testing files and give them proper column names.
2. **Explore** the data (protocol types, attack labels, normal vs attack balance).
3. **Prepare** the data: every attack type is turned into one "attack" label, the text columns (`protocol_type`, `service`, `flag`) are one-hot encoded, and all numbers are scaled.
4. **Train** a Decision Tree and a Random Forest.
5. **Evaluate** with accuracy, precision, recall, F1-score and confusion matrices, and show the top 10 most important features.
6. **Test** the model on single connections to see its prediction next to the real label.

## Key Information

- It's a binary classification problem: Normal (0) vs Attack (1).
- The test set includes some attack types that never appear in training, so it is a fair test of how the model handles new attacks.
- Recall on the Attack class is the most important number, because a missed attack is worse than a false alarm.

## Future Improvements

- Classify the attack category (DoS, Probe, R2L, U2R) instead of just yes/no
- Try other models like XGBoost or a neural network
- Handle the class imbalance for rare attack types
