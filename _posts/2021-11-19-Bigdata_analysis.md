---
layout: single
title: "Big Data Analysis"
date: 2021-11-19 12:00:00 -0000
categories: big data spark  machine learning   
excerpt: Perform data analysis and machine learning on large messy data sets.
---

In this project, we performed  data manipulation, analysis, and machine learning on the Stack Overflow data set. 

## Data Preparation
### Data 
The data we used here is already anonymized.

We are intersted in patterns in data such as:
<ul> 
  <li>Relationship between the number of times a post was favorited (the `FavoriteCount`) and the `Score`.</li>
  <li>correlation between a user's reputation and the kind of posts they make.</li>    
  <li>Identify "veterans" (user to remain active on the site over a long period of time) and compare their characterstics with  "brief   
      users".</li>  
</ul>

### Predict question tags

We'd intend to predict the tags of a question from its body text. To this end, we first find the ten most common tags for questions in the training data set (the tags have been removed from the test set). Then train a learner to predict from the text of the question (the Body attribute) if it should have one of those ten tags in it - you will need to process the question text with NLP techniques such as splitting the text into tokens.

```python
paramGrid = (ParamGridBuilder() 
    .addGrid(hashingTF.numFeatures, [2000, 3000, 5000]) 
    .addGrid(logreg.regParam, [0.1, 0.01, 0.5])
    .addGrid(logreg.elasticNetParam, [0.1, 0.5, 0.8])         
    .build())


crossval = CrossValidator(estimator=pipeline,
                          estimatorParamMaps=paramGrid,
                          evaluator=BinaryClassificationEvaluator(),
                          numFolds=6, # 3 or 4 ?
                          seed=17)

cvModel = crossval.fit(train)
better_predictions = cvModel.transform(test)
```