# VAAK - Voice Augmented Assisstive Kit

[![N|Solid](https://i.ebayimg.com/images/g/pT0AAOSwX~dWmbz4/s-l300.jpg)](https://www.arduino.cc/)
[![N|Solid](https://s3.amazonaws.com/ionic-marketplace/ionic-2-firebase-auth-starter/icon.png)](https://firebase.google.com/)
[![N|Solid](https://raw.githubusercontent.com/iiiypuk/rpi-icon/master/256.png)](https://www.raspberrypi.org/)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

VAAK is a college project under the TARP course. Under this course we had to make groups and come up with creative solutions to real world problems and implement them. Our group decided to make a project that helped specially-abled people who cannot speak by making a device that took input from their fingers in a fixed format(For example: American Sign Language), process it and play out the processed data via a speaker that is either interfaced with an android smartphone or simply a smartphone's inbuilt speaker. Members under the project are:

  - Aditya Kshettri
  - Naman Arora
  - Rishabh Agarwal
  - Soham Sengupta
  - Arpan Satpathi
  - Dharoori Rakesh Acharya

# Breif working of the project

We use flex sensors for getting the input from the fingers of the user. These sensors are connected to an arduino uno, which processes and sends the data to a raspberry pi serially or to a wifi card, which then sends the data to a firebase realtime database. The android app interacts with this database and reads out the interpreted text.

For now, we did not study the American Sign Language, so we used the sensors to send alphabet combinations instead.
For example, since we have 26 alphabets, we use 5 flex sensors and assign each binary combinaion of the input to a specific alphabet.
In this repository, however, we have only used 2 sensors, so make sure to edit the .ino file accordingly.


So the project can be divided in the following parts:
  - Getting the data from arduino uno
  - Processing the data inside the arduino script
  - Sending the data to a raspberry pi, or a wifi module
  - Transmitting the data to a specific firebase realtime database
  - Using the android app to consume the data from the database
  - Using the app to control the speakers connected to the device and reading out the text/alphabet

The code given in this repo is only for *alphabet* reading and nothing else.

We used a raspberry pi to send the data to the firebase realtime database using the *rev.py* script. You can learn more about it [here](https://www.instructables.com/id/Raspberry-Pi-Arduino-Serial-Communication/).

### Installation

The application requires [Arduino IDE](https://www.microsoft.com/en-in/p/arduino-ide/9nblggh4rsd8?ocid=badge&rtc=1&activetab=pivot%3Aoverviewtab) so that you can push your code into your arduino and needs [Android Studio](https://developer.android.com/studio) so that you can build the android app files.

First push the arduino.ino file to your arduino and then test it on your pc for testing the accuracy of your sensors. For that you will need to replace all *Serial.write* commands with *Serial.print* commands in the arduino.ino file.

If you are using a raspberry pi as we have to send the data over to a firebase realime database, you will need to install the following dependencies:


```sh
$ pip install serial
$ pip install firebase-admin
$ pip install time      #only if you want to give delays like: time.sleep(3)
```

After making sure you are getting the accurate values from your arduino, connect your raspberry pi with your arduino as mentioned [here](https://www.instructables.com/id/Raspberry-Pi-Arduino-Serial-Communication/).
Now our arduino code is running on a serial connection on the raspberry pi continuously. You can check if your raspberry pi detected your arduino by running the following command in your terminal:

```sh
ls /dev/tty*
```
If /dev/ttyACM0 shows up in the list, you're good to go!
Now run the python script by running the following command in your terminal:
```sh
python rev.py
```
This will send your arduino data to your firebase realtime database. Which you can use in an android app.

# ABSTRACT :

In our project, we have designed an assistive technology to empower the people with disabilities. Mainly, we have focused on the people who are deaf or dumb. Basically, we have developed a product which will help the disabled people to communicate easily with the rest of us, just by using their hand gestures. Our product has flex sensors placed on the gloves which will be worn by the disabled people. With each of their hand gesture, a particular alphabet or word will be generated and sent to our App which will convert text to speech as well as display the text on screen. As a matter of fact, our product will be beneficial for all, for instance, we will be able to hear and understand what a mute person is trying to convey to us, without even having the knowledge of sign language. In the same way, a deaf person can see the text on the App screen and understand what a mute person wants to say to him. This will enhance their communication as well as increase the literacy rate too. Hence they will be treated as equal in the society.

# OBJECTIVES & GOALS :

•	To understand the problems faced by deaf and dumb people in their day to day life.
•	To understand what kind of product they need to cope up with their problems.
•	To understand what exactly they need from the product so that it solves their problems.
•	Finally, to come up with a cost efficient solution for their problems.

# MOTIVATION FOR CHOSEN PROJECT :

•	We wanted to do some project in the field of humanitarian technology.
•	After few brainstorming sessions, we came down to solving problems for the physically challenged people.
•	We came up with a thought that communication is a big problem for the mute and deaf people in one of brainstorming sessions, so we wanted to develop a project that would make their communication easy

# BENEFITS :

•	This will help mute and deaf people for communication such that they will no longer be treated as disabled anymore and will get the same education as other children and this will increase literacy in India.

# FIELD VISIT :

We visited few schools for deaf and dumb people for our survey to know about their problems in daily life communication with people. We mainly focused on framing questions related to the help which the mute people want from the society and government for themselves, what they expect from us and what kind of tech support they want from us and how do they expect our tech to ease their daily life problems.
1)	Chettinad Srihari Vikasam, Chennai
2)	CSI School for the Deaf, Chennai

# HARDWARE COMPONENTS :

•	Flex Sensors

This flex sensor is a variable resistor like no other. The resistance of the flex sensor increases as the body of the component bends.
One side of the sensor is printed with a polymer ink that has conductive particles embedded in it. When the sensor is straight, the particles give the ink a resistance of about 30k Ohms. When the sensor is bent away from the ink, the conductive particles move further apart, increasing this resistance
When the sensor straightens out again, the resistance returns to the original value. By measuring the resistance, you can determine how much the sensor is being bent.

•	Arduino Uno R3 ATmega328P
•	Raspberry Pi 3B+
•	Resistors : 3.9k ohms
•	Connecting Wires
•	USB Cables
•	Smartphone

# SOFTWARES REQUIRED :

•	Arduino IDE 1.8.9 (for burning the code into the Arduino)
Language used – Embedded C/C++
•	Python 2.7 (to upload the alphabets received by the Raspi to the Firebase)
•	Android Studio 3.1.4 (for making an app for text to speech conversion)
Language used – JAVA and XML

# WORKING :

1.	In our project, we have used flex sensors which are bend sensitive. This way, the system can sense it whenever there is a bent in the sensor.
2.	We have used 5 flex sensors, since we need to display only 26 English Alphabets for now, so 2^5=32 binary combinations will be more than enough for that.
3.	So, we have placed 5 flex sensors on a pair gloves, 3 on the right hand and 2 on the left.
4.	The gloves are then connected to the Arduino Uno.
5.	In each flex sensor, one end is connected to Gnd of Arduino. The other end is connected to an AnalogIn pin and a resistor which is hence connected to Vcc of the Arduino.
6.	A mute person wears these gloves and the Arduino is connected to 5V power supply.
7.	When he tries different gestures using his hand, different values are generated by the flex sensors.
8.	We assume that when the flex sensor is straight, it’s value is 1 and when it is bent, it’s value is 0.
9.	When user wears this gloves and try a hand gesture, there comes many binary  combination with all sensors, in which each combination represents a different English Alphabet.
10.	These binary combination of values are sent to the Arduino.
11.	Each combination of values have a different predefined alphabet which is fed to the Arduino.
12.	The Arduino is then serially connected to the Raspi using USB cable.
13.	The alphabets are sent to the Raspi one by one synchronously.
14.	The Raspi directly transfers the received alphabets on the User’s Firebase Account.
15.	The user then retrieves the alphabets from the Firebase using our Android App.
16.	The Android App converts the Text to Speech as well as displays it too.
17.	Any person or even a blind person can hear the Speech through the speaker and understand what the mute person wants to convey.
18.	If he is a deaf person, he can understand what is conveyed to him by the mute person just by seeing the text display of alphabet or word in our app.
19.	This way, this product will make the communication of the disabled people (mainly deaf and mute people) easy.

# CONSTRAINTS :

While we have achieved the primary target of our project, the following constraints restricted us from making further enhancements:

	Cost constraints
Additional and more effective sensors were not procured as these entailed greater expenditure and subsequent increase of the product cost beyond its affordable rate in the target market segment. 

	Usability Constraints
The current form of the product is bulky since we do not have access to chip fabrication to miniaturize the product. The same can be attributed other constraints such as time and cost.

	Safety Constraints
Although unlikely, there may be a possibility of mild electrical shock if the sensors come into direct contact with skin and the user is grounded.

	Technical Constraints
The sensor readings were not always constant or dependable. Additionally, the sensors take a while to become straight once they have been bent, leading to erroneous values.

	Environmental Constraints
None. The product should function in all environments (except extreme scenarios such as fire or ice).

	Time Constraints
Inclusion of additional features such as word or sentence generation could not be achieved due to this.

	Ethical Constraints
      None. The product aims to empower the differently abled and serve society at large.
      
	Social Constraints
None. The product aims to create a more inclusive society by empowering the differently abled. 

	Manufacturability and Sustainability
The product is fit for mass production. It is also commercially sustainable since its revenue will soon ‘break-even’ with its capital costs.

# TESTING & QUALITY ASSURANCE

We tested our projects giving various inputs using different hand gestures, it was giving all the alphabets successfully as output. The flex sensors are very sensitive, hence even as slight bend will change the input instantly and hence give the output. Hence, the user doesn’t need to bend it too much, a little also is fine. This ensures the quality assurance of our product. Also, the flex sensors are very light in weight. So the user won’t feel trouble in handling the gloves at all. Hence, we have made a user friendly product.

# CONCEPTS LEARNED

We understood the working of flex sensors and how its bend-sensitive nature can be used to generate any number of binary combinations of 1’s and 0’s. We also understood how to interface Raspberry Pi with Arduino.

# PROBLEMS FACED

The most challenging part of our project was calibrating the flex sensors. The main problem was that every sensor gives a different set of values when it is straight as well as for when it is bent. The only thing that could be used was that all the sensors gave higher values for when it was bent than when it was straight. So we used this logic to solve the issue. We coded the Arduino in such a way that as soon as it receives power, it will generate initial Sum of first 10 values of each Sensor and consider it as a threshold value when the sensors are straight. Then, as the sensors are bent or straightened later, again the sum of 10 values of each is calculated and compared with initial Sum. If the difference of any sensor is greater than 100, then it is assumed to be bent, else it is straight. This logic was the key in our project.

# INFERENCE

Flex sensors are highly bent sensitive. They give a higher value when bent as compared to when they are straight. Different Flex Sensors give different values when they are straight as well as when they are bent. 

# FUTURE WORK

We have planned to extend our product on a higher level. After alphabets, we will try to generate words from the flex sensors. This will be same like a normal person speaking. It will be of great benefit to the disabled people.

# REFERENCES

https://www.youtube.com/watch?v=BzpzcWBUZGc

https://www.youtube.com/watch?v=b7zT94WV-Ek

https://forum.arduino.cc/index.php?topic=529567.0

https://maker.pro/raspberry-pi/tutorial/how-to-connect-and-interface-raspberry-pi-with-arduino

https://www.youtube.com/watch?v=s4o8T6F-zGU
