# Quiz021


# 1. hl

![CommSci 6](https://github.com/Rokyyz/unit2/assets/134658259/c7b0af05-b77b-45bd-bac9-397e5d16c360)


# 2. solutions


```.py

import random
random.seed(1234)
def produce (n:int, m:int, s:int):
    x_out = []
    y_out = []
    for _ in range(n):
        x =  random.randint(0,100)
        y = x ** (0.5 * ((m/s)**2))
        x_out.append(x)
        y_out.append(y)
    return y_out, x_out

import matplotlib.pyplot as plt

plt.style.use('ggplot')

y, x = produce(n=10, m=5, s=2)

plt.plot(x, y, color = 'r', marker = "*")
plt.xlabel('x', fontsize = 20)
plt.ylabel('$y=x^{(1/2)(m/s)}$ ', fontsize = 20)
plt.show()

```
# 3. proof of work
<img width="1440" alt="Screenshot 2023-11-19 at 02 15 41" src="https://github.com/Rokyyz/unit2/assets/134658259/b161d87e-170e-4502-8c48-05da29b92884">


