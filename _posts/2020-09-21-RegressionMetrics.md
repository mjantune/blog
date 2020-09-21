---
layout: post
title: Regression Metrics
---

1. Regression:
1.1 MSE, RMSE, R-Squared
1.2 MAE
1.3 (R)MSPE, MAPE
1.4 (R)MSLE

2. Classification
2.1 Accuracy, Logloss, AUC
2.2 Cohen's (Quadratic weighted) Kappa

1.1 Mean Square Error
 MSE = 1/N*Sum(i=1..N,(yi-y^i)^2)
 
 Root Mean Square Error
 RMSE = sqrt(1/N*Sum(i=1..N,(yi-y^i)^2)) = (MSE)^0.5
 
 - Every minimizer of RMSE is a minimizer of MSE
 - There is a difference between RMSE and MSE for gradient based models:
     dRMSE/dyi = 1/(2*sqrt(MSE))*dMSE/dyi
 
 R-Squared
 R^2 = 1 - 1/N*sum(yi - y'i)^2 / 1/N*sum(yi - mean(y))^2 = 1 - MSE / (1/N*sum(yi-mean(y))^2)
 
 1.2 MAE: Mean Absolute Error
 MAE = 1/N*sum(|yi-y'i|)
 This metric is not as sensitive to outliers as MSE.
 - Its usually used in finance
 
 Best Constant: target median
 
 MAE vs MSE:
 - So you have outliers in your data?
    Use MAE
 - Are you sure they are outliers?
    Use MAE
 - Or are they unexpected values we should still care about?
    Use MSE
 
 1.3 MSPE and MAPE:
 1.3.1 MSPE Mean Square Percentage Error
  - Optimal Constant: Weighted Target Mean
     100%/N*sum(((yi-alpha)/yi)^2
     
 1.3.2 MAPE Mean Absolute Percentage Error
 - Optimal Constant: Weighted Target Median
     100%/N*sum(|(yi-alpha)/yi|)
     
 1.4 (R)MSLE: Root Mean Square Logarithmic Error
 RMSLE = sqrt(1/N*sum((log(yi+1)-log(y'i+1))^2)
       = RMSE(log(yi+1),log(y'i+1))
       
   Best Constant:
   - Best constant in log space is a mean target value
   - We need to exponentiate it to get an answer
  
