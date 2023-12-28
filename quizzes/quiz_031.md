# Quiz031



# 1. hl



# 2. solutions


```.py

from unt2_lib import get_sensor, smoothing
import matplotlib.pyplot as plt
import matplotlib

plt.style.use('ggplot')
matplotlib.use('MacOSX')

sensors = []
for s in [4, 5]:
    data = get_sensor(id=s)
    sensors.append(data)
    print(f'sensor {s} obtained with {len(data)} samples')

t = []
average = []
for i in range(len(sensor_id_1)):
    average.append(sensor_id_1[i]+sensor_id_2[i])
    t.append(i)

x, y = smoothing(x=average)
plt.subplot(3,1,1)
plt.plot(sensor_id_1)
plt.subplot(3,1,2)
plt.plot(sensor_id_2)
plt.subplot(3,1,3)
plt.plot(x, y)


plt.plot(x,y)
plt.show()

```
# 3. proof of work
