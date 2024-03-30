# Touch-Piano

Take out three fruits or vegetables like banana, apple,Potato, orange, tomato, chili anything
Not you must be wondering how these fruits and vegetables will make piano
The basic idea is based on touch sensing, where we touch fruits, and with the help of the ESP32 Touch pin, it will generate different frequency sounds corresponding to the various vegetables and fruits.

We need a buzzer to produce sound
Buzzer: A Buzzer works like a magnetic speaker, it needs voltage with a different frequency to be able to make a sound. It gets louder as the frequency increases and vice versa
● It makes a sound when the fruit is touched and stops it when it’s not.
● Basically, it will make a melody
The buzzer has two pins:
GND pin: connect this pin to GND (0V)
VCC pin: connect this pin to VCC (3.3V)

Step-1: Gather the material from the IoT kit
3 x Fruits, Vegetables
8 x Jumper wires
1 x ESP 32
1 x Buzzer

Step-2: Mount Components
Mount the ESP32 on the breadboard. Try to mount it from one end and to leave a few terminals open on one side.

Step-3: Mount the components on the breadboard
● Connect the positive part(VCC (+ve)) of the buzzer with ESP32 pin D26. Take the jumper wire and insert it into just below the buzzer VCC (+ve) part and drag it to pin D26 of the ESP32
● Connect the negative part (GND(-ve)) of the buzzer with ESP32(GND(-ve)) pin.

Step -4: Fruits & Connections
● Take three fruits/vegetables and insert male jumper wires one by one in each fruit/vegetable and other ends into ESP32 D13, D12, D14

Now, it's time to write a program
Open Arduino IDE
Step-1: Define and declare variables:
● Define buzzer and assign I/O pin D26
● Define variable along with datatype:
○ Int, const int is called data types, data type int is used to store an integer value
○ VALUE_THRESHOLD
○ TOUCH_SENSOR_VALUE_1, is used for Fruit/vegetable -1
○ TOUCH_SENSOR_VALUE_2, is used for Fruit/vegetable -2
○ TOUCH_SENSOR_VALUE_3, is used for Fruit/vegetable -3

Step-2: Initialization under setup() function
● void setup() is used to initialize
● Describe pinMode() for Buzzer Pin Mode() :PinMode() will declare Buzzer as digital OUTPUT
● Serial.begin() Serial.begin(9600) is used for data exchange data speed. This tells the Arduino to get ready to exchange messages with the Serial Monitor at a data rate of 9600 bits per second. That's 9600 binary ones or zeros per second and is commonly called a baud rate.
● Syntax for serial.begin : Serial.begin(speed)
● Set up delay()
● digitalWrite() will make the buzzer value LOW at the beginning.

Step-3: Execution of the main process:
void loop() function is used to execute the main process
The ESP32 chip comes with inbuilt touch sensors. These touch sensors are the capacitive type. These touch sensors are shared with I/O pins of ESP32. As mentioned earlier, capacitive sensors can detect electrical changes on respective GPIO pins. For example, if you touch any of these pins, the GPIO pin will produce an output based on the electrical charge on your finger. Because the body also carries some electrical charge. Therefore these touch sensors can detect electrical changes on GPIO pins.
● touchRead(touch_sensor_pin_number): This function is used to read the touch sensor value associated with the touch pin. We simply need to write the pin number we will be using. For example, if we are using touch pin zero, we would use this function like touchRead(T0)
● Store the touchRead() value of all fruit/Vegetable in respective variables.
● Serial.print() is used to print the data.
● Print the values of all touch sensors

Step-4:Conditions:
The active buzzer will only generate a sound when it is electrified.If TOUCH_SENSOR_VALUE_1 is less than VALUE_THRESHOLD then using digitalWrite() function changes the state of the Buzzer High or Low. 
Set delay of 100 ms between HIGH and LOW state of Buzzer
Our condition for one fruit/vegetable has been set, but we need to set conditions for other fruits and vegetables too.
If no conditions match with the if conditions else make the Buzzer Low
