# Quiz023


# 1. hl
![CommSci 7](https://github.com/Rokyyz/unit2/assets/134658259/2dddc55b-3abd-4d6f-a58f-8f219ea31ae1)


# 2. solutions


```.py

from matplotlib import pyplot as plt

def produce ():
    x_out = []
    y_out = []
    for n in range(-10,11):
        y_out.append(abs(n))
        x_out.append(n)
    return y_out, x_out

plt.style.use('ggplot')
y, x = produce()
plt.xlabel("Interval", fontsize=20)
plt.ylabel("$f(x) = |x|$", fontsize=20)
plt.plot(x, y)
plt.show()

```
# 3. proof of work

<img width="1440" alt="Screenshot 2023-11-19 at 02 20 01" src="https://github.com/Rokyyz/unit2/assets/134658259/b1569d30-1c86-4238-b8b2-b23e61d3e504">
