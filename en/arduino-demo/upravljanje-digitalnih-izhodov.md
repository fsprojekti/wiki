# Controlling digital outputs

We will use the microcontroller to switch an LED on and off at $$1s$$ intervals. Writing digital outputs transfers information from the controller to its output pins, which control an actuator: an LED in this example. We divide the task into electrical hardware and software.

## Electrical hardware

The hardware requires a circuit consisting of an LED, a microcontroller and supporting components. See [LED and microcontroller](../elektrotehnika/led-in-mikrokrmilnik.md) for an example.

## Software

We will use functions from the Arduino library when writing the code.

* [pinMode()](https://www.arduino.cc/reference/en/language/functions/digital-io/pinmode/)
* [digitalWrite()](https://www.arduino.cc/reference/en/language/functions/digital-io/digitalwrite/)

This example changes a digital output's state at one-second intervals.

```c
//Global constants
//Microcontroller pin 1
int K1pin = 1;

//Setup function
void setup() {
  //Configure K1pin as a digital output
  pinMode(K1pin, OUTPUT);
}

//Main loop
void loop() {
  //Write the outputs
  //Set K1pin high (5 V on the Arduino Nano)
  digitalWrite(K1pin, HIGH);
  //Pause program execution for 1 second
  delay(1000);
  //Set K1pin low (0 V)
  digitalWrite(K1pin, LOW);
  //Pause program execution for 1 second
  delay(1000);
}
```
