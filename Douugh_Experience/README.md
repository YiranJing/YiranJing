# Summary of my learning at Douugh
**Part-time Data Scientist Intern (two days per week)**

Date: Aug 13 2019 - Oct 31 2019 (12 weeks)
## Problem-solving skills I learnt at Douugh
### Experiment-based decision in DS lifeCycle:
Experiment-based decision for data engineering is a more efficiency and secure way to handle project. That is, using **Feedback lifecycle** (Purpose of MLflow usage): 
- Step 1: Do simple necessary data cleaning at the begining, and then train model quickly (baseline: logistic, naive bayes, and NN). 
- Step 2: based on model performance and comparison, thinking about **why better/worse** based on data pattern. After that, go back to step 1 to do another necessary data cleanning. i.e. **Only focus on one most important issues each time**, analysis, justify and check every deicison I made. (*Instead of concerning all kinds of data cleaning steps based on the EDA of raw input, since some of cleaning needs lots of time to finish (e.g. fix all spelling mistakes, remedy inconsistent data issue), but no one knows if all of them are worth to do.*)

### Time difference thinking in cross-sectional modelling
Data difference based on time line are common and important in the real world. Some possible reasons are: Company or governments changes their strategies, or customer behavors change. 

### Improve data quality is more valuable than modelling:
I am not saying good model is not important, but data quality is the pre-condition of good prediction result. Apart from dealing with missing value and default value, discovering incorrect value and inconsistent value is more tricky. During NN model turning process, I realized that the noise and error in the data gives the implicit limitation of model performance, (*possible we can get an insensible incorrect model if the training data is further away from the unknown data in the future*). Therefore, I need to keep improving data quality in my mind. 
##### The ways to find and then fix incorrect values:
Some incorrect values are not easy to find and fix. There are some practical rules I learnt that can help discorver incorrect labels:
1. Analysis the FN predictions from the model. For example. If my model predict "Apple" to "Laptop" rather than "Fruit", then I use text similarity to search the whole dataset, also background/business knowledge to justify whether the original label is wrong.
2. Understand the whole system running rules to avoid change correct value to incorrect ones. Also these background knowlesge can help to fingure out some "dependent" observations. For example, 'financial service' observation and 'bank fee' observation can happen at the same time from the same transaction. Realize these invisible patterns based on different business models are important in DS works, for example, can help feature selection. 

### Unittest and Pytest are as important as write new functions. 
Some small unknown mistake can lead to significant influence, and the more functions I wrote, the more likely I made mistakes. I realized how important to keep functools/pytest in my mind. To minimize the rist/avoid making mistakes again, since Week 6, I begin to write pytest at the same time I write new function.  

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

### Week 4:
-  Try to fix the overfiting issue in NN model with two layers. Learned how to control epochs and modify "Early Stopping" (a technique for controlling overfitting in machine learning models). 
- Finding that the multinomial logistic regression is expensive to train (even more time than NN) when the number of classes increase. (easy to do if less than 15 classes, but when come to 60 classes, nearly 1 hour to train it)
- Find a big advanatge of classifical logistic model compared to ML models: we donot need to worry much about overfitting in logistic cases. However, we can easily overfitting using ML model. For example, I try simple Sequential model with one hidden layers, but overfit already. And then, I have to consider Epoch numer turnning, regularizer. But still cannot beat the simple logistic model.
- focus on loss, rather than accuracy , since the model optimizer is minimize the loss function we choice. 

### Week 5:
- The goal of Neural Network hyperparameter turning: 1. mini gap between train and test dataset, fix overfitting problem. 2. Try to improve overall accuracy further.
- Try to build automated tools to remedy data quality issue: find problem and try to fix it. Since hard to mini train and test accuracy, and cannot improve model accuracy further. Incorrect values(Help system debug) and Inconsistent values(it is a challenge part for NLP modeeling, since it is hard to handle different expressions) are the main issues in the given dataset. 
- Try Fuzzy Matching to reclassify the incorrect classification. 
