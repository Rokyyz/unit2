![weather stat](https://github.com/Rokyyz/unit2/assets/134658259/1443c891-8a7f-4e90-9141-ac65ce82dd78)

[^1]

# Unit 2: A Distributed Weather Station for ISAK

## Criteria A: Planning

## Problem definition

A student in an international boarding school has been struggling with sleep quality and is complaining to the school's nurses about disrupted sleep, dry skin, dry throat, and nostrils. This is becoming a common trend on campus as nurses have received multiple similar complaints from other students. The nurses in the Health Center are guessing that this is due to dry air/low humidity levels in the air of the room. The nurses are keen on knowing if this is truly the issue at hand and if true, how to solve this issue. They want to know the precise data of humidity levels during the day as well as the temperature, to assess health risks, compare the living conditions of students from different houses, and think of methods to counteract this issue. The data can vary depending on the part of the room so nurses need the data to be collected from different parts of the room (recommended 3 different parts) to get the most accurate representation of the humidity and temperature levels.

## Success criteria

1. The gathered data and graphs provide a visual representation of the Humidity and Temperature values inside (local) and outside (remote) a student's room for a minimum of 48 hours.
2. The local data will be recorded using a set of 3 sensors around the dormitory.
3. The solution provides a non-linear mathematical modelling for the humidity and temperature levels both inside and outside the room.
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

## System Diagrams 

# System diagram for gathering data, DHT11 + Arduino UNO connection with computer

<img width="987" alt="Screenshot 2023-12-11 at 20 18 12" src="https://github.com/Rokyyz/unit2/assets/134658259/194524e9-6fd6-4cc6-88e3-6e59bab50c83">

<img width="987" alt="Screenshot 2023-12-11 at 20 18 41" src="https://github.com/Rokyyz/unit2/assets/134658259/9a954f50-c879-46d3-baab-7ae2b4e9bc98">

<img width="982" alt="Screenshot 2023-12-11 at 20 19 06" src="https://github.com/Rokyyz/unit2/assets/134658259/0efb6c45-9912-44f9-8bc0-4d14f7efcf37">

 # System diagram for gathering data into a CSV file and API server

<img width="943" alt="Screenshot 2023-12-11 at 20 22 00" src="https://github.com/Rokyyz/unit2/assets/134658259/5399887e-c1e7-4abc-b9c7-a70d7b31925b">

<img width="948" alt="Screenshot 2023-12-11 at 20 22 19" src="https://github.com/Rokyyz/unit2/assets/134658259/ae30c1cc-4daf-435a-bc90-626d54c1de7b">

# List of materials

3 DHT11 sensors


1 breadboard


1 Arduino UNO


2 male connecting wires


6 female connecting wires


6 long wires


1 remote desktop


## Record of Tasks


| Task no | Planned action                                                                                                                 | Planned outcome                                                                                                                                                                                | Time estimate   | Target completion date | Criterion |
|---------|--------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|------------------------|-----------|
| 1       | Familiarize and create success criteria                                                                                        | Create success criteria that will guide us into fully accomplishing project's, clients needs, as well as gain knowledge on what to do in what order                                            | 15min           | Nov 23                 | A         |
| 2       | Create the problem definition                                                                                                  | A clear problem definition on Github                                                                                                                                                           | 10min           | Nov 23                 | A         |
| 3       | Create the design statement                                                                                                    | A clear design statement that suits the needs of the client in hand                                                                                                                            | 15min           | Nov 23                 | A         |
| 4       | Create the rationale for proposed solution                                                                                     | A clear justification that suits both the client and developer                                                                                                                                 | 30min           | Nov 23                 | A         |
| 5       | Create server account                                                                                                          | Create an account on the API server where we can save data and use as storage                                                                                                                  | 30min           | Nov 27                 | B         |
| 6       | Create new sensor id for server                                                                                                | Create new sensor ID in the API server so we can store the data on their names                                                                                                                 | 30min           | Nov 27                 | B         |
| 7       | Request hardware for the projeect                                                                                              | Request and know the necessary technology to successfully carry out the data recordings                                                                                                        | 15min           | Nov 30                 | B         |
| 8       | Sign a document for hardware and proper use of the given technology                                                            | Get given the requested hardware and be allowed to work with it knowing no bad intentions will be bond to our activities                                                                       | 5min            | Nov 30                 | B         |
| 9       | Create code in the Arduino UNO                                                                                                 | The code is valid, uploadable to the Arduino UNO, works as intended, and records values for 3 sensors, their detected humidity and temperature                                                 | 75min           | Nov 30                 | B         |
| 10      | Create code for the Arduino UNO in Pycharm                                                                                     | Create code that works, it reads the sensor data from the Arduino UNO and puts it in a CSV file as well as uploads it to the API server                                                        | 40min           | Dec 1                  | B         |
| 11      | Set up the Arduino UNO with the 3 sensors and the bread board together with the computer                                       | All the technology is connected and the sensors are set up in the room in 3 different locations                                                                                                | 70min           | Dec 1                  | B         |
| 12      | Create code to sign up for the server                                                                                          | Allows the user to create a username and password for the server                                                                                                                               | 30min           | Dec 2                  | B         |
| 13      | Create code to log in to the server                                                                                            | Allows the user to log into their account they had created                                                                                                                                     | 30min           | Dec 2                  | B         |
| 14      | Create a CSV file and 6 API server spots to send data from the 3 sensors of their readings of humidity and temperature levels. | Setup both the CSV file and API to which the data will be sent every 5 minutes for minimum of 48 hours                                                                                         | 40min           | Dec 2                  | B         |
| 15      | Create code for collecting the data and sending it to both the API server and the CSV file                                     | Make sure that the code is successfully connected with both CSV and API servers and can successfully send the obtained data to both of them                                                    | 20min           | Dec 4                  | B         |
| 16      | Make a code to get the data from the sensors in a refined format and send it to the CSV file, and the API server               | The data is stripped from unwanted symbols for easier work and analysis further on                                                                                                             | 20min           | Dec 4                  | B         |
| 17      | Start recording the data with sensors                                                                                          | The data is starting to be recorded and it is then successfully added to API server and CSV file                                                                                               | minimum 2880min | Dec 6                  | B         |
| 18      | Improving the code                                                                                                             | Making sure the code is concise, and efficient                                                                                                                                                 | 35min           | Dec 6                  | B         |
| 19      | Work on the development part in criteria C                                                                                     | Provided a explanation and process behind the data recording in a .csv file, and API server                                                                                                    | 90min           | Dec 6                  | C         |
| 20      | Writing code for the creation of the diagrams from data                                                                        | Data of readings from all 3 sensors and their humidity, temperature, line of best fit, prediction, mean of temperature and humidity, standard deviation, minimum, maximum, and median are made | 300min+         | Dec 7                  | B         |
| 21      | Comparison from local and remote data of sensors in graph format using code                                                    | Data of 3 sensors recording remote data are compared with a similar day of recordings from local data                                                                                          | 30min           | Dec 8                  | B         |
| 22      | Work on the development part in criteria C                                                                                     | Show how the 3 sensors we used were set up as well as the different locations inside the room from which the temperature and humidity were measured                                            | 15min           | Dec 8                  | C         |
| 23      | Write the test plan                                                                                                             | Procedures in which one should take to test the program and descriptions of the expected outcome of each test is on Github                                                                     | 90min           | Dec 8                  | B         |
| 24      | Work on the development part in criteria C                                                                                     | Have a visual representation with an explanation with easy-to-understand graphs of the data which fulfills criteria 1 stated by the client                                                     | 30min           | Dec 9                  | C         |
| 25      | Work on the development part in criteria C                                                                                     | Have visual representation of the prediction for the data in the following 12 hours                                                                                                            | 30min           | Dec 9                  | C         |
| 26      | Draw and describe the flow diagrams                                                                                            | Drawn flow diagrams for different parts of the code for problem solving and important parts of the code along a brief explanation                                                              | 140min          | Dec 10                 | B         |
| 27      | Describe important parts of the code                                                                                           | Description of important parts of the code and how it works is made                                                                                                                            | 130min          | Dec 11                 | B         |
| 28      | Work on the development part in criteria C                                                                                     | Show the use of mathematical tools for the comparison of the humidity and temperature data locally and remotly                                                                                 | 30min           | Dec 11                 | C         |
| 29      | Create a scientific poster                                                                                                     | The scientific poster for the project is created and ready to be presented                                                                                                                     | 120min          | Dec 13                 | B         |
| 30      | Create a video including explaining a bit of code and presentation of the scientific poster                                    | All of our work surrounding code and overall problem solving from clients wants are represented in a video                                                                                     | 20min           | Dec 14                 | B         |

## Test Plan

| Test type                                           | Target                                                                                                                                                                                                                                                                                                                   | Procedure                                                                                                                                                                                                                                                                                                                                                                                   | Expected outcome                                                                                                                                                                                                                                                                |
|-----------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Functional: Integrational testing                   | Connect to CSV and API server                                                                                                                                                                                                                                                                                            | 1. Open the Python file containing the code created to connect to the server and CSV file, and extract, and send data to a suitable place 2. Run the program 3. Check in the terminal if data is being collected and uploaded in the right format to the .csv file and the server by looking at the adequate sensor id and see if it matches the id of sensors used for the data collecting | The program should run and print data into the remote server. All sensors are collecting data, and uploading it onto both a CSV file and the remote server in a correct, easy-to-work-with style.                                                                               |
| Functional: Integrational testing                   | Sensor connectivity                                                                                                                                                                                                                                                                                                      | 1. Connect the 3 DHT11 sensors to the breadboard which is connected to the Arduino UNO. 2. Run read function which both collects humidity and temperature levels from all 3 sensors and returns a message if they are not properly connected, and prints the values in the terminal if they are getting written also in the CSV file and API server                                         | The program should return readings for all sensors connected, and if there is an error within any of the sensors, an error message should appear.                                                                                                                               |
| Functional: Integrational testing                   | Login and signup                                                                                                                                                                                                                                                                                                         | 1. Open the Python file containing the code created to both signup and login for the API server to access the recorded data. 2. Create a username and password that will serve as a key to access the stored data. 3. Make sure that log in is also possible.                                                                                                                               | The program should allow to create an account with a never-before-existing username and password attached to it. If any problems would arise, like an account already existing, an error message should appear. This should serve as a key to access the data stored on demand. |
| Non-functional：Load testing                        | Testing if the program has little lag, stoppages or glitches due to the amount of time the program is run (48 hours) or wifi issues. See if more data equals to slower processing speeds of the program.                                                                                                                 | 1. Run the program. 2. Continously check up on the code, after waking up, coming from class, to and from lunch, before sleep, etc.                                                                                                                                                                                                                                                          | All data is up to date, and the program is still continously running and recoridng data wihtout any glitches or lag.                                                                                                                                                            |
| Non-functional: Performance testing (response time) | Testing if the sensor responds quickly to the running program and see how long it takes for the sensor to register and print out the current temperature and humidity                                                                                                                                                    | 1. Open the Python file containing the code created to print the current temperature and humidity the sensor collects. 2. Monitor the terminal, CSV file to see speed of the data addition and accuracy                                                                                                                                                                                     | The program returns the current temperature and humidity quickly, without pauses and disturbances, and the sensor collects the data without any lag or delay.                                                                                                                   |
| Non-functional：Code review                         | Reviewing if the code has too many or non-efficient comments, functions, and variable names that would make the code too lengthy, hard to understand and overview, and find ways to make it more concise and structured. There are no inputs, because the review is based on monitoring the quality of the code written. | 1. Involve a person not connected with this project, so they wouldn't be familiar with the code and methods used. 2. Gather feedback from the external developer on which parts are not understandable, too lengthy, can be improved on in terms of efficiency, which names, functions, and variables are not logically made and named.                                                     | The developer gives feedback on the code, which includes comments explaining what are the prominent issues and if some reoccur. That includes the names of variables and the crosscheck if they are simple and it is easy to understand their usage in the program is           |

# Flow Diagrams


**Fig 6**
![IMG_1971](https://github.com/Rokyyz/unit2/assets/134658259/b3c76488-4bce-491d-ae79-e577c13a0ea8)

![IMG_1972](https://github.com/Rokyyz/unit2/assets/134658259/2ab3bbbd-f0f0-4057-89e1-c435547d8a79)



**Fig 7**


![CommSci 9](https://github.com/Rokyyz/unit2/assets/134658259/e3b90504-0645-49c2-b968-0621d472f23a)
![CommSci 10](https://github.com/Rokyyz/unit2/assets/134658259/861f0ad6-51b0-4cde-983f-686d36cbc6ad)



**Fig 8**

![IMG_1975](https://github.com/Rokyyz/unit2/assets/134658259/14261893-de77-4210-811a-6bfd4cffd31a)
![CommSci 11](https://github.com/Rokyyz/unit2/assets/134658259/6e03b5b7-0672-42e0-b016-7f7c924d9e0f)



**Fig 9**


![IMG_1977](https://github.com/Rokyyz/unit2/assets/134658259/59d52716-1e88-4fe2-afc6-43cd5e83049f)
![IMG_1978](https://github.com/Rokyyz/unit2/assets/134658259/4f059f4a-e894-45fe-bc0d-e2c59f4908f6)

# Criteria C: Development

## List of techniques used
1. Functions
2. For loops
3. Lists
4. Dictionaries
5. If/elif statements
6. Matplotlib's Pyplot to generate graphs
7. Matplotlib's GridSpec to generate composite graphs
8. Numpy to calculate standard deviation and generate quadratic models
9. Reading from csv files
10. Appending to csv files
11. Logging into online API servers
12. Requests library to work with online API servers
13. Reading from online API servers
14. Posting data to online API servers
15. Arduino IDE to work with Arduino
16. DHT library to work with DHT11 sensors in Arduino
17. Serial library to work with Arduino in Python
18. Time library to create pauses between readings from DHT sensors

## 1. The gathered data and graphs provide a visual representation of the Humidity and Temperature values inside (local) and outside (remote) a student's room for a minimum of 48 hours.
We used the pyplot function from the Matplotlib library in order to create graphs that visualize the data. We also used the GridSpec function from the same library to present the readings from all the sensors side by side. This, in conjunction with plt.xlim() and plt.ylim() which make the graphs depicting local data have the same scale, makes it easier to see the difference between the sensors' data. The remote sensor has its own scale because it has a higher range of values and adjusting the local sensors' scales to fit it would make them harder to read.

Another technique we used to make the visual representation easier to understand is the smoothing function. Through it, we utilized the Abstraction part of CT: by taking the average out of a certain size window of values and only presenting those averages on the graph, we were able to ignore most outliers and show the most important information, which is the general trend of the data. This also made the graph more visually appealing.

We also utilized Abstraction when creating a graph with the mean local humidity and temperature with a quadratic model attached to it. Both the mean and the model serve to better show the general trend of data from all of the local sensors, while ignoring less relevant information. We utilized the same quadratic model for the graph of the remote sensor.

However, we had a problem when trying to gather data from the remote sensor . We had 3 remote sensors to choose from with 6 sensors being registered in the remote API server because humidity and temperature are counted seperately. The pair of sensors 0 and 3 were clearly broken, so we did not consider them. That left us with pairs 1, 4 and 2, 5, both of which had problems most notably in the temperature. From around the 750th x-value and onwards the graphs flatten, which leaves those values out of consideration. The first sensor had an outlier in the form of temperature reaching over 30C, which definitely did not happen during the time in November when that value was taken. The second sensor had values consistently above 15C, when past wheather data showed us that 12C was the highest temperature recorded at that time. Thus, we decided to use the November readings form sensors 1 and 4. We realize that the outlier makes this data not completely reliable, but we believe that this is the best out of the available options.
Another problem that this creates is that the available remote sensor readings are only 56 hours long, which is 6 hours below the readings we have for our local sensors. However, even 56 hours is well above the 48 hour minimum required from us, so we believe that adjusting the graphs with the remote data accordingly will alleviate this issue.


## 2. The local data will be recorded using a set of 3 sensors around the dormitory.
In order to fulfill success criterion 2 we used 3 DHT11 sensors to collect data on the room's humidity and temperature. We decided to place the first sensor near the floor next to the radiator, the second one on the table, and the third one near the ceiling next to the window. We knew that temperature tends to be lower near the floor and higher near the ceiling, so we were curious to see how the sensors would reflect that. We also wanted to see how a running radiator and open window would impact the data for sensors 1 and 3. The sensor on the table was supposed to be the average

We also decided to place a humidifier a few hours after the sensors started to collect data. The humidity is known to be low in the students' rooms and the DHT11 sensors cannot detect humidity below 20 per cent, so we were afraid that the sensors would keep sending the value 20. We hoped that the humidifier would provide variety to the data.

We also decided to collect data for 62 hours, from 2023-12-06 23:27 (Wednesday) to 2023-12-09 13:22 (Saturday). We knew that the weather on Saturday was supposed to be sunny from the weather forecast, and we were curious how it would impact the sensor readings, so we went over the 48 hour minimum.
## 3. The solution provides a non-linear mathematical modelling for the humidity and temperature levels both inside and outside the room.
In order to fulfill success criterion 3 we used the Numpy library to create a quadratic mathematical modelling for both local and remote data. We then proceeded to create three different graphs: one showing the contrast between the mean local data and the qudratic model for that data, the second showing the contrast between the remote data and the quadratic model for that data, and finally the third showing the contrast between local and remote models. The first two graphs are able to show the client how reliably the quadratic models cover the data they are supposed to represent. While the models have the benefit of showing the trends in the data most clearly, they do so by sacrificing a lot of details. These graphs serve to show that to the client so that they know this limitation. The third graph serves to show the contrast between general trends in local and remote data, so that the client has an idea on how the two types of data differ.
## 4. The solution provides a comparative analysis of the humidity and temperature levels in the room using mean, standard deviation, minimum, maximum, and median.
In order to fulfill success criterion 4, we used the Decomposition part of CT. We split the mean, standard deviation, minimum, maximum, and median for both humidity and temperature into their own individual problems, solving them one by one through each of the 744 iterations of the for loop (which represents 62 hours) and appending the result into the respective list. We then split those values into 4 different graphs, 2 for humidity and 2 for temperature, with one graph representing the mean and median, and the other representing the mean, standard deviation, minimum, and maximum. We decided to split the median from the rest of the values because the graph was too hard to read with so many values at once.

The advantage that these values give is that the client can see how much the values across the three local sensors differ from each other through pattern recognition. The lines on the graph being close to each other represents similar readings across the three sensors, while the lines being further away represents differing readings.
## 5. The Local data is stored in a csv file and posted to the remote API server as a backup.
We created three csv files for each of the three local sensors. In order to store the data from the sensors in the correct csv file, we created an algorithm that splits the data sent over from Arduino to Python by comma and checks the last value, which is the number of the sensor that sent the data. It then utilizes the with open function and sets the mode to append in order to send the data to the corresponding csv file.

As for sending the data to the remote API server, we decided to wait until we had all the values in the csv file. We decided that this would be easier because of the faulty connection to the WiFi in the room downstairs where the data was being taken. Were we to send the data to the API server over the 48 hours, this problem would have certainly created gaps in the data, which would invalidate it.

When we were preparing to send the data from the csv files to the API server, we noticed a pattern in the code. Hence, instead of running three similar blocks of code for all three of the csv files, we created a function that took the name of the csv file and the id's of the humidity and temperature sensors. This made the code more condensed and visually appealing.
In the function we extract the data from the chosen csv file and iterate over it line by line by using a for loop. We then split the lines by comma to get the humidity, temperature, and the datetime. We then modify the datetime to fit the API server's format. Finally we post the humidity and temperature together with the datetime to the specified sensors.

Thus, we have fulfilled criterion 5
## 6. Create a prediction of the data for temperature and humidity inside the room for the following 12 hours
When we created the quadratic model for the mean of the data from the local sensor, we made sure to extend the model's domain by 12 hours, which created our prediction. We did the same for the model for the remote data, but instead extended the domain by 18 hours in order to match the local model. This is because the remote sensor has 6 hours less of data for reasons stated earlier.
Thus we have fulfilled success criterion 6
## 7. The solution includes a poster summarizing the visual representations, model and analysis created. The poster includes a recommendation about healthy levels for Temperature and Humidity


# Criteria D: Functionality

A 7 min video demonstrating the proposed solution with narration

