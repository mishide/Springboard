S​pringboard ​D​ata ​S​cience ​C​apstone Orthopedic Biomechanical Features
Michelle Ide
● Muscle spasms in the hamstring.
● Back stiffness.
● Difficulty walking or standing.
● Pain when bending over.
● Numbness or tingling in the foot.
Have you ever had these symptoms? Yes, they are very common, yet these are some of the common symptoms of a serious spinal injury called Spondylolisthesis, which also is referred to as a slipped vertebra.
Not the same as a slipped disc, a slipped
vertebra has many possible causes and requires a simultaneous comparison of several angles in order to properly diagnose. These complex
comparisons require specialized training for physicians, expertise that is costly and in high demand, reducing the likelihood of early or quick diagnosis. Yet, early treatment can reduce further damage, improve outcomes for patients, and reduce expensive late-stage treatments such as surgery.
Machine learning models are the perfect tool for simultaneous processing and classification, useful in assisting physicians to streamline the process and providing a valuable validation tool for improving accuracy.
The combined contribution of multiple human experiences as input into the models with the simultaneous processing power of a machine would create a powerful hub of combined experience and knowledge to be used in a single tool. This project will
  
 create and review various models to combine human knowledge with processing power with the goal of improving speed, accuracy, and patient outcomes in identification of spondylolisthesis, vertebral slippage.
Project
This is a supervised classification project using quantitative biomechanical data taken from patient x-rays to predict results as either "Normal" or "Abnormal". In this project abnormal indicates spondylolisthesis (slipped vertebra) of the lumbar spine specifically.
Data Source & Details
Data obtained from UCI Machine Learning Repository※ at the following link:
http://archive.ics.uci.edu/ml/datasets/Vertebral+Column#
  Normal 1 Target:
● ●
1) Pelvic Incidence
2) Pelvic tilt
3) Lumbar lordosis angle
4) Sacral slope
5) Pelvic radius
6) Grade of spondylolisthesis
Feature
Column (new name)
INCIDENCE TILT ANGLE SLOPE RADIUS DEGREE
The data is unbalanced, a stratified train-test split will be necessary. Resampling during hyper-parameter tuning is also suggested.
● Total 310 records:
binomial string: Abnormal/Normal 6 Features: Quantitative (integer) below:
210 Abnormal, 100

 Data Cleaning
● No empty values were found in this data set.
● No strings or unusual text were identified.
● Non-unique values were found but expected, nothing highly unusual, no changes.
● Target:​ ​ The string class was encoded for modeling purposes as:
○ 0 = Abnormal, ○ 1 = Normal
The violin plot below shows the mean, standard deviations, IQR and we can see that "degree" has potential outliers.
 Looking at the distribution in the plot below, we see normal distributions for all, however, the "degree" distribution is skewed to the right..
 
  Because this project utilizes medical data and due to the skewed nature of the "degree" feature I choose Tukey's (z-score) method to identify potential outliers. The chart above visualizes 3 potential outliers identified. Two are close to the remaining population while 1 is very from any neighboring point.
To make a determination of how to handle these points I would normally research how the data is collected and/or speak with experts involved in this project. Without this option, I researched the meaning behind the data. The image below demonstrates the "degree" feature which describes the amount of slippage or difference between 1 vertebra relative to another. This means 100% occurs when the vertebra is completely misaligned with adjacent vertebra . While infrequent, measurements > 150 are potentially valid measurements, however a measurement > 400, while possible, indicates an unlikely measurement or unusual event.
 
 Therefore I identified the point >400 to be an outlier. This record was removed from the dataset and data exploration was performed starting with correlation comparisons.
EDA
Correlations
  Left, a Pearson's correlation map shows a high correlation between "slope" and "incidence".
All are under the 90% limit and all are included in the model.

 A correlation plot, below, shows strong separation in the "degree" feature yet some overlap remains and indicates the need for the other features inclusion in the model.
All features show some separation but not complete separation.
 
 Hypothesis Testing
The correlation plot above displays a normal distribution of all features. The "degree" feature demonstrate the best separation yet some overlap still exists. Remaining features have clear overlap and a Null hypothesis test was performed to validate the statistical significance of the features relationship with the target.
Alpha was defined as >0.05%
H0 asserts:
There exists no difference between normal vs abnormal within any of the features (degree, incidence, slope, angle, tilt, radius).
A student t-test was performed on all features. Results are as follows:
All p-values were <0.05, failing the Null hypothesis proving statistically significant relationships exist for all features. Therefore we reject the null hypothesis, all features were proved useful for this project and included in models.
Deliverables
After cleaning there remained 309 records (209 Abnormal, 100 Normal).
The following variables were created and stored in csv files for use in ML models:
   ● Data​: ● Y​:
● ​X:​
6 Features, 1 Target
1 Target, encoded binomial
● 0 (abnormal)'
● 1 (normal)
6 quantitative Features:
● tilt, angle, slope, incidence, degree, radius

 Machine Learning
Method
● Stratified Train-Test Split, 30% test
● Resampling: SMOTE, ADASYN
● Parameter Tuning: GridSearch with KFold split
Models
● Logistic Regression
● Gradient Boost
● Support Vector Machine
● Random Forest
● KNearest Neighbors
● Naive Bayes
Results
A summary of accuracy scores below compare models using f1 as the scoring method:
            Model
logreg BGC SVM RandomForest KNN
Naive Bayes
SMOTE ADASYN Score Model 87.88% 85.71% 80.00% 73.02% 80.00% 77.61% 81.25% 81.16% 73.85% 73.85% 73.24% 72.22%
                                       Logistic Regression provided the best performance for both resampling methods. With a recall rate of 89 for normal and 97 for abnormal values, using a SMOTE resampling method, if a total of 100 abnormal results existed, we can expect 97 of these to be properly

 identified, for 100 normal results 89 would be found. ADASYN's performance was similar with a recall of 100 for abnormal and 84 for normal. Below is a summary of the Logistic Regression scores and confusion matrix.
SMOTE
 
 ADASYN
 Detailed results are contained in the addendum at the end of this report.

 ADDENDUM
Summary of scores by resampling method:
 
 Conclusion
While the Logistic Regression model demonstrated great performance in identifying x-ray results, All models performed similarly and clearly demonstrates the usefulness of machine learning to assist physicians in validation and determination of appropriate diagnosis.
In order to take advantage of the full possible uses of these technologies I would recommend the use of this model as a validation system initially, and periodic retraining of the model from all physician labeling of results which can improve with these inputs,
References
※(Dr. Henrique da Mota during medical residence period in the Group of Applied Research in Orthopaedics (GARA) of the Centre Medicao-Chirurgical de Radaptation des Massues, Lyon, France)
