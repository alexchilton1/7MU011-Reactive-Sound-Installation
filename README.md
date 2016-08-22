# 7MU011-Reactive-Sound-Installation
A sound installation that responds to stimuli and continuously evolves via user input. This input is made possible through the use of a range of different sensors. This project employs the use of HCI (Human-Computer Interaction) through several Arduinos. The software element of this project was built using two main platforms; each sensor had its behaviour written using the Arduino's IDE (Intergrated Development Environment). The audio section of this installation was built in Pure Data.

## Acronyms/Abbreviations/Symbols
```
cm - centimeters
DC - Direct Current
EEPROM - Electrically Erasable Programmable Read-only Memory
HCI - Human-Computer Interaction
Hz - Hertz
IC - Intergrated Circuit
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
This module recognises when the laser beam is pointing at its sensor. The sensor in question is an LDR (light dependent resistor), the resistance of an LDR decreases with increasing incident light intensity. When the light level is low the resistance of the LDR is HIGH. However, when the light shines onto the LDR, its resistance lowers and the outputing signal would be LOW. This sensor combined with the laser module is used to create a trip sensor. As a person passes through the beam it cuts off the light source to the LDR, therefore, switching its output to HIGH, allowing the circuit to affect the chosen variable(s) within the Pure Data patch.

![Laser Receiver Transceiver LED Module](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_019.jpeg)

## Prototypes

###### First Prototypes

After the datasheets for the modules had been collected and studied it was time to start progamming their behaviour, this would not only decide how they operate but it would also define what information would be sent over serial to Pure Data. For each sensor the respective datasheet had to be investigated to help specify what the sensor was actually capable of doing and how it had to be wired. The way it has to be wired along with its capability are the framework in deciding how it must be programmed.

**Ultrasonic Sensor**

The first sensor  to be programmed was the Ultrasonic Module HC-SR04 Distance Sensor, the device features four pins; a VCC (Voltage Common Collector), a Trigger pin, an Echo pin and GND (Ground). The Nano can supply the necessary 5V and GND direct to the sensor thus dealing with the power aspect of the module. To be able to use this sensor to measure distance requires an understanding of how the trigger and echo pins operate, the trigger pin has to be sent to a digital/analogue output pin on the Arduino and the echo pin has to be routed to a digital/analogue input. The tigger pin requires a pulse producing a HIGH output for a minimum of 10μs (microseconds), the sensor then has to wait for a HIGH level to return on the echo pin. The length of time the echo pin stays HIGH corresponds to the distance that the ultrasonic sound has travelled. The quicker the response, the closer the sensor is to an obstacle.

For this prototype the trigger pin was routed to A1 (Analogue Pin 1) and the echo pin to A0. The trigger pin receives a HIGH pulse for 10μs, when the return is picked up by the echo pin this length of time since the send and receive is stored as the duration. The duration is used in the final calculation to work out the distance in cm. 

Sound travels at approxiamtely 340 metres per second. This corresponds roughly to 29.412μs per centimeter. To measure the distance the sound has travelled, this formula is used: Distance = (Time x SpeedOfSound)/2. The "2" is in this formula becuase the sound has to tavel back and fourth. The sound travels away from the sensor first, then it bounces back off a surface and returns. The best wasy to read the distance in centimeters is to use this formula: Centimeters = ((Microseconds/2)/29).

An LED is also used as a visual prompt to the current status of the sensor. The LED is a Kingbright 5mm, 3-pin, green/red, though-hole LED. It has forward voltage of 2.5V and a forward current of 25mA on green and 30mA on red. With the source voltage being 5V, the forward voltage being 2.5V and the max forward current being 30mA a 100Ω (ohm) resistor would be recommended. This would mean each 100Ω resistor would dissipate 90 mW, the diodes dissipate 75 mW, the total power dissipated by the array would equal 165 mW and the array would draw current of 30 mA from the source. However as a precaution a 150Ω resistor was used. The LED has three pins, a GND and two VCC pins. The resistor is attached to the GND pin on the LED and then routed back to the GND pin on the Arduino, the two VCC pins receive HIGH and LOW signals to light both of the colours. For example, when one VCC pin is HIGH it would make the LED turn green, the VCC pin controlling the red side would be LOW at this point. In the reverse set up the LED would be red. The sensor is programmed check whether there is an obstacle in front of it. It measures the distance in front of it and if the distance is less that the chosen number, it will recognise that there is an obstacle in range. When this happens the LED will turn red, when the distance is greater than the chosen variable the LED is lit green and the sensor does not register that an obstacle is blocking it. It will however, still report the distance of any obstruction in cm. - DIGITAL PIN 10!

![Ultrasonic First Prototype](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_025.jpeg)

**IR Proximity Sensor**

The IR sensor has 3 pins: VCC, GND and an output pin which sends either a HIGH or LOW signal depending on its detection status. This sensor is capable of detecting the presence of an object, however, it is not capable of determining the distance of the obstruction. This sensor is ideal for triggering on/off values and coupled with Pure Data it could be used to randomise variables within a sequence or prompt the introduction of a new piece of audio to the overall mix. The infrared transmitter emits an infrared radiation, when there is an obstacle in range, the wave bounces back to the receiver and the circuit becomes active. The range of the sensor can be adjusted by its onboard potentiometer, the datasheet professes that the range is 2cm-30cm but this does not seem to be the case. The safe range before the sensor becomes unpredicable seems to be around 25cm, any more and the module becomes unreliable. Also the sensor suffers heavily from light interference, natural light seems to be the worst. Sunlight makes the module very unreliable and artifical light also seems to affect its reliability.

The sensor has its VCC and GND pins connected to the Arduino the same way as the ultrasonic sensor, the OUT pin is routed to A0. The sensor has been programmed to know, in compliance with the datasheet, that if and obstacle is within its agreed range it outputs a LOW singal. If the sensor does not detect an obstruction then its output is HIGH. An LED has been connected to digital pin 12 to help aid this detection process visually. With the source voltage from the Nano at 5V, the VF at 2.5V and the IF at 30mA, the recommended resistor was again at 100Ω. When the module detects an obstacle the LED turns blue, when no obstacle is present the LED switches off.

The only problem with the wasy in which this sensor works is that it emits a LOW signal when the sensor is active and a HIGH signal was it is inactive. This function is opposite to the way the PD patch has been set up, when a variable is active the signal is HIGH, so within PD the receive signals have been switched.

![IR Proximity First Prototype](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_023.jpeg)

**PIR Motion Sensor**

PIR sensors are more complex that IR proximity sensors because there are more variables that affect the sensors input and output. The sensor itself has two channels in it, each of the channels consist of special IR sensitive material. The lens does not do a great deal, the two channels can look out through this providing the sensitivity of the sensor. When the sensor is idle both channels detect the same amount of IR, the ambient amount radiated from the room, walls or outdoors. When a warm body, such as, a human or animal passes in front of the sensor it is identified by one half of the PIR sensor. This causes a positive differential between the two halves. When the warm body leaves the sensing area, the reverse happens, whereby the sensor generates a negative differential. These change pulses are what is detected. The IR sensor is housed in a hermetically sealed metal to help improve immunity to noise, temperature and humidity. There is a window made of IR-transmissive material, typically coated silicon, that protects the sensing element. Behind this window are the two balanced sensors.

The smart part of the PIR sensor is the optics. The lens is just a piece of plastic and detection area is only two rectangles, which is not ideal as it is not particularly large. To counteract this a fresnel lens is used, this lens helps to condense a large area into a small one. The Fresnel lens condenses light, providing a larger range of IR to the sensor, however, there are two sensors scanning large rectangular areas which is not the desired effect. The intended outcome is to have multiple small areas, so the lens is split up into multiple sections, each of which is a fresnel lens.

The prototype is designed to detect motion and turn on the LED when this is true providing a visual indication. The PIR detects movement and prints this to the serial, it however is programmed to pause serial printing until there is a state change and the motion stops. It will continue to detect motion for as long it recognises that movement is present, when the movement haults the sensor is programmed with a pause time, if the hault in motion is greater than the stated pause time the sensor will print that over serial and send a LOW signal to the LED causing it to switch off. The sensor has been made less responsive like this on purpose, not printing to serial every 100ms for example, so that it can provide a precise function in the PD patch. This function is to change the variables in the ambient section, if it rapidly changed it would not operate as intended and would begin to interfere with the other sections. Using the PIR in this way helps to keep the ambience dynamic as it ungulates in the background without becoming too distacting.

![PIR First Prototype](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_029.jpeg)

**Touch Sensor**

The touch sensor can sense the electrical capacitance of the human body. The sensor produces a signal that gets routed to the send pin and waits for the receive pin to change to this new state. A variable is incremented inside the loop to time the state change of the receive pin. The value of this variable is then reported as HIGH or LOW meaning 1 or 0 respectively.

The sensor is programmed to respond to touch, sending a HIGH signal when contact is made and a LOW signal when there is none. The response is very quick, with the cycle refreshing every 100ms, this means that everytime it is touched and released it will trigger and there is no delay.  An LED has again been used as a visual aid, when the signal is HIGH the LED is active and when LOW it is not.

The first step in the process is to state where the sensor and LED are routed to on the Arduino.
```
#define ctsPin 2 // This tells the Arduino to look for ctsPin (capacitive touch sensor) and replace it with 2 (digital pin 2)
int LED1 = 10 // This adds the first LED as an integer on digital pin 10
```
The reason define is used for the sensor and int is used for the LED is because the #define function acts as a search an replace setting and int is a variable. Whenever the compiler reads "ctsPin" it now believes it saw "2". It can't be changed while the sketch is running however, it takes no memory in the processor. Meanwhile the int function is a variable and does take a small amount of memory, 2 bytes to be precise, to store the value and takes an extra bit of memory to store the original value. This, however, allows the sketch to modify the variable under any desired circumstance and use the altered value from that point on.

The sketch then requires the serial to started on the chosen baud rate and the pinModes to be specified in the void setup. The serial is set to begin on baud rate 9600, the ctsPin is set as an input and the LED is chosen as the output. The void loop is where the the previously mentioned variable between the send and receive pin is detailed. The variable value is stated as the condition of the touch sensor. The code for the loop would look similar to this.
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

The way this circuit was designed to work, was by the laser beaming its output into the LDR of the laser receiver module which would the output a variable. If the signal was HIGH then the beam was present, if LOW the beam of light had been broken by an obstacle. This would presumably mean that a person had walked past causing the line of sight of the sensor to become obstructed, thereby, triggering a signal over serial to PD. The laser sensor module simply required to be connected to 5V and GND pins. The receiver module was programmed similiar to how the touch sensor was coded. The input of the receiver was connected to the Arduino pin A0. Using the analogRead function within the Arduino IDE the initial value range was analised to observe output of the sensor when the laser was present and removed.
```
void loop() {
  Serial.println(analogRead(ldrPin)); // This prints the output over serial
  delay(100); // Delays the process by 100ms each time
}
```
The output of the sensor ranged from 2-20 when the laser was removed and between 1010-1019 when the laser was shone onto the receiver. With this in mind it was fairly simple to decide how best to programme the circuit for both being efficient in the sketch and producing usable results in PD. An LED was again used as a visual aid, using a 150Ω resistor as in the previous prototypes. For PD, the output was scaled between 0 and 1. This was accomplished by dividing the output of the receiver by 1000. Next an integer was created to store the variables of the receiver module. Even though the sensor over serial read 0-1, the actual numbers remained the same, from approximately 2-1020. With this in mind it was intelligible to state that if the variable value was greater than 1000 this means the circuit was active, if the value was below 1000 then it should be perceived as off. The on and off statements are was turns on the LED and the 0-1 is what was send to PD creating simple binary values. The whole process was delayed by 100ms each time to make the receiver responsive but not too sensitive.
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

###### Second Prototypes

**Multiple Ultrasonic Sensors**

This prototype is a reworked version of the previous one, it allows multiple separate sensors to print their individual values over serial. With this sensor especially, this method allows for different trigger parameters to be specified so they can all react differently. Firstly the trigger and echo pins from the sensors have to be defined along with the LEDs, this sketch also needs a long command; long variables are extended size variables for number storage. Duration, distance and the sensor groups will be detailed later in the explanation.
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
The loop section on this multiple sensor prototype now works a little differently than before, for example each sensor is put into a group; in this case "SonarSensor" and has its integers sepcified. This is because, the generic sensor pins will used later in there own void declarations but will not be specific to any particular sensor. Instead they will state how the sensor should behave and thus it requires separate, additional declaration to make each sensor variable otherwise they would all behave the same. The individual sensors are then given names; for this example they are "FirstSensor", "SecondSensor" and "ThirdSensor". The module uses a combination of the unique pins and the generic calculation to understand how it should behave. The serial printing is divided into three separate numbers and waits 300ms before printing each time.
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
How the SonarSensor group functions in the sketch now has to be delared; this is so that it can be recalled in the loop section. The "void" indicates that the function is expected to return no information to the function from which it was called; this means actions can be executed in the functions "setup" and "loop" but it will not extend to the larger programme. The trigger and echo pins are declared as the two that are in use. The calculation has been written in conjunction with the operational information from the datasheet; this stated that the trigger pin had to be pulsed HIGH for at least 10µs before waiting for the echo to return the signal. So it sets to LOW, pulses HIGH then goes LOW. When the echo pin receives a HIGH return pulse, the time that elapses equals the duration. The distance uses the duration in the calculation as seen below. Now, because the sensors have been grouped and are ready to be recalled in the loop section, their behaviour can now be written here. If the first sensor encounters an obstacle that is closer than 20cm it turns LED1 on and LED2 off. If the obstacle is further than 20cm the reverse happens. Because the LED used is a bi-colour green and red LED, both times it is impacting the same one.
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
The other two sensors are programmed the same way. As this was the first attempt at a multiple sensor sketch it did take quite a lot of trial and error to get it working correctly. Using if else if was the way the sketch finally became usuable and worked in the corect manner. However, through perseverance, the idea became a reality and offered a template to start working from on other mulitple sensor sketches.

![Ultrasonic Second Prototype](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_034.jpeg)

**Multiple IR Sensors**



![IR Second Prototype](https://github.com/alexchilton1/7MU011-Reactive-Sound-Installation/blob/Edit/Pictures/File_036.jpeg)
