---
layout: post
title: Work Smarter
subtitle: Predict how much time an employee will need off
image:  img/AliceBunnyClockCorner2.png
---
## The Data
Acquired from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Absenteeism+at+work), this dataset outlines specific request offs made for one of 28 reasons, as well as personal information regarding additional factors that might contribute to employee absenteeism.

## The Purpose
Employees are human beings, and we all know that can get complicated. So it's important for management to allow their staff to request time off for health or personal reasons when needed. Still, there may be times when a supervisor may need to touch base with a team member, whether for a few minutes or perhaps a full length staff meeting. In some context, the number of hours requested off ultimately decides whether this task can occur.

With the goal of estimating whether an employee is likely to be able to check in with their boss, a binary classification of the 'Absenteeism time in hours' column was engineered called 'HalfDayOnly'. When True, this column asserts that the number of hours requested off was 5 or fewer, thus leaving ample time for the employee to drop into the office in whatever form that is.

![Target Bar Plot](https://raw.githubusercontent.com/iambrookedrake/iambrookedrake.github.io/master/img/Spr2TargetBar.png){: .center-block :}

## Data Exploration
For the baseline expectation, the majority class frequency of the binary column 'HalfDayOnly' being True is 60.9% which is both greater than 50% and less than 70%, so accuracy was used as the evaluation metric. Considering this data exists for instances of employees requesting time off, it was logical to assume that entries listing zero "0" Absent Hours could be removed as this was clearly incorrect data.

## Data Engineering

* Since cannabis legality is still a stateside issue, it's fair to assume that many people wouldn't be honest with their employer or insurance provider about their social smoking habits, I combined this column with 'Social Drinker' to list total 'Vices', then dropped both of those columns.
* Rather than using the entire BMI range I converted this column to a binary class reading whether or not the employee is considered 'Overweight' based on a [BMI>25](https://www.nhlbi.nih.gov/health/educational/lose_wt/BMI/bmicalc.htm). Dropping the 'Body mass index' column, in addition to the 'Weight', and 'Height' columns it was based off of helped to reduce leakage.
* Since 'Service time' and 'Age' both increase at the same rate, I decided to combine them with 'Education' to portray the ratio of how much of their life an employee has spent with the company. A new employee will have a lower 'WorkToAge'rating than a more seasoned staff member.
* Rather than using the number of hours requested off directly, I used that number to clarify an employee's ability to touch base with their boss. If the number of hours requested off was 5 or fewer, they would be expected in the office at some point. This established the target column 'HalfDayOnly' for a binary classification model.

![CoefficientsGraph](https://raw.githubusercontent.com/iambrookedrake/iambrookedrake.github.io/master/img/Spr2Coeff.png){: .center-block :}

## The Models
* The baseline using the majority class frequency from the training set produced a validation set accuracy of 68.7% on its own.
* Gradient Boosting model resulted in a validation accuracy of 80.3%.
* A Logistic Regression Model pipeline returned a validation accuracy of 83.9% and test accuracy of 79.2%


### How is this model useful?
The output of [this model](https://colab.research.google.com/drive/1kJoVkDwnhxshTntaIbsA6-FNswf7accV?usp=sharing) is a measure of whether an employee is more or less likely to be able to make an appearance at the office based on the information provided. This could be apapted for use by the employee themselves if they are planning a new or progressive healthcare treatment and aren't sure how much time they'll need off. 

It's important for the people making decisions to have some assurance they are making the right choice for their team. This prediction can be used to establish the liklihood an employee in a similar situation could manage a minimum threshold of work, versus being entirely unavailable for the work day. Even with data, it's important to consider that employees are human beings and each one is unique. Simply put, just because one person who has 2 kids and lives 45 minutes away only needed a half day for a dental appointment, doesn't mean every person would be able to get to work that day. 

It is up to the supervisor or Human Resource team to understand that this metric is one of Reasonability and requires some level of tact and compassion to be useful. The Question it answers is **NOT** "_Can this employee come in for a staff meeting even though they specifically requested the day off_?" but rather "_Is it even reasonable for them to be expected to do so_?"

![Test Results](https://raw.githubusercontent.com/iambrookedrake/iambrookedrake.github.io/master/img/Spr2ShaplyTest.png){: .center-block :}


