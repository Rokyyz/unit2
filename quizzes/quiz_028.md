# Quiz028



# 1. hl

![CommSci 17](https://github.com/Rokyyz/unit2/assets/134658259/24fabf92-b17e-4d6d-ba10-2795478e4be0)


# 2. solutions


```.py

def invert(in_dict):
    inverted_dict = {}
    for k, v in in_dict.items():
        if k not in inverted_dict:
            inverted_dict[v] = [k]
        else:
            inverted_dict[v].append(k)

    return inverted_dict

case1 ={'q1': True, 'q2': False, 'q3': True}
inverted_dict = invert(case1)
print("Original Dictionary:", case1)
print("Inverted Dictionary:", inverted_dict)

case2 ={'a': 1, 'b': 2, 'c': 3}
inverted_dict = invert(case2)
print("Original Dictionary:", case2)
print("Inverted Dictionary:", inverted_dict)

case3 ={'bob': 26, 'alice': 30, 'carl': 40}
inverted_dict = invert(case3)
print("Original Dictionary:", case3)
print("Inverted Dictionary:", inverted_dict)

```
# 3. proof of work

<img width="1440" alt="Screenshot 2023-12-28 at 22 23 05" src="https://github.com/Rokyyz/unit2/assets/134658259/5dd2f55e-8b2c-4f75-9c63-f7337370abb2">
