# 7MU011-Reactive-Sound-Installation
A sound installation that responds to stimuli and continuously evolves via user input. This input is made possible through the use of a range of different sensors. This project employs the use of HCI (Human-Computer Interaction) through several Arduinos. The software element of this project was built using two main platforms; each sensor had its behaviour written using the Arduino's IDE (Intergrated Development Environment). The audio section of this installation was built in Pure Data.

## Background

## Prerequisites

## Arduino

The chosen board for this project is the Arduino Nano. The Nano is a small, powerful and breadboard-friendly board based on the ATmega328. The ATmega328 has 32KB of Flash memory. Having Flash memory and a microcontroller on the same chip means advantage can be taken of additional intelligence. For example there is an additional ROM (Read-only Memory) section holding the code for handling the Flash programming. The code does not only provide functions to erase or program the Flash memory, it also provides boot code. Even with a completely erased Flash, the chip can still execute this boot code and accept inputs via the serial port. The ROM is not erasable, therefore, applications can always rely on it being present. Also it contains 1KByte of EEPROM (Electrically Erasable Programmable Read-only Memory) which is user-modifiable read-only memory (ROM) that can be erased and reprogrammed repeatedly. Finally it has 2KBytes of RAM (Random-access Memory) is a form of computer data storage. A random-access memory device allows data items to be accessed (read or written) in almost the same amount of time irrespective of the physical location of data inside the memory. RAM is the place where the operating system, application programs and data in current use are kept so that they can be quickly reached by the processor.

(Voltage, pins, uses)

```
Microcontroller: ATmega328
Operating Voltage (logic level): 5 V
Input Voltage (recommended): 7-12 V
Input Voltage (limits): 6-20 V
Digital I/O Pins: 14 (of which 6 provide PWM output)
Analogue Input Pins: 8
DC Current per I/O Pin: 40 mA
Flash Memory: 32 KB of which 2 KB used by bootloader
Clock Speed: 16 MHz
```

![Arduino Nano ATmega328](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_007.jpeg)

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

The 100mW laser module emits a small intense focused beam of visible red light. Alone, this sensor would be useless to the project as it does not offer and type of input, it would require an external sensor to trigger it. However the interest in this module lies with a coupled receiver module that will allow the creatation of a small circuit which, in turn, will add another different way to affect the variables in the project.


![KY-008 650NM 5V Laser Sensor Module](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_017.jpeg)

**Laser Receiver Transceiver LED Module**

```
Working Voltage: 5V (DC)
```

This module recognises when the laser beam is pointing at its sensor. The sensor in question is an LDR (light-dependent resistor), the resistance of an LDR decreases with increasing incident light intensity. When the light level is low the resistance of the LDR is HIGH. However, when the light shines onto the LDR, its resistance lowers and the outputing signal would be LOW. This sensor combined with the laser module is used to create a trip sensor. As a person passes through the beam it cuts off the light source to the LDR, therefore, switching its output to HIGH, allowing the circuit to affect the chosen variable(s) within the Pure Data patch.

![Laser Receiver Transceiver LED Module](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_019.jpeg)

## Prototypes

###### First Prototypes

**Ultrasonic**

![Ultrasonic First Prototype](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_025.jpeg)

