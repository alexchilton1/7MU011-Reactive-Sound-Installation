# 7MU011-Reactive-Sound-Installation
This project is a sound installation that responds to stimuli and continuously evolves via user input. User input is made possible through the use of a range of different sensors, interfaced with a computer via several Arduino microcontrollers. The software element of this project was built using two main platforms; each sensor had its behaviour scripted using the Arduino's IDE (Intergrated Development Environment), and the audio section of this installation was built in Pure Data.

## Acronyms/Abbreviations/Symbols
```
ANN - Artificial Neural Network
cm - centimeters
DC - Direct Current
EEPROM - Electrically Erasable Programmable Read-only Memory
HCI - Human-Computer Interaction
Hz - Hertz
IC - Integrated Circuit
IDE - Integrated Development Environment
IF - Forward Current
IR - Infrared
KB - Kilobyte
kHz - kilohertz
LDR - Light Dependent Resistor
LED - Light Emitting Diode
m - metre
mA - milliamps
MHz - Megahertz
mW - milliwatts
NM - Nanometers
PD - Pure Data
PIR - Passive Infrared
RAM - Random Access Memory
ROM - Read-only Memory
V - Volts
VF - Forward Voltage
Ω - Ohms
° - Degrees
```
## Background
This project is a sound installation, which is situated under the umbrella of sound art. Sound installations, deriving from sound art and sound sculpture, are an inter-disciplinary and time-based art form. Sound art is an artistic field of study, in which, sound is employed as a medium. This project includes multiple audio generation techniques such as generative music, artificial neural networks and phase distortion synthesis to name a few. It employs the use of HCI to provide analogue sensors with the ability to control virtual parameters in a software audio workstation.

