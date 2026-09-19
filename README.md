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
