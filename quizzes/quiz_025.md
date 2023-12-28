# Quiz025



# 1. hl

![CommSci 14](https://github.com/Rokyyz/unit2/assets/134658259/6a807c4c-89d0-4e77-a8d8-7ccf7dffb41e)


# 2. solutions


```.py
import numpy as np
import matplotlib.pyplot as plt

plt.style.use('ggplot')

#step1: read data
heart_rate = []
with open('health2.csv', 'r') as f:
    header = f.readline() # read 1 line
    data = f.readlines() # read all the other line

print(header)
print(data)

time = []
t = 0
for d in data:
    sub1, sub2, sub3 = d.strip().split(',')
    heart_rate.append([int(sub1), int(sub2), int(sub3)])
    time.append(t)
    t += 1

#step 2: statistics
mean = []
std = []
min_hr =[]
max_hr = []
for v in heart_rate:
    mean.append(np.mean(v))
    std.append(np.std(v))
    min_hr.append(np.min(v))
    max_hr.append(np.max(v))

print(mean, std)

#step 3: vizualize
plt.errorbar(time, mean, std, fmt="o", color="#023047")
plt.xlabel("Time(hours)")
plt.ylabel("Heart Rate (pulses per minute)")
plt.fill_between(time, max_hr,min_hr, alpha=0.5, linewidth=0, color="#8ecae6")
plt.show()


```
# 3. proof of work
<img width="1440" alt="Screenshot 2023-12-28 at 21 23 28" src="https://github.com/Rokyyz/unit2/assets/134658259/1f32b113-2042-4971-9ab7-881ca39a3c90">