## Prerequisites
In order to be able to use the sound installation, Pure Data extended is required to be installed on your system. Pure Data is free and available here [https://puredata.info/downloads/pd-extended](https://puredata.info/downloads/pd-extended) follow the guide online on how to set up Pure Data on your operating system. Once installed, make sure all of the files have been downloaded, available here [https://drive.google.com/open?id=0By6_1xhwTEChNi1Fc25XaU5hcE0](https://drive.google.com/open?id=0By6_1xhwTEChNi1Fc25XaU5hcE0).
The physical sound installation with the sensors is also required.

## Build Structure Overview (Initial plan of the stages in the project)
###### Sensors
The first plan of action is to read the datasheets for all of the sensors, this will provide insight into how the sensors can be programmed, what the various pins do and what they can be used to control. After completing this basic step, prototypes will need to be created for each sensor to determine if the theoretical information corresponds with their behaviour in a physical space.

###### Multiple Sensors
Once the initial prototypes have been created, a second iteration of the prototyping stage will ensue. This time combining multiple sensors to make sure they are able to interact will other sensors without any problems.

###### Pure Data Patch
Construction will now be able to begin on the audio section of the installation. After working with the sensors and understanding how they operate individually and as small groups, the audio section can be designed with their behaviour in mind. When creating the patch, with the chosen audio generation techniques, thinking about how the different audio aspects will interact with the chosen sensors will help define a scope for the layout. The first few audio aspects to implement will be an ambient drone section and an audio sample playback section.

###### Mapping the Sensors
After the first two audio elements have been created and are functioning as intended, an initial test can be carried out by mapping one or two of the sensors to the audio components; making sure that they actually work together as intended. This is because it is much easier to make changes near to the start, as trying to make a lot of changes when the product has been completed is a very difficult and time-consuming task.

###### Pure Data Additional Features
The rest of the audio generation elements can be added at this stage, these include; a white noise generator, a spectral bank, some phase distortion synthesis and a reverberation unit. After these features have been built, every element should be connected to the various prototypes to make sure they all work as intended before it progresses to the soldering stage.

###### Design and Build the Installation Structure
At this point, all of the sensors should have be programmed and the audio components should have been built, so the design process will begin to decide on the appearance of the installation. This needs to incorporate a logical system of interaction with the sensors so they do not suffer from crosstalk and so that the user can physically interact with them without restriction. Once the structure has been designed, it will need to be built. Regardless of the appearance of the final design, it will all be made from wood.

###### Connect and Test
The final stage will be to connect the finished installation to the audio patch and confirm that everything works as intended.

## Arduino

The microcontroller used in this project is the Arduino Nano. The Nano is a small, powerful and breadboard-friendly board based on the ATmega328. The ATmega328 has 32KB of Flash memory. There is an additional ROM section that handles the code for programming the Flash memory. This code not only provides functions to erase or program the Flash memory, it also provides boot code. Even with a completely erased Flash, the chip can still execute this boot code and accept inputs via the serial port. The ROM is not erasable, therefore, applications can always rely on it being present. As well as this, it contains 1KByte of EEPROM which is user-modifiable read-only memory  that can be erased and reprogrammed repeatedly. Finally it has 2KBytes of RAM, which is a form of computer data storage. A random-access memory device allows data items to be accessed (read or written) in almost the same amount of time irrespective of the physical location of data inside the memory. RAM is the place where the operating system, application programs and data in current use are kept so that they can be quickly reached by the processor. This particular model contains 8 analogue input pins, which provide the ability to read analogue sensor values and return integers from 0 to 1023. It also contains 13 digital pins, these can be configured to behave as either inputs or outputs. However, the pins default to inputs, so they do not need to be explicitly delcared as inputs with the pinMode command when using them in this manner.

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
### Sensors Used
**Ultrasonic Module HC-SR04 Distance Sensor**
```
Working Voltage: 5V (DC)
Sensor Angle: Up to 15°
Detection Distance: 2cm-500cm
```
The sensor uses ultrasound to measure distance, just like bats and dolphins. Ultrasound has such a high pitch that humans cannot hear it. This sensor outputs ultrasound at a frequency of 40kHz. The sensor contains two main components: a transducer that creates an ultrasonic sound when the trigger pin is active and another that listens for its echo. Using this sensor to measure distance requires the calculation of the amount of time it takes for the ultrasonic sound to travel.

![Ultrasonic Module HC-SR04 Distance Sensor](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_010.jpeg)

**Infrared Obstacle Avoidance Proximity Sensor Module FC-51**
```
Working Voltage: 3.3V-6V (DC)
Sensor Angle: 35°
Detection Distance: 2cm-30cm
```
The sensor is an IR transmitter and receiver and it consists of an LED that emits IR radiation and a photo diode which acts as a receiver. The transmitter sends an IR radiation (in the infrared wavelength region), which is reflected off a surface and falls upon the receiver. Due to the light falling on the receiver, a potential difference is created across the ends. The potential difference is recognised by a microcontroller as high or low.

![Infrared Obstacle Avoidance Proximity Sensor Module FC-51](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_013.jpeg)

**Pyroelectric Infrared PIR Motion Sensor Detector Module HC-SR501**
```
Working Voltage: 5V-20V (DC)
Sensor Angle: 110°
Detection Distance: Up to 7m
```
PIR sensors allow the detection of motion and are almost always used to detect the presence of a human. PIRs are essentially made of a pyroelectric sensor, which can detect levels of infrared radiation. Everything emits low level radiation and the hotter something is, the more radiation it emits. The sensor in a motion detector is actually split into two halves. The reason for that is because the sensor is looking to detect motion, change, not average IR levels. The two halves are wired so that they cancel each other out. If one half sees more or less IR radiation than the other, the output will change to high or low.

![Pyroelectric Infrared PIR Motion Sensor Detector Module HC-SR501](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_004.jpeg)

**TTP223B Touch Sensing Module**
```
Working Voltage: 2V-5.5V (DC)
Sensor Detection: Operated via touch
```
The sensor is based on a touch-sensing IC (TTP223B) capacitive touch switch module. The difference with this chip is that it has only one input instead of multiple. In its normal state, when there is no user input, the module output is low and is in a low power consumption mode. When touched, the module outputs a high signal. If the module is not touched for 12 seconds, it switches back to the low power mode.

![TTP223B Touch Sensing Module](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_002.jpeg)

**KY-008 650NM 5V Laser Sensor Module**
```
Working Voltage: 5V (DC)
Beam Output: 100mW
Max Current: ~30mA (Laser on)
```
The 100mW laser module emits a small intense focused beam of visible red light. Alone, this sensor would be useless to the project as it does not offer any type of input; it would require an external sensor to trigger it. However, coupled with a receiver module, this allows the creatation of a small circuit which, in turn, will add a different way to affect the variables in the project.

![KY-008 650NM 5V Laser Sensor Module](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_017.jpeg)

**Laser Receiver Transceiver LED Module**
```
Working Voltage: 5V (DC)
```
This module recognises when the laser beam is pointing at its sensor. The sensor in question is a light dependent resistor (LDR). The resistance of an LDR decreases with increasing incident light intensity. When the light level is low, the resistance of the LDR is high. However, when the light shines onto the LDR, its resistance lowers and the signal would be low. This sensor combined with the laser module is used to create a trip sensor. As a person passes through the beam it cuts off the light source to the LDR, therefore, switching its output to high, allowing the circuit to affect the chosen variables within the Pure Data patch.

![Laser Receiver Transceiver LED Module](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_019.jpeg)

**Light Dependent Resistor Module**
```
Working Voltage: 3.3V-5V (DC)
```
Similar to the laser receiver transceiver module this sensor uses an LDR to detect light level. When the light level is low, the resistance of the LDR is high. However, when a light source shines onto the LDR its resistance falls. This module will require an analogue input on the Arduino, which means that the analogRead command will need to be employed. The value will not range from 0 to 1, but instead it will output a variable value. If it is to behave as a switch or toggle, the code will have to specify what value makes the LDR module affect the parameter it is controlling. For example, if the LDR value is less than 100, then turn off the LED, however, if the value is greater than 100 turn on the LED.

![Light Dependent Resistor Module](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_039.jpeg)

**Analogue Joystick Controller**
```
Working Voltage: 5V (DC)
Potentiometers: 2
Push Buttons: 1
Axis: X/Y
```
The analogue joytsick controller has three outputs; two analogue 10K potentiometers that represent the X/Y axis and one switch contact output representing the push button on the joystick. However, the switch has no pull-up resistor, so the internal pull-up from the Arduino is required. The two potentiometers provide the ability to measure the movement of the stick across a two-dimensional plane. These potentiometers are variable resistors and present a variable voltage depending on the rotation of the stick. The joystick is spring-loaded, meaning the mechanism will always return to its centered position once released.

![Analogue Joystick Controller](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_039-2.jpeg)

## Prototypes

### First Prototypes

After the datasheets for the modules had been collected and studied, it was time to start programming their behaviour, this would not only decide how they operate but it would also define what information would be sent over serial to Pure Data. For each sensor the respective datasheet had to be investigated to help specify what the sensor was actually capable of doing and how it had to be wired. The wiring layout along with its capability are the framework in deciding how it must be programmed.

**Ultrasonic Sensor**

The first sensor  to be programmed was the Ultrasonic Module HC-SR04 Distance Sensor, the device features four pins; a VCC (Voltage Common Collector), a Trigger pin, an Echo pin and GND (Ground). The Nano can supply the necessary 5V and GND direct to the sensor thus dealing with the power aspect of the module. To be able to use this sensor to measure distance requires an understanding of how the trigger and echo pins operate, the trigger pin has to be sent to a digital/analogue output pin on the Arduino and the echo pin has to be routed to a digital/analogue input. The trigger pin requires a pulse producing a high output for a minimum of 10μs (microseconds). The sensor then has to wait for a high level to return on the echo pin. The length of time the echo pin stays high corresponds to the distance that the ultrasonic sound has travelled. The quicker the response, the closer the sensor is to an obstacle.

For this prototype the trigger pin was routed to A1 (Analogue Pin 1) and the echo pin to A0. The trigger pin receives a high pulse for 10μs, when the return is picked up by the echo pin, the length of time since the send and receive is stored as the duration. The duration is used in the final calculation to work out the distance in cm. 

Sound travels at approxiamtely 340 metres per second. This corresponds roughly to 29.412μs per centimeter. To measure the distance the sound has travelled, this formula is used: Distance = (Time x SpeedOfSound)/2. The "2" is in this formula because the sound has to travel back and fourth. The sound travels away from the sensor first, then it bounces back off a surface and returns. The best way to read the distance in centimeters is to use this formula: Centimeters = ((Microseconds/2)/29).

An LED is also used as a visual prompt to the current status of the sensor. The LED is a Kingbright 5mm, 3-pin, green/red, though-hole LED. It has forward voltage of 2.5V and a forward current of 25mA on green and 30mA on red. With the source voltage being 5V, the forward voltage being 2.5V and the max forward current being 30mA, a 100Ω (ohm) resistor would be recommended. This would mean each 100Ω resistor would dissipate 90 mW, the diodes dissipate 75 mW, the total power dissipated by the array would equal 165 mW and the array would draw current of 30 mA from the source. However as a precaution, a 150Ω resistor was used. The LED has three pins, a GND and two VCC pins. The resistor is attached to the GND pin on the LED and then routed back to the GND pin on the Arduino, the two VCC pins receive high and low signals to light both of the colours. For example, when one VCC pin is high it would make the LED turn green, the VCC pin controlling the red side would be low at this point. In the reverse set up the LED would be red. The sensor is programmed to check whether there is an obstacle in front of it. It measures the distance of the obstacle and if the distance is less that the chosen number, it will recognise that there is an obstacle in range. When this happens the LED will turn red, when the distance is greater than the chosen variable the LED is lit green and the sensor does not register that an obstacle is blocking it. It will however, still report the distance of any obstruction in cm.

![Ultrasonic First Prototype](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_025.jpeg)

**IR Proximity Sensor**

The IR sensor has 3 pins: VCC, GND and an output pin which sends either a high or low signal depending on its detection status. This sensor is capable of detecting the presence of an object, however, it is not capable of determining the distance of the obstruction. This sensor is ideal for triggering on/off values and coupled with Pure Data it could be used to randomise variables within a sequence or prompt the introduction of a new piece of audio to the overall mix. The infrared transmitter emits infrared radiation. When there is an obstacle in range, the wave bounces back to the receiver and the circuit becomes active. The range of the sensor can be adjusted by its on-board potentiometer, the datasheet claims that the range is 2cm-30cm but this does not seem to be the case. The safe range before the sensor becomes unpredicable seems to be around 25cm, any more and the module becomes unreliable. Also the sensor suffers heavily from light interference, natural light seems to be the worst. Sunlight makes the module very unreliable and artificial light also seems to affect its reliability.

The sensor has its VCC and GND pins connected to the Arduino the same way as the ultrasonic sensor, the out pin is routed to A0. The sensor has been programmed to know, in compliance with the datasheet, that if and obstacle is within its agreed range it outputs a low signal. If the sensor does not detect an obstruction then its output is high. An LED has been connected to digital pin 12 to help aid this detection process visually. With the source voltage from the Nano at 5V, the VF at 2.5V and the IF at 30mA, the recommended resistor was again at 100Ω. When the module detects an obstacle, the LED turns blue, when no obstacle is present the LED switches off.

The only problem with the way in which this sensor works is that it emits a low signal when the sensor is active and a high signal when it is inactive. This function is opposite to the way the PD patch has been set up, when a variable is active the signal is high, so within PD the receive signals have been switched.

![IR Proximity First Prototype](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_023.jpeg)

**PIR Motion Sensor**

PIR sensors are more complex that IR proximity sensors because there are more variables that affect the inputs and outputs of the sensor. The sensor itself has two channels in it, each of the channels consist of special IR sensitive material. The lens does not do much, the two channels can look out through this providing the sensitivity of the sensor. When the sensor is idle both channels detect the same amount of IR, the ambient amount radiated from the room, walls or outdoors. When a warm body, such as, a human or animal passes in front of the sensor it is identified by one half of the PIR sensor. This causes a positive differential between the two halves. When the warm body leaves the sensing area, the reverse happens, whereby the sensor generates a negative differential. These change pulses are what is detected. The IR sensor is housed in a hermetically sealed metal case to help improve immunity to noise, temperature and humidity. There is a window made of IR-transmissive material, typically coated silicon, that protects the sensing element. Behind this window are the two balanced sensors.

The smart part of the PIR sensor is the optics. The lens is just a piece of plastic and the detection area is only two rectangles, which is not ideal as it is not particularly large. To counteract this, a fresnel lens is used, this lens helps to condense a large area into a small one. The Fresnel lens condenses light, providing a larger range of IR to the sensor, however, there are two sensors scanning large rectangular areas which is not the desired effect. The intended outcome is to have multiple small areas, so the lens is split up into multiple sections, each of which is a fresnel lens.

The prototype is designed to detect motion and turn on the LED when this is true providing a visual indication. The PIR detects movement and prints this to the serial, it however, is programmed to pause serial printing until there is a state change and the motion stops. It will continue to detect motion for as long it recognises that movement is present, when the movement haults, the sensor is programmed with a pause time. If the hault in motion is greater than the stated pause time, the sensor will print that over serial and send a low signal to the LED causing it to switch off. The sensor has been made less responsive like this on purpose, not printing to serial every 100ms for example, so that it can provide a precise function in the PD patch. This function is to change the variables in the ambient section, if it rapidly changed it would not operate as intended and would begin to interfere with the other sections. Using the PIR in this way helps to keep the ambience dynamic as it undulates in the background without becoming too distacting.

![PIR First Prototype](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_029.jpeg)

**Touch Sensor**

The touch sensor can sense the electrical capacitance of the human body. The sensor produces a signal that gets routed to the send pin and waits for the receive pin to change to this new state. A variable is incremented inside the loop to time the state change of the receive pin. The value of this variable is then reported as low or high meaning 0 or 1 respectively.

The sensor is programmed to respond to touch, sending a high signal when contact is made and a low signal when there is none. The response is very quick, with the cycle refreshing every 100ms, this means that everytime it is touched and released, it will trigger and there is no delay. An LED has again been used as a visual aid, when the signal is high the LED is active and when low it is not.

The first step in the process is to state where the sensor and LED are routed to on the Arduino.
```
#define ctsPin 2 // This tells the Arduino to look for ctsPin (capacitive touch sensor) and replace it with 2 (digital pin 2)
int LED1 = 10 // This adds the first LED as an integer on digital pin 10
```
The reason define is used for the sensor and int is used for the LED is because the #define function acts as a search and replace setting and int is a variable. Whenever the compiler reads "ctsPin" it now believes it saw "2". It can't be changed while the sketch is running however, it takes no memory in the processor. Meanwhile the int function is a variable and does take a small amount of memory, 2 bytes to be precise, to store the value and takes an extra bit of memory to store the original value. This, however, allows the sketch to modify the variable under any desired circumstance and use the altered value from that point on.

The sketch then requires the serial to be started on the chosen baud rate and the pinModes to be specified in the void setup. The serial is set to begin on baud rate 9600, the ctsPin is set as an input and the LED is chosen as the output. The void loop is where the previously mentioned variable between the send and receive pin is detailed. The variable value is stated as the condition of the touch sensor. The code for the loop would look similar to this.
```
void loop() {
 int ctsValue = digitalRead(ctsPin); // Variable is condition of sensor
 if (ctsValue == HIGH){ // If sensor is touched...
  digitalWrite(LED1, HIGH); //  Turn LED on
  Serial.println("1"); // Then print the number 1 to the serial
}
 else{ // Otherwise, if it is not touched...
  digitalWrite(LED,LOW); //  Turn LED off
  Serial.println("0"); Then print the number 0 to the serial
} 
  delay(100); // Delay the steps in this process by 100ms
```
There are a few known issues with capacitive sensors; especially when it comes to using them near or with a laptop. The grounding of the Arduino board is very important in capacitive sensing and it is imperative the board has some ground connection. A main problem that seems to materialise is with laptops not being connected to the mains power via the charging cable. The laptop itself tends to become sensitive and bringing a hand near the laptop will change the returned values. Connecting the charging cable to the laptop usually resolves the problem.

![Touch Sensor Prototype](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_031.jpeg)


**Laser Sensor and Laser Receiver Module**

The way this circuit was designed to work, was with the laser beaming its output into the LDR of the laser receiver module which would the output a variable. If the signal was high then the beam was present, if low the beam of light had been broken by an obstacle. This would presumably mean that a person had walked past causing the line of sight of the sensor to become obstructed, thereby, triggering a signal over serial to PD. The laser sensor module simply required to be connected to 5V and GND pins. The receiver module was programmed similar to how the touch sensor was coded. The input of the receiver was connected to the Arduino pin A0. Using the analogRead function within the Arduino IDE the initial value range was analised to observe output of the sensor when the laser was present and removed.
```
void loop() {
  Serial.println(analogRead(ldrPin)); // This prints the output over serial
  delay(100); // Delays the process by 100ms each time
}
```
The output of the sensor ranged from 2-20 when the laser was removed and between 1010-1019 when the laser was shone onto the receiver. With this in mind it was fairly simple to decide how best to programme the circuit for both being efficient in the sketch and producing usable results in PD. An LED was again used as a visual aid, using a 150Ω resistor as in the previous prototypes. For PD, the output was scaled between 0 and 1. This was accomplished by dividing the output of the receiver by 1000. Next an integer was created to store the variables of the receiver module. Even though the sensor over serial read 0-1, the actual numbers remained the same, from approximately 2-1020. With this in mind it was intelligible to state that if the variable value was greater than 1000 it meant the circuit was active, if the value was below 1000 then it should be perceived as off. The on and off statements are what turn on the LED and the 0-1 is what was sent to PD creating simple binary values. The whole process was delayed by 100ms each time to make the receiver responsive but not too sensitive.
```
void loop() {
 Serial.println(analogRead(ldrPin)/1000); // Divide by 1000 to scale 0-1
  int ldrValue = analogRead(ldrPin); // Store variable value
  if (ldrValue > 1000) { // If value is greater than 1000
   digitalWrite(LED1, HIGH // Turn LED on
} else {
   digitalWrite(LED1, LOW); // Turn LED off
}
   delay(100);
}
```

![Laser Sensor and Laser Receiver Module First Prototype](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_038-1.jpeg)

Unfortunately, shortly after writing this the receiver module broke. It is presumed that this is due to its cheapness. The module only cost a few pounds and was apparently not very robust or well made. The receiver module was switched out for a LDR module instead.

**Laser Sensor and LDR Module**

This module works exactly the same as the laser receiver module as they are essentially the same sensor, they differ only in the range of values that are output. The LDR module, when the laser is pointing at the module, outputs a value of approximately 24 and when the laser beam is block by an obstacle the value raises to around 190. In the prototype, the LDR module acted as a switch; if the value was less than 100 then an LED was turned off and if the value was greater than 100 the LED was turned on.

![Laser Sensor and LDR Module First Prototype](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_033-1.jpeg)

**Analogue Joystick Controller**

This prototype was used to test the different values the controller was capable of outputting. These results were then used to try to determine if there was a relevant place for it in the installation. The controller required only a few simple instructions to become operational. The first was defining the two potentiometers into analogue pins 0 and 1 and then defining the switch pin. The pinMode for the switch was set to input and the pull-up resistors on the Arduino were enabled. The positions of the two potentiometers were set to print to the serial monitor, their values ranging from 0 to 1023. The switch is a push button set to print a 0 when untouched and a 1 when pressed. Its place in project is still undecided as of now.

![Analogue Joystick First Prototype](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_039-3.jpeg)

### Second Prototypes 

**Multiple Ultrasonic Sensors**

This prototype is a reworked version of the previous one, it allows multiple separate sensors to print their individual values over serial. With this sensor especially, this method allows for different trigger parameters to be specified so they can all react differently. Firstly the trigger and echo pins from the sensors have to be defined along with the LEDs, this sketch also requires a long command; long variables are extended size variables for number storage. Duration, distance and the sensor groups will be detailed later in the explanation.
```
#define trigPin1 A1  // defining first trigger pin, this pin will receive a short pulse in microseconds (µs) to begin ranging. Module sends out 8 cycle burst of ultrasound at 40kHz to raise  its echo. (Analogue pin 1).
#define echoPin1 A0  // defining first echo pin, this pin will gauge distance in conjunction with the trigger pin.
#define trigPin2 A2
#define echoPin2 A3
#define trigPin3 A4
#define echoPin3 A5
#define led1 10  //defining the first led. (Digital pin 10).
#define led2 9
#define led3 8
#define led4 7
#define led5 6
#define led6 5
    
long duration, distance, FirstSensor, SecondSensor, ThirdSensor;
```
During the void setup the serial needs to be started on the chosen baud rate. Next the pins on the ultrasonic sensors and LEDs need specifying to state whether they are input or output pins.
```
void setup() {
    Serial.begin (9600);  //starting serial on 9600 baud rate.
    pinMode(trigPin1, OUTPUT); //stating how the trigger pin behaves.
    pinMode(echoPin1, INPUT);  //stating how the echo pin behaves.
    pinMode(trigPin2, OUTPUT);
    pinMode(echoPin2, INPUT);
    pinMode(trigPin3, OUTPUT);
    pinMode(echoPin3, INPUT);
    pinMode(led1, OUTPUT); //stating how the echo pin behaves.
    pinMode(led2, OUTPUT);
    pinMode(led3, OUTPUT);
    pinMode(led4, OUTPUT);
    pinMode(led5, OUTPUT);
    pinMode(led6, OUTPUT);
}
```
The loop section on this multiple sensor prototype now works a little differently than before, for example each sensor is put into a group; in this case "SonarSensor" and has its integers specified. This is because, the generic sensor pins will be used later in their own void declarations but will not be specific to any particular sensor. Instead they will state how the sensor should behave and thus require a separate, additional declaration to make each sensor variable otherwise they would all behave the same. The individual sensors are then given names; for this example they are "FirstSensor", "SecondSensor" and "ThirdSensor". The module uses a combination of the unique pins and the generic calculation to understand how it should behave. The serial printing is divided into three separate numbers and waits 300ms before printing each time.
```
void loop() {
    SonarSensor(trigPin1, echoPin1); //adding the SonarSensor into the loop, to be recalled later and with intergers specified to the corresponding pins and leds.
    FirstSensor = distance; //sensors = distance, distance = echo pin return/2/29.1
    SonarSensor(trigPin2, echoPin2);
    SecondSensor = distance;
    SonarSensor(trigPin3, echoPin3);
    ThirdSensor = distance;

    Serial.print(FirstSensor); //printing first sensor distance in cm to serial monitor.
    Serial.print(" ");
    Serial.print(SecondSensor);
    Serial.print(" ");    
    Serial.println(ThirdSensor); //end printing line so each stack will appear below after ever interval.
    
    delay(300); //print interval in ms. Recommended to use above 60ms to prevent trigger and echo signals becoming confused.
}
```
How the SonarSensor group functions in the sketch now has to be declared; this is so that it can be recalled in the loop section. The "void" indicates that the function is expected to return no information to the function from which it was called; this means actions can be executed in the functions "setup" and "loop" but it will not extend to the larger programme. The trigger and echo pins are declared as the two that are in use. The calculation has been written in conjunction with the operational information from the datasheet; this stated that the trigger pin had to be pulsed hig for at least 10µs before waiting for the echo to return the signal. So it sets to low, pulses high then goes low again. When the echo pin receives a high return pulse, the time that has elapsed equals the duration. The distance uses the duration in the calculation as seen below. Now, because the sensors have been grouped and are ready to be recalled in the loop section, their behaviour can now be written here. If the first sensor encounters an obstacle that is closer than 20cm it turns LED1 on and LED2 off. If the obstacle is further than 20cm the reverse happens. Because the LED used is a bicolour green and red LED, both times it is impacting the same one.
```
void SonarSensor(int trigPin, int echoPin) {
    digitalWrite(trigPin, LOW);
    delayMicroseconds(2);
    digitalWrite(trigPin, HIGH); 
    delayMicroseconds(10); //supplying the trigger pin with short 10µs pulse.
    digitalWrite(trigPin, LOW);
    duration = pulseIn(echoPin, HIGH);
    distance = (duration/2) / 29.1; //Distance = (Time x SpeedOfSound) /2. The "2" is because the sound has to travel back and forth. /29 because sound travels at approximately 340 meteres per second, which corresponds to about 29.412µs per cm. The easy way to read the formula: cm = ((µs/2)/29). If it takes 100µs for the ultrasonic sound to bounce back, then the distance is ((100/2)/29) or approximately 1.7cm.
    
  if (FirstSensor < 20) { 
    digitalWrite(led1,HIGH);
    digitalWrite(led2,LOW);
  }
  else if (FirstSensor > 20) {
    digitalWrite(led1,LOW);
    digitalWrite(led2,HIGH);
  }
  if (SecondSensor < 40) { 
    digitalWrite(led3,HIGH);
    digitalWrite(led4,LOW);
  }
  else if (SecondSensor > 40) {
    digitalWrite(led3,LOW);
    digitalWrite(led4,HIGH);
  }
  if (ThirdSensor < 80) { 
    digitalWrite(led5,HIGH);
    digitalWrite(led6,LOW);
  }
  else if (ThirdSensor > 80) {
    digitalWrite(led5,LOW);
    digitalWrite(led6,HIGH);
  }
}
```
The other two sensors are programmed the same way. As this was the first attempt at a multiple sensor sketch it did take quite a lot of trial and error to get it working correctly. Using if else if was the way the sketch finally became usuable and worked in the corect manner. However, through perseverance, the idea became a reality and offered a template to start working from on other multiple sensor sketches.

![Ultrasonic Second Prototype](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_034.jpeg)

**Multiple IR Sensors**

This prototype is again a reworked version of the previous one. It allows multiple separate sensors to print their individual values over serial. Unlike the ultrasonic sensor, the range does not need to be specified in the code as it uses an on-board potentiometer altered with a screwdriver. The integers are specified so that the individual sensors can write their data to the serial monitor separately. The five sensors are split into five groups, all using the same variable; obstacle.
```
void ObstacleSensor(int obstaclePin)
  {
  obstacle = digitalRead(obstaclePin); //etc, only a fraction of the void declaration
```
As the variable equals the state of the obstaclePin, each sensor is given its own unique pin value.
```
void loop() {
  ObstacleSensor(obstaclePin1);
  FirstSensor = obstacle;
  ObstacleSensor(obstaclePin2);
  SecondSensor = obstacle; //this continues up to the fifth sensor
```
The sensors will print their values over serial, depending on if an obstacle is detected they will either print a 0 or a 1. Also in this prototype if an obstacle is detected an LED for the corresponding sensor turns on. In the final design these LEDs may be scrapped due to the IR sensors having internal LEDs.

![IR Second Prototype](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_036.jpeg)

**Multiple PIR Sensors**

The first PIR sensor will be acting as a motion sensing toggle for the ambient section in the patch. The idea was to add a second sensor and use it in a similar way. Unfortunately, due to the way the print function works, when one PIR sensor detects motion and prints its value, the other sensor loses its ability to print over serial. Both sensors could be made to work at the same time, but their values continuously printed to the serial monitor and this was not the desired effect. Because of this, the decision was made to use only one PIR sensor as originally intended.

![PIR Second Prototype](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_037-1.jpeg)

**Multiple Sensor Prototype**

This prototype contains five different sensors; a touch capacitive sensor, an ultrasonic range finder, an analogue joystick, a laser sensor module and an LDR module. The idea behind this was to put all of the leftover sensors on their own Arduino board, mostly because the PIR has to remain on its own, there were already five IR sensors on one board and obviously, the more sensors on a board the slower each subsquent sensor will respond and the more power they will draw. By this point, programming this collection of sensors was fairly straight forward. As usual, it starts by defining the integers and specifying the long values.
```
#define trigPin1 A1  //defining first trigger pin, this pin will receive a short pulse in microseconds (µs) to begin ranging. Module sends out 8 cycle burst of ultrasound at 40kHz to raise  its echo. (Analogue pin 1).
#define echoPin1 A0  //defining first echo pin, this pin will gauge distance in conjunction with the trigger pin.
#define led1 10  //defining the first led. (Digital pin 10).
#define led2 9
#define led3 8
#define led4 7
#define ctsPin1 2  //defining the touch sensor.
#define psrPin1 A2  //defining the LDR module.
#define joyPin1 A3  //defining the x-axis
#define joyPin2 A4  //defining the y-axis

long duration, distance, ctsValue, psrValue, joyValue, FirstSensor, SecondSensor, ThirdSensor, FourthSensor, FifthSensor;
```
From here, a simple case of starting the serial monitor and specifying the pinModes for the sensors. In the loop, stating what the different groups do, making sure they print and at what interval. Finally it is a case of stating what each group actually does.
```
void SonarSensor(int trigPin, int echoPin) {
    digitalWrite(trigPin, LOW);
    delayMicroseconds(2);
    digitalWrite(trigPin, HIGH); 
    delayMicroseconds(10); //supplying the trigger pin with short 10µs pulse.
    digitalWrite(trigPin, LOW);
    duration = pulseIn(echoPin, HIGH);
    distance = (duration/2) / 29.1; //Distance = (Time x SpeedOfSound) /2. The "2" is because the sound has to travel back and forth. /29 because sound travels at approximately 340 metres per second, which corresponds to about 29.412µs per cm. The easy way to read the formula: cm = ((µs/2)/29). If it takes 100µs for the ultrasonic sound to bounce back, then the distance is ((100/2)/29) or approximately 1.7cm.
    if (FirstSensor < 63) { 
    digitalWrite(led1, HIGH);
    digitalWrite(led2, LOW);
  }
  else if (FirstSensor > 63) {
    digitalWrite(led1, LOW);
    digitalWrite(led2, HIGH);
  }

}

void TouchSensor(int ctsPin) {
  ctsValue = digitalRead(ctsPin);
  if (ctsValue == HIGH) {
    digitalWrite(led3, HIGH);
  }
  else {
    digitalWrite(led3, LOW);
  }
}

void LaserSensor(int psrPin) {
  psrValue = (analogRead(psrPin));
  if (psrValue > 100) {
    digitalWrite(led4, HIGH);
  } else {
    digitalWrite(led4, LOW);
  }
}

void JoySensor(int joyPin) {
  joyValue = analogRead(joyPin);
}
```
Once this was complete, everything was set up and ready to use.

![Multiple Sensor Prototype](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_040.jpeg)

## Pure Data Patch Initial Build
The chosen location for the sound installation is a cemetery in Birmingham, the purpose of this project is to engage with the environment and add an extra dimension to the surroundings. Due to the location being a cemetery, the theme of the audio was to create and ominous and unnerving atmosphere. With this in mind, various audio techniques that could potentially create appropriate results we chosen and researched. The goal of the first patch iteration was to produce a ghostly ambient tone generator and a sample playback machine that could be used to trigger various relevant field recordings and samples.

![First Patch Iteration](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/1.png)

### Ambient Tone Generator
The ambient tone generator is the first section in the Pure Data patch and is based on a system that creates ever-different and changing music known as generative music. The tone generator produces a sound, which is the outcome of multiple waveforms being summed together. Once the generator is triggered, a MIDI value is selected every 15000 to 25000 milliseconds, in relation to the chosen scale. This value then splits down several different routes and has a range of variables added to it before it reaches its designated oscillator. The individual numbers are multiplied by 4 and have a range of millisecond variables running into a vline~ object, this causes the numbers to slowly increase or decrease to their chosen end point. Each number is added together with an external oscillator value and set to modulate at a particular rate. When combined with a reverb using early reflections, the modulation depth will increase creating an eerie tone. These oscillators are summed and then a single waveform is output.

![Ambient Tone Generator](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/2.png)

The tabread function that reads the scales has the choice of five different scales, these are created by specifying the relevant intervals. From this, a number will be selected which corresponds to a MIDI note from any key within the scale.

![Scale Values](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/3.png)

This generator, as long as it is active, will continuously create a tone based on a set of predefined rules. The tone generator has been based up the idea of generative music because of its responsiveness to user input and its innate ability to adapt to ever changing circumstances. It is based on sets of rules that determine iterative sequences, shifting permutations and random routine thus creating unique experiences, even when completing the same task repeatedly.

### Sample Triggers
The sample playback machine is capable of playing a sample while possessing the ability to alter its volume, pitch and direction. There are nine samples in total and they are split into three groups; 1-3, 4-6 and 7-9.

![Sample Groups](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/4.png)

They will use one IR sensor each, this means that every time a sensor is triggered it has the chance to play one of three samples randomly.

![Three Samples](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/5.png)

Not only that, each sampler is polyphonic and has eight voices, meaning up to eight of the same sample can play at once. This helps to prevent the samples from ending prematurely to start again. Also each time a sample is triggered it has the possibility to be transposed to a higher or lower pitch, as well as possibly playing in reverse.

![Transposition and Direction](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/6.png)

The samples are preloaded into the patch so the user does not have to locate them, as soon as the patch is opened the samples are ready to work; this is due to the message boxes with the relevant information being connected to a loadbang.

![Preloaded Samples](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/7.png)

The samples are read from a table, so it is important to first write them to one.

![Table Samples](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/8.png)
![Table 1](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/9.png)

The samples are split into nine different audio banks, inside each one are the receives for the transpositional value, direction, volume and sample length. As before there are eight separate sample abstractions due to the polyphony aspect.

![Sample Banks](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/10.png)
![Individual Sample Banks](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/11.png)

Inside each sample bank is the structure for the way the sample playback operates.

![Sample Playback](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/12.png)

## Sensor Mapping Test
The ambient tone generator does not require multiple input triggers to operate, because of this, it receives its input from the PIR sensor. If the value is high then the generator becomes active, it will remain active until it no longer detects motion. A metro object is toggled on and has its millisecond variable randomised. 

The three sample section were connected to the first three IR sensors, triggering a sensor every now and then worked well and constantly triggering the sensors also created some interesting results. This is due to the samples having multiple variations, even if the same sample is triggered twice, it is very probable that it will be transposed and possibily playing in reverse.

![IR Sensor Sample Triggers](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_068.jpeg)

With this all working as intended, it was time to continue building the patch.

## Finalising the Pure Data Patch 
Now that the first two audio generation sections have been built and connected to the sensors it is time to finish building and implementing the rest of the audio sections.

### White Noise Generator
The white noise generator uses a feedback artificial neural network to generate white noise, modulating from 0 to 1Hz, which is filtered through 24 bandpass filters at different frequencies ranging from 46 to 69Hz. Once the network is active the artificial neurons will fire and will either trigger a 0 or 1, a low or high signal, through the snapshot function. The output depends on the value of the threshold, as the threshold value changes it affects the amount of neurons that are allowed to pass, which changes the sound of the modulating white noise.

![ANN Overview](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/13.png)

The network is 3x3, incorporates feedback and in this installation the time-scale dynamics are set to 1ms via the snapshot object, so the response is extremely fast. 

![Neural Network](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/14.png)

The learning rule has been adapted to work alongside user interaction with the sensors. The sensors with variable outputs, such as the ultrasonic or joystick modules, have their outputs monitored and averaged. The averages are summed, multiplied, averaged once more and finally reversed. This final number is used as a millisecond counter to trigger different threshold values for the network; which means the more the user interacts with the sensors, the faster the threshold will change, which will make the network more dynamic. The threshold is the last deciding factor in whether the neurons fire. If the output of the neuron is below the threshold, it will not fire.

![Learning Algorithm](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/15.png)

The outcome of the 24 neurons are sent to the noise bank, there they are received by 24 toggle boxes. If the neuron does not fire, produces a 0, the respective modulated white noise will not be audible, however, if the neuron does fire, produces a 1, the respective modulated white noise will be heard.

![Noise Bank](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/16-1.png)

All of the outputs are sent to one vline~ object. 

![24 Outputs](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/17.png)

If the main toggle is switched on, then the artificial neural network will become active, this toggle also controls the metro object for the learning algorithm.

![ANN vline~](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/18.png)

Depending on the threshold, more or less neurons will fire. This will affect the overall tonal density of the white noise generator. Since loops are present in this type of network it becomes a non-linear, dynamic system, which changes consistently. This is due to connections forming between layers of neurons, resulting in the generation of a directed cycle, which, subsequently creates a dynamic state allowing the network to exhibit dynamic temporal behavior.

### Spectral Bank
This section is an audio filter bank that uses multiple bandpass filters to attenuate frequencies between 100Hz and 1250Hz. White noise is the audio source used for this filter bank, it is ideal as it possesses a full range of frequencies.

![Spectral Bank Overview](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/19.png)

The value from an ultrasonic sensor, scaled between 0 and 120, will raise as the user moves closer. As the user presses down on the touch sensor it will trigger two random values. The first being a divisional value between 1 and 5, this number is used so that the different filter frequencies do not raise with the same value. The user can remain at the same frequency and keep pressing the touch sensor to dynamically change the way the spectral bank sounds. The second value is a random millisecond variable, set between 1000 and 2000, that will make each fader move at a different speed.

![Spectral Bank Controls](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/20.png)

The final outputs from that section are mapped to the 10 faders, which will be raised depending on the parameters selected by the variables. The white noise will be running through each of the different filters and the fader values will be divided to raise each of the volumes bewteen 0 and 1.

![Filter Bank](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/21.png)

Finally, in the last part of the signal chain is a flanger, which mixes two identical signals together, one of which is delayed by a small amount that produces a swept comb-filter effect. The flanger is set to modulate faster the further away the user gets from the sensor.

![Flanger](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/22.png)

### Distortion Synthesiser
This section within the installation is controlled by an ultrasonic range finder and an analogue joystick. The range finder controls the carrier wave value and is set to only trigger values when an obstacle is within a predetermined range. This is indicated by a bicolour LED, when an obstacle moves within the target range of the sensor a variable value is sent to Pure Data. The closer an obstacle is to the sensor, the higher the phasor value will be. The index and two additional waveform values are decided by using the analogue joystick. The x-axis controls the index value, this value is variable and ranges from 0 to 1000. Finally the y-axis controls both the additional waveform values; which are specified in hertz. These are also scaled between 0 and 1000, however, the first waveform reads the y-axis value whereas the second waveform is reversed. The joystick also controls whether the synthesiser is turned on or off, the push button has been programmed to behave as a toggle. An LED has been connected as a visual aid, so when the light is on or off, the synthesiser is on or off respectively.

![Phase Distortion Controls](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/23.png)
![Phase Distortion Synthesiser](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/24.png)

### Perceptual Artificial Reverb
The reverb section in this installation is constructed from several different aspects. There are four main controllable elements; a roomsize control, a dampen control which is a lowpass filter connected to the comb-filters, finally a dry and wet amount.

![Reverberator Controls](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/25.png)

There are two sets of four comb-filters for each side, left and right, which are specifically tuned to sound less metallic and harsh.

![Internal Layout](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/26.png)
![Reverberator Tunings](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/29.png)

This totals eight tuned comb-filters per side which all run in parallel.

![Comb-Filters](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/27.png)

These are routed into their respective left and right diffusion sections, inside these contain four all-pass filters in series and affect how fast or slow the initial reflections of the artificial reverberant space are smoothed out over time. 

![All-Pass Filters](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/28.png)

The final section is a wet and dry mix, offering two separate channels like in most digital audio workstations not by turning down one to increase the other.

### Completed Patch
The audio section of the installation is now complete and all of the chosen generation techniques have been built and implemented.

![Completed Audio Section](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/PD/30.png)

## Designing the Installation Structure
The initial idea for layout of the sound installation was to set up small groups of sensors in multiple places within a small space at the chosen location, which is a cemetery. However, due to there being no power and not many places to suspend sensors it was decided that the installation would be an all-in-one style scaled down version. With this in mind, a few sketches were created concerning how the design might look. These designs incorporated considerations such as cost, accessibility, usability and mobility. It was important to create a product that could be moved easily without having to dismantle the entire array, that was inexpensive and that could be accessed easily by the audience.

![First Sketch](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_042-3.jpeg)

The idea was to have a series of wooden boxes with the sensors either mounted inside, on top of or on the side of them. The difficult part was designing a way to incorporate all of the sensors without any crosstalk between them or without the user accidentally operating multiple sensors simultaneously due to them being too close to each other or their range overlapping. As the IR sensors suffer from interference from artificial and natural light sources, the more that could be done to reduce this, the more reliable they would become. To try and reduce the light intereference, the IR sensors have all been housed inside boxes. A large box, acting as the main support, sits at the bottom and contains three IR sensor while two smaller boxes containing one IR sensor each sit on top. The PIR sensor was designed to be situated at the front and on top of the two boxes, the thought process behind this was that if a person is interacting with the patch they should be triggering the ambient generator. The Arduinos were to be mounted on the back out of the way and the ultrasonic sensors were originally supposed to be attached to the sides.

![Second Sketch](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_042-4.jpeg)

Unfortunately, it was soon realised that if the ultrasonic sensors were situated on the sides then every time the user moved forward to activate an IR sensor they had the potential to unintentionally control the ultrasonic sensors as well. Because of this the ultrasonic sensors were moved to the top of the box and placed back to back, this is because they suffer from crosstalk if they are placed close together facing the same direction. Each ultrasonic sensor is combined with an additional sensor, the left side contains the touch capacitive sensor and the right is equiped with the analogue joystick. The ultrasonics are placed far back and the two other sensors are placed right on the edge, the reason behind this is to offer the user the ability to place one hand on the touch sensor or joystick whilst using their other hand or torso to control the ultrasonic sensors. The laser sensor and LDR module are positioned on the top left box and the Arduinos remain in the same position.

![Final Sketch](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_042-5.jpeg)

After finalising the design a visit was paid to a carpenter named Maurice Northall. After showing him the design, sensors and explaining how it needed to operate, we calculated precise measurements for each box. He then proceeded to cut the wood and assemble all three boxes.

![Smaller Box](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_044.jpeg)
![All Three Boxes](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_043.jpeg)

All three boxes were then bolted together. A final small wooden frame was constructed and attached to the top for the PIR sensor. Five short pieces of wood were cut and glued into the boxes ready for the IR sensors to be attached to.

![Box Frame Bare](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_045.jpeg)
![Box Frame with IR Sensor](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_046.jpeg)

On the back of the large box, the four Arduinos were laid out and measured ready to be attached. The Arduinos would be attached to terminal adapters which allows cables to be connected to them without the need of a soldering iron, this not only removed an extra job but also provided a sturdy method to mount the boards onto the box.

![First Arduino Mounted](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_047.jpeg)
![All Arduinos Mounted](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_048.jpeg)

Next the PIR sensor was screwed to the wooden brace on the top of the box, the location was actually perfect for the job the sensor carried out.

![PIR Sensor Connected to Brace](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_049.jpeg)

The ultrasonic mounting brackets were attached back to back, the touch sensor and joystick were also connected according to the design sketch.

![Mounting Brackets and Two Sensors](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_052.jpeg)

The laser sensor and LDR module were connected on the top left of the box and the five IR sensors were connected to the first Arduino, as previously discussed, the external LEDs for these sensors were not included as they were no longer necessary.

![Five IR Sensors](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_053.jpeg)
![First Arduino Connections](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_054.jpeg)

Before the joystick, touch sensor, laser sensor and LDR module were soldered a few last minute adjustments were made. The third ultrasonic sensor was removed and the switch for the joystick was implemented. However, the switch only acted as a momentary push button and it needed to behave as a toggle, so the code had to be altered to accommodate these changes.
```
void JoySwitch(int switchPin) {
  reading = digitalRead(switchPin);
  if (reading == HIGH && previous == LOW && millis() - time > debounce) {
    if (state == HIGH)
    state = LOW;
    else
    state = HIGH;

    time = millis();
  }
    digitalWrite(led1, state);
    previous = reading;
}
```
The integers state, reading and previous are declared in the setup. Time, measured in milliseconds, is declared as a long variable as it will quikcly become a larger number than can be stored in an int. There is another long variable called debounce, this is a minimum delay between toggles to ignore noise. The above code states that if the input just went from low to high and has waited long enough to ignore any noise on the circuit, toggle the output pin and vice versa while remembering the time. The state value will be 0 or 1, which will turn and LED off and on respectively. When the switch is toggled on, the joystick will affect certain parameters within Pure Data and when it is toggled off it turns off the sound to the phase distortion section.

![Last Minute Prototyping](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_055.jpeg)

After this the two ultrasonic sensors were added and connections were soldered.

![All Sensors Present](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_057.jpeg)

The final LEDs were put into place for the two ultrasonic range finders, touch sensor and joystick switch. These were soldered and connected to the relevant Arduinos. One final test was completed to make sure everything functioned as expected and with that the whole process was complete.

![Finished Structure](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_065.jpeg)
