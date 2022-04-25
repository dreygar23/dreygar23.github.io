# Predicting Future-Term Student Performance Based on Historical Enrollment Data

## Abstract

The higher education sector has vast amounts of unexplored data that can be used to drive decision making and better inform student success initiatives for undergraduate students. Student success can be measured objectively by using historical enrollment data to predict future-term undergraduate course outcomes for students enrolled in a degree seeking capacity at a higher education institution. The objective of this project is to predict whether a student will pass or fail an undergraduate course based on historical enrollment attributes, demographic data, and specific course grades. This information has the potential to facilitate the development of targeted student success programs to help students proactively by providing them with the support and resources they need to succeed. 

## Background

Student performance in undergraduate courses is important not only for the purpose of pushing the needle on a metric but also due to the impact that this first exposure to college has on the future success of a learner. Research shows that the drop-out rate for undergraduate college students in the United States is 40%, with college freshmen and sophomores making up 30% of that rate. One of the reasons stated for dropping out of college is being unprepared for the academic workload that the student is required to take. These students are then discouraged and delayed in their academic careers by having to take remedial courses which often leads to financial impacts and late graduation [3]. It is for this reason that by focusing on student success initiatives will not only lead to a more prepared student overall but also to an increase in BOG metrics as an effect of good student performance. 

## Motivation

Focusing on undergraduate student success is important to ensure that the learner is comfortable with college-level course work. This can be achieved by putting in place a pro-active approach to course enrollment as well providing those students who need support with access to the appropriate resources. However, the only way to do this is to be able to identify those students who are at risk of failing a course at the time of enrollment rather than waiting for end-of-term course results. By placing the point of intervention prior to the actual failing of a course, it allows the university to allocate the appropriate resources and personnel to help the student or provide an alternate option with a higher chance of success. This will not only aid students be better prepared but will also help the university boost metrics based on course-performance. This project aims to utilize historical enrollment data and course-specific grades to predict future-term student course performance by classifying them into a pass or fail category.

## Dataset

The raw dataset consisted of 637,327 unique student/course pairings with 48 attributes. This included 38,738 unique undergraduate students with 2,899 different courses across the span of 17 unique enrollments terms running from Fall 2014 to Fall 2021. For the purposes of this project, only three colleges are examined and only two departments within each of these colleges are part of the experiment.

<img width="470" alt="image" src="https://user-images.githubusercontent.com/48109080/165015564-259da16b-4cbd-47d7-996f-8e57a9e8cd11.png">
_Student demographics_

<img width="479" alt="image" src="https://user-images.githubusercontent.com/48109080/165015572-7e20c3ae-cb05-4f7b-8ae2-45baedfc7950.png">
_Course highlights_

## Implementation 

The experimental approach is performed in four stages as shown in the figure below.

<img width="438" alt="image" src="https://user-images.githubusercontent.com/48109080/165015632-59d60310-51e4-43c6-831b-afcfa0af6a73.png">

## Attribute Sets and Algorithms

The model building and testing stage of the implementation of this project was a two-phased approach. The first phase consisted of selecting the set of attributes that would perform the best when attempting to predict future-term outcomes. The second phase consisted of using the selected set of attributes to test machine learning algorithms and select the best performing algorithm for the task at hand.

<img width="376" alt="image" src="https://user-images.githubusercontent.com/48109080/165015723-77d303cd-fb37-41f1-8b32-01fc372a40ff.png">

## Results

### Attribute Set Selection

The average overall scores across all 24 courses test of the first phase of the model building process are summarized in the figure below, which shows both the evaluation metric (F1 score for the positive class as f1_pos) as well as the F1 macro average (f1_macro) for context. 

<img width="234" alt="image" src="https://user-images.githubusercontent.com/48109080/165015789-f7bc8496-5a4b-42b3-b561-97973e6c73e0.png">


### Model Selection

After selecting the best performing attribute set, this was used to test the three ML algorithms in Step Two. All three ML algorithms underwent hyperparameter tuning and cross-validation using SciKit-learn’s GridSearchCV. For every cross-validation step in this implementation, it was always ensured that the appropriate validation set was used to avoid data leakage and overly optimistic training and validation scores.
The overall average scores across all 24 courses tested are quickly summarized in the figure below by model and data set (training vs validation vs testing). 

<img width="363" alt="image" src="https://user-images.githubusercontent.com/48109080/165015943-64e1ba57-dba9-4099-860a-9335da02398b.png">

_Comparison of 3 ML algorithms tested on the Enriched Course Specific Model_

Metric	Baseline Dummy Classifier
- f1_positive	0.054023
- f1_macro	0.500267

## Feature Importances 

<img width="426" alt="image" src="https://user-images.githubusercontent.com/48109080/165016058-40f9e821-ac54-4404-bd6d-6e469e1c247f.png">
_Using RFE_


<img width="251" alt="image" src="https://user-images.githubusercontent.com/48109080/165016066-469ca3ba-0af3-4b14-a1fe-40778591883a.png">
_ANOVA_

## Final Model with Selected Features

<img width="233" alt="image" src="https://user-images.githubusercontent.com/48109080/165016109-649568e8-f8a3-4790-b996-b291df9672c1.png">

## Findings

In summary there were four key findings as a result of this experiment that focused on addressing the questions posed by each of the two objectives. 

1.	The best attribute set for predicting future-term student outcomes is the Enriched Course Specific model w/selected features. The sparse course matrix of pass/fail outcomes was out performed by the more complex set of attributes during testing.
2.	The best performing machine learning algorithm for the course outcome classification task is the AdaBoost mode with Decision Trees as its base classifier. This model was able to obtain the highest F1 test score for the positive class and the highest AUC score, making it the most robust out of the three algorithms tested
3.	The features identified as important in this experiment ranged from student GPA to credits attempted, however it was evident that student aggregate enrollment attributes are very informative when attempting to predict success in future-term undergraduate courses
4.	It is relevant to point out that various aggregate enrollment attributes centered around UCC and Gateway courses, and these were identified as relevant when attempting to predict success in future-term undergraduate courses


### Author: Andrea Garcia 

