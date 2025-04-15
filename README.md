# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:
#### NAME: MUKESH KUMAR S
#### REG NO:212223240099
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose
# Load the dataset
data = pd.read_csv('dataset.csv')
# Convert 'Date' to datetime and set it as the index
data['date'] = pd.to_datetime(data['date'])
data.set_index('date', inplace=True)
# Drop rows with missing values in 'USD'
data.dropna(subset=['meantemp'], inplace=True)
# Regular differencing
data['meantemp_diff'] = data['meantemp'].diff()
result_meantemp = seasonal_decompose(data['meantemp'], model='additive', period=12)
data['meantemp_sea_diff'] = result_usd.resid
# Log transformation
data['meantemp_log'] = np.log(data['meantemp'])
# Log transformation + regular differencing
data['meantemp_log_diff'] = data['meantemp_log'].diff().dropna()
# Seasonal decomposition after log differencing
if len(data['meantemp_log_diff'].dropna()) >= 12:  # Check if enough data exists for decomposition
    result_meantemp_log = seasonal_decompose(data['meantemp_log_diff'].dropna(), model='additive', period=12)
    data['meantemp_log_seasonal_diff'] = result_meantemp_log.resid
else:
    data['meantemp_log_seasonal_diff'] = np.nan
    print("Not enough data for seasonal decomposition after log differencing for USD.")
# Plotting results
plt.figure(figsize=(16, 12))
plt.subplot(6, 1, 1)
plt.plot(data['meantemp'], label='Original meantemp')
plt.legend(loc='best')
plt.title('Original meantemp Data')
plt.subplot(6, 1, 2)
plt.plot(data['meantemp_diff'], label='meantemp Difference')
plt.legend(loc='best')
plt.title('meantemp Regular Differencing')
plt.subplot(6, 1, 3)
plt.plot(data['meantemp_sea_diff'], label='meantemp Seasonal Adjustment')
plt.legend(loc='best')
plt.title('meantemp Seasonal Adjustment')
plt.subplot(6, 1, 4)
plt.plot(data['meantemp_log'], label='Log Transformation (meantemp)')
plt.legend(loc='best')
plt.title('Log Transformation of meantemp')
plt.subplot(6, 1, 5)
plt.plot(data['meantemp_log_diff'], label='Log Transformation + Diff (meantemp)')
plt.legend(loc='best')
plt.title('Log Transformation and Differencing (meantemp)')
plt.subplot(6, 1, 6)
plt.plot(data['meantemp_log_seasonal_diff'], label='Log + Diff + Seasonal Diff (meantemp)')
plt.legend(loc='best')
plt.title('Log, Differencing, and Seasonal Adjustment (meantemp)')
```

### OUTPUT:
#### Original Data:
![Screenshot 2025-04-15 101406](https://github.com/user-attachments/assets/837d3c57-2843-4325-b8dc-dcdc4f80cb55)


#### REGULAR DIFFERENCING:
![Screenshot 2025-04-15 101500](https://github.com/user-attachments/assets/21f25150-d9f0-468a-accc-1c52de35fdbf)

#### SEASONAL ADJUSTMENT:
![Screenshot 2025-04-15 101548](https://github.com/user-attachments/assets/566992b8-d9f6-4bd3-a790-d605ab8980e6)



#### LOG TRANSFORMATION:
![Screenshot 2025-04-15 101619](https://github.com/user-attachments/assets/72ecd6ba-a0a3-4142-8062-eb9664851398)



### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
