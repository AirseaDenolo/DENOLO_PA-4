# Programming Assignment #4 - DATA WRANGLING AND DATA VISUALIZATION
### Overview
This repository contains a Python Jupyter notebook that performs data wrangling and visualization on the dataset of ECE board exam results. The objective is to analyze the data and gain insights using techniques such as filtering, cleaning, and visual storytelling.

## ECE BOARD EXAM PROBLEM
### Problem Statement
1. Data Wrangling:

- Instru DataFrame: Create a DataFrame with students from the "Instrumentation" track, who live in "Luzon" and scored over 70 in Electronics. Include Name, GEAS, and Electronics >70.
- Mindy DataFrame: Create a DataFrame with female students from "Mindanao" who have an average score of 55 or more. Include Name, Track, Electronics, and Average >=55.
2. Data Visualization:

- Create visualizations to show how factors like the chosen track, gender, and hometown influence the average grade.

## Code Implementation
```
#Import necessary library
import pandas as pd
#Load the data from an Excel file into a DataFrame
df = pd.read_excel('board2.xlsx')
#Calculate the average of numeric columns for each row and create a new column 'Average'
df['Average'] = df.mean(numeric_only=True, axis=1)
df
```
![image](https://github.com/user-attachments/assets/f8965594-ac8c-4b82-a632-8b060bbfe04a)
```
#Filter the DataFrame for students in the 'Instrumentation' track from 'Luzon' and with 'Electronics' score greater than 70, selecting specific columns
Instru = df.loc[(df.Track=='Instrumentation') & (df.Hometown=='Luzon') & (df.Electronics>70), ['Name', 'GEAS', 'Electronics']]
Instru
```
![image](https://github.com/user-attachments/assets/89e958ff-a63d-467d-8315-0bcd4110149a)
```
#Filter the DataFrame for female students from 'Mindanao' with an average score of 55 or higher, selecting specific columns
Mindy = df.loc[(df.Hometown=='Mindanao') & (df.Gender=='Female') & (df.Average>=55), ['Name', 'Track', 'Electronics', 'Average']]
Mindy
```
![image](https://github.com/user-attachments/assets/8d085dc3-6f06-4081-805b-561bf6e00b05)

```
#Import matplotlib library for data visualization
import matplotlib.pyplot as plt
#Create a bar graph (5x6 inches) showing average grades by college track, with labeled axes and a title
plt.figure(figsize=(5,6))
plt.bar(df['Track'], df['Average'])
plt.xlabel('College Track')
plt.ylabel('Average Grade')
plt.title('Table 1.1: A bar graph showing the relationship of chosen track in college to average grade.')
```
![image](https://github.com/user-attachments/assets/019c73b2-c8bb-48cc-9693-c2d6a32cf928)
```
#Create a second bar graph (5x6 inches) showing average grades by gender, with labeled axes and a title
plt.figure(figsize=(5,6))
plt.bar(df['Gender'], df['Average'])
plt.xlabel('Gender')
plt.ylabel('Average Grade')
plt.title('Table 1.2: A bar graph showing the relationship of gender to average grade.')
```
![image](https://github.com/user-attachments/assets/4dcf7ebb-d48d-413b-ab1a-293eb7dbfa78)
```
#Create a third bar graph (5x6 inches) showing average grades by hometown, with labeled axes and a title
plt.figure(figsize=(5,6))
plt.bar(df['Hometown'], df['Average'])
plt.xlabel('Hometown') 
plt.ylabel('Average Grade')
plt.title('Table 1.3: A bar graph showing the relationship of hometown to average grade.')
```
![image](https://github.com/user-attachments/assets/75a0d07f-b076-43b4-8094-bc0e58dec82f)

## Code Explanation
The main steps in the notebook:

1. Load Dataset: The dataset is loaded from the Excel file using pandas.read_excel.
2. Data Wrangling: Filter and create new DataFrames based on certain conditions:
- Instru: Filter for students in the Instrumentation track, Electronics score > 70, and hometown in Luzon.
- Mindy: Filter for female students from Mindanao with an average score >= 55.
3. Visualization: Visualize the relationship between average score and other features such as track, gender, and hometown using bar graphs.

## Author
Airsea Grace B. Denolo
