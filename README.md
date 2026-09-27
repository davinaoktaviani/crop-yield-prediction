# Crop Yield Prediction

A deep learning regression project that predicts **crop yield** using agricultural, environmental, and crop-related features.

The project compares a baseline neural network with a modified neural network designed to improve training stability and reduce overfitting.

## Overview

The dataset contains **500 records and 22 columns**. The target variable is `yield`.

Features include:

- Region and crop type
- Soil moisture and soil pH
- Temperature
- Rainfall
- Humidity
- Sunlight hours
- Irrigation type
- Fertilizer type
- Pesticide usage
- Total growing days
- NDVI index
- Crop disease status

Metadata such as farm ID, sensor ID, timestamp, sowing date, harvest date, latitude, and longitude are removed before modeling.

## Workflow

1. Load the dataset from `1A.parquet`
2. Perform basic exploratory data analysis
3. Handle missing values
4. Separate features and target
5. Split the data into training, validation, and test sets
6. Standardize numerical features
7. One-hot encode categorical features
8. Scale the target variable
9. Train a baseline neural network
10. Modify the architecture to reduce overfitting
11. Evaluate both models on the test set

The data is split into:

- 70% training
- 10% validation
- 20% testing

## Models

### Baseline Neural Network

The baseline model uses:

- Dense layers
- ReLU activation
- Linear output layer
- Adam optimizer
- MSE loss

The training results showed a large gap between training and validation performance, indicating overfitting.

### Modified Neural Network

The modified model introduces:

- Additional Dense layers
- Batch Normalization
- Dropout
- Early Stopping
- Adam optimizer

These changes were intended to make training more stable and improve generalization.

## Evaluation

The models are evaluated using:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R² Score

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Baseline | 10,762.997 | 12,613.820 | -0.152 |
| Modified | **10,513.330** | **11,702.725** | **0.008** |

The modified model produced lower MAE and RMSE and improved the R² score compared with the baseline model.
