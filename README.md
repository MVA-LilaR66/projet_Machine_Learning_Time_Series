# ROCKET for Time Series Classification and Forecasting
> Project - MVA 2024/2025  
> **The ROCKET Algorithm: From Classification to Prediction**  
> Authors: **Lila Roig** (bibliographic research, method development, implemented the code),  **Eva Robillard** (run code, wrote report)
> *Date: January 2025*

## Project Overview

This project explores the **ROCKET** algorithm, originally designed for fast and accurate **time series classification**, and extends its application to two new contexts:
- **Multivariate time series**
- **Time series forecasting (prediction)**

> In this project, we extended the original ROCKET algorithm beyond its initial scope of univariate time series classification. First, we adapted ROCKET to handle multivariate time series, proposing a memory-efficient approach by sharing convolutional kernels across dimensions. Second, we repurposed ROCKET for time series forecasting, replacing the classifier with a regression model and introducing a robust sliding window mechanism to generate training sequences. These adaptations allow ROCKET to address more complex and practical time series tasks while preserving its computational efficiency.

Our implementation is mostly from scratch, except for:
- The original ROCKET implementation from [Dempster et al., 2020](https://doi.org/10.1007/s10618-020-00701-z)
- Dataset loading functions from the Monash Time Series Forecasting Archive


## What is ROCKET?

ROCKET (RandOm Convolutional KErnel Transform) is a method for time series classification that:
- Uses **random convolutional kernels**
- Extracts features using **maximum value** and **proportion of positive values (PPV)**
- Trains a **ridge regression** model for classification

This project adapts ROCKET for:
- **Multivariate input** by sharing kernels across variables
- **Forecasting**, by replacing the classifier with a **regression model** using sliding windows

## Datasets
- Classification: OliveOil Dataset
- 60 univariate time series (570 time steps)
- Task: Classify the origin of olive oils
- Achieved accuracy: 88.9%

## Forecasting: Monash Archive
- 58 datasets with different frequencies (hourly, daily, monthly, etc.)
- Forecast horizons and window sizes determined dynamically
- Evaluation metrics used:
  - MASE
  - MSE / RMSE
  - sMAPE

## Models Used
  - Ridge Regression (best performance overall)
  - Random Forest
  - XGBoost

## Results Summary
- **Classification:** ROCKET performs well, confirming results from original paper
- **Forecasting:**
  - Weekly datasets show promising results (MASE < 1)
  - Struggles with high-frequency data (hourly, daily)
  - Ridge regression performs best in terms of accuracy, though with more variance

See detailed visualizations in the notebooks/ folder and the Excel summary in results/.
