```.py
import requests

user = {"username": '---', "password": "---"}
ip = "192.168.6.153"
answer = requests.post(f"http://{ip}/login", json=user)
cookie = answer.json()["access_token"]
header = {"Authorization": f"Bearer {cookie}"}


def upload_data(file: str, h_sensor: int, temp_sensor: int):
    with open(file, 'r') as f:
        data = f.readlines()
    for d in data:
        humidity, temperature, date = d.split(',')
        date = date.replace(" ", "T")
        record = {"sensor_id": h_sensor, "value": humidity, "datetime": date}
        requests.post(f"http://{ip}/reading/new",
                      json=record,
                      headers=header)
        record = {"sensor_id": temp_sensor, "value": humidity}
        requests.post(f"http://{ip}/reading/new",
                      json=record,
                      headers=header)


upload_data('sensor1.csv', 83, 86)
upload_data('sensor2.csv', 84, 87)
upload_data('sensor3.csv', 85, 88)

```
