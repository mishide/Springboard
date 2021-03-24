Data Science Capstone: Classification of Spondylolisthesis
========================================================
author: Michelle Ide
date:  March 2021
<div>
<img src="images/R_B_spine.png" ALIGN="left" width="200"
</div>
  <h3 style="font-size: 11">Code</b> can be found by clicking </h3>
  <br>
 </b>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<a href="https://github.com/mishide/Springboard/blob/master/Capstone_1/scripts/Spondylo_Classification_EDA.ipynb" target="_blank">EDA</a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; performs the cleaning and initial statistical analysis
<br>
<a href="https://github.com/mishide/Springboard/blob/master/Capstone_1/scripts/Spondlyo_Classification_Models.ipynb" target="_blank">Machine Learning Models</a>&nbsp;&nbsp; 1) build and tests the models 2) results & recommendations

<br>
<br>

Why
========================================================

<small>
Spondylolisthesis is a slipped vertebra.  The first step in proper diagnosis requires an x-ray.
 
 A study published in "The Spine", April 2017 researched accuracy rates of MRI Lumbar Spine results.  They found significant variability and high rate of interpretive errors.  Radiologists, are unique, with unique training and skill, the result being high variance in reporting results.  Conclusions included,  "There was an average of 12.5±3.2 interpretive errors (both false-positives and false-negatives)...The high average interpretive miss rate of 43.6%±11.7 across the study examinations means that important pathologies are routinely underreported."
<br>
 <i> Where a patient obtains his or her MRI examination and which radiologist interprets the examination may have a direct impact on radiological diagnosis, subsequent choice of treatment, and clinical outcome."</i>
 
 Machine learning is well suited for the types of simultaneous angle comparisons performed in determining Spondylolisthesis results.  This project has built a model that improves interpretive errors resulting in reduced cost for everyone, hospitals, physicians, insurance, and patients, as well as improving patient outcomes.  It can also replace the need for the second human interaction for validation.
 <br>

 


Project
========================================================

<small>This project creates a predictive machine to label lumbar x-ray results as "Abnormal" or "Normal' in cases of Spondylolisthesis.  It ingests 6 quantitative measurements to determine the results using the predictive model created.  This model will result in a reduced error rate, improving consistency, and can be used as an initial sorting or secondary validation system.  As the model continues to train on new data, from various Radiological results, I expect the algorithm to imrove and develop into a system that can be relied on as accurate with only the occassional need for human input.
 
 Gathering the experience of physicians that are contained in the data from previous results, machine learning models can learn to recognize and label results quickly, consistently, alerting radiologists to potential conflicts with their findings.  This validation system can result in reducing the costs of human validation, reduce costs with fewer lawsuits through consistent findings, and resulting in improved patient outcomes.

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
Total of 309 Patient Records were used (1 outlier was removed)
 
209 Abnormal, 100 Normal results
 </small> 
 
 <small>
Tukey's Method with a z-score of 2 identified three potential outliers, only 1 was removed, the other 2 were still within 99% confidence range.  
 </small>   


Modeling
========================================================
<small>To address this imbalance the train-test split was stratified to ensure identical proportions within the split.  The test data split contained 30% of the population.

Several methods of oversampling were performed on the minority class (normal). Initially, oversampling methods SMOTE and ADASYN were tested.  While SMOTE creates synthetic data points from the minority class at random, ADASYN adds weight to the boundary cases which are of importance to this project.  However, due to research performed by  'Santos, Soares, Abreu, Araujo"* in 2018 I choose to add SMOTE-TL due to it's superior performance when compared to SMOTE and the potential for ADASYN's weighting measure, the benefit we seek to balance the minority data, can also adds weight to noisy data skewing the results toward the majority.  All oversampling methods were performed inside cross-validation to prevent overly-optomistic estimates.  
K-Fold validation of five was used during hyper parameter tuning to avoid overfitting. </small> 


Results
========================================================
<small>Three of the models performed comparably well.  Logistic Regression had the top accuracy score of 91% with the Gradient Boosting Classifier and Support Vector Machine coming in second at 86%, just 5% less. </small> 


References
========================================================
Ref 1:  https://www.sciencedirect.com/science/article/pii/S1529943016310932
