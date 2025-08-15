## DoorDash ETA Prediction

### Project Overview

This project aims to predict the **Estimated Time of Arrival (ETA) for DoorDash deliveries** based on a rich dataset of historical orders. By analyzing features related to store and market conditions, order details, and dasher availability, the goal is to develop a regression model that can accurately forecast delivery duration. This is crucial for improving customer experience, optimizing logistics, and ensuring efficient operations.

-----

### Technical Highlights

  * **Dataset**: [Kaggle - DoorDash ETA Prediction](https://www.kaggle.com/datasets/dharun4772/doordash-eta-prediction)
  * **Size**: 197,428 entries, 16 columns (initial). The dataset is extensively cleaned and engineered before being used for modeling.
  * **Key Features**:
      * `market_id`, `store_id`, `store_primary_category`, `order_protocol`, `total_items`, `subtotal`, `estimated_order_place_duration`, and several engineered features related to time, dasher availability, and price.
  * **Approach**:
      * **Data Preprocessing**: Datetime columns (`created_at`, `actual_delivery_time`) were converted and used to calculate the target variable `delivery_duration_minutes`. New time-based features (`hour`, `day_of_week_num`, `is_weekend`, `is_holiday`) and custom features (`dashers_per_order`, `price_range`, `delivery_difficulty`) were engineered. Outliers were removed using the IQR method. Missing values were handled using `KNNImputer` for numerical columns and mode imputation for categorical columns. Finally, `LabelEncoder` was applied to categorical features.
      * **Model Architecture**: A **deep neural network (ANN)** was built using Keras with three `Dense` hidden layers and two `Dropout` layers for regularization. The output layer uses a linear activation function, appropriate for a regression task.
      * **Training**: The model was compiled with the `Adam` optimizer and `mean_squared_error` loss. It was trained for 50 epochs with `EarlyStopping` to prevent overfitting.
  * **Best Performance**:
      * The model achieved a Mean Absolute Error (MAE) of **8.12 minutes** and a Root Mean Squared Error (RMSE) of **10.41 minutes** on the test data, indicating that the model can predict delivery duration with good accuracy.

-----

### Purpose and Applications

  * **Accurate ETA prediction** for food delivery services like DoorDash, enhancing customer satisfaction.
  * Optimize dasher dispatching and routing to improve delivery efficiency.
  * Support data-driven decision-making in logistics and operational management.
  * Provide a foundation for developing more sophisticated real-time delivery management systems.

-----

### Installation

Clone the repository:

```bash
git clone https://github.com/BhaveshBhakta/DoorDash-ETA-Prediction-Using-ANN.git
cd DoorDash-ETA-Prediction-Using-ANN
```

Install the necessary libraries:

```bash
pip install pandas numpy seaborn matplotlib scikit-learn tensorflow holidays
```

-----

### Collaboration

We welcome contributions to improve the project. You can help by:

  * Performing comprehensive hyperparameter tuning for the neural network architecture and training process.
  * Exploring other regression models or ensemble methods (e.g., XGBoost, Gradient Boosting) to compare performance against the ANN.
  * Investigating different feature engineering techniques to create more powerful predictive features.
  * Adding a more detailed analysis of the model's errors to understand where the predictions are most inaccurate.
