# JiameiShi-bonus_deep_learning_time_series
***Time Series Forecasting on the M4 Dataset***

***Methods***

This study applies a time series forecasting pipeline to a large-scale benchmark dataset in order to demonstrate correct dataset handling, model training, and evaluation. The M4 Daily dataset was selected for this task due to its widespread use in forecasting research and its large size, containing well over 500,000 observations across thousands of univariate time series.

The dataset was loaded using the sktime library, which provides standardized tools for time series analysis in Python. To ensure computational efficiency in a notebook environment, a deterministic subset of the data was used. Specifically, the first ten time series were selected based on their index ordering. This selection method avoids randomness and ensures full reproducibility.

Each time series was split into training and testing segments using a temporal train-test split, where the final observation of each series was reserved for testing. This mirrors realistic forecasting scenarios in which future values are predicted strictly from past data.

For modeling, a Naive Forecaster with the "last" strategy was employed. This model predicts future values by repeating the most recent observed value in the training set. While simple, the Naive Forecaster is a standard baseline in time series forecasting and provides a useful reference point for evaluating more complex models.

Model performance was assessed using two commonly used regression metrics: Mean Absolute Error (MAE) and Root Mean Squared Error (RMSE). These metrics quantify forecast accuracy by measuring the deviation between predicted and actual values.

***Results***

The forecasting process completed successfully for all selected time series. The Naive Forecaster generated one-step-ahead predictions for each series in the test set.

The evaluation produced the following results:

Mean Absolute Error (MAE): 1069.49

Root Mean Squared Error (RMSE): 1069.49

Because the test horizon consisted of a single time step per series and the Naive model produces constant predictions, the MAE and RMSE values are identical in this case. The results are deterministic and reproducible across different runs and environments.

***Discussion***

The results reflect the limitations and characteristics of the Naive forecasting approach. By construction, the model assumes that the most recent observation is the best predictor of future values, ignoring trends, seasonality, and other temporal dynamics. Consequently, while the error values are relatively large, they are expected given the simplicity of the model and the scale of the data.

Despite its simplicity, the Naive Forecaster plays an important role in time series analysis. It serves as a baseline against which more advanced models—such as ARIMA, exponential smoothing methods, or deep learning approaches—can be compared. Any sophisticated model should demonstrate improved performance relative to this baseline to justify its additional complexity.

An important aspect of this experiment is its reproducibility. The deterministic dataset selection, temporal splitting strategy, and non-random model ensure that identical results are obtained across runs. This is particularly valuable in academic and applied settings, where reproducibility is essential.

Future work could extend this analysis by incorporating seasonal naive models, classical statistical forecasting techniques, or neural architectures such as LSTMs or Transformers. These models may better capture complex temporal patterns present in the M4 dataset and lead to improved forecasting accuracy.
