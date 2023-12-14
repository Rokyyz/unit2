```.py
from matplotlib import pyplot as plt
import numpy as np
from matplotlib.gridspec import GridSpec
from project_lib import smoothing, read_data, qmodel, get_sensor


s1 = read_data('sensor1.csv')
s2 = read_data('sensor2.csv')
s3 = read_data('sensor3.csv')
s_outside = {'h': get_sensor(5)[34:706], 'temp': get_sensor(1)[34:706]}

plt.style.use('ggplot')

# Plot 1: Showing the individual data from all the sensors

fig = plt.figure(figsize=(10, 8))
grid = GridSpec(2, 4, figure=fig)

box1 = fig.add_subplot(grid[0, 0])
x, y = smoothing(x=s1['h'], size_window=12)
plt.ylabel('Humidity (%)', fontsize=16)
plt.title('Sensor 1')
plt.ylim(19, 49)
plt.plot(x, y)

box2 = fig.add_subplot(grid[1, 0])
x, y = smoothing(x=s1['temp'], size_window=12)
plt.ylabel('Temperature (C)', fontsize=16)
plt.ylim(16, 33)
plt.plot(x, y)

box3 = fig.add_subplot(grid[0, 1])
x, y = smoothing(x=s2['h'], size_window=12)
plt.plot(x, y)
plt.title('Sensor 2')

box4 = fig.add_subplot(grid[1, 1])
x, y = smoothing(x=s2['temp'], size_window=12)
plt.ylim(16, 33)
plt.plot(x, y)

box5 = fig.add_subplot(grid[0, 2])
x, y = smoothing(x=s3['h'], size_window=12)
plt.title('Sensor 3')
plt.plot(x, y)

box6 = fig.add_subplot(grid[1, 2])
x, y = smoothing(x=s3['temp'], size_window=12)
plt.ylim(16, 33)
plt.plot(x, y)

box7 = fig.add_subplot(grid[0, 3])
x, y = smoothing(x=s_outside['h'], size_window=12)
plt.title('Remote Sensor')
plt.xlim(0, 62)
plt.plot(x, y)

box8 = fig.add_subplot(grid[1, 3])
x, y = smoothing(x=s_outside['temp'], size_window=12)
plt.xlim(0, 62)
plt.plot(x, y)

fig.text(0.5, 0.05, 'Time (hours)', ha='center', va='center', fontsize=16)
plt.show()

# Plot 2: Average temperature and humidity + non-linear model


avg_h = []
avg_temp = []
for i in range(len(s1['h'])):
    avg_h.append((s1['h'][i] + s2['h'][i] + s3['h'][i]) / 3)
    avg_temp.append((s1['temp'][i] + s2['temp'][i] + s3['temp'][i]) / 3)


plt.subplot(2, 1, 1)
x, y = smoothing(x=avg_h, size_window=12)
h_model, x1 = qmodel(x, y, 12)
plt.plot(x, y, label='Average')
plt.plot(x1, h_model, label='Model')
plt.ylabel('Humidity (%)')
plt.legend()
plt.title('Local Average Humidity')

plt.subplot(2, 1, 2)
x, y = smoothing(x=avg_temp, size_window=12)
temp_model = qmodel(x, y, 12)[0]
plt.plot(x, y, label='Average')
plt.plot(x1, temp_model, label='Model')
plt.ylabel('Temperature (C)')
plt.xlabel('Time (hours)')
plt.legend()
plt.title('Local Average Temperature')
plt.subplots_adjust(hspace=0.5)

plt.show()

# Plot non-linear model for outside sensor
plt.subplot(2, 1, 1)
x, y = smoothing(x=s_outside['h'], size_window=12)
out_h_model, x2 = qmodel(x, y, 18)
plt.plot(x, y, label='Humidity')
plt.plot(x2, out_h_model, label='Model')
plt.ylabel('Humidity (%)')
plt.legend()
plt.title('Remote Humidity')

plt.subplot(2, 1, 2)
x, y = smoothing(x=s_outside['temp'], size_window=12)
out_temp_model = qmodel(x, y, 18)[0]
plt.plot(x, y, label='Temperature')
plt.plot(x2, out_temp_model, label='Model')
plt.ylabel('Temperature (C)')
plt.xlabel('Time (hours)')
plt.legend()
plt.title('Remote Temperature')
plt.subplots_adjust(hspace=0.5)
plt.show()


# Plot local and remote models side by side
plt.subplot(2, 1, 1)
plt.plot(x1, h_model, color='red', label='Local')
plt.plot(x2, out_h_model, color='blue', label='Remote')
plt.ylabel('Humidity (%)')
plt.legend()
plt.title('Local and Remote Humidity Models')

plt.subplot(2, 1, 2)
plt.plot(x1, temp_model, color='red', label='Local')
plt.plot(x2, out_temp_model, color='blue', label='Remote')
plt.ylabel('Temperature (C)')
plt.xlabel('Time (hours)')
plt.legend()
plt.title('Local and Remote Temperature Models')

plt.subplots_adjust(hspace=0.5)
plt.show()

# Plot mean, std, min, max, median
max_h = []
min_h = []
max_temp = []
min_temp = []
std_h = []
std_temp = []
med_h = []
med_temp = []

for i in range(744):
    max_h.append(max(s1['h'][i], s2['h'][i], s3['h'][i]))
    min_h.append(min(s1['h'][i], s2['h'][i], s3['h'][i]))
    max_temp.append(max(s1['temp'][i], s2['temp'][i], s3['temp'][i]))
    min_temp.append(min(s1['temp'][i], s2['temp'][i], s3['temp'][i]))
    std_h.append(float(np.std([s1['h'][i], s2['h'][i], s3['h'][i]])))
    std_temp.append(float(np.std([s1['temp'][i], s2['temp'][i], s3['temp'][i]])))
    x = [s1['h'][i], s2['h'][i], s3['h'][i]]
    med_h.append(sorted(x)[1])
    x = [s1['temp'][i], s2['temp'][i], s3['temp'][i]]
    med_temp.append(sorted(x)[1])

# plt.subplot(2, 1, 1)
x, mean_y = smoothing(avg_h, size_window=12)
plt.plot(x, mean_y, label='Mean', color='red')
x, std_y = smoothing(std_h, size_window=12)
upper_y = []
lower_y = []
for i in range(62):
    upper_y.append(mean_y[i] + std_y[i])
    lower_y.append(mean_y[i] - std_y[i])
plt.fill_between(x, upper_y, lower_y, color='gray', alpha=0.2, label='Standard Deviation')

x, max_y = smoothing(max_h, size_window=12)
plt.plot(x, max_y, linestyle='--', label='Max')
x, min_y = smoothing(min_h, size_window=12)
plt.plot(x, min_y, linestyle='--', label='Min')
plt.ylabel('Humidity (%)')
plt.xlabel('Time (hours)')
plt.legend()
plt.title('Mean, Std, Min, Max Humidity')

plt.show()


med_y = smoothing(med_h, size_window=12)[1]
plt.plot(x, med_y, label='Median', color='blue')
plt.plot(x, mean_y, label='Mean', color='red')
plt.ylabel('Humidity (%)')
plt.xlabel('Time (hours)')
plt.legend()
plt.title('Mean and Median Humidity')
plt.show()


# plt.subplot(2, 1, 2)
x, mean_y = smoothing(avg_temp, size_window=12)
plt.plot(x, mean_y, label='Mean', color='red')
x, std_y = smoothing(std_temp, size_window=12)
upper_y = []
lower_y = []
for i in range(62):
    upper_y.append(mean_y[i] + std_y[i])
    lower_y.append(mean_y[i] - std_y[i])
plt.fill_between(x, upper_y, lower_y, color='gray', alpha=0.2, label='Standard Deviation')


x, max_y = smoothing(max_temp, size_window=12)
plt.plot(x, max_y, linestyle='--', label='Max')
x, min_y = smoothing(min_temp, size_window=12)
plt.plot(x, min_y, linestyle='--', label='Min')
plt.ylabel('Temperature (C)')
plt.xlabel('Time (hours)')
plt.legend()
plt.title('Mean, Std, Min, Max Temperature')

plt.show()

med_y = smoothing(med_temp, size_window=12)[1]
plt.plot(x, med_y, label='Median', color='blue')
plt.plot(x, mean_y, label='Mean', color='red')
plt.ylabel('Temperature (C)')
plt.xlabel('Time (hours)')
plt.legend()
plt.title('Mean and Median Temperature')
plt.show()


```
