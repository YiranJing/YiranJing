# Summary of my learning at Douugh
**Part-time Data Scientist Intern (two days per week)**

Date: Aug 13 2019 - Oct 31 2019 (12 weeks)
## Problem-solving skills I learnt at Douugh

### Considering the whole picture whenever dealing with problem.
*It is fact that everyone knows, but easy to forget when we are dealing with one specific probelm*: The solution of the problem generally consists of several different parts. Always ensuring check and fix the most important one first. Work efficiency and correct direction are always important in the work.
- For example, when I try to overcome time difference issue between train and test data. I use 2 weeks to build yelp API and add new informations to raw data, and use 2 weeks to try test similarity to fix the mis-label data. They are good solution/idea, but they are just quite small amount among all misclassification results (less than 20%). By contrast, go back to think problem again and again, then change the 'split date' between train and test data is more efficient and actually should be the first thing to do before considering other small issues.


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

### Week 7:
- Stemmer algorithms choice: In NLP tech, we can collect less number of key words using LancasterStemmer compared to PorterStemmer method. In the case that we want to control total number of features and avoid collinearity issue (for example, logistic regression), it might be better to choice LancasterStemmer. However, In most ML models (such as NN), we donot care if collinearity exits or large number of features, then, PorterStemmer method is better. For example, `ubs` stands for bank, but LancasterStemmer will treat it same as `uber`, which is misleading and incorrect.

```python
from nltk.stem import PorterStemmer
from nltk.stem import LancasterStemmer

#create an object of class PorterStemmer
porter = PorterStemmer()
lancaster=LancasterStemmer()
#proide a word to be stemmed
print("Porter Stemmer")
print(porter.stem("uber"))  #uber
print(porter.stem("ubs"))  #ubs 
print("------------------")
print("Lancaster Stemmer")
print(lancaster.stem("uber")) #ub
print(lancaster.stem("ubs"))  #ub
```
- To improve FN predictions based on data pattern, Using Web spider and Yep API for example to collect help dataset. 
- Regularly Reviewing previous desicions is important, which is not only helps to justify/be more confident to current status, but also can find possible mistakes or incorrect decision and fix them.


### Week 8 and 9:
- Importance of normalization for comtinuous feature: Ealier converge by more smoothing plot, and thus more efficient and robust results. The reason behind normalization is the `weight` of each features. 
- Policy effect to the data: deplore row data and try to understand them. For example, Public transport policy changed in one city of America, before and after 2019-5-31. Thus I need to adjust train and test data for `Public transport service` category. 
- EDA is important than model itself in some cases, and it is much more than plots and tables. Thus we should do it not only before modelling, but (more) after modelling to find error, understand hidden patterns etc. 
- Fix all ambiguous words costs lots of time, but fix some of them is important. For example clean `superm` to `supermarket` is important, since it can help predict some ‘new' observations only in test dataset. 
- Re-run NN model multiple times with same hyperparameters are important. Since if the test result changes a lot (more than 1%) between different trials, it implies that some observations(pattern) is unsure in model prediction. That is, model doesnot know what spicific pattern should be classificed, thus predict quite similar probability in several different categories. Possible reasons are:
  1. misclassification in train data. 
  2. new observations in test data only. 
To ensure **robust** prediction result. It is important to find these patterns and fix them. 
- Compare accuracy difference between ’time’ and ‘random’ data split method can help to find out time difference pattern. For example, some categories have quite high prediction acuracy using 'random' method, but not perform well using 'date-split' method. The possible reason is some new business only shown in recent month.
