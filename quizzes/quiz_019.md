# Quiz019



# 1. hl

![CommSci 4](https://github.com/Rokyyz/unit2/assets/134658259/077df92b-d3b4-4154-b495-df8a6af1c6e0)


# 2. solutions


```.py

def get_truth() -> str:
    message = "A | B | C | AB + (Not B) + (Not (BC))\n"
    num = [0, 1]
    for a in num:
        for b in num:
            for c in num:
                result = (a and b or (not b) or not (b and c))
                message += f"{a} | {b} | {c} | {str(int(result)).center(26)}\n"
    return message

print(get_truth())

```
# 3. proof of work
<img width="1440" alt="Screenshot 2023-11-19 at 02 12 05" src="https://github.com/Rokyyz/unit2/assets/134658259/56552eb3-8f29-4c6e-877e-8d2236c576a8">
