---
layout: post
title: Work Smarter
subtitle: Predict how much time an employee will need off
subtitle: Will I see them at the staff meeting?
image: /img/AliceBunnyClock.png
---

## The Data

## The Purpose
Employees are human beings, and we all know that can get complicated. So it's important for management to allow their staff to request time off for health or personal reasons when needed. In many cases the team is not affected in any way as long as adequate communication occurs. Still, there may be times when a supervisor may need to touch base with a team member, whether for a few minutes or perhaps a full length staff meeting. In some context, the number of hours requested off ultimately decides whether this task can occur. With the goal of estimating whether an employee is likely to be able to check in with their boss, a binary classification of the 'Absenteeism time in hours' column was engineered called 'HalfDayOnly'. When True, this column asserts that the number of hours requested off was 5 or fewer, thus leaving ample time for the employee to drop into the office in whatever form that is.

## Data Exploration
Baseline
Since the majority class frequency of column 'HalfDayOnly' is 60.9% which is both >= 50% and < 70%, I will be using accuracy as the evaluation metric.

## Data Engineering
For some perspective, I currently live in Colorado where cannabis is legal but tobacco is frowned upon, but I'm from West Virginia where cannabis is illegal and so is discriminating against an employee for using tobacco products. So assuming many people wouldn't be honest with their employer or insurance provider about their social smoking habits, I combined this column with 'Social Drinker' to list total 'Vices', then dropped both of those columns.

Rather than using the entire BMI range I converted this column to a binary class reading whether or not the employee is considered 'Overweight'. Dropping the 'Body mass index' column, in addition to the 'Weight', and 'Height' columns it was based off of helped to reduce leakage.

Since 'Service time' and 'Age' both increase at the same rate, I decided to combine them with 'Education' to portray the ratio of how much of their life an employee has spent with the company. A new employee will have a lower 'WorkToAge'rating than a more seasoned staff member.

Rather than using the number of hours requested off directly, I used that number to clarify an employee's ability to touch base with their boss. If the number of hours requested off was 5 or fewer, they would be expected in the office at some point. This established the target column 'HalfDayOnly' for a binary classification model.


## How is this model useful?
As disability rights become common work place discussion, it's important for the people making decisions to have some assurance they are making the right choice for their team. This prediction can be used to establish the liklihood an employee in a similar situation could manage a minimum threshold of work, versus being entirely unavailable for the work day. Even with data, it's important to consider that employees are human beings and each one is unique. Simply put, just because one person who has 2 kids and lives 45 minutes away only needed a half day for a dental appointment, doesn't mean every person would be able to get to work that day. It is up to the supervisor or Human Resource team to understand that this metric is one of Reasonability and requires some level of tact and compassion to be useful. The Question it answers is NOT "Can this employee come in for a staff meeting even though they specifically requested the day off?" but rather "Is it even reasonable for me to ask them to do so?"




