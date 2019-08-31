# The Summery of Practical Skills I Leart at Douugh
**Part-time Data Scientist Intern (two days per week)**

Date: Aug 13 2019 - Oct 31 2019 (12 weeks)

## Week 1: 
- Know my role in data team, and begin work on the multi-classification project.
- Learnt basic NLP tech, including bag of word and word Embeddings. 
- Begin the data cleaning for text classification. 


## Week 2:
- Realize the 'Imbalanced' classification can be NOT a problem in the practical, and can get really good prediction results, as long as we can find key featurers for the low frequency class. 
- After realized that the 'perfect cleaned' data in text/NLP case is hopeless, try to find a 'smarter' and 'more efficient' way to clean and select (50k+) key features: good enough cleaned dataset + (pre-trained) embedding dataset + good classifier.
- Understanding the limitation of trandictional logistic model, since based on the number of events per variable (EPV) rule, trandictional regression cannot handle lots of predictors, but we do have to use thoushands of featuers in NLP/text classification. 
- Check and fill uncover row based on data distribution.

## Week 3:
- MLflow for ML lifecycle monitor
- Learn how to debug through command line. For example, `ps aux | grep mlflow` to check and kill mlflow. 
- Build a automatical word selection rule to pick as many key words/featurers as possible, which can automatically increasing the size of features on the larger dataset. 
- Split train and test dataset based on time-series data in the cross-sectional dataset. There are three main reasons: Firstly, we always make decision using the most recent data based on the model trained by old data in daily operation. Secondly, the time horizon is important and necessary to help us notify customer behavor change over time. Thirdly,my interesting finding is that, actually we could get "more even split" in some "extremely imbalanced" classes by time series spliting, rather than random state. 
- Train Simple Neural Network BOW. 
