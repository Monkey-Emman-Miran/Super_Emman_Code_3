## <center> __University of Santo Tomas – Faculty of Engineering Electronics Engineering Department__ </center>
## <center> __ECE 2112: Advanced Computer Programming and Algorithms__ </center>
# <center> __EXPERIMENT 4: DATA WRANGLING AND DATA VISUALIZATION__ </center> 
#### Emmanuelle D.G. Miran| 2ECE-C
## **I.** Intended Learning Outcomes
1. Filter tabular data using several categorical and numerical conditions;
2. Construct focused DataFrames by selecting relevant features;
3. Summarize the relationship between categorical features and a numerical variable; and
4. Communicate a data comparison using clear and correctly labeled plots.
## **II.** Panda and Matplot Initialization | Average Setup
```python
import pandas as pd
mp = pd.read_excel('board2.xlsx')
mp
```
```python
import matplotlib.pyplot as plt
```
```python
mp['Average'] = mp[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)
```
## **III.** Programming Problems
>  ##  **A.** VISAYAS COMMUNICATION DATAFRAME
>Create a DataFrame named VisComm containing students whose Hometown is Visayas and whose Track is Communication. Retain only these columns, in the stated order: Name, Gender, Math, Electronics, Average<br><br>
>Display the resulting DataFrame and its number of rows. Both filtering conditions must be applied to
the source dataset before the columns are selected.
> ## Explanation

>>For this **Programming Assignment**, there are a few things that we need to handle and initialize to even attempt to accomplish any of the programming problems. First off, we need to set up Panda to access the original Excel file and convert it into the **Panda Dataframe**. Next, we need to set up **Matplotlib**, which would allow us to make a graph for the third Programming Problem for later. Lastly, we need to create a new column in the data frame; this column will contain the average grade for each student from the original data frame we are able to do this because when we used the function ***[Average]*** to create a new column named as such, and we use the function [].mean to get the mean/average of all the rows indicated in the [], and lastly the ***axis=1*** will ensure this will happen for each row of student. With all these setups in place, we can finally start solving the programming assessments.<br><br>

>>For this **Programming Problem**, we primarily use one function to solve this problem. The instructions indicated that we are asked to create a DataFrame called **Viscom**. To create the DataFrame called **VisCom**, we use the function ***mp[mp['Hometown'] == 'Visayas'] & (mp['Track'] == 'Communication')][['Name', 'Gender', 'Math', 'Electronics', 'Average']]***. The inner part, **mp['Hometown'] == 'Visayas'**, checks every row in the Hometown column and returns True if the value matches "Visayas" and False if it doesn't. When we place all this inside **mp[]**, the dataframe only keeps the ones that were returned as True. This is also the same case for the **(mp['Track'] == 'Communication')**, this function searches the Track column for every student that was listed down as **Communication**. Lastly, the function **['Name', 'Gender', 'Math', 'Electronics', 'Average']** simply makes sures that the only columns that displayed were the ones inputted inside **[]**.<br><br>
>>The function ***len()*** returns the number of rows in the DataFrame, which is 5.

> ## Code & Outputs
```python
VisComm = mp[(mp['Hometown'] == 'Visayas') & (mp['Track'] == 'Communication')][['Name', 'Gender', 'Math', 'Electronics', 'Average']]
VisComm
```
```
VisComm DataFrame:
    Name  Gender  Math  Electronics  Average
10  S11  Female    48           56    54.75
11  S12    Male    89           67    76.00
17  S18    Male    81           40    63.50
21  S22  Female    64           39    62.50
27  S28    Male    85           53    67.75
```
```python
print("Number of rows in VisComm:", len(VisComm))
```
```
Number of rows in VisComm: 5
```
>  ##  **B.** VISAYAS FEMALE DATAFRAME
>Create a second DataFrame named VisFemale containing students whose Hometown is Visayas and
whose Gender is Female. Retain only: Name, Track, GEAS, Electronics, Average<br><br>
>Display VisFemale. Then display only the rows of VisFemale whose Average is at least 60. Do not overwrite VisFemale when performing this second filter.
> ## Explanation

