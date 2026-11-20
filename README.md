# Ex.No: 01A PLOT A TIME SERIES DATA

### Date: 06 - 11 - 2026

# AIM:
To develop a Python program to plot time series data and evaluate its properties and stationarity.

# DATASET:
- **Daily Minimum Temperatures in Melbourne**: `daily-min-temperatures.csv` (10-year daily temperature observations)

# ALGORITHM:
1. Import the required packages like pandas, numpy, and matplotlib.
2. Read the time series dataset using pandas.
3. Handle missing values, parse datetime indexing, and calculate descriptive statistics.
4. Resample and interpolate the data according to business frequency or calendar intervals.
5. Plot the time series data and display the graph.

# PROGRAM:
```python
import pandas as pd
import matplotlib.pyplot as plt

# Load the daily minimum temperatures dataset
url = 'https://raw.githubusercontent.com/jbrownlee/Datasets/master/daily-min-temperatures.csv'
temp_data = pd.read_csv(url)

# Prepare the data
temp_data['Date'] = pd.to_datetime(temp_data['Date'])
temp_data = temp_data.sort_values('Date')
temp_data = temp_data.set_index('Date')

# Display the first few rows
display(temp_data.head())

# Plot the raw temperature data
plt.figure(figsize=(14, 5))
plt.plot(temp_data['Temp'], color='blue', label='Daily Min Temp')
plt.title('Daily Minimum Temperatures')
plt.xlabel('Date')
plt.ylabel('Temperature')
plt.legend()
plt.grid(True)
plt.show()
```

# OUTPUT:

### Sample Data
<img width="109" height="166" alt="{5D6C208D-7150-4013-A3A7-452B0EFBAEE2}" src="https://github.com/user-attachments/assets/7ae782b1-edab-4b4c-b91c-fd2a57b7519e" />

### Time Series Plot of Daily Minimum Temperatures
<img width="1151" height="470" alt="image" src="https://github.com/user-attachments/assets/290a5ca9-f4d1-4423-a1fc-1e9efd2d0ade" />

# RESULT:
Thus, the Python code for plotting the time series of the given dataset has been created and executed successfully.
