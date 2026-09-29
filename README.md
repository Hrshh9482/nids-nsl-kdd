# nids-nsl-kdd
# Network Intrusion Detection with Machine Learning

A machine learning model that looks at a network connection and decides if it is **normal** or an **attack**.

## Dataset
- NSL-KDD, file `KDDTrain+.txt`
- 125,973 connections, 41 features each
- Source: University of New Brunswick, http://nsl.cs.unb.ca/NSL-KDD/ (also on Kaggle)
- The dataset is not in this repository. Download it and upload it to Google Colab to run the notebook.

## What I did
1. Loaded the data and added the column names
2. Explored the data with pandas and matplotlib
3. Made a binary target: normal = 0, attack = 1
4. Removed `label` and `difficulty` from the features to avoid data leakage
5. One-hot encoded `protocol_type`, `service` and `flag` (41 features became 122 columns)
6. Split the data: 80% train, 20% test (stratified)
7. Trained a Random Forest with 100 trees
8. Evaluated with accuracy, confusion matrix, precision and recall

## Results
Tested on a 20% hold-out from the same file (25,195 rows):

| Metric | Value |
|--------|-------|
| Accuracy | 99.90% |
| Attack precision | 99.94% |
| Attack recall | 99.84% |
| False alarms | 7 |
| Missed attacks | 19 |

## Limitation
Train and test rows come from the same file, so the score is very high.
The official `KDDTest+.txt` file has new attack types, so the score there is expected to be lower. Testing on it is a next step.

## Tools
Python, pandas, numpy, matplotlib, scikit-learn, Google Colab
