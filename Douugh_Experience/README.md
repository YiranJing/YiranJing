# Summary of my learning at Douugh
**Part-time Data Scientist Intern (two days per week)**

Date: Aug 13 2019 - Oct 31 2019 (12 weeks)
## Problem-solving skills I  learnt at Douugh
### Week 2-3:
- **Experiment-based** decision for data engineering (More efficiency and secure). **Feedback lifecycle** (Purpose of MLflow usage): At the begining, I concern many data cleaning steps based on the EDA of raw input, but some of cleaning needs lots of time to finish, and no one knows if all of them are worth to do. So, instand of spending time on all possible data cleaning steps before modelling, I only did few necessary data cleaning and then train model quickly (baseline: logistic, naive bayes, and NN). Then, based on model performance and comparison, thinking about **why better/worse** based on data pattern. After that, go back to add one more step in data cleanning. i.e. **Only focus on one most important issues each time**, analysis, justify every deicison I made. 
- **Time difference thinking in cross-sectional modelling**. Data difference based on time line are turly common and important in the real world. Some possible reasons are: Company or governments changes their strategies, or customer behavors change. Also, after spliting train and test dataset based on time-series , the difference we find might not caused by time! 


## Practical Skills I Leart at Douugh
### Week 1: 
- Know my role in data team, and begin work on the multi-classification project.
- Learnt basic NLP tech, including bag of word and word Embeddings. 
- Begin the data cleaning for text classification. 

### Week 2:
- Realize the 'Imbalanced' classification can be NOT a problem in the practical, and can get really good prediction results, as long as we can find key featurers for the low frequency class. 
- After realized that the 'perfect cleaned' data in text/NLP case is hopeless, try to find a 'smarter' and 'more efficient' way to clean and select (50k+) key features: good enough cleaned dataset + (pre-trained) embedding dataset + good classifier.
- Understanding the limitation of trandictional logistic model, since based on the number of events per variable (EPV) rule, trandictional regression cannot handle lots of predictors, but we do have to use thoushands of featuers in NLP/text classification. 
- Check and fill uncover row based on data distribution.

### Week 3:
- MLflow for ML lifecycle monitor
- Learn how to debug through command line. For example, `ps aux | grep mlflow` to check and kill mlflow. 
- Build a automatical word selection rule to pick as many key words/featurers as possible, which can automatically increasing the size of features on the larger dataset. 
- Split train and test dataset based on time-series in the cross-sectional dataset. There are three main reasons: Firstly, we always make decision using the most recent data based on the model trained by old data in daily operation. Secondly, the time horizon is important and necessary to help us notify customer behavor change over time. Thirdly,my interesting finding is that, actually we could get "more even split" in some "extremely imbalanced" classes by time series spliting, rather than random state. 
- Overfitting is easily happen in small category with quite few observations. For example, the selected key words in "Healthcare" inlcudes "Sydney", "Mel" etc, which are quite general words. I need to keep it in mind in the future test using new data.
- Train Simple Neural Network BOW. 
