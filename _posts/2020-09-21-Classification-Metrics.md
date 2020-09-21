---
layout: post
title: Classification Metrics
---

Notation
- N: is the number of objects
- L: is the number of classes

- y: ground truth
- y': predictions
- [a = b] : Indicator function

- Soft labels (soft predictions) are classifier's scores

- Hard labels (hard predictions):
    - arg max fi(x)
    - [f(x) > b], b: threshold
    
  Accuracy Score
  Accuracy = 1/N * Sum(alpha = yi)
  - How frequently our class prediction is correct.
  - Best Constant: Predict the most frequent class.
  
  Logarithmic Loss (logloss)
  - Binary:
  LogLoss = -1/N*sum(yi*log(y') + (1-yi)*log(1-y'))
  - LogLoss works with soft predictions
  - LogLoss strongly penalizes completely wrong answers
  
  Best Constant: Set alpha_i to frequency of ith class

Area Under Curve (AUC ROC)
ROC: Receiver Operating Curve
- Only for binary tasks
- Dependes only on ordering of the predictions, not on absolute valus
- Several explanations:
1) Area under curve
2) Pairs ordering

In the AUC graph the diagonal is the base rate, with an area of 0.5, which is the equivalent of a random prediction.

AUC =  # correctly ordered pairs / total number of pairs
    = 1 - # incorrectly orddered pairs / total numer of pairs
    
Cohen's Kappa:
Similar to: For perfect accuracy gives a score of 1, and for baseline accuracy gives score of 0

Cohen's Kappa = 1 - (1 - accuracy) / (1 - pe)
pe: what accuracy would be on average, if we randomly permute our predictions
