# 7MU011-Reactive-Sound-Installation
A sound installation that responds to stimuli and continuously evolves via user input. This input is made possible through the use of a range of different sensors. This project employs the use of HCI (Human-Computer Interaction) through several Arduinos. The software element of this project was built using two main platforms; each sensor had its behaviour written using the Arduino's IDE (Intergrated Development Environment). The audio section of this installation was built in Pure Data.

## Background

## Prerequisites

## Sensors
###### Sensors Used
**Ultrasonic Module HC-SR04 Distance Sensor**

```
Working Voltage: 5V (DC)
Sensor Angle: Up to 15°
Detection Distance: 2cm-500cm
```
The sensor uses ultrasonic sound to measure distance just like bats and dolphins. Ultrasonic sound has such a high pitch that humans cannot hear it. This sensor ouputs an ultrasonic sound that has a frequency of 40kHz. The sensor contains two main components: a transducer that creates an ultrasonic sound when the trigger pin is active and another that listens for its echo. Using this sensor to measure distance requires the calculation of the amount of time it takes for the ultra sonic sound to travel.

![Ultrasonic Module HC-SR04 Distance Sensor](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_010.jpeg)

**Infrared Obstacle Avoidance Proximity Sensor Module FC-51**

```
Working Voltage: 3.3V-6V (DC)
Sensor Angle: 35°
Detection Distance: 2cm-30cm
```

The sensor is an IR (Infrared) transmitter and reciever and it consists of an LED that emits the IR radiation and a photo diode which acts as a receiver. The transmitter sends an IR radiation (in the infrared wavelength region), which is reflected off a surface and falls upon the receiver. Due to the light falling on the receiver, a potential difference is created across the ends. The potential difference is recognised by a microcontroller as HIGH or LOW.

![Infrared Obstacle Avoidance Proximity Sensor Module FC-51](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_013.jpeg)

**Pyroelectric Infrared PIR Motion Sensor Detector Module HC-SR501**

```
Working Voltage: 5V-20V (DC)
Sensor Angle: 110°
Detection Distance: Up to 7m
```

PIR (Passive Infrared) sensors allow the detection of motion and are almost always used to detect if a human has moved in or out of the sensor's range. PIRs are essentially made of a pyroelectric sensor, which can detect levels of infrared radiation. Everything emits low level radiation and the hotter something is, the more radiation it emits. The sensor in a motion detector is actually split in two halves. The reason for that is that it is looking to detect motion, change, not average IR levels. The two halves are wired so that they cancel each other out. If one half sees more or less IR radiation than the other, the output will change to HIGH or LOW.

![Pyroelectric Infrared PIR Motion Sensor Detector Module HC-SR501](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_004.jpeg)

**TTP223B Touch Sensing Module**

```
Working Voltage: 2V-5.5V (DC)
Sensor Detection: Operated via touch
```

The sensor is based on a touch-sensing IC (TTP223B) capacitive touch switch module. The difference with this chip is that it has only one input instead of multiple. In its normal state, when there is no user input, the module output is LOW and in is a low power consumption mode. When touched, the module outputs a HIGH signal. If the module is not touched for 12 seconds, it switches back to the low power mode.

![TTP223B Touch Sensing Module](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_002.jpeg)

**KY-008 650NM 5V Laser Sensor Module**

```
Working Voltage: 5V (DC)
Beam Output: 100mW
Max Current: ~30mA (Laser on)
```

![KY-008 650NM 5V Laser Sensor Module](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_017.jpeg)

**Laser Receiver Transceiver LED Module**

```
Working Voltage: 5V (DC)
```

![Laser Receiver Transceiver LED Module](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_019.jpeg)