>>For this **Programming Problem**, we are asked to create a second DataFrame named **VisFemale** where we only include students who's Hometown is Visayas and Gender is Female.

>>For this **Programming Problem**, we can easily reuse the functions we used from the previous problem, but we replace the function **(mp['Track'] == 'Communication')** with the function **(mp['Gender'] == 'Female')**. The reasoning for this is because we are no longer asked to find students from Visayas who has the strand of Communication; we are instead asked to find students from **Visayas** who's gender is **Female**. Next requirement of this problem is that we are to display only the columns **Name, Track, GEAS, Electronics, Average**, for this, we can use the function **'Name', 'Track', 'GEAS', 'Electronics', 'Average']** as this would allow the DataFrame to retain only these columns.<br><br>
>>As a filter to only display the students who has an Average that is at least 60. We use the function ***VisFemale = VisFemale1[VisFemale1['Average'] >= 60]***. This takes care of two things: firstly, the function **VisFemale1['Average'] >= 60**, which checks every row in the Average column and returns True if the value is 60 or higher and False if it isn't. We use >= because the instructions say "at least 60", which includes 60 itself, then we put this all inside **VisFemale1[]** so it would only display the rows that were returned as True. Lastly we use **VisFemale =** si the name of this DataFrame is defined as VisFemale.

> ## Code & Outputs
```python
VisFemale1 = mp[(mp['Hometown'] == 'Visayas') & (mp['Gender'] == 'Female')][['Name', 'Track', 'GEAS', 'Electronics', 'Average']]
VisFemale = VisFemale1[VisFemale1['Average'] >= 60]
VisFemale
```
```
VisFemale DataFrame:
    Name             Track  GEAS  Electronics  Average
5    S6  Microelectronics    86           45    75.50
20  S21  Microelectronics    68           51    68.50
21  S22     Communication    89           39    62.50
25  S26   Instrumentation    83           47    65.75
```
>  ##  **C.** Category-Average Visualization
>Examine how the recorded Average differs across the three categorical features Track, Gender, and Hometown.
>>**A.** For each feature, compute the mean of Average for every category using Pandas.<br>
>>**B.** Display the three summary tables.<br>
>>**C.** Create one figure containing three bar charts: mean Average by Track, by Gender, and by Hometown<br>
>>**D.** Below the figure, write three concise statements identifying the category with the highest sample mean for each feature<br>
>**Interpretation rule**: Describe the observed dataset only. A difference in group means does not, by itself, establish that a feature causes a higher board-exam score.
> ## Explanation

>>For this **Programming Problem**, we are asked to compare the mean across three categorical features (Track, Gender, and Hometown), and we are to use **Panda** to compute the mean, and we are to display these means as bar charts.<br><br>
>> To compute the means, let's first use the first function used in the solution ***mp.groupby('Track')['Average'].mean().reset_index().***. The first part, **mp.groupby('Track')**, splits the DataFrame into groups (Communications, Instrumentation, and Microelectronics), one for each unique value in the Track column. Then ['Average'] selects only the Average column of each group, and .mean() calculates the mean of every group. Lastly, .reset_index() turns the group labels back into a regular column, so that the result is a clean DataFrame with two columns (the category and its mean) instead of a Series indexed by category. This function is repeated for **Gender** and **Hometown**, we simply have to replace **'Track'** in the function **mp.groupby('Track')**. <br><br>
>>To create the figure with three bar charts, we first use ***plt.subplots(1, 3, figsize=(16, 5), sharey=True)***. This creates one figure with 1 row and 3 columns of charts, stored in axes, and figsize sets the overall size of the figure. The sharey=True makes all three charts use the same y-axis scale, which is important because it lets us fairly compare the bars across the charts. We use the function ***axes[].bar(track_mean[''], track_mean['Average'], color='color', edgecolor='color')*** to generate the graphs that we need to be displayed. In the function, **axes[]** refers to the number of the chart and the order in which they are to be displayed. The function **track_mean['Track'], track_mean['Average']** takes from the previous part of this problem, where **track_mean['Track']** takes the name of Track, and **track_mean['Average']** takes the average of the Track; this also controls the height of the graph. The functions **color='color', edgecolor='color'** simply control the color of the bar graph itself and its border colors. The function ***axes[].set_title('')*** puts a title on the selected axes, **axes[].set_xlabel('')** sets a label on the x axis of the axes chosen, and **axes[].set_ylabel('')** sets a label on the y axis on the chosen axes. <br><br>
>>For the last part, we use **8track_mean.loc[track_mean['Average'].idxmax()]***. The inner part, **track_mean['Average'].idxmax()**, returns the index label of the row that has the highest value in the Average column. When we place this inside .loc[], we get the entire row of that category, which tells us which Track has the highest mean. We also do the same  **Gender** and **Hometown**.  Then, the **print(f"...")** statements build a sentence for each feature. The curly braces {} insert the values directly into the text: **.loc[..., 'Track']** gives the name of the top category, and .max() gives its mean Average score. We do this so we don't have to repeat a function to display same thing by hand.

