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
| 19      | Work on the development part in criteria C                                                                                     | Provided an explanation and process behind the data recording in a .csv file, and API server, including CT.                                                                                                    | 90min           | Dec 6                  | C         |
| 20      | Writing code for the creation of the diagrams from data                                                                        | Data of readings from all 3 sensors and their humidity, temperature, line of best fit, prediction, mean of temperature and humidity, standard deviation, minimum, maximum, and median are made | 300min+         | Dec 7                  | B         |
| 21      | Comparison from local and remote data of sensors in graph format using code                                                    | Data of 3 sensors recording remote data are compared with a similar day of recordings from local data                                                                                          | 30min           | Dec 8                  | B         |
| 22      | Work on the development part in criteria C                                                                                     | Show how the 3 sensors we used were set up as well as the different locations inside the room from which the temperature and humidity were measured, including CT.                                            | 15min           | Dec 8                  | C         |
| 23      | Write the test plan                                                                                                             | Procedures in which one should take to test the program and descriptions of the expected outcome of each test is on Github                                                                     | 90min           | Dec 8                  | B         |
| 24      | Work on the development part in criteria C                                                                                     | Have a visual representation with an explanation with easy-to-understand graphs of the data which fulfills criteria 1 stated by the client, including CT                                                     | 30min           | Dec 9                  | C         |
| 25      | Work on the development part in criteria C                                                                                     | Have visual representation of the prediction for the data in the following 12 hours, including CT.                                                                                                            | 30min           | Dec 9                  | C         |
| 26      | Draw and describe the flow diagrams                                                                                            | Drawn flow diagrams for different parts of the code for problem solving and important parts of the code along a brief explanation                                                              | 140min          | Dec 10                 | B         |
| 27      | Describe important parts of the code                                                                                           | Description of important parts of the code and how it works is made                                                                                                                            | 130min          | Dec 11                 | B         |
| 28      | Work on the development part in criteria C                                                                                     | Show the use of mathematical tools for the comparison of the humidity and temperature data locally and remotely, including CT                                                                                 | 30min           | Dec 11                 | C         |
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

