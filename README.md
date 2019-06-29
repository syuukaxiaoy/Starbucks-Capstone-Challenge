# Starbucks-Capstone-Challenge
An analysis about the data set contains simulated data that mimics customer behavior on the Starbucks rewards mobile app.
## Introduction
This data set contains simulation data to simulate customer behavior on Starbucks reward mobile applications. Every few days, Starbucks sends out an offer to users of mobile applications. An offer can be just an advertisement for a beverage or an actual offer, such as a discount or forgery (buy one get one free). This data set is a simplified version of a real Starbucks application because the underlying simulator has only one product, and Starbucks actually sells dozens of products. Some users may not receive any offers within a specific few weeks.

Each offer has a validity period before it expires. For example, a counterfeit offer may be valid for only five days. It can be seen in the data set that even if these advertisements only provide information about the product, the information quotation is valid; for example, if the information quotation is valid for 7 days, it can be assumed that customers will feel the impact of the quotation within 7 days after receiving the advertisement.

The transaction data purchased by the user on the application, including the purchase timestamp and the amount spent on the purchase. This transactional data also has a record of each product that the user receives, as well as the record when the user actually views the product. There is also a record of the completion of the quotation by the user.

It is important to note that people using the application may purchase through the application without receiving or seeing the offer. This is the challenge of using this data set.

My goal is to combine transaction, demographic and data provision to observe the completion of various classifications, and then to select an optimal predictive classifier through machine learning training data to determine whether the target user can complete the offer.

I also finished a post on Medium, the url is here: 

https://medium.com/@1915671841/starbucks-capstone-challenge-1289b0e427ec

## Part:
- Data Cleaning, EDA
- Visualization
- Making a pipeline
- Modeling
- Scoring
- Prediction
- GridSearch
- Cross validation
- Comment

## Files
- Starbucks.html
- Starbucks.ipynb
- modppt.csv
- portfolio.json
- profile.json

## About data set
**portfolio.json**
* id (string) - offer id
* offer_type (string) - type of offer ie BOGO, discount, informational
* difficulty (int) - minimum required spend to complete an offer
* reward (int) - reward given for completing an offer
* duration (int) - time for offer to be open, in days
* channels (list of strings)

**profile.json**
* age (int) - age of the customer 
* became_member_on (int) - date when customer created an app account
* gender (str) - gender of the customer (note some entries contain 'O' for other rather than M or F)
* id (str) - customer id
* income (float) - customer's income

**transcript.json**
* event (str) - record description (ie transaction, offer received, offer viewed, etc.)
* person (str) - customer id
* time (int) - time in hours since start of test. The data begins at time t=0
* value - (dict of strings) - either an offer id or transaction amount depending on the record

## Library
- pandas
- numpy
- math
- json
- matplotlib
- seaborn
- sklearn
- sklearn.pipeline
- time
- dateutil.parser
- datetime

## Algorithm：
- SVC
- RandomforestClassifier
- AdaboostClassifier

## Techniques：
- Pipeline

## Metrics：
- Accuracy
- f1 score
- cost time

## Model Evaluation and Validation：

The accuracy of RFE is the highest by comparing the charts, and the other two are not very different. Then compare the time spent on training data. From the figure above, we can see that the longest time spent on SVC is more than 3000s, the other two are relatively faster, RFE is the fastest, followed by ABC. Considering the above results, SVC is not a good choice. The time spent on SVC does not bring higher accuracy. Then the best one is the RFE, and the shortest one is the RFE. Although ABC is fast, it is still inferior to RFE in all aspects. So in the end, I think RandomForestClassifier is the best choice under this data set.

## Reflection：
Retrain the selected model on the whole data set

Result：
The accuracy of random forest is more than 80%, the F1 value has been improved, the data set has changed greatly, but it does not take a long time, so I think this is a good choice.

## Improvements：

Selection of experimental subjects：

Further investigation of unrealistic data excluded by users

Choose people who are really interested in offers, but for some reasons, they don’t have enough time to complete it. 
