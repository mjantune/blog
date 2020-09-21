*MSE*
Most modelling software will use MSE as a loss function:

- Tree Based: XGBoost, LightGBM
- Linear Models: sklearn.<>regression, sklearn.<>SGDRegressor, Vowpal Wabbit (quantile loss)
- Neural Nets: PyTorch,Keras, TF, etc.

Synonims: L2 Loss

*MAE*

- Tree Based: LightGBM
- Linear Models: Vowpal Wabbit (quantile loss)
- Neural Nets: PyTorch,Keras, TF, etc.

Synonims: L1, Median regression

*MSPE and MAPE*
How do you optimize them?
- Use weights for samples, and use MSE (or MAE)
- Resample the train set
   - df.sample(weights=sample_weights)
   - And use any models that optimizes MSE (MAE)
   - Usually need to resample many times and average

*RMSLE*

