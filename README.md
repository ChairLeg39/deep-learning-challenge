# deep-learning-challenge
KU Boot Camp Module 21 Challenge

## Overview

This project aims to develop a binary classifier using machine learning and neural networks to predict the success of applicants funded by Alphabet Soup, a nonprofit foundation. The goal is to create a tool that helps Alphabet Soup select applicants with the highest chance of success in their ventures.

The analysis is based on a dataset containing information about more than 34,000 organizations that have received funding from Alphabet Soup. The dataset includes various features about each organization, such as application type, industry affiliation, classification, use case for funding, and more.

## Requirements

1. Data Preprocessing
2. Model Compilation, Training, and Evaluation
3. Model Optimization
4. Analysis Report

## Methodology

### 1. Data Preprocessing

- Load the charity_data.csv into a Pandas DataFrame
- Identify target and feature variables
- Remove non-beneficial ID columns (EIN and NAME)
- Analyze unique values in each column
- Handle rare categorical variables
- Create feature array (X) and target array (y)
- Split data into training and testing sets
- Scale the data using StandardScaler

### 2. Model Compilation, Training, and Evaluation

- Design a neural network model with appropriate input features and layer nodes
- Create hidden layers and output layer with suitable activation functions
- Compile and train the model
- Evaluate model performance using test data
- Export results to AlphabetSoupCharity.h5 file

### 3. Model Optimization

- Perform preprocessing steps in a new Jupyter notebook
- Create an optimized neural network model
- Implement at least 3 optimization methods
- Save and export results to AlphabetSoupCharity_Optimization.keras file (model exported to the native Keras format, since the HDF5 file format is considered to be legacy)

### 4. Analysis Report

- Prepare a comprehensive report including:
  - Purpose of the analysis
  - Results discussion (addressing specific questions)
  - Overall model performance summary
  - Comparison with alternative models

## Findings

(To be added after analysis completion)
