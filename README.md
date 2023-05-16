# Ex-07-Data-Visualization-

## AIM
To Perform Data Visualization on the given dataset and save the data to a file. 

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4
Apply data visualization techniques to identify the patterns of the data.

# CODE:

# Data Pre-Processing
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
df=pd.read_csv("/content/Superstore.csv",encoding="ISO-8859-1")
df
df.isnull.sum()
df.info()
df.describe()
```

# Which Segment has Highest sales?

```
sns.lineplot(x="Segment",y="Sales",data=df,marker='o')
plt.title("Segment vs Sales")
plt.xticks(rotation = 90)
plt.show()

sns.barplot(x="Segment",y="Sales",data=df)
plt.xticks(rotation = 90)
plt.show()
```

# Which City has Highest profit?

```
df.shape
df1 = df[(df.Profit >= 60)]
df1.shape

plt.figure(figsize=(30,8))
states=df1.loc[:,["City","Profit"]]
states=states.groupby(by=["City"]).sum().sort_values(by="Profit")
sns.barplot(x=states.index,y="Profit",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("City")
plt.ylabel=("Profit")
plt.show()
```

# Which ship mode is profitable?

```
sns.barplot(x="Ship Mode",y="Profit",data=df)
plt.show()

sns.lineplot(x="Ship Mode",y="Profit",data=df)
plt.show()

Sales of the product based on region.

states=df.loc[:,["Region","Sales"]]
states=states.groupby(by=["Region"]).sum().sort_values(by="Sales")
sns.barplot(x=states.index,y="Sales",data=states)
plt.xticks(rotation = 90)
plt.xlabel=("Region")
plt.ylabel=("Sales")
plt.show()-

df.groupby(['Region']).sum().plot(kind='pie', y='Sales',figsize=(6,9),pctdistance=1.7,labeldistance=1.2)

Find the relation between sales and profit.

df["Sales"].corr(df["Profit"])

df_corr = df.copy()
df_corr = df_corr[["Sales","Profit"]]
df_corr.corr()

sns.pairplot(df_corr, kind="scatter")
plt.show()
```

# Segment

```
grouped_data = df.groupby('Segment')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
ax.legend()
plt.show()

```

# City

```
grouped_data = df.groupby('City')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('City')
ax.set_ylabel('Value')
ax.legend()
plt.show()
```


# States

```
grouped_data = df.groupby('State')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('State')
ax.set_ylabel('Value')
ax.legend()
plt.show()
```


# <--Segment and Ship Mode -->
```
grouped_data = df.groupby(['Segment', 'Ship Mode'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index='Segment', columns='Ship Mode', values=['Sales', 'Profit'])
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
pivot_data.plot(kind='bar', ax=ax)
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
plt.legend(title='Ship Mode')
plt.show()


Segment, Ship mode and Region

grouped_data = df.groupby(['Segment', 'Ship Mode','Region'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index=['Segment', 'Ship Mode'], columns='Region', values=['Sales', 'Profit'])
sns.set_style("whitegrid")
sns.set_palette("Set1")
pivot_data.plot(kind='bar', stacked=True, figsize=(10, 5))
plt.xlabel('Segment - Ship Mode')
plt.ylabel('Value')
plt.legend(title='Region')
plt.show()

```

## OUPUT

Data Pre-Processing

![image](https://github.com/Hemasonica774/Ex-08-Data-Visualization-/assets/118361409/e08376b2-30f7-410f-94fb-0396a1c1b4d3)

![image](https://github.com/Hemasonica774/Ex-08-Data-Visualization-/assets/118361409/aaa6afb8-ae1b-49cd-a7a5-1e6101a428f6)

![image](https://github.com/Hemasonica774/Ex-08-Data-Visualization-/assets/118361409/ee0edf8f-e674-4662-b839-05794aaf576e)

![image](https://github.com/Hemasonica774/Ex-08-Data-Visualization-/assets/118361409/430b9c75-49b1-48d9-9c2b-f19f1ef30f4e)


# Which Segment has Highest sales?

![image](https://github.com/Hemasonica774/Ex-08-Data-Visualization-/assets/118361409/98865336-2ba1-4025-bd83-1960374afdd1)

![image](https://github.com/Hemasonica774/Ex-08-Data-Visualization-/assets/118361409/8ef74020-859f-46bf-9925-acb51617bfac)


# Which City has Highest profit?

![image](https://github.com/Hemasonica774/Ex-08-Data-Visualization-/assets/118361409/2ed63905-4c35-4922-b1cf-4b8284be19bf)

Which ship mode is profitable?

![image](https://github.com/Hemasonica774/Ex-08-Data-Visualization-/assets/118361409/d39d8d04-75a5-4a77-931d-180d462fb281)


Sales of the product based on region.
![image](https://github.com/Hemasonica774/Ex-08-Data-Visualization-/assets/118361409/ab7ec56f-d542-4de2-b7b1-1248f287aded)

![image](https://github.com/Hemasonica774/Ex-08-Data-Visualization-/assets/118361409/c51236e8-917e-446e-ad6a-1d0cace118a9)


Find the relation between sales and profit

![image](https://github.com/Hemasonica774/Ex-08-Data-Visualization-/assets/118361409/555c281b-6659-4976-aa3f-b52e2e5da20b)


Find the relation between sales and profit based on the following category.

Segment

![image](https://github.com/Hemasonica774/Ex-08-Data-Visualization-/assets/118361409/e918829a-811e-4fa1-86b5-c56cd9015d93)


City

![image](https://github.com/Hemasonica774/Ex-08-Data-Visualization-/assets/118361409/bcb5098f-14c6-4aaf-a4ac-50ddafe93239)


States

![image](https://github.com/Hemasonica774/Ex-08-Data-Visualization-/assets/118361409/44d9d4b2-6725-4155-ba64-bf2476a8228f)


Segment and Ship Mode

![image](https://github.com/Hemasonica774/Ex-08-Data-Visualization-/assets/118361409/1ff49213-75af-459d-b35f-0e17cb4c259f)


Segment, Ship mode and Region

![image](https://github.com/Hemasonica774/Ex-08-Data-Visualization-/assets/118361409/15fa86be-500f-477d-ae62-6cb3c1570a6e)


# Result:

Thus, Data Visualization is performed on the given dataset and save the data to a file.




