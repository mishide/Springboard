Data Science Capstone: Classification of Spondylolisthesis
========================================================
author: Michelle Ide
date:  March 2021
<div>
<img src="images/R_B_spine.png" ALIGN="left" width="200"
</div>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<b><font-size: 30">Code can be viewed by clicking</b>
 <br>
 <br>
 </b>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<a href="https://github.com/mishide/Springboard/blob/master/Capstone_1/scripts/Spondylo_Classification_EDA.ipynb" target="_blank">EDA</a>&nbsp;&nbsp;&nbsp;&nbsp; performs the cleaning and initial statistical analysis
<br>
<a href="https://github.com/mishide/Springboard/blob/master/Capstone_1/scripts/Spondlyo_Classification_Models.ipynb" target="_blank">Machine Learning Models</a>&nbsp; 1) build and tests the models 2) results & recommendations

<br>
<br>
<br>

Why
========================================================

<small>
Spondylolisthesis is a slipped vertebra.  The first step in proper diagnosis requires an x-ray determination of "Abnormal" or "Normal".
 <br>
  <br>
 A study published in "The Spine", April 2017(ref1) researched accuracy rates of MRI Lumbar Spine results.  It found significant variability and a high rate of interpretive errors. The conclusions stated,
<br><br>
 <i> "There was an average of 12.5±3.2 interpretive errors (both false-positives and false-negatives)...The high average interpretive miss rate of 43.6%±11.7 across the study examinations means that important pathologies are routinely underreported.  Where a patient obtains his or her MRI examination and which radiologist interprets the examination may have a direct impact on radiological diagnosis, subsequent choice of treatment, and clinical outcome."</i>
 <br><br>
 Machine learning is well suited for the types of simultaneous angle comparisons performed in determining Spondylolisthesis results.  This project has built a model that improves interpretive errors resulting in reduced cost for many; hospitals, physicians, insurance, and patients, while improving many patient outcomes.
 <br>

 


Project
========================================================

<small><b>This project creates a predictive machine to label lumbar x-ray results as "Abnormal" or "Normal' in cases of Spondylolisthesis to reduce interpretive errors and increase consistency resulting in reduced costs and improved outcomes.</b>  
</small> 


Data
========================================================

<small>
The data for this project cam from Kaggle's collection in csv format.
  <br><br>
 - 309 records after outlier removal. 
  <br><br>
  - The data is clean and contains no null values.
  <br><br>
 - 6 quantitative variables
 - 1 Target binomial variable (Normal/Abnormal)
</small><small>

* Pelvic Tilt
* Pelvic Incidence
* Pelvic Radius
* Lumbar Lardosis Angle
* Sacral Slope
* Degree Spondylolisthesis.</small>


Approach
========================================================
Six well-known classification models were tested using 70% of the data to train and 30% to test. A large range of potential hyper parameter settings were tested for each model, determining the best settings for this project. Each model was selected due to it's usefulness in classification problems and it's differences in algorithmic process compared to the remaining models.

A stratified train-test split was used due to the imbalanced data in combination with upsampling methods performed during crossvalidation.  Upsampling methods were selected for their performance and potential for addressing the complexity in 'boundry' cases that exist in this project.  SMOTE-TL was determined to perform best overall by research performed by  'Santos, Soares, Abreu, Araujo"* in 2018.  ADASYN was included due to it's approach to the minority class, adding weight to boundry minority data in an effort to amplify and clarify separation.


Modeling
========================================================
<small>
When comparing results, this algorithmic process was taken into account, given the nature of the data. Three models performed similarly with the Logistic Regression performing 5% higher than the Gradient Boosting and Support Vector Machine. The linear nature of the Logistic Regression is not as reliable when dealing with extreme, sparse, values making the remaining 2 algorithms a good first choice. The Gradient Boosting algorithm is extremely slow on just 309 samples and may be undesirable with large amounts of data, depending on the hardware used. The Support Vector Machine, similar to Logistic Regression in accuracy with a 3% difference, would provide the flexible boundaries needed to absorb infrequent extremes without dragging the center population down in precision.
 </small> 


Results
========================================================
<small>Logistic Regression preformed with the highest accuracy of 91%, Support Vector Machine 88%. </small> 
<br><br>
Using the ADASYN upsampling method: Out of 100 samples, 10 will be false positive ( Abnormal ), and 0 will be false negative ( Normal )
<br><br>
Using SMOTE-TL: Out of 100 samples, 7 will be false positive ( Abnormal ) and 1 will be false negative ( Normal )


Recommendations
========================================================
<small>I recommend Support Vector Machine with either ADASYN or SMOTE-TL method for upsampling. The choice between these two methods depends on the sensitivity requirements for false negatives and positives.
Using ADASYN it can be expected to have rarely, if ever, false negative results, there will however be 3 more false positive contained in every 100 samples.
My past experience in healthcare research leads me to lean toward ADASYN and avoid false negatives. However, 10 out of 100 false positives could reduce confidence in results and lead to additional costs in follow-up testing. This decision betweenn the 2 sampling methods would require feedback from decision makers.


Future Development
========================================================
Test several stacking methods to search for improved accuracy - this would provide additional layers of testing results to verify.
Test and train on more data, 309 samples is not bad to start but much more would be needed to validate results condidently.
Create unique splits to data prior to train-test split to test sparse data processing for small radiology departments with fewer results to run.


References
========================================================
ref1:  https://www.sciencedirect.com/science/article/pii/S1529943016310932
