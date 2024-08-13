# Neural Network Model Report

## Overview of the Analysis

The purpose of this analysis is to develop a deep learning model for Alphabet Soup, a nonprofit foundation, to predict the success of funding applicants. Using machine learning and neural networks, the goal is to create a binary classifier that can determine whether applicants will be successful if funded by Alphabet Soup. This tool will assist the foundation in selecting applicants with the best chance of success in their ventures, thereby optimizing the use of their resources and maximizing the impact of their funding.

The analysis is based on a dataset containing information about more than 34,000 organizations that have received funding from Alphabet Soup in the past. By leveraging various features about each organization, such as application type, industry affiliation, and use case for funding, the model seeks to effectively predict funding success.

## Results

### Data Preprocessing

#### 1. What variable(s) are the target(s) for your model?
The target variable for the model is `IS_SUCCESSFUL`. This column represents a binary outcome (1 or 0) indicating whether a particular application or organization was successful. It is the variable the model is trying to predict based on the other features.

#### 2. What variable(s) are the features for your model?
The features for the model include all the remaining columns after preprocessing, except for 'IS_SUCCESSFUL'. These are:

- `APPLICATION_TYPE`
- `AFFILIATION`
- `CLASSIFICATION`
- `USE_CASE`
- `ORGANIZATION`
- `INCOME_AMT`
- `SPECIAL_CONSIDERATIONS`
- `ASK_AMT`

Note: Since `get_dummies()` was used to convert categorical data to numeric, the actual feature set is larger, with binary columns for each category in the categorical variables.

#### 3. What variable(s) should be removed from the input data because they are neither targets nor features?
The following variables were removed:

- `EIN`: This is an Employer Identification Number, which acts as a unique identifier for each organization. It doesn't provide predictive information for the model.
- `NAME`: This is also an identifier and doesn't contain information that would generalize well for predictions.
- `STATUS`: This column was removed due to its severe class imbalance. The `value_counts()` output indicated 34,294 entries with a value of 1, and only 5 entries with a value of 0. Such a severe imbalance makes this feature less useful for prediction, as it doesn't provide much discriminative power.

### Compiling, Training, and Evaluating the Model

#### 1. How many neurons, layers, and activation functions did you select for your neural network model, and why?
Based on the three optimization attempts:

- **Optimization 1 & 2**: 
  - 3 hidden layers with 120, 80, and 30 neurons respectively
  - Activation functions: 
    - ReLU for the first two layers
    - Sigmoid for the third layer and output layer
  
- **Optimization 3**:
  - Used Keras Tuner to find the best hyperparameters
  - The best model had 5 layers (4 hidden layers + output layer)
  - Neurons: 9, 5, 7, 7, 7 (for each layer)
  - Activation function: 
    - LeakyReLU for hidden layers
    - Sigmoid for output layer

This choice was made to ensure that the total number of neurons in the model was between 2-3 times the number of input features. The strategy was to pick the highest number of neurons for the first layer, then decrease for each subsequent layer. This approach allows the model to learn complex patterns while avoiding overfitting.

Additionally, it was discussed in class that the use of three hidden layers is optimal, as that can detect complex patterns similar to image recognition tasks. This influenced the decision to use three hidden layers in Optimizations 1 and 2.

The use of ReLU and LeakyReLU activation functions in hidden layers helps with faster learning and mitigating the vanishing gradient problem, while sigmoid in the output layer is appropriate for binary classification tasks.

#### 2. Were you able to achieve the target model performance?
The models did not achieve the target model performance of 75%. Here are the results:

- Optimization 1: Accuracy of 72.89%
- Optimization 2: Accuracy of 72.98%
- Optimization 3: Accuracy of 73.04%

While there was a slight improvement across the optimization attempts, the model performance remained relatively consistent around 73% accuracy.

#### 3. What steps did you take in your attempts to increase model performance?
Several steps were taken to attempt to increase model performance:

- **Increasing model complexity**:
   - In Optimizations 1 and 2, the number of hidden layers was increased to 3, with a larger number of neurons (120, 80, 30) compared to the initial model.

- **Adjusting activation functions**:
   - A combination of ReLU and sigmoid activation functions was used in Optimizations 1 and 2.

- **Removing potentially non-beneficial features**:
   - In Optimization 2, the 'STATUS' column was removed from the input data, as it showed extreme class imbalance (34,294 vs. 5).

- **Using Keras Tuner for hyperparameter optimization**:
   - In Optimization 3, Keras Tuner was employed to automatically search for the best hyperparameters, including:
     - Number of layers (1 to 6)
     - Number of neurons in each layer
     - Choice of activation function (ReLU, tanh, LeakyReLU, or sigmoid)

- **Adjusting the preprocessing steps**:
   - Across all optimizations, careful attention was paid to feature engineering, including binning rare categories and using pd.get_dummies() for categorical variables.

- **Increasing training epochs**:
   - The model was trained for 100 epochs in Optimizations 1 and 2, allowing for more training time.

Despite these efforts, the model's performance improved only marginally, suggesting that either the problem is inherently challenging given the available features, or that alternative approaches (such as ensemble methods or different types of models) might be worth exploring.

## Summary

The analysis aimed to develop a deep learning model for Alphabet Soup to predict the success of funding applicants. A neural network was built using a dataset of over 34,000 past funding recipients. The model used various organizational features as inputs to predict a binary outcome of funding success. Despite multiple optimization attempts, including increasing model complexity, adjusting activation functions, removing non-beneficial features, and using Keras Tuner for hyperparameter optimization, the model's performance consistently hovered around 73% accuracy, falling short of the 75% target.

### Recommendation

Given the consistent performance around 73% accuracy despite various optimization attempts, the following recommendations are recommended:

- **Continued hyperparameter tuning**: Further explore different model architectures by varying the number of layers and neurons and experiment with different combinations of activation functions.
- **Ensemble methods**: Consider using ensemble techniques such as Random Forests or Gradient Boosting Machines, which might capture complex relationships in the data more effectively.
- **Consider alternative models**: Explore other machine learning algorithms like Support Vector Machines or even simpler models like Logistic Regression to compare performance.
