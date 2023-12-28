# Quiz026



# 1. hl

![CommSci 15](https://github.com/Rokyyz/unit2/assets/134658259/ea269be2-f108-446d-b473-ce19fbbe8462)


# 2. solutions


```.py

import matplotlib.pyplot as plt
plt.style.use('ggplot')

data = {
    'x':[0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19],
    'y':[24,1,2,25,26,21,23,34,49,2,19,32,7,17,36,7,45,28,40,46]
}
if "title" in data:
    print(data['title'])
else:
    data["title"] = "quiz_data_science"  # create a new key with an empty value

print(data)

plt.plot(data["x"],data['y'])
plt.show()


```
# 3. proof of work

<img width="1440" alt="Screenshot 2023-12-28 at 21 40 14" src="https://github.com/Rokyyz/unit2/assets/134658259/c2485ffc-f67b-40ff-9292-05f5744029a4">


