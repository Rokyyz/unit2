# Quiz022


# 1. hl

![CommSci 7](https://github.com/Rokyyz/unit2/assets/134658259/04edca91-0b82-463d-b374-5faff528f7f0)


# 2. solutions


```.py

def produce ():
    x_out = []
    y_out = []
    x = -10
    for n in range(100):
        y = 2*(x+5)**2
        y_out.append(y)
        x_out.append(x)
        x += 0.1
    return y_out, x_out

plt.style.use('ggplot')
y, x = produce()
plt.plot(x, y,)
plt.show()

```
# 3. proof of work

<img width="1440" alt="Screenshot 2023-11-19 at 02 17 32" src="https://github.com/Rokyyz/unit2/assets/134658259/7f6d8fc5-eeb1-4701-b8fa-97f63a8ee19e">
