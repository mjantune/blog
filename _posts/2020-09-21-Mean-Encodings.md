*Mean Encodings*

Ways to use Target Variable
- Likelihood = Goods / (Goods + Bads) = Mean(target)
- Weight of Evidence =  ln(Goods/Bads)*100
- Count  Goods = Sum(target)
- Diff = Goods - Bads

Springleaf Dataset Example

  means = X_tr.groupby(col).target.mean()
  train_new[col+'_mean_target' = train_new[col].map(means)
  val_new[col+'_mean_target'] = val_new[col],map(means)
  
  *Regularization*
  1. CV (Cross Validation) loop inside training data
  To get mean ecoding from a subset, we dont use the data points from that subset, but we use the rest of subsets. Usually 4 to 5 olds is usually enough.
  - Robust and Intuitive
  - Usually decent results with 4-5 foldsa across different datasets
  - Need to be careful with extreme situations like LOO (Leave One Out)
  
    y_tr = df_tr['target'].values #target variable
    skf = StratifiedKFold(y_tr, 5 shuffle=True, random_state = 123)
    
    for tr_ind, val_ind in skf:
        X_tr, X_val = df_tr.iloc[tr_ind], df_tr.iloc[val_ind]
        for col in cols: #iterate though the columns we want to encode
            means = X_val[col].map(X_tr.groupby(col).target.mean()
            X_val[col + '_mean_target'] = mean
        train_new.iloc[val_ind] = X_val
        
    prior = df_tr['target'].mean() #Global mean
    train_new.fillna(prior, inplace = True) #Fill NaNs with global mean
    
  
  2. Smoothing
  - Alpha controls the amount of regularization
  - Only works together with some other regularization method
  
  (mean(target) * nrows + globalmean*alpha) / (nrows+alpha)

  
  3. Adding random noise
  This method is quite unstable, so its difficult to use
  - Noise degrades the quality of encoding
  - How much noise should we add?
  - Usually together with LOO
  
  4. Sorting and Calculating expanding mean
  - Least amount of leakage
  - No hyper parameters
  - Irregular encoding quality
  - Built-in CatBoost
  
  e.g.
      cumsum = df_tr.groupby(col)[target].sumsum() - df_tr['target']
      cumcnt = df_tr.groupby(col).cumcount()
      train_new[col + '_mean_target] = cumsum/cumcnt
  
