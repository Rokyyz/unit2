# Quiz022


# 1. hl

![CommSci 7](https://github.com/Rokyyz/unit2/assets/134658259/04edca91-0b82-463d-b374-5faff528f7f0)


# 2. solutions


```.py

from matplotlib import pyplot as plt

def produce ():
    x_out = []
    y_out = []
    for n in range(-10,11):
        res = 2*((n+5)**2)
        y_out.append(res)
        x_out.append(n)
    return y_out, x_out

plt.style.use('ggplot')
y, x = produce()
plt.xlabel("Interval", fontsize=20)
plt.ylabel("$f(x) = 2(x + 5)^{2}$", fontsize = 20)
plt.plot(x, y,)
plt.show()

```
# 3. proof of work
<img width="1440" alt="Screenshot 2023-11-19 at 02 31 08" src="https://github.com/Rokyyz/unit2/assets/134658259/b330e194-a11d-4baf-a3dc-62b5fbda2903">


