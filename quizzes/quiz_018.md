# Quiz018


# 1. hl

![CommSci 3](https://github.com/Rokyyz/unit2/assets/134658259/4c717986-e1d4-4f34-a433-1468d4f0454f)


# 2. solutions


```.py
def get_truth() -> str:
    message = "A | B | C\n"
    input = [0, 1]
    for x in input:
        for y in input:
            for z in input:
                message += f"{x} | {y} | {z}\n"
    return message

print(get_truth())


```
# 3. proof of work
<img width="1440" alt="Screenshot 2023-11-19 at 02 09 51" src="https://github.com/Rokyyz/unit2/assets/134658259/1a800bc2-d49d-4904-aa18-fe11db2f4b9e">
