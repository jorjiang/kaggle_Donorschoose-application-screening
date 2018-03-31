# kaggle_Donorschoose-application-screening[link to leaderboard!](https://www.kaggle.com/c/donorschoose-application-screening/leaderboard)
Is solution get an AUC score of 0.82435, the leader has 0.82830, currently ranked at 13 (top 4%)

## Feature engineering
### Text features
  - Tfidf of Title, item_summary, eassay (with lemmatization, stopwords revomal, punctuation included)
  - word tags
  - sentiment Title, item_summary, eassay (polarity and subjectivity)
### Resource features
  - total cost of each project
  - mean, std, min, max of single price, amount of items asked, total price
  
### Teacher features
  - Amount of previous applications from that teacher
  - Amount of total applications from that teacher
### Date features
  - hour, day, month, quarter, year, week of the year, day of the month, day of the week, holidays
## model
Lightgbm with K-fold (k = 5)
```
params = {
        'boosting_type': 'gbdt',
        'objective': 'binary',
        'metric': 'auc',
        'max_depth': 12,
        'num_leaves': 31,
        'learning_rate': 0.02,
        'feature_fraction': 0.85,
        'bagging_fraction': 0.85,
        'bagging_freq': 5,
        'verbose': 0,
        'num_threads': 1,
        'lambda_l2': 1,
        'min_gain_to_split': 0,
    }
    ```  
