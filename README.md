# Practice-Python
This repository contains practice Python exercises and exploritory data analysis  

# Bring the data into Python
For this particular project, I used Google Colab to test my python code. In order to import the data into Colab, I used the syntax:

from google.colab import files uploaded = files.upload()

I then used the following code in order to create a dataframe with this dataset df = pd.read_csv('student_python_task.csv')

# Understand what you have been given
Before starting any analysis, it is important to first look at the data to see what it involves. Using df.head() allows you to inspect the first few data points from the dataset. This is important to show you the column names so you can understand what information we are working with. Next, using df.info() will show you the amount of rows, columns and data types involved in the dataset.

# Data-quality check
The df.info() function used previously also shows that there is a missing data point located in the columns "name" and "class" and there are 2 missing data points in the column "gender". Before deleting the null value, you would need to know if the missing data points have been intentionally or accidentally excluded and if so, should this missing data be included to complete the records or should the records with null values be deleted.

# FILTERING THE DATA
I first wanted to filter the data to show the students with a mark greater than 70. This for example could be the pass mark and the code would be needed to show all students who had achieved a pass grade.

(df[df['mark']>70][['name', 'mark']])

# What is the typical student mark, and what are the lowest and highest marks?
Here I began to analyse using aggregation functions such as min, max, mean etc

Calculate the typical (mean) student mark:

typical_mark = df['mark'].mean() print(f"Average student mark {typical_mark:.2f}")

Calculate the lowest student mark:

lowest_mark = df['mark'].min() print(f"Lowest student mark: {lowest_mark}")

Calculate the highest student mark:

highest_mark = df['mark'].max() print(f"Highest student mark: {highest_mark}")

Calculate the median student mark:

median_mark = df['mark'].median() print(f"Median student mark: {median_mark}")

The median mark is good to use when there are outliers as it shows the middle result regardless of the extreme high or low values whereas the mean is easily distorted

# Compare groups
Here I used a short line of code to group together data points and count the total. The example here was the gender of the students in the dataset. This showed that the data used was quite an even split.

df['gender'].value_counts()

# Create a reusable output
Exporting results is important because you can return the completed task and exclude lots of unnecessary data to make the results much more readable and understandable. Here I created a dataframe which removed all unnecessary data and just kept student name and mark. I then exported this condensed dataframe into a new csv file.

student_test_scores_df = df[['student', 'test_score']] student_test_scores_df.to_csv('student_test_scores.csv', index=False)