> ## Code & Outputs
```python
track_mean = mp.groupby('Track')['Average'].mean().reset_index()
gender_mean = mp.groupby('Gender')['Average'].mean().reset_index()
hometown_mean = mp.groupby('Hometown')['Average'].mean().reset_index()

print('**Average Mean by Track**')
display(track_mean)
print('**Average Mean by Gender**')
display(gender_mean)
print('**Average Mean by Hometown**')
display(hometown_mean)
```
```
**Average Mean by Track**
               Track  Average
0     Communication   67.975
1   Instrumentation   65.225
2  Microelectronics   67.500
```
```
**Average Mean by Gender**
    Gender    Average
0  Female  66.616667
1    Male  67.183333
```
```
**Average Mean by Hometown**
    Hometown    Average
0     Luzon  68.083333
1  Mindanao  66.678571
2   Visayas  65.750000
```
```python
fig, axes = plt.subplots(1, 3, figsize=(16, 5), sharey=True)

axes[0].bar(track_mean['Track'], track_mean['Average'], color='aquamarine', edgecolor='black')
axes[0].set_title('Mean Average by Track')
axes[0].set_xlabel('Track')
axes[0].set_ylabel('Mean Average Score')

axes[1].bar(gender_mean['Gender'], gender_mean['Average'], color='salmon', edgecolor='black')
axes[1].set_title('Mean Average by Gender')
axes[1].set_xlabel('Gender')

axes[2].bar(hometown_mean['Hometown'], hometown_mean['Average'], color='mediumpurple', edgecolor='black')
axes[2].set_title('Mean Average by Hometown')
axes[2].set_xlabel('Hometown')

plt.tight_layout()
plt.show()
```
```
**GRAPH**
```
```python
track_mean.loc[track_mean["Average"].idxmax()];
gender_mean.loc[gender_mean["Average"].idxmax()];
hometown_mean.loc[hometown_mean["Average"].idxmax()];

print(f"1. Track: The {track_mean.loc[track_mean['Average'].idxmax(), 'Track']} track recorded the highest sample mean Average score ({track_mean['Average'].max()}).")

print(f"2. Gender: {gender_mean.loc[gender_mean['Average'].idxmax(), 'Gender']} students recorded the highest sample mean Average score ({gender_mean['Average'].max()}).")

print(f"3. Hometown: Students from {hometown_mean.loc[hometown_mean['Average'].idxmax(), 'Hometown']} recorded the highest sample mean Average score ({hometown_mean['Average'].max()}).")
```
```
1. Track: The Communication track recorded the highest sample mean Average score (67.975).
,2. Gender: Male students recorded the highest sample mean Average score (67.18333333333334).
,3. Hometown: Students from Luzon recorded the highest sample mean Average score (68.08333333333333).
```
README File Version History:

```September 17, 2026 ```- Initial README.md was uploaded<br>
```September 24, 2026``` - Fixed formatting, and modified the explanations to the code.
