# ArduinoI2cSerialCommunication
Sometimes, the folks in charge just don't know when to shut up! In some situations, it can be helpful to set up two (or more!) Arduino boards to share information with each other. In this example, two boards are programmed to communicate with one another in a Master Writer/Slave Receiver configuration via the I2C synchronous serial protocol. Several functions of Arduino's Wire Library are used to accomplish this. Arduino 1, the Master, is programmed to send 6 bytes of data every half second to a uniquely addressed Slave. Once that message is received, it can then be viewed in the Slave board's serial monitor window opened on the USB connected computer running the Arduino Software (IDE).

The I2C protocol involves using two lines to send and receive data: a serial clock pin (SCL) that the Arduino Master board pulses at a regular interval, and a serial data pin (SDA) over which data is sent between the two devices. As the clock line changes from low to high (known as the rising edge of the clock pulse), a single bit of information - that will form in sequence the address of a specific device and a a command or data - is transferred from the board to the I2C device over the SDA line. When this information is sent - bit after bit -, the called upon device executes the request and transmits it's data back - if required - to the board over the same line using the clock signal still generated by the Master on SCL as timing. The initial eight bits (i.e. eight clock pulses) from the Master to Slaves contain the address of the device the Master wants data from. The bits after contain the memory address on the Slave that the Master wants to read data from or write data to, and the data to be written, if any.

Each Slave device has to have its own unique address and both master and slave devices need to take turns communicating over a the same data line line. In this way, it's possible for your Arduino boards to communicate with many device or other boards using just two pins of your microcontroller, using each device's unique address.

Hardware Required:
2	Arduino Uno R3
1	Pushbutton
2	220 Ω Resistor
1	Blue LED

Circuit:

Connect pin A5 (the clock, or SCL, pin) and pin A4 (the data, or SDA, pin) on the master Arduino to their counterparts on the slave board. Make sure that both boards share a common ground. In order to enable serial communication, the slave Arduino must be connected to your computer via USB.

If powering the boards independently is an issue, you can power the Slave from the Master board. With a 5 V slave, this would be done by connecting the 5V output of the Master to the 5V pin on the slave.
![led on](https://github.com/HazimAliAlFaqih/ArduinoI2cSerialCommunication/assets/138938425/c81559b4-5947-496b-8095-31a37c9ce872)
Schematic
![schematic](https://github.com/HazimAliAlFaqih/ArduinoI2cSerialCommunication/assets/138938425/86a71915-b79a-4ef9-91a1-26412014288d)
