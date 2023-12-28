# Quiz032



# 1. hl



# 2. solutions


```.py

from unt2_lib import get_sensor, smoothing
import matplotlib.pyplot as plt
from matplotlib.gridspec import GridSpec
import matplotlib

plt.style.use('ggplot')
matplotlib.use('MacOSX')

sensor4 = get_sensor(4)
sensor5 = get_sensor(5)

minus_sensors = []
for i in range(len(sensor4)):
    minus_sensors.append(-sensor4[i]-sensor5[i])

fig = plt.figure(figsize=(10,5))
grid = GridSpec(3,4, figure = fig)
plt.subplots_adjust(hspace=0.5)

box1 = fig.add_subplot(grid[1,0])
plt.plot(sensor4, color='red')
plt.title('Sensor id=4')
plt.ylim([0,100])
plt.xlim([0,800])

box2 = fig.add_subplot(grid[1,3])
plt.plot(sensor5, color = 'black')
plt.title('Sensor id=5')
plt.ylim([0,100])
plt.xlim([0,800])

box3 = fig.add_subplot(grid[0:3, 1:3])
plt.plot(minus_sensors, color = 'black')
plt.title('-sensor 4 -sensor 5')

plt.show()

```
# 3. proof of work
