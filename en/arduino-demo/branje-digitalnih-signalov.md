# Reading digital signals

We will read the button state and store it in the microcontroller's memory. Reading a digital signal transfers information from a digital sensor to the controller through an input pin. We divide the task into electrical hardware and software.

## Electrical hardware

The hardware requires a circuit consisting of a button, a microcontroller and supporting components. See [Button and microcontroller](../elektrotehnika/tipka-in-mikrokrmilnik.md) for an example.

### Software

We will use functions from the Arduino library when writing the code.

* [pinMode()](https://www.arduino.cc/reference/en/language/functions/digital-io/pinmode/)
* [digitalRead()](https://www.arduino.cc/reference/en/language/functions/digital-io/digitalread/)

This example reads a digital input and stores its state in a global program variable.

```c
//Global constants
//Button on pin 0
int S0pin = 0;

//Global variables
//Button state variable
bool S0 = false;

//Setup function
void setup() {
  //Configure S0pin as a digital input
  pinMode(S0pin, INPUT);
}

//Main loop
void loop() {
  //Read the digital inputs
  S0 = digitalRead(S0pin);
}
```
