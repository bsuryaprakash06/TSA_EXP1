# Ex.No: 01A PLOT A TIME SERIES DATA

###  Date: 06 - 11 - 2026
# AIM:
To Develop a python program to Plot a time series data (population/ market price of a commodity
/temperature.

# ALGORITHM:
1. Import the required packages like pandas and matplot
2. Read the dataset using the pandas
3. Calculate the mean for the respective column.
4. Plot the data according to need and can be altered monthly, or yearly.
5. Display the graph.

# PROGRAM:
```python
from matplotlib import pyplot as plt
import pandas as pd

df = pd.read_csv("/content/ADANIPORTS-selected-columns.csv")

df.head()

df['Date'] = pd.to_datetime(df['Date'])

print(df.dtypes)

df = df.sort_values('Date')

df = df.set_index('Date')

df_resampled = df['Close'].resample('B').last()

df_resampled = df_resampled.interpolate(method='time', limit_area='inside')

df_resampled.plot(kind='line', label='Closing Price', color='black')

plt.title('Time Series Plot of Adani Ports Closing Stock Price')
plt.xlabel('Date')
plt.ylabel('Closing Price')
plt.legend()
plt.grid(True)
plt.show()

```
# OUTPUT:

### Time Series Plot of Adani Ports Closing Stock Price
<img width="580" height="455" alt="image" src="https://github.com/user-attachments/assets/6e651a07-ae5e-48cb-8227-920b15ca4693" />

# RESULT:
Thus we have created the python code for plotting the time series of given data.
