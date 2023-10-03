# Analyzing Road Accidents Data

[Link for the dashboard is here](https://public.tableau.com/app/profile/sridhar.kadhiri/viz/Road_accidents_Dashboard/Dashboard1?publish=yes) 

    - below explanation is a part of EDA_on_Vehicle_Accidents.ipynb
## Introduction

In this project, we analyze road accident data using Python and various data visualization libraries like Pandas, NumPy, Matplotlib, and Seaborn. The dataset contains information about different aspects of road accidents, such as accident severity, vehicle types, road conditions, and weather conditions.

## Data Preprocessing

First, we loaded the dataset and performed initial data exploration:

```python
import pandas as pd
import numpy as np

# Load data
data = pd.read_csv("accident_data.csv")

# Check data info
data.info()

# Convert "Accident Date" to datetime
data["Accident Date"] = pd.to_datetime(data["Accident Date"], format="%d-%m-%Y")
```

## Data Exploration

We explored various columns to understand the unique values and their counts:

```python
# Explore unique values in non-integer columns
for column in data.columns:
    if type(data[column][1]) == str:
        print(data[column].value_counts())
        print("No of Unique values: ", len(data[column].value_counts()))
        print("*" * 30)
```

## Data Visualization

We created visualizations to understand accident trends over the years and the impact of different factors on accidents.

1. **Accidents Over Years:**
   - Created a bar chart showing the total number of accidents each year.
   
   ![image](https://github.com/SridharKadhiri/Undersatanding-Road-Accidents/assets/90100318/b9dd1707-f127-44e9-84b4-6672f4843d7d)




2. **Year-over-Year (YoY) Accident Growth:**
   - Calculated YoY growth percentage for accidents and created a bar chart.
   
   ![image](https://github.com/SridharKadhiri/Undersatanding-Road-Accidents/assets/90100318/3146be5e-c0e6-4e15-a75b-71680edb075e)



3. **Casualties Over Years:**
   - Plotted the total number of casualties each year.
   
   ![image](https://github.com/SridharKadhiri/Undersatanding-Road-Accidents/assets/90100318/056bfbbd-0c9e-49e5-aef5-2b6f4a248ffe)




4. **Fatal Accidents Over Years:**
   - Analyzed the number of fatal accidents and their YoY growth.
   
   ```python
   print("total fatal Accidents :",len(df2[df2["Accident_Severity"] == "Fatal"]))
   year_wise_fatal_accidents  = df2[df2["Accident_Severity"] == "Fatal"].groupby("years")["Index"].count().reset_index()
   year_wise_fatal_accidents["Yoy Growth"] = year_wise_fatal_accidents["Index"].pct_change()*100
   year_wise_fatal_accidents.round(2)

   year_wise_fatal_accidents_plot = GenericBarPlot(year_wise_fatal_accidents,x= "years",y = "Index",title= "Fatal Accidents over Years")
   # year_wise_fatal_accidents_plot.plot()
   year_wise_fatal_accidents
   ```
   ![image](https://github.com/SridharKadhiri/Undersatanding-Road-Accidents/assets/90100318/ff88d770-4fe0-40c6-b7c8-3b13858e3cba)



5. **Serious Accidents Over Years:**
   - Explored serious accidents and their YoY growth.
  
     ```python
     # YoY number_of_serious_accidents
     number_of_serious_accidents["Yoy change %"] = number_of_serious_accidents["Index"].pct_change().round(4)*100
     number_of_serious_accidents
     ```
     ![image](https://github.com/SridharKadhiri/Undersatanding-Road-Accidents/assets/90100318/42e13557-2f6a-45e7-9ae7-84a004e0ae56)



6. **Slight Accidents Over Years:**
   - Investigated slight accidents and their YoY growth.
   
   ```python
   numberOfSlightaccidents = df2[df2["Accident_Severity"] == "Slight"].groupby("years")["Index"].count().reset_index()
   numberOfSlightaccidents["Yoy change %"] = numberOfSlightaccidents["Index"].pct_change().round(4)*100

   numberOfSlightaccidents_plot = GenericBarPlot(numberOfSlightaccidents,y = "Index",x= "years",title="Number of Slight Accidents over Years")
   numberOfSlightaccidents_plot.plot()
   numberOfSlightaccidents
   ```
   ![image](https://github.com/SridharKadhiri/Undersatanding-Road-Accidents/assets/90100318/152c0c31-ac72-4386-977a-7fa2f5c76d0f)




7. **Vehicle Group Analysis:**
   - Grouped vehicles into categories and analyzed casualties for each group.
  
   ```python
   casualities_vehicle_group_2 = df2.groupby('Vehicle_group')["Index"].count().reset_index().sort_values(by = 'Index',ascending = False)
   casualities_vehicle_group_2
   ```
   ![image](https://github.com/SridharKadhiri/Undersatanding-Road-Accidents/assets/90100318/770f95f9-4e50-4854-9186-a0da4e3f7f21)

   



## Conclusion

This analysis provides valuable insights into road accidents, including trends over the years and the impact of various factors. Understanding these patterns can aid in policymaking and implementing safety measures to reduce accidents and casualties on the roads. Further analyses and machine learning models can be explored to predict accidents and prioritize preventive actions.

- Note: we can use this data to crosscheck if our dashboard is providing the correct information or not

[Link for the dashboard is here](https://public.tableau.com/app/profile/sridhar.kadhiri/viz/Road_accidents_Dashboard/Dashboard1?publish=yes) 
