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

After the datasheets for the modules had been collected and studied it was time to start progamming their behaviour, this would not only decide how they operate but it would also define what information would be sent over serial to Pure Data. For each sensor the respective datasheet had to be investigated to help specify what the sensor was actually capable of doing and how it had to be wired. The way it has to be wired along with its capability are the framework in deciding how it must be programmed.

**Ultrasonic Sensor**

The first sensor  to be programmed was the Ultrasonic Module HC-SR04 Distance Sensor, the device features four pins; a VCC (Voltage Common Collector), a Trigger pin, an Echo pin and GND (Ground). The Nano can supply the necessary 5V and GND direct to the sensor thus dealing with the power aspect of the module. To be able to use this sensor to measure distance requires an understanding of how the trigger and echo pins operate, the trigger pin has to be sent to a digital/analogue output pin on the Arduino and the echo pin has to be routed to a digital/analogue input. The tigger pin requires a pulse producing a HIGH output for a minimum of 10μs (microseconds), the sensor then has to wait for a HIGH level to return on the echo pin. The length of time the echo pin stays HIGH corresponds to the distance that the ultrasonic sound has travelled. The quicker the response, the closer the sensor is to an obstacle.

For this prototype the trigger pin was routed to A1 (Analogue Pin 1) and the echo pin to A0. The trigger pin receives a HIGH pulse for 10μs, when the return is picked up by the echo pin this length of time since the send and receive is stored as the duration. The duration is used in the final calculation to work out the distance in cm. 

Sound travels at approxiamtely 340 meters per second. This corresponds roughly to 29.412μs per centimeter. To measure the distance the sound has travelled, this formula is used: Distance = (Time x SpeedOfSound)/2. The "2" is in this formula becuase the sound has to tavel back and fourth. The sound travels away from the sensor first, then it bounces back off a surface and returns. The best wasy to read the distance in centimeters is to use this formula: Centimeters = ((Microseconds/2)/29).

An LED is also used as a visual prompt to the current status of the sensor. The LED is a Kingbright 5mm, 3-pin, green/red, though-hole LED. It has forward voltage of 2.5V and a forward current of 25mA on green and 30mA on red. With the source voltage being 5V, the forward voltage being 2.5V and the max forward current being 30mA a 100Ω (ohm) resistor would be recommended. This would mean each 100Ω resistor would dissipate 90 mW, the diodes dissipate 75 mW, the total power dissipated by the array would equal 165 mW and the array would draw current of 30 mA from the source. However as a precaution a 150Ω resistor was used. The LED has three pins, a GND and two VCC pins. The resistor is attached to the GND pin on the LED and then routed back to the GND pin on the Arduino, the two VCC pins receive HIGH and LOW signals to light both of the colours. For example, when one VCC pin is HIGH it would make the LED turn green, the VCC pin controlling the red side would be LOW at this point. In the reverse set up the LED would be red. The sensor is programmed check whether there is an obstacle in front of it. It measures the distance in front of it and if the distance is less that the chosen number, it will recognise that there is an obstacle in range. When this happens the LED will turn red, when the distance is greater than the chosen variable the LED is lit green and the sensor does not register that an obstacle is blocking it. It will however, still report the distance of any obstruction in cm. - DIGITAL PIN 10!

![Ultrasonic First Prototype](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_025.jpeg)

**IR Proximity Sensor**

The IR sensor has 3 pins: VCC, GND and an output pin which sends either a HIGH or LOW signal depending on its detection status. This sensor is capable of detecting the presence of an object, however, it is not capable of determining the distaction of the obstruction.

![IR Proximity First Prototype](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_023.jpeg)
