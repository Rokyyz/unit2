# Quiz027



# 1. hl

![CommSci 16](https://github.com/Rokyyz/unit2/assets/134658259/7fc73455-bbf7-45e7-8af2-0a04aea81c20)


# 2. solutions


```.py

def count_letter(my_dict,msg):
    for let in msg:
        if let in my_dict:
            my_dict[let]+=1
    return my_dict
my_dict = {
    "w":0,
    "l":0,
    'c':0
}

case1 = count_letter({'w':0,'l':0,'c':0}, "hello world")
print(case1)
case2 = count_letter({'a':0,'e':0,'i':0,'o':0,'u':0}, "Why did I choose CS?")
print(case2)

```
# 3. proof of work

<img width="1440" alt="Screenshot 2023-12-28 at 21 47 23" src="https://github.com/Rokyyz/unit2/assets/134658259/5f2d4e19-fc5c-41b4-b3f9-a28297fd3496">

