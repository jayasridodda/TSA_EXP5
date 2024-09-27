### Developed by : Dodda Jayasri
### Register no : 212222240028
# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 
### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```
# Step 1: Import the required packages
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Step 2: Read the data using pandas (replace this with the path to your actual dataset)
df=pd.read_csv('Salesforcehistory.csv')
df.head()


# Step 3: Convert 'Date' column to datetime format
df['Date'] = pd.to_datetime(df['Date'])

# Set 'Date' as the index
df.set_index('Date', inplace=True)

# Step 4: Aggregate the data daily for the 'Total' column
df_daily = df.resample('D').sum()

# Perform seasonal decomposition on the 'Total' column (additive model and weekly period assumption)
result = seasonal_decompose(df_daily['Open'], model='additive', period=7)

# Step 5: Plot the decomposed components
fig = result.plot()
plt.tight_layout()

# Step 6: Display the decomposed results
plt.show()

# Print the results (Trend, Seasonal, Residuals)
print("Trend Component:\n", result.trend.dropna().head())
print("\nSeasonal Component:\n", result.seasonal.dropna().head())
print("\nResidual Component:\n", result.resid.dropna().head())



```

### OUTPUT:
FIRST FIVE ROWS:

![image](https://github.com/user-attachments/assets/b64a280c-42dc-48e3-ae56-dfdd5fc6c42a)

PLOTTING THE DATA:

![image](https://github.com/user-attachments/assets/902905e4-c807-4be0-9c0b-e02f6a2c1f38)

SEASONAL PLOT REPRESENTATION :

![image](https://github.com/user-attachments/assets/9c5022c3-dcc5-4fdd-96af-5e833e67c4b5)

TREND PLOT REPRESENTATION :

![image](https://github.com/user-attachments/assets/b503f37b-dccd-4141-abbd-c73d046f665a)


OVERAL REPRESENTATION:

![image](https://github.com/user-attachments/assets/63972977-236b-4113-acbc-1b91ef794451)



### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
