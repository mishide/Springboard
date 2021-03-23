Data Science Capstone: Classification of Spondylolisthesis
========================================================
author: Michelle Ide
date:  March 2021
autosize: true
font-family: 'Helvetica'

<div>
<img src="coursera.png" style="width:15%"
</div>

Description
========================================================

<small>
Spondylolisthesis is a slipped vertebra in the spine.  With early intervention, the treatment and outcomes can be non-invasive and less costly.  A low-grade abnormality can be treated with a brace, physical therapy, and rest, allowing the bone to heal.  Higher-grade fractures require major surgery, long recovery, and potential lifelong disability.

The symptoms are common to many minor sports injuries and everyday aches and pains such as tight hamstrings and tingling in the feet.  Without distinctive symptoms it can be difficult to recognize the issue early.  An x-ray is required to help physicians determine the proper treatment.  Proper classification of the results contains an additional challenge, it requires several angles to be compared simultaneously in order to determine normal or abnormal.  This takes years of training and expertise.  Machine learning models are well suited for such simultaneous comparisons.  Gathering the experience of physicians that are contained in the data from previous results, machine learning models can learn to recognize and label results quickly, assisting radiologists, reducing costs, and providing patients faster results.

This project takes a look at how to best classify cases of Spondylolisthesis as 'Normal' versus 'Abnormal'.  The machine will feed previous results into the model, allowing it to learn from the data, and generate predictions that label each result as Normal or Abnormal, indicating if a need to follow-up with a physician is recommended.
</small> 


Data
========================================================

<small>
The data for this project was gathered from Kaggle's collection in csv format.** Originally containing 310 records prior to statistical analysis, 309 after. The data is clean and contains no null values.  It included a class label of Abnormal or Normal for each record and 6 quantitative variables
</small><small>

* Pelvic Tilt
* Pelvic Incidence
* Pelvic Radius
* Lumbar Lardosis Angle
* Sacral Slope
* Degree Spondylolisthesis.</small>


Statistical Analysis
========================================================
<small>
The data is imbalanced with 210 Abnormal and 100 Normal which is addressed during model development.  Using Tukey's Method with a z-score of 2, three potential outliers were identified.  A radiologist was consulted and it was agreed one record >400 in the 'degree' feature was a probable outlier.  This record was removed resulting in 209 Abnormal and 100 Normal records.
 </small>   


Modeling
========================================================
<small>To address this imbalance the train-test split was stratified to ensure identical proportions within the split.  The test data split contained 30% of the population.

Several methods of oversampling were performed on the minority class (normal). Initially, oversampling methods SMOTE and ADASYN were tested.  While SMOTE creates synthetic data points from the minority class at random, ADASYN adds weight to the boundary cases which are of importance to this project.  However, due to research performed by  'Santos, Soares, Abreu, Araujo"* in 2018 I choose to add SMOTE-TL due to it's superior performance when compared to SMOTE and the potential for ADASYN's weighting measure, the benefit we seek to balance the minority data, can also adds weight to noisy data skewing the results toward the majority.  All oversampling methods were performed inside cross-validation to prevent overly-optomistic estimates.  
K-Fold validation of five was used during hyper parameter tuning to avoid overfitting. </small> 


Results
========================================================
<small>Three of the models performed comparably well.  Logistic Regression had the top accuracy score of 91% with the Gradient Boosting Classifier and Support Vector Machine coming in second at 86%, just 5% less. </small> 