![IMG_1971](https://github.com/Rokyyz/unit2/assets/134658259/b3c76488-4bce-491d-ae79-e577c13a0ea8)
**Fig 6**
The figure shows the flow diagram used to access the data from the server. The function extracts the data from the sensors with an id indicated. The range of the sensor_ids used while collecting temperature and humidity data during the minimum of 48 hours of data collecting inside the room. By using this function only the relevant data during that time will be used and later on presented, preventing any mistakes in the data correlation between the readings inside and outside the room.

![IMG_1972](https://github.com/Rokyyz/unit2/assets/134658259/2ab3bbbd-f0f0-4057-89e1-c435547d8a79)
**Fig 7**
## Explanation of accessing, and adding data from sensors

![CommSci 12](https://github.com/Rokyyz/unit2/assets/134658259/babcc7a9-43ad-4f86-84ac-41f3ed35ce1e)

**Fig 8**
The figure shows the flow diagram used to allow reading/appending data to an empty list, during the 48-hour recording period from the sensors with an ID indicated. By using this function it reads the data in the csv that was recorded in the sensors and it strips it off of symbols that make the data unusable to perform further actions, like using the data for graph point plotting
![CommSci 13](https://github.com/Rokyyz/unit2/assets/134658259/1d4411d1-e8ac-4513-8d7d-b32618686400)

**Fig 9**
## Explanation of the function that allows to read/append data to an empty list

![IMG_1975](https://github.com/Rokyyz/unit2/assets/134658259/14261893-de77-4210-811a-6bfd4cffd31a)
**Fig 10**
The figure shows the flow diagram used to smooth the data obtained from server data during the 48 hours required for the project when plotting graphs. It also showed the explanation of each step for the flow diagram used to smooth the data obtained from the server.
![CommSci 11](https://github.com/Rokyyz/unit2/assets/134658259/6e03b5b7-0672-42e0-b016-7f7c924d9e0f)
**Fig 11**
## Explanation of data smoothing

![IMG_1977](https://github.com/Rokyyz/unit2/assets/134658259/59d52716-1e88-4fe2-afc6-43cd5e83049f)
**Fig 12**
The flow diagram of the model function takes input data (x and y), fits a quadratic polynomial to the data, and then extends the x-values into the future. It returns a tuple containing the predicted values (model) based on the quadratic polynomial and the extended x-values (future_x).
![IMG_1978](https://github.com/Rokyyz/unit2/assets/134658259/4f059f4a-e894-45fe-bc0d-e2c59f4908f6)
**Fig 13** 
## Explanation of prediction for data, fitting quadratic polynomials to the data, extending the x values.

## Data Storing
## 1. CSV Files
We one csv file per sensor and sent the data gathered from the sensors to the correct csv file.

![csv1](https://github.com/Rokyyz/unit2/assets/142757981/463914e0-fb52-4d8c-809a-83f047415221)

**Fig 14**
Data from sensor 1 in 'sensor1.csv' file

![csv2](https://github.com/Rokyyz/unit2/assets/142757981/6e4e2394-71f5-441f-8cb0-29c6261ef866)

**Fig 15**
Data from sensor 2 in 'sensor2.csv' file

![csv3](https://github.com/Rokyyz/unit2/assets/142757981/0f6a82c2-05d5-4fa1-baf7-abf9733796d8)

**Fig 16**
Data from sensor 3 in 'sensor3.csv' file



## 2. Remote API Server
Once we had all of the values stored in the csv files, we uploaded the data to the remote API server.

![API](https://github.com/Rokyyz/unit2/assets/142757981/b233285b-0935-438a-9956-2b5763ab5aa3)
**Fig 17**
Data uploaded on the server


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
We used the pyplot function from the Matplotlib library in order to create graphs that visualize the data. We also used the GridSpec function from the same library to present the readings from all the sensors side by side (**Fig 1.1**). This, in conjunction with plt.xlim() and plt.ylim() which make the graphs depicting local data have the same scale, makes it easier to see the difference between the sensors' data (**Code 1.1**). The remote sensor has its own scale because it has a higher range of values and adjusting the local sensors' scales to fit it would make them harder to read.

Another technique we used to make the visual representation easier to understand is the smoothing function. Through it, we utilized the Abstraction part of CT: by taking the average out of a certain size window of values and only presenting those averages on the graph (one value per hour), we were able to ignore most outliers and show the most important information, which is the general trend of the data. This also made the graph more visually appealing.

We also utilized Abstraction when creating a graph with the mean local humidity and temperature with a quadratic model attached to it (**Fig 1.2**). For the mean, we recognized the pattern calculating the mean and utilized it through a for loop that iterated over all of the readings from the local sensors (**Code 1.2**). For the model, we created an algorithm in the form of the qmodel function. This function begins by creating a quadratic model by making use of the polyfit function from the Numpy library. Then, if a prediction is requested for it, it goes on to create a new list of x-values that it then iterates over to plot the model (**Code 1.3**). Both the mean and the model serve to better show the general trend of data from all of the local sensors, while ignoring less relevant information. We utilized the same quadratic model for the graph of the remote sensor (**Fig 1.3**)(**Code 1.4**).

However, we had a problem when trying to gather data from the remote sensor . We had 3 remote sensors to choose from with 6 sensors being registered in the remote API server because humidity and temperature are counted seperately (**Fig 1.4**). Sensors 0 and 3 were clearly broken, so we did not consider them. That left us sensors 1 and 2 for temperature and sensors 4 and 5 for humidity, all of which had their problems. From around the 750th x-value and onwards the graphs flatten, which leaves those values out of consideration. The first sensor had an outlier in the form of temperature reaching over 30C, which definitely did not happen during the time in November when that value was taken. The second sensor had values consistently above 15C, when past wheather data showed us that 12C was the highest temperature recorded at that time. Thus, we decided to use the November readings from sensors 1 for the temperature. We realize that the outlier makes this data not completely reliable, but we believe that this is the best out of the available options.
As for the humidity sensor, we decided to use sensor 5 as it did not have the sudden spikes that sensor 4 had.
Another problem that this creates is that the available remote sensor readings are only 56 hours long, which is 6 hours below the readings we have for our local sensors. However, even 56 hours is well above the 48 hour minimum required from us, so we believe that adjusting the graphs with the remote data accordingly will alleviate this issue.


![Sensor Readings](https://github.com/Rokyyz/unit2/assets/142757981/b9aacc07-bb0b-4ec2-afb5-43df3f2d5086)

**Fig 1.1** 
A composite plot containing the graphs of all the sensors' recordings. Plots for local sensors have the same scale, plots for remote sensor have different scale



![Local Average Readings](https://github.com/Rokyyz/unit2/assets/142757981/239fb2c1-a2eb-48ef-b0fe-45f6c884c796)

**Fig 1.2**
A graph showing the mean humidity and temperature from the local sensors + quadratic model of the data



![Remote Readings](https://github.com/Rokyyz/unit2/assets/142757981/fbc62543-1f73-4337-a171-49cd16a268f9)

**Fig 1.3**
A graph showing the data collected from the remote sensor + quadratic model of the data



![Remote Sensors](https://github.com/Rokyyz/unit2/assets/142757981/2576888c-50fc-47ae-bc9c-9d15009f6e25)

**Fig 1.4**
A graph showing the data collected from all three remote sensors. The first three plots are temperature and the last three are humidity.



```.py
fig = plt.figure(figsize=(10, 8))
grid = GridSpec(2, 4, figure=fig)

box1 = fig.add_subplot(grid[0, 0])
x, y = smoothing(x=s1['h'], size_window=12)
plt.ylabel('Humidity (%)', fontsize=16)
plt.title('Sensor 1')
plt.ylim(19, 49)
plt.plot(x, y)

box2 = fig.add_subplot(grid[1, 0])
x, y = smoothing(x=s1['temp'], size_window=12)
plt.ylabel('Temperature (C)', fontsize=16)
plt.ylim(16, 33)
plt.plot(x, y)

box3 = fig.add_subplot(grid[0, 1])
x, y = smoothing(x=s2['h'], size_window=12)
plt.plot(x, y)
plt.title('Sensor 2')

box4 = fig.add_subplot(grid[1, 1])
x, y = smoothing(x=s2['temp'], size_window=12)
plt.ylim(16, 33)
plt.plot(x, y)

box5 = fig.add_subplot(grid[0, 2])
x, y = smoothing(x=s3['h'], size_window=12)
plt.title('Sensor 3')
plt.plot(x, y)

box6 = fig.add_subplot(grid[1, 2])
x, y = smoothing(x=s3['temp'], size_window=12)
plt.ylim(16, 33)
plt.plot(x, y)

box7 = fig.add_subplot(grid[0, 3])
x, y = smoothing(x=s_outside['h'], size_window=12)
plt.title('Remote Sensor')
plt.xlim(0, 62)
plt.plot(x, y)

box8 = fig.add_subplot(grid[1, 3])
x, y = smoothing(x=s_outside['temp'], size_window=12)
plt.xlim(0, 62)
plt.plot(x, y)

fig.text(0.5, 0.05, 'Time (hours)', ha='center', va='center', fontsize=16)
plt.show()
```

**Code 1.1**
Code for constructing the composite plot with data from all of the sensors



```.py
avg_h = []
avg_temp = []
for i in range(len(s1['h'])):
    avg_h.append((s1['h'][i] + s2['h'][i] + s3['h'][i]) / 3)
    avg_temp.append((s1['temp'][i] + s2['temp'][i] + s3['temp'][i]) / 3)


plt.subplot(2, 1, 1)
x, y = smoothing(x=avg_h, size_window=12)
h_model, x1 = qmodel(x, y, 12)
plt.plot(x, y, label='Average')
plt.plot(x1, h_model, label='Model')
plt.ylabel('Humidity (%)')
plt.legend()
plt.title('Local Average Humidity')

plt.subplot(2, 1, 2)
x, y = smoothing(x=avg_temp, size_window=12)
temp_model = qmodel(x, y, 12)[0]
plt.plot(x, y, label='Average')
plt.plot(x1, temp_model, label='Model')
plt.ylabel('Temperature (C)')
plt.xlabel('Time (hours)')
plt.legend()
plt.title('Local Average Temperature')
plt.subplots_adjust(hspace=0.5)

plt.show()
```

**Code 1.2**
Code for contructing the graph with the mean humidity and temperature from the local sensors and for creating appropriate quadratic models



```.py
def qmodel(x: list, y: list, prediction: int):
    a, b, c = np.polyfit(x, y, 2)
    model = []
    future_x = x.copy()
    for i in range(prediction):
        future_x.append(len(future_x))
    for i in range(len(future_x)):
        model.append(a * (i ** 2) + b * i + c)
    return model, future_x
```

**Code 1.3**
Code for the qmodel function



```.py
plt.subplot(2, 1, 1)
x, y = smoothing(x=s_outside['h'], size_window=12)
out_h_model, x2 = qmodel(x, y, 18)
plt.plot(x, y, label='Humidity')
plt.plot(x2, out_h_model, label='Model')
plt.ylabel('Humidity (%)')
plt.legend()
plt.title('Remote Humidity')

plt.subplot(2, 1, 2)
x, y = smoothing(x=s_outside['temp'], size_window=12)
out_temp_model = qmodel(x, y, 18)[0]
plt.plot(x, y, label='Temperature')
plt.plot(x2, out_temp_model, label='Model')
plt.ylabel('Temperature (C)')
plt.xlabel('Time (hours)')
plt.legend()
plt.title('Remote Temperature')
plt.subplots_adjust(hspace=0.5)
plt.show()
```

**Code 1.4**
Code for creating the graphs with the remote data and the appropriate quadratic models



## 2. The local data will be recorded using a set of 3 sensors around the dormitory.
In order to fulfill success criterion 2 we used 3 DHT11 sensors connected to an Arduino to collect data on the room's humidity and temperature (**Fig 2.1**). We decided to place the first sensor on the curtain next to the window which is at about half the room's height, the second one on the table, and the third one near the ceiling next to where the window opens (**Fig 2.2**). We knew that temperature tends to be lower near the floor and higher near the ceiling, so we were curious to see how the sensors would reflect that. We also wanted to see how an open window would impact the data for sensor 3.

We also decided to place a humidifier a few hours after the sensors started to collect data. The humidity is known to be low in the students' rooms and the DHT11 sensors cannot detect humidity below 20 per cent, so we were afraid that the sensors would keep sending the value 20. We hoped that the humidifier would provide variety to the data.

We also decided to collect data for 62 hours, from 2023-12-06 23:27 (Wednesday) to 2023-12-09 13:22 (Saturday). We knew that the weather on Saturday was supposed to be sunny from the weather forecast, and we were curious how it would impact the sensor readings, so we went over the 48 hour minimum.


![Arduino](https://github.com/Rokyyz/unit2/assets/142757981/1d96e07b-ade1-42f2-8753-6ed9d920502c)

**Fig 2.1**
Picture of the Arduino, the breadboard, and the wires connecting the sensors to the Arduino



![Sensors](https://github.com/Rokyyz/unit2/assets/142757981/9a600d0c-74e9-4427-a9b8-73aa0e03b7a5)

**Fig 2.2**
Picture of the locations of the sensors in the room



## 3. The solution provides a non-linear mathematical modelling for the humidity and temperature levels both inside and outside the room.
In order to fulfill success criterion 3 we used the Numpy library to create a quadratic mathematical modelling for both local and remote data. We then proceeded to create three different graphs: one showing the contrast between the mean local data and the quadratic model for that data (**Fig 3.1**), the second showing the contrast between the remote data and the quadratic model for that data (**Fig 3.2**), and finally the third showing the contrast between local and remote models (**Fig 3.3**). The first two graphs are able to show the client how reliably the quadratic models cover the data they are supposed to represent. While the models have the benefit of showing the trends in the data most clearly, they do so by sacrificing a lot of details. These graphs serve to show that to the client so that they know this limitation. The third graph serves to show the contrast between general trends in local and remote data, so that the client has an idea on how the two types of data differ.

![Local Average Readings](https://github.com/Rokyyz/unit2/assets/142757981/ad493311-05b8-40aa-a8b3-7ec9ca4acbb8)

**Fig 3.1**
Graph of the mean of the data from the local sensors and the quadratic model


![Remote Readings](https://github.com/Rokyyz/unit2/assets/142757981/64b6f3c7-e638-43da-b561-be1be233f78e)

**Fig 3.2**
Graph of the data from the remote sensor and the quadratic model


![Model Comparison](https://github.com/Rokyyz/unit2/assets/142757981/983d6436-13b9-4a0d-b624-9c4369ab73f9)

**Fig 3.3**
Graph comparing the quadratic models



```.py
plt.subplot(2, 1, 1)
plt.plot(x1, h_model, color='red', label='Local')
plt.plot(x2, out_h_model, color='blue', label='Remote')
plt.ylabel('Humidity (%)')
plt.legend()
plt.title('Local and Remote Humidity Models')

plt.subplot(2, 1, 2)
plt.plot(x1, temp_model, color='red', label='Local')
plt.plot(x2, out_temp_model, color='blue', label='Remote')
plt.ylabel('Temperature (C)')
plt.xlabel('Time (hours)')
plt.legend()
plt.title('Local and Remote Temperature Models')

plt.subplots_adjust(hspace=0.5)
plt.show()
```

**Code 3.1**
Code for creating the graphs that compare the local and remote models


## 4. The solution provides a comparative analysis of the humidity and temperature levels in the room using mean, standard deviation, minimum, maximum, and median.
In order to fulfill success criterion 4, we used the Decomposition part of CT. We split the mean, standard deviation, minimum, maximum, and median for both humidity and temperature into their own individual problems, solving them one by one through each of the 744 iterations of the for loop (which represents 62 hours) and appending the result into the respective list (**Code 4.1**). We then split those values into 4 different graphs, 2 for humidity and 2 for temperature, with one graph representing the mean and median, and the other representing the mean, standard deviation, minimum, and maximum. We decided to split the median from the rest of the values because the graph was too hard to read with so many values at once.

When plotting the standard deviation, we notice a pattern: we need to fill the space from the difference of the mean and standard deviation to the sum of the mean and standard deviation. Thus, we create a for loop that iterates 62 times (because of smoothing we have 1 value per hour) and appends to lists containing the upper and lower bounds of the standard deviation (**Code 4.2**). These are then used to represent the standard deviation on the plot.

The advantage that these values give is that the client can see how much the values across the three local sensors differ from each other through pattern recognition. The lines on the graph being close to each other represents similar readings across the three sensors (**Fig 4.3**, **Fig 4.4**), while the lines being further away represents differing readings (**Fig 4.1**, **Fig 4.2**).


![Min Max Humidity](https://github.com/Rokyyz/unit2/assets/142757981/123b1a6c-fe8c-4ffa-b68b-387325f85fa1)

**Fig 4.1**
Graph showing the mean, standard deviation, minimum, and maximum of the humidity recorded from the local sensors


![Median Humidity](https://github.com/Rokyyz/unit2/assets/142757981/52d80deb-1e6b-44dc-93bd-5ad14a745b52)

**Fig 4.2**
Graph showing the mean and median of the humidity recorded from the local sensors


![Min Max Temperature](https://github.com/Rokyyz/unit2/assets/142757981/ff12abca-8b3d-4938-a56a-c5e2b5383330)

**Fig 4.3**
Graph showing the mean, standard deviation, minimum, and maximum of the temperature recorded from the local sensors


![Median Temperature](https://github.com/Rokyyz/unit2/assets/142757981/9f084424-ec86-4824-a392-5716b070cf36)

**Fig 4.4**
Graph showing the mean and median of the temperature recorded from the local sensors


```.py
max_h = []
min_h = []
max_temp = []
min_temp = []
std_h = []
std_temp = []
med_h = []
med_temp = []

for i in range(744):
    max_h.append(max(s1['h'][i], s2['h'][i], s3['h'][i]))
    min_h.append(min(s1['h'][i], s2['h'][i], s3['h'][i]))
    max_temp.append(max(s1['temp'][i], s2['temp'][i], s3['temp'][i]))
    min_temp.append(min(s1['temp'][i], s2['temp'][i], s3['temp'][i]))
    std_h.append(float(np.std([s1['h'][i], s2['h'][i], s3['h'][i]])))
    std_temp.append(float(np.std([s1['temp'][i], s2['temp'][i], s3['temp'][i]])))
    x = [s1['h'][i], s2['h'][i], s3['h'][i]]
    med_h.append(sorted(x)[1])
    x = [s1['temp'][i], s2['temp'][i], s3['temp'][i]]
    med_temp.append(sorted(x)[1])
```

**Code 4.1**
Code for calculating the values needed in the graphs



```.py
x, mean_y = smoothing(avg_h, size_window=12)
plt.plot(x, mean_y, label='Mean', color='red')
x, std_y = smoothing(std_h, size_window=12)
upper_y = []
lower_y = []
for i in range(62):
    upper_y.append(mean_y[i] + std_y[i])
    lower_y.append(mean_y[i] - std_y[i])
plt.fill_between(x, upper_y, lower_y, color='gray', alpha=0.2, label='Standard Deviation')

x, max_y = smoothing(max_h, size_window=12)
plt.plot(x, max_y, linestyle='--', label='Max')
x, min_y = smoothing(min_h, size_window=12)
plt.plot(x, min_y, linestyle='--', label='Min')
plt.ylabel('Humidity (%)')
plt.xlabel('Time (hours)')
plt.legend()
plt.title('Mean, Std, Min, Max Humidity')

plt.show()


med_y = smoothing(med_h, size_window=12)[1]
plt.plot(x, med_y, label='Median', color='blue')
plt.plot(x, mean_y, label='Mean', color='red')
plt.ylabel('Humidity (%)')
plt.xlabel('Time (hours)')
plt.legend()
plt.title('Mean and Median Humidity')
plt.show()
```

**Code 4.2**
Code for creating the graphs for mean, standard deviation, minimum, maximum, and median for the recorded humidity values

## 5. The Local data is stored in a csv file and posted to the remote API server as a backup.
We created three csv files for each of the three local sensors (**Fig 5.1**). In order to store the data from the sensors in the correct csv file, we created an algorithm that splits the data sent over from Arduino to Python by comma and checks the last value, which is the number of the sensor that sent the data (**Code 5.1**). It then utilizes the with open function and sets the mode to append in order to send the data to the corresponding csv file.

As for sending the data to the remote API server, we decided to wait until we had all the values in the csv file. We decided that this would be easier because of the faulty connection to the WiFi in the room downstairs where the data was being taken. Were we to send the data to the API server over the 48 hours, this problem would have certainly created gaps in the data, which would invalidate it.

When we were preparing to send the data from the csv files to the API server, we noticed a pattern in the code. Hence, instead of running three similar blocks of code for all three of the csv files, we created a function that took the name of the csv file and the id's of the humidity and temperature sensors (**Code 5.2**) . This made the code more condensed and visually appealing.
In the function we extract the data from the chosen csv file and iterate over it line by line by using a for loop. We then split the lines by comma to get the humidity, temperature, and the datetime. We then modify the datetime to fit the API server's format. Finally we post the humidity and temperature together with the datetime to the specified sensors (**Fig 5.2**).

Thus, we have fulfilled success criterion 5


![csv1](https://github.com/Rokyyz/unit2/assets/142757981/ba3b571f-f4fc-4048-a421-020dd8c403fc)

**Fig 5.1**
Picture of one of the three csv files



![API](https://github.com/Rokyyz/unit2/assets/142757981/b7412e2e-c53b-46f4-82c6-8363fb17a81d)


**Fig 5.2**
Picture of the data uploaded to the remote API server


```.py
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

**Code 5.1**
Code that reads the data from the sensors connected to the Arduino and appends it to the appropriate csv file



```.py
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

**Code 5.2**
Code that uploads the data from the csv files to the remote API server


## 6. Create a prediction of the data for temperature and humidity inside the room for the following 12 hours
When we created the quadratic model for the mean of the data from the local sensor, we made sure to extend the model's domain by 12 hours by making use of the qmodel function, which created our prediction. We did the same for the model for the remote data, but instead extended the domain by 18 hours in order to match the local model. This is because the remote sensor has 6 hours less of data for reasons stated earlier.

Thus, we have fulfilled success criterion 6


![Local Average Readings](https://github.com/Rokyyz/unit2/assets/142757981/7527761a-7eea-4418-9a08-638c3e9cc38f)

**Fig 6.1**
Graph of the mean of the data from the local sensors and the corresponding quadratic model



![Remote Readings](https://github.com/Rokyyz/unit2/assets/142757981/24ccfa35-0928-4466-b9d7-61a108a2203b)

**Fig 6.2**
Graph of the data from the remote sensor and the corresponding quadratic model


```.py
def qmodel(x: list, y: list, prediction: int):
    a, b, c = np.polyfit(x, y, 2)
    model = []
    future_x = x.copy()
    for i in range(prediction):
        future_x.append(len(future_x))
    for i in range(len(future_x)):
        model.append(a * (i ** 2) + b * i + c)
    return model, future_x
```

**Code 6.1**
Code for the qmodel function
## 7. The solution includes a poster summarizing the visual representations, model and analysis created. The poster includes a recommendation about healthy levels for Temperature and Humidity


# Criteria D: Functionality

A 7 min video demonstrating the proposed solution with narration

https://youtu.be/crNc5wXMmDY?si=2ASautwjL4P8nHQ4 

https://drive.google.com/drive/folders/116m6XckluCguFD21VpoFRdTZhC5qgeBz?usp=drive_link



