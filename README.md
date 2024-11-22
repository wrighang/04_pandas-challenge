# 04_pandas-challenge: PyCitySchools

[PyCitySchools.ipynb Completed Assignment](.PyCitySchools/PyCitySchools.ipynb)

## Background
You are the new Chief Data Scientist for your city's school district. In this capacity, you'll be helping the school board and mayor make strategic decisions regarding future school budgets and priorities.

As a first task, you've been asked to analyze the district-wide standardized test results. You'll be given access to every student's math and reading scores, as well as various information on the schools they attend. Your task is to aggregate the data to showcase obvious trends in school performance.

## Requirements

## District Summary
- Calculate the total number of unique schools
- Calculate the total number of students
- Calculate the total budget
- Calculate the average math score
- Calculate the average reading score
- Calculate the percentage of students who passed math
- Calculate the percentage of students who passed reading
- Calculate the percentage of students who passed both math and reading
- Create a new DataFrame for the above calculations called `district_summary`

## School Summary
- Select the school type
- Calculate the total student count
- Calculate the per capita spending
- Calculate the average test scores
- Calculate the number of schools with math scores of 70 or higher
- Calculate the number of schools with reading scores of 70 or higher
- Calculate the schools that passed both math and reading with scores of 70 or higher
- Calculate the passing rates
- Create a new DataFrame for the above calculations called `per_school_summary`

## Highest-Performing Schools by Percentage of Overall Passing
- Sort the schools by % Overall Passing in descending order
- Save the results to a DataFrame called `top_schools`
- Display the first 5 rows

## Lowest-Performing Schools by Percentage of Overall Passing
- Sort the schools by % Overall Passing in ascending order
- Save the results to a DataFrame called `bottom_schools`
- Display the first 5 rows

## Math Scores by Grade
- Separate the data by grade
- Group by "school_name" and calculate the mean
- Select only the `math_score`
- Combine the scores into a single DataFrame called `math_scores_by_grade`

## Reading Scores by Grade
- Separate the data by grade
- Group by "school_name" and calculate the mean
- Select only the `reading_score`
- Combine the scores into a single DataFrame called `reading_scores_by_grade`

## Scores by School Spending
- Use `pd.cut` to bin data by the spending ranges
- Calculate the averages for each bin
- Create `spending_summary` DataFrame using the binned and averaged spending data

## Scores by School Size
- Use `pd.cut` to bin data by school size
- Calculate the averages for each bin
- Create `size_summary` DataFrame using the binned and averaged size data

## Scores by School Type
- Group the `per_school_summary` DataFrame by "School Type" and calculate the averages
- Select the new column data
- Create a new DataFrame called `type_summary` using the new column data

## Written Report
- Present a cohesive analysis summarizing the findings
- Draw two correct conclusions or comparisons from the calculations

  -----------------------------------


Overall, this challenge involved me referencing previous activities, if needed, to find examples of the methods I planned to use. After completing the challenge, I created a separate copy of my work for two reasons: a) to ensure my final results were saved and secure and b) to experiment with other methods we’ve learned in class that weren’t part of the original assignment. Additionally, I had a 3-hour study group on Sunday, October 12th, which only Amy Hanks attended. During the 3 hour session, I helped walk her through the challenge, which reinforced my own understanding by allowing me to talk through what I had learned. While guiding her, I also discovered an error in my code related to the per_school_budget, which I’ve noted below.

Areas I Noted that I Noted During the Assignment:
1. School Summary Section
    * Initially, I didn’t include .sort_index() at the end of the below code. When I reviewed the DataFrame output futher down the assignment, I noticed the school names and types were alphabetized/sorted. I traced the sorting back to the school_types code. I had to look up the proper syntax for sorting an index, and once I ran it, the output matched the expected result. Here’s the code that caused the issue:
    school_types = school_data_df.set_index(["school_name"])["type"].sort_index()

    * For the below following code, I initially used .sum for calculating per_school_budget. However, after reviewing the later output, I realized the use of .sum was incorrect since the budget total had already been solved earlier in the code. I corrected this by changing it to .mean, which produced the expected result:
    per_school_budget = school_data_complete_df.groupby("school_name")["budget"].mean()


2. Highest-Performing Schools (By % Overall Passing) / Bottom-Performing Schools (By % Overall Passing) Section
    * I had to look up the code structure for sorting the data to determine the highest- and lowest-performing schools by overall passing percentage.

3. Analysis 
    * I outlined my initial analysis below. To modify my approach and write like a career analyst, I used assistance from ChatGPT referencing my inital analysis. The guidance I received was to include a detailed analysis that breaking down key insights such as trends, comparisons, and any outliers or unexpected findings. After the detailed analysis, explain what the data means or suggests. This will help me not only with this challenge, but with future data analysis reporting.
    When comparing my intial analysis with the revised version on the .ipynb file, that I had a good first draft, I improved the structure of the the written sections and I included and explaination of what the data suggests. 
    
---Two observable trends based on the data:
% Overall Passing
1- Charter schools, which mostly have a medium school size, were the highest performers with a '% Overall Passing' ranging from 97.04 to 95.85. In contrast, District schools, all with a large school size, had the lowerest performance, with a  '% Overall Passing' ranging from 81.93 to 80.22. Overall, by school size, medium size schools have a higher "% Overall Passing" rate at 90.62. 

Spending
2- District shools, while having low performance, received the higher end of 'Spending Ranges (Per Student)' ranging from $630-680. Charter schools, the highetst performers, recieved the lower range of 'Spending Ranges (Per Student)' at <$585-$645. 

Charter schools are achieving higher performace despite having a lower spend per student. District schools will higher spend per student may not be allocating their spend in the right areas to achieve better academic results. 
