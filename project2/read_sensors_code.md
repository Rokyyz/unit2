```.py
import serial
import time
import requests
import datetime

arduino = serial.Serial(port='COM3', baudrate=9600, timeout=.1)

user = {"username": '---', "password": "---"}
ip = "192.168.6.153"
answer = requests.post(f"http://{ip}/login", json=user)
cookie = answer.json()["access_token"]
header = {"Authorization": f"Bearer {cookie}"}


def read():
    data = ""
    while len(data) < 1:
        data = arduino.readline()
    return data



while True:
    time.sleep(0.1)
    value = read()  # wait until data is in the port
    msg = value.decode('utf-8')
    print(msg.strip('\r\n').split(','))

    if msg.strip('\r\n').split(',')[2] == '1':
        with open('sensor1.csv', mode='a') as f:
            f.writelines(f'{msg[:-4]},{datetime.datetime.now()}\n')

    elif msg.strip('\r\n').split(',')[2] == '2':
        with open('sensor2.csv', mode='a') as f:
            f.writelines(f'{msg[:-4]},{datetime.datetime.now()}\n')

    elif msg.strip('\r\n').split(',')[2] == '3':
        with open('sensor3.csv', mode='a') as f:
            f.writelines(f'{msg[:-4]},{datetime.datetime.now()}\n')

```
