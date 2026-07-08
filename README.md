# Breast Cancer Prediction using Machine Learning

This project uses a well-known medical dataset to predict whether a breast tumor is **malignant (cancerous)** or **benign (non-cancerous)**, based on measurements taken from cell samples. Five different machine learning models were built and compared to see which one predicts best.

## What data was used?

The dataset comes built into the `scikit-learn` Python library — the **Breast Cancer Wisconsin dataset**. It contains:

- **569 patient records**
- **30 numeric features** per record (things like the size, texture, and shape of the cell nuclei)
- **1 target column** telling us if the tumor was malignant or benign

## Step 1: Cleaning and Preparing the Data

Before building any models, the data was checked and prepared:

- **Checked for missing values** → there were none, so no data had to be fixed or filled in.
- **Checked for duplicate rows** → there were none either.
- **Checked for outliers** using a boxplot, which showed a few extreme high values in some measurements — this is expected in medical data, since a small number of tumors can be much larger or more irregular than average.
- **Scaled the features** using `StandardScaler`. This puts all 30 measurements on the same scale (instead of some being in the thousands and others being tiny decimals), which helps several of the models perform correctly and fairly.
- **Split the data** into a training set (80%) and a testing set (20%). The model learns from the training set and gets scored on the testing set, which it has never seen before — this is how we check if it *really* learned the pattern, rather than just memorizing.

## Step 2: The Five Models

Five different classification models were trained and tested:

| Model | Simple Explanation |
|---|---|
| **Logistic Regression** | Draws a straight line (a boundary) to separate malignant from benign cases based on the patterns in the data. |
| **Decision Tree** | Asks a series of yes/no questions about the measurements (like a flowchart) to arrive at a prediction. |
| **Random Forest** | Builds many different decision trees and lets them "vote" together, which usually gives a more reliable answer than just one tree. |
| **Support Vector Machine (SVM)** | Finds the best possible dividing line (or curve) between the two groups, trying to keep as much distance as possible between them. |
| **k-Nearest Neighbors (k-NN)** | Looks at the closest matching patients in the training data and predicts based on what most of them turned out to be. |

## Step 3: Results

Each model was scored on how many test cases it predicted correctly (**accuracy**):

| Model | Accuracy |
|---|---|
| **Logistic Regression** | **97.4%** |
| **SVM (Support Vector Machine)** | **97.4%** |
| Random Forest | 96.5% |
| Decision Tree | 94.7% |
| k-Nearest Neighbors | 94.7% |

A bar chart was also plotted to visually compare the accuracy of all five models.

## What does this mean?

- **Best models:** Logistic Regression and SVM tied for the top spot, both correctly predicting about **97 out of 100** cases. This dataset's measurements separate the two tumor types quite cleanly, which is exactly the kind of pattern these two models are good at picking up.
- **Weakest models:** Decision Tree and k-NN came in a bit lower, at around **95 out of 100** correct. A single Decision Tree can be a bit "rigid" and overly sensitive to the exact training data it saw, and k-NN's predictions depend a lot on which nearby cases happen to be in the training set.
- **Random Forest** landed in the middle — better than a single Decision Tree because it combines many trees together, but still slightly behind Logistic Regression and SVM.

## Overall Takeaway

For this dataset, the simpler, more "clean-cut" models (Logistic Regression and SVM) actually performed the best. This tells us the two tumor types are quite well separated based on their measurements, so a straightforward boundary between them works very well — a more complex model isn't always needed to get great results.

## Files in this project

- `Assignment7.ipynb` — the Jupyter Notebook containing all the code, steps, and results
- `README.md` — this report
