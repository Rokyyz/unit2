![weather stat](https://github.com/Rokyyz/unit2/assets/134658259/1443c891-8a7f-4e90-9141-ac65ce82dd78)

[1]

# Unit 2: A Distributed Weather Station for ISAK

## Criteria A: Planning

## Problem definition

A student in an international boarding school has been struggling with sleep quality and is complaining to the school's nurses about disrupted sleep, dry skin, dry throat, and nostrils. This is becoming a common trend on campus as nurses have received multiple similar complaints from other students. The nurses in the Health Center are guessing that this is due to dry air/low humidity levels in the air of the room. The nurses are keen on knowing if this is truly the issue at hand and if true, how to solve this issue. They want to know the precise data of humidity levels during the day as well as the temperature, to assess health risks, compare the living conditions of students from different houses, and think of methods to counteract this issue. The data can vary depending on the part of the room so nurses need the data to be collected from different parts of the room (recommended 3 different parts) to get the most accurate representation of the humidity and temperature levels.

## Success criteria

1. The gathered data and graphs provide a visual representation of the Humidity and Temperature values inside a student's room for 48 hours.
2. The local data will be recorded using a set of 3 sensors around the dormitory.
3. The solution provides mathematical modeling for the humidity and temperature levels in the room.
4. The solution provides an analysis of the humidity and temperature levels in the room using mean, standard deviation, minimum, maximum, and median.
5. The Local data is stored in a csv file and posted to the remote API server.
6. Create a prediction of the data for temperature and humidity inside the room for the following 12 hours
7. Create and present a scientific poster summarizing the visual representations, background research, methods used, model, and analysis.

## Design statement

Our group will create a device and program that will calculate both humidity and temperature in a room of a residential house on campus. To do this, we will use an Arduino Uno and three DHT11 sensors to collect data on the humidity and temperature in the room. The program will upload the collected data into a CSV file that will onward go to a outside API server in real-time to permanently store the data. We will use the DHT11 device to record the humidity and temperature inside of a room for 48 hours, and based on the data and results the nurses in the Health Center will be able to see and evaluate the information that the data presents with the help of visual representation - graphs and raw data with the help of a login token. From then on, the nurses can use the data collected to evaluate the living conditions and compare them with their information on optimal humidity and temperature in healthy living conditions. This project will take approximately 4 weeks and will be evaluated according to the criteria shown above.

## Proposed Solution
Taking into consideration that the client wants the solution to be at an adequate/low price but with data that can be trusted, analysed because it is precise. In order to complete these wishes of the client, the best solution found for this request was a low-cost sensor device for humidity and temperature and a custom data script that can process and analyze the data recorded. The device For a low cost is the DHT11 sensor which is offered online for less than 5 USD and provides adequare precision and range for the client requirements (Temperature Range: 0°C to 50°C, Humidity Range: 20% to 90%). Similar devices such as the DHT22, AHT20 or the AM2301B [^2] have higher specifications, however the DHT11 uses a simple serial communication (SPI) rather than more eleborated protocols such as the I2C used by the alternatives. For the range, precision and accuracy required in this applicaiton the DHT11 provides the best compromise. Connecting the DHT11 sensor to a computer requires a device that provides a Serial Port communication. A cheap and often used alternative for prototyping is the Arduino UNO microcontroller [^3]. "Arduino is an open-source electronics platform based on easy-to-use hardware and software"[^4]. In additon to the low cost of the Arduino (< 6USD), this devide is programable and expandable[^1]. Other alternatives include diffeerent versions of the original Arduino but their size and price make them a less adequate solution.

Considering the budgetary constrains of the client and the hardware requirements, the software tool that I proposed for this solution is Python. Python's open-source nature and platform independence contribute to the long-term viability of the system. The use of Python simplifies potential future enhancements or modifications, allowing for seamless scalability without the need for extensive redevelopment [^5][^6]. In comparison to the alternative C or C++, which share similar features, Python is a High level programming language (HLL) with high abstraction [^7]. For example, memory management is automatic in Python whereas it is responsability of the C/C++ developer to allocate and free up memory [^7], this could result in faster applications but also memory problems. In addition a HLL language will allow me and future developers extend the solution or solve issues proptly.  

**Design statement**

``` Fill out here```

## Success Criteria

[^1]: Industries, Adafruit. “DHT11 Basic Temperature-Humidity Sensor + Extras.” Adafruit Industries Blog RSS, https://www.adafruit.com/product/386. 
[^2]: Nelson, Carter. “Modern Replacements for DHT11 and dht22 Sensors.” Adafruit Learning System, https://learn.adafruit.com/modern-replacements-for-dht11-dht22-sensors/what-are-better-alternatives.   
[^3]:“How to Connect dht11 Sensor with Arduino Uno.” Arduino Project Hub, https://create.arduino.cc/projecthub/pibots555/how-to-connect-dht11-sensor-with-arduino-uno-f4d239.  
[^4]:Team, The Arduino. “What Is Arduino?: Arduino Documentation.” Arduino Documentation | Arduino Documentation, https://docs.arduino.cc/learn/starting-guide/whats-arduino.  
[^5]:Tino. “Tino/PyFirmata: Python Interface for the Firmata (Http://Firmata.org/) Protocol. It Is Compliant with Firmata 2.1. Any Help with Updating to 2.2 Is Welcome. the Capability Query Is Implemented, but the Pin State Query Feature Not Yet.” GitHub, https://github.com/tino/pyFirmata. 
[^6]:Python Geeks. “Advantages of Python: Disadvantages of Python.” Python Geeks, 26 June 2021, https://pythongeeks.org/advantages-disadvantages-of-python/. 
[^7]: Real Python. “Python vs C++: Selecting the Right Tool for the Job.” Real Python, Real Python, 19 June 2021, https://realpython.com/python-vs-cpp/#memory-management. 

1. The solution provides a visual representation of the Humidity and Temperature values inside a dormitory (Local) and outside the house (Remote) for a period of minimum 48 hours. 
1. ```[HL]``` The local variables will be measure using a set of 3 sensors around the dormitory.
2. The solution provides a mathematical modelling for the Humidity and Temperature levels for each Local and Remote locations. ```(SL: linear model)```, ```(HL: non-lineal model)```
3. The solution provides a comparative analysis for the Humidity and Temperature levels for each Local and Remote locations including mean, standad deviation, minimum, maximum, and median.
4. ```(SL)```The Local samples are stored in a csv file and ```(HL)``` posted to the remote server as a backup.
5. The solution provides a prediction for the subsequent 12 hours for both temperature and humidity.
6. The solution includes a poster summarizing the visual representations, model and analysis created. The poster includes a recommendation about healthy levels for Temperature and Humidity.

_TOK Connection: To what extent does ```the use of data science``` in climate research influence our understanding of environmental issues, and what knowledge questions arise regarding the ```reliability, interpretation, and ethical implications``` of data-driven approaches in addressing climate change_

1. How does our use of technology shape our understanding of the environment
2. What responsibilities do we have as technologists when it comes to handling personal data related to our living spaces?
3. What cultural and contextual factors might impact our interpretation of the results, especially when comparing our local readings with those from the campus? 

# Criteria B: Design

## System Diagram **SL**

![SL](https://github.com/comsci-uwc-isak/unit2_2023/assets/53995212/6161f2f6-67c5-4742-9961-e46475376370)

**Fig.1** shows the system diagram for the proposed solution (**SL**). The indoor variables will be measured using an Arduino microprocessor and one sensor DHT11 conencted to the local computer (Laptop) located inside a room. The outdoor variables will be requested to the remote server using a GET request to the API of the server at ```192.168.6.153/readings```. The local values are stored in a CSV database locally.


![HL](https://github.com/comsci-uwc-isak/unit2_2023/assets/53995212/4891d5e9-b8ab-46ed-bd75-b606e25e3383)

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
