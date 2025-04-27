# Customers Performance Analysis and Visualization of an Automobile Company Sales Data:
A Data Science Project that Analysed  the sales performance of an Automobile company Based in the United States. The company’s sales transaction data generated over the past years was used for this  analysis.

# Project Overview: 
This Data  Science Project aims to provide  insights into the sales performance of  an Automobile  company Based in the United State. 

# About the Company:
The Automobile Company operates in different countries and  sells a wide variety of product categories , including bikes, accessories and clothings.  


## DATA PRE-PROCESSING

### Data Loading
```Python
##  importing all the necessary python packages


# solution 

import numpy as np 
import pandas as pd 
import matplotlib.pyplot as plt

print("The packages have been successfully imported")
```

```Python
# reading the sales data into the pandas dataframe

# Solution

bikes_df =  pd.read_csv("C:/Users/HP/Desktop/_EXCLUSIVE DATA SCIENCE BOOT CAMP_STUDENT FOLDER/_DATASET/bikes.csv")

bikes_df.head()
```
![Data Science Project2_DataLoading](https://github.com/user-attachments/assets/1e746714-6213-4c49-87c6-9cebeafd14f3)

###  Data Modification
```Python
# Adding the following 3 columns; TotalCostPrice, SalesRevenue, Profit.

# TotalCostPrice : To be obtained by (OrderQuantity x CostPrice_usd)
bikes_df["TotalCostPrice"] = bikes_df["OrderQuantity"] * bikes_df["CostPrice_usd"] 

# SalesRevenue : To be obtained by (OrderQuantity x SellingPrice_usd)
bikes_df["SalesRevenue"] = bikes_df["OrderQuantity"] * bikes_df["SellingPrice_usd"] 

# Profit : To be obtained by (SalesRevenue - TotalCostPrice)
bikes_df["Profit"] = bikes_df["SalesRevenue"] - bikes_df["TotalCostPrice"]

bikes_df.head()
```
![Data Science Project2_Modification](https://github.com/user-attachments/assets/341a0d3b-9f16-4e06-8803-116365c5e0b1)

## DATA ANALYSIS
### Data Filtering
```Python
# Filtering out only the data relevant to solving the problem statement

USA = bikes_df["CustomerCountry"] == "United States"

bikes_df[(USA)]

USA_Customers = bikes_df[(USA)]

USA_Customers
```
![Data Science Project2_DataFiltering](https://github.com/user-attachments/assets/165a08d8-eabf-48f7-a54d-430340315eb4)

### Data Aggregation
```Python
# Aggregating the Filtered Data for Each USA customer

USA_Customers.pivot_table( values = 'Profit', index = 'CustomerName', aggfunc = np.sum)

Customer_Total_Profit = USA_Customers.pivot_table( values = 'Profit', index = 'CustomerName', aggfunc = np.sum)

Customer_Total_Profit
```
![Data Science Project2_Aggregation](https://github.com/user-attachments/assets/5229e3c8-0111-43df-ad54-c5d5e4d7285e)

### Data Sorting
```Python
Customer_Total_Profit.sort_values("Profit", ascending = False)
```
![Data Science Project2_Sorting](https://github.com/user-attachments/assets/491c83a2-adf7-428e-90b5-2cc071a87abb)

## RESULT
```Python
Customer_Total_Profit.sort_values("Profit", ascending = False).head(10)

Top_10_Customers = Customer_Total_Profit.sort_values("Profit", ascending = False).head(10)

Top_10_Customers
```
![Data Science Project2_Sorting](https://github.com/user-attachments/assets/69c0d673-ef07-4805-9dfa-5b8092c909c9)

## VISUALIZATION
```Python
# Visualizing The Result

# Ploting
Top_10_Customers.plot(kind = 'bar')

# Adding Title, and Labels
plt.title('The Top Ten (10) Customers in the United States')

plt.ylabel('Total Profit')

plt.xlabel('Customer Name')

# Showing the Result
plt.show()
```
![Data Science Project2_visualization](https://github.com/user-attachments/assets/816ab578-fbf3-496e-b9e6-1f8052930865)

# THANK YOU
