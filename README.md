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
Developed By: Sai Eswar Kandukuri
Reg. No: 212221240020
```
```python
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Load the Passenger Details
# Replace 'AirPassengers.csv' with the path to your data file
data = pd.read_csv('AirPassengers.csv')

# Ensure that the 'Month' column is in datetime format
data['Month'] = pd.to_datetime(data['Month'])
data['Year'] = data['Month'].dt.year
# Set the 'Month' column as the index
data.set_index('Month', inplace=True)
data.head()

# Plotting the Data
ar1 = data['Year'].values.reshape(-1, 1)
ma1 = data['#Passengers'].values.reshape(-1, 1)
plt.plot(ar1,ma1,label='Data')
plt.title('Plotting the Data')
plt.legend()
plt.show()

# Perform time series decomposition
period=13
result = seasonal_decompose(data,model='multiplicative', period=period)

# Plot the seasonal component
plt.subplot(4, 1, 3)
plt.plot(result.seasonal, label='Seasonal', color='green')
plt.title('Seasonal Component')
plt.legend()
plt.show()

# Plot the trend component
plt.subplot(4, 1, 2)
plt.plot(result.trend, label='Trend', color='yellow')
plt.title('Trend Component')
plt.legend()
plt.show()

# Plot the original time series
plt.figure(figsize=(12, 6))
plt.subplot(4, 1, 1)
plt.plot(data['#Passengers'], label='original')
plt.title('Original Time Series')
plt.legend()
plt.show()
```
### OUTPUT:

#### FIRST FIVE ROWS:

![11](https://github.com/saieswar1607/TSA_EXP5/assets/93427011/6e3b399c-f14a-49a1-a96f-2fe7a059bbf8)


#### PLOTTING THE DATA:

![1](https://github.com/saieswar1607/TSA_EXP5/assets/93427011/4e2a4fe1-33bb-4d37-b19d-1a9393b377b0)


#### SEASONAL PLOT REPRESENTATION :

![2](https://github.com/saieswar1607/TSA_EXP5/assets/93427011/a9bc1de3-b964-4486-8298-238e246421d7)


#### TREND PLOT REPRESENTATION :


![3](https://github.com/saieswar1607/TSA_EXP5/assets/93427011/13e1b854-0206-488f-9794-e2cc91e5d54f)


#### OVERAL REPRESENTATION:

![4](https://github.com/saieswar1607/TSA_EXP5/assets/93427011/e7d23810-ccb6-428e-9901-ed16c7e592ab)


### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
