# Quiz020


# 1. hl

![CommSci 5](https://github.com/Rokyyz/unit2/assets/134658259/e2222239-2fb3-40ab-b60e-a12177c4540e)


# 2. solutions


```.py
import random

random.seed(1234)


def produce(n: int, m: int, s: int):
    message = "| x  |  y(x)  |\n"
    for num in range(n):
        x = random.randint(0, 100)
        res = round(x ** ((1/2) * ((m / s) ** 2)), 2)
        message += f"| {str(x).center(2)} | {str(res).center(6)} |\n"
    return message

print(produce(n=5, m=3, s=2))

```
# 3. proof of work

<img width="1440" alt="Screenshot 2023-11-19 at 02 13 41" src="https://github.com/Rokyyz/unit2/assets/134658259/3577dbbe-e51b-416c-afa4-d9a9835a56ed">
