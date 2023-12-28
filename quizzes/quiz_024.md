# Quiz024


# 1. hl

![CommSci 8](https://github.com/Rokyyz/unit2/assets/134658259/8f706a3e-59b1-4682-b623-5b846b4e6214)


# 2. solutions


```.py
import matplotlib.pyplot as plt
import numpy as np

plt.style.use('ggplot')
#imaginary temperature taken every 5 min
h = [
    57.0, 56.0, 57.0, 56.0, 55.0, 55.0, 54.0, 54.0, 54.0,
    53.0, 53.0, 54.0, 53.0, 53.0, 52.0, 52.0, 51.0, 51.0, 51.0,
    50.0, 50.0, 49.0, 50.0, 49.0, 49.0, 48.0, 49.0, 49.0, 48.0, 48.0, 48.0, 49.0]
time = []
t = 0
for i in range(len(h)):
    time.append(t)
    t += 10 #10min

plt.scatter(time, h, color="blue")
plt.xlabel("Time (min)")
plt.ylabel("Humidity (%)")

m, b = np.polyfit(time, h, 1)
print(f"Linear model T(t) = {m:.2f}t + {b:.2f}")

time_model = []
h_model = []
t = 0
for i in range(len(h)):
    time_model.append(t)
    h_model.append(m*t + b)
    t += 10 #10min

plt.plot(time_model, h_model, color = 'black')
plt.text(1, 4, f"T(t) = {m:.2f}t + {b:.2f}", fontsize = 10 )
plt.show()

#use the model to predict the temp 5 minutes in the future
h_future = (m*(45) + b)
print(f"Prediction linear model {h_future:.2f}C = {m:.2f}t + {b:.2f}")


```
# 3. proof of work

<img width="1440" alt="Screenshot 2023-12-28 at 20 38 24" src="https://github.com/Rokyyz/unit2/assets/134658259/76eb9548-512e-4ccb-a630-27c33ec93d0c">


