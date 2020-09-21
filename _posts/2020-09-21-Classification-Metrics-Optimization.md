*LogLoss*

All neural nets use logLoss by default.
Random Forest classifiers tend to be quite bad for logLoss, but we an calibrate the predictions to better fit the predictions.

Probability Calibration
- Platt sclaing
- Isotonic regression
- Stacking

*Accuracy*
There is no way to directly optimize Accuracy
Fit any metric and tune threshold!

*Pairwise loss vs Pointwise Loss*

*Quadratic Weighted Kappa*
- Optimize MSE and find right Thresholds (simple)
    Kappa similar to: 1 - MSE / hard to deal with part
    Find right thresholds:
    Bad: np.round(preidictions)
    Better: optimize thresholds
    
- Custom smooth loss for GBDT or Neural nets (Harder)

