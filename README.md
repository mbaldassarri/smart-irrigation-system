# Smart Irrigation System - University of Bologna

The idea behind this project is to gather some data from the ground with ESP32 board, send it via BLE to Raspberry Pi which acts as sensors controller (Fog Computing).
This hub will store received data in a local database. Every 10 minutes, the controller will aggregate stored data and send average sensors metrics to the AWS Cloud. AWS will store aggregated data in a DynamoDB NoSQL database. An AWS Lambda will be activated once in a while and will decide, based on the received information, if it's a good idea to start the irrigation pump. This way, the human presence is actually not needed.

Nowadays, Smart Agricolture technologies use Drones to fully monitor ground fields. We wanted to make a step ahead.
A Drone (DJI Tello) will start autonomously and take it's own path over a specified ground area. After this task, he will go back to its starting point and wait for the next mission. If there is a motor issue or the battery is low, the user will be notified for manual intervention.

Even if everything is working automatically, the user can still interact with the smart ground field by asking Telegram dedicated Bot to start the Drone or the irrigation manually. The user can also ask the Bot to take some pictures or a short video to moninitor the ground. For this purpose, a security RaspiCam is being installed on the Raspberry Pi. Moreover, if human motion is detected, the user will receive a notification with the pictures of the thief. This has been achieved by using dedicated Machine Learning algorithms to detect the human body and avoid false friends that can walk in fron of the camera during the night (eg. a little fox looking for some food).

In case he doesn't like the decision the System made for him, the smart farmer can also ask Alexa to start the irrigation manually. So an Alexa Skill was developed and made up and running for this purpose.

To simulate a real IoT environment, the communication between the devices is being made by using lightweight protocols, like MQTT and BLE.

You can find more detailed information about this amazing project on each specific module README file. There are three modules, each describing each layer designed for this purpose: in the sensor layer (Micro Irrigation) you can find all the code dedicated to the sensors installed on the ground to fetch environment data, fog layer (Control Unit Irrigation) is the middle controller that saves sensors data and aggregate it, and Cloud layer (Cloud Backend) is the backend that handles all the irrigation decisions, drone decisions and Alexa skill logic.

Languages used:
- C++
- Python
- Javascript
- SQL

Technologies used:
- BLE 
- AWS IoT Core (MQTT Broker)
- AWS Lambda 
- AWS DynamoDB
- Alexa Skill Kit SDK
- Telegram APIs
- OpenCV

Hardware used:
- ESP32
- temperature/humidity sensor, light sensor, rain sensor, moisture sensor, battery status sensor
- Raspberry Pi 4
- RaspiCam 5M
- DJI Tello
- Alexa Echo Dot 

Other details are available (in Italian) on the project 'report.pdf' file

Enjoy! :)
