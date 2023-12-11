![weather stat](https://github.com/Rokyyz/unit2/assets/134658259/1443c891-8a7f-4e90-9141-ac65ce82dd78)

[^1]

# Unit 2: A Distributed Weather Station for ISAK

## Criteria A: Planning

## Problem definition

A student in an international boarding school has been struggling with sleep quality and is complaining to the school's nurses about disrupted sleep, dry skin, dry throat, and nostrils. This is becoming a common trend on campus as nurses have received multiple similar complaints from other students. The nurses in the Health Center are guessing that this is due to dry air/low humidity levels in the air of the room. The nurses are keen on knowing if this is truly the issue at hand and if true, how to solve this issue. They want to know the precise data of humidity levels during the day as well as the temperature, to assess health risks, compare the living conditions of students from different houses, and think of methods to counteract this issue. The data can vary depending on the part of the room so nurses need the data to be collected from different parts of the room (recommended 3 different parts) to get the most accurate representation of the humidity and temperature levels.

## Success criteria

1. The gathered data and graphs provide a visual representation of the Humidity and Temperature values inside a student's room for minimum of 48 hours.
2. The local data will be recorded using a set of 3 sensors around the dormitory.
3.  The solution provides mathematical modeling for the humidity and temperature levels in the room, both linear and non-linear models.
4. The solution provides a comparative analysis of the humidity and temperature levels in the room using mean, standard deviation, minimum, maximum, and median.
5. The Local data is stored in a csv file and posted to the remote API server as a backup.
6. Create a prediction of the data for temperature and humidity inside the room for the following 12 hours
7. The solution includes a poster summarizing the visual representations, model and analysis created. The poster includes a recommendation about healthy levels for Temperature and Humidity.

_TOK Connection: To what extent does the use of data science in climate research influence our understanding of environmental issues, and what knowledge questions arise regarding the reliability, interpretation, and ethical implications of data-driven approaches in addressing climate change_

1. How does our use of technology shape our understanding of the environment

This inquiry delves into the role of technology, namely data science, in altering our perception and understanding of the environment. Considerations could include the sorts of data collected, the precision of measurements, and how technology improvements affect the scope and depth of environmental study.

2. What responsibilities do we have as technologists when it comes to handling personal data related to our living spaces?

This inquiry goes into the ethical implications of data collecting, particularly when it incorporates personal information about living spaces. It emphasizes concerns about privacy, permission, and the appropriate use of data, emphasizing technologists' ethical responsibility to protect sensitive information.
  
3. What cultural and contextual factors might impact our interpretation of the results, especially when comparing our local readings with those from the campus?

This issue emphasizes the need to take cultural and contextual aspects into account when evaluating data, especially when comparing local readings to larger datasets. It recognizes that various cultural settings can influence how data is received and understood, and it encourages contemplation of any biases or variances in data interpretation.


By answering these questions, we can gain a better grasp of the larger implications of data science in climate research. It supports not just technical aspects of data collecting and analysis, but also ethical duties and cultural complexities linked with these practices.

## Design statement

Our group will create a device and program that will calculate both humidity and temperature in a room of a residential house on campus. To do this, we will use an Arduino Uno and three DHT11 sensors to collect data on the humidity and temperature in the room. The program will upload the collected data into a CSV file that will onward go to an outside API server in real-time to permanently store the data. We will use the DHT11 device to record the humidity and temperature inside of a room for 48 hours, and based on the data and results the nurses in the Health Center will be able to see and evaluate the information that the data presents with the help of visual representation - graphs and raw data with the help of a login token. From then on, the nurses can use the data collected to evaluate the living conditions and compare them with their information on optimal humidity and temperature in healthy living conditions. This project will take approximately 4 weeks and will be evaluated according to the criteria shown above.

## Proposed Solution
Taking into consideration that the client wants the solution to be at an adequate/low price but with data that can be trusted, and analyzed because it is precise. To complete these wishes of the client, the best solution found for this request was a low-cost, but accurate reading sensor device for humidity and temperature and a custom data script that can process and analyze the data recorded. The device fitting the description is the DHT11 sensor. 3 sensors are usually sold online for roughly 5-9 USD and provide adequate precision and range for the client's requirements - humidity range 20-90%, temperature range 0 to 50°C. Similar devices such as the DHT22, AHT20, or the AM2301B [^3][^4][^5] have higher specifications, however, the DHT11 uses a simple serial communication (SPI) rather than more elaborated protocols such as the I2C used by the alternatives. Also, the cost difference is important as DHT11 is a budget option. For example, the DHT22 is almost twice the price of the DHT11, thus taking into consideration the price and the specs of all the sensors DHT11 seems to be a better fit. DHT22 has better reading capabilities in terms of range and precision error for both humidity and temperature but because one can gain good insight from the readings from both the sensors and the client doesn't require too professional, specific analysis but the basics of what the issue is, how the data looks DHT11 is the best choice. As the price difference between 3 DHT11 and 3 DHT22 sensors is about $15 and that is quite significant and DHT11 is good enough for data reading and analysis we are leaning towards DHT11 as our choice.[^2][^4] For the range, precision, and accuracy required in this application, the DHT11 provides the best compromise. Connecting the DHT11 sensor to a computer requires a device that provides a Serial Port communication. A cheap and often-used alternative for prototyping is the Arduino UNO microcontroller [^5]. "Arduino is an open-source electronics platform based on easy-to-use hardware and software"[^6]. Other alternatives include different versions of the original Arduino but their size and price make them a less adequate solution.

Given the client's budgetary limits and hardware needs, the software tool that I offered for this solution is Python. Python's open-source nature and platform freedom contribute to the system's long-term viability. Python streamlines potential future upgrades or alterations, enabling smooth scalability without extensive reconstruction [^7][^8][^9]. Python is a great-level programming language (HLL) with great abstraction, as opposed to the alternatives C or C++, which share comparable features [^10]. For example, memory management is automatic in Python, whereas memory allocation and freeing are the responsibility of the C/C++ developer [^10], which may result in quicker applications but also memory difficulties.  

[^1]: AEM. "Portable Weather Stations - AEM"  Portable Weather Stations,
https://aem.eco/product/portable-weather-stations/
[^2]: Seed studios. "DHT11 vs DHT22 – Which Temperature and Humidity Sensor Should You Use?" NEWS, temperature humidity sensors,
https://www.seeedstudio.com/blog/2020/04/20/dht11-vs-dht22-am2302-which-temperature-humidity-sensor-should-you-use/
[^3]: Industries, Adafruit. "Modern Replacements for DHT11 and DHT22 Sensors" What are better alternatives?,
https://learn.adafruit.com/modern-replacements-for-dht11-dht22-sensors/what-are-better-alternatives
[^4]: Industries, Adafruit. “DHT11 Basic Temperature-Humidity Sensor + Extras.” Adafruit Industries Blog RSS, https://www.adafruit.com/product/386. 
[^5]: Nelson, Carter. “Modern Replacements for DHT11 and dht22 Sensors.” Adafruit Learning System, https://learn.adafruit.com/modern-replacements-for-dht11-dht22-sensors/what-are-better-alternatives.   
[^6]:“How to Connect dht11 Sensor with Arduino Uno.” Arduino Project Hub, https://create.arduino.cc/projecthub/pibots555/how-to-connect-dht11-sensor-with-arduino-uno-f4d239.  
[^7]: Team, The Arduino. “What Is Arduino?: Arduino Documentation.” Arduino Documentation | Arduino Documentation, https://docs.arduino.cc/learn/starting-guide/whats-arduino.  
[^8]: Tino. “Tino/PyFirmata: Python Interface for the Firmata (Http://Firmata.org/) Protocol. It Is Compliant with Firmata 2.1. Any Help with Updating to 2.2 Is Welcome. the Capability Query Is Implemented, but the Pin State Query Feature Not Yet.” GitHub, https://github.com/tino/pyFirmata. 
[^9]: Python Geeks. “Advantages of Python: Disadvantages of Python.” Python Geeks, 26 June 2021, https://pythongeeks.org/advantages-disadvantages-of-python/. 
[^10]: Real Python. “Python vs C++: Selecting the Right Tool for the Job.” Real Python, Real Python, 19 June 2021, https://realpython.com/python-vs-cpp/#memory-management. 

# Criteria B: Design

## System Diagram **HL**



![HL](https://github.com/comsci-uwc-isak/unit2_2023/assets/53995212/4891d5e9-b8ab-46ed-bd75-b606e25e3383)

https://github.com/comsci-uwc-isak/unit2_2023/assets/53995212/4891d5e9-b8ab-46ed-bd75-b606e25e3383 

**Fig.2** shows the system diagram for the proposed solution (**HL**). The indoor variables will be measured using an Arduino and three DHT11 sensors located inside a room. Three sensors are used to determine more precisely the physical values and include measurement uncertainty. The outdoor variables will be requested to the remote server using a GET request to the API of the server at ```192.168.6.153/readings```. The local values are stored in a CSV database locally and a backup copy will be store in the remote server using the **Weather API**. 


## Record of Tasks
| Task No | Planned Action                                                | Planned Outcome                                                                                                 | Time estimate | Target completion date | Criterion |
|---------|---------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|---------------|------------------------|-----------|
| 1       | Write the Problem context                        | 10min         | Nov 22                 | A         |

## Test Plan

# Criteria C: Development

## List of techniques used

## Development


# Criteria D: Functionality

A 7 min video demonstrating the proposed solution with narration

## Citations 
[1]
https://s39920.pcdn.co/wp-content/uploads/2022/04/StormLink-Quick-Deploy-Early-Warning-System-600px.jpeg
