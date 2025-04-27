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


## DATA ANALYSIS

### Data Filtering
```Python
# Filtering out only the data relevant to solving the problem statement

USA = bikes_df["CustomerCountry"] == "United States"

bikes_df[(USA)]

USA_Customers = bikes_df[(USA)]

USA_Customers
```

### Data Aggregation
```Python
# Aggregating the Filtered Data for Each USA customer

USA_Customers.pivot_table( values = 'Profit', index = 'CustomerName', aggfunc = np.sum)

Customer_Total_Profit = USA_Customers.pivot_table( values = 'Profit', index = 'CustomerName', aggfunc = np.sum)

Customer_Total_Profit
```

### Data Sorting
```Python
Customer_Total_Profit.sort_values("Profit", ascending = False)
```

## RESULT
```Python
Customer_Total_Profit.sort_values("Profit", ascending = False).head(10)

Top_10_Customers = Customer_Total_Profit.sort_values("Profit", ascending = False).head(10)

Top_10_Customers
```

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
