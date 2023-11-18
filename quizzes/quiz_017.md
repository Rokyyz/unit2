# Quiz017


# 1. hl

![CommSci 2](https://github.com/Rokyyz/unit2/assets/134658259/f336d168-f1dc-4868-8462-9a573f154fe1)


# 2. solutions


```.py

def letter(msg: str) -> str:
    message = ""
    let_change = {
        "a": "4",
        "e": "3",
        "i": "1",
        "o": "0",
        " ": "_"
    }
    for l in msg:
        if l.lower() in let_change:
            message += let_change[l.lower()]
        else:
            message += l

    return message

print(letter("Hello World"))
print(letter('Why did I choose CS?'))
print(letter('Remember the Figure Caption'))

```
# 3. proof of work

<img width="1440" alt="Screenshot 2023-11-19 at 02 07 46" src="https://github.com/Rokyyz/unit2/assets/134658259/19af8adc-acc1-4d37-af28-087536f8332b">

