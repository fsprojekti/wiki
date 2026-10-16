# Controllino MINI

Controllino MINI from [Controllino](https://www.controllino.com/) adapts the Arduino platform into a compact PLC system for automation applications.

Resources:

* [User manual](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOjZ1XG64rvc2AeRBUH5H%2Fuploads%2FJbzJmQr460GY2c4w9Sxh%2FminiManual.pdf?alt=media\&token=3511fd91-3ec2-48f6-8e2a-197b98b8a069)
* [Signal wiring and pinout](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOjZ1XG64rvc2AeRBUH5H%2Fuploads%2F2AWveZKx8HxqJlxtXKGR%2FminiPinout.pdf?alt=media\&token=8fd727af-bfdc-4873-bf23-45ab0a9fd637)
* [Datasheet](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOjZ1XG64rvc2AeRBUH5H%2Fuploads%2F1UuDSsDUpCvJkR7ZWQCb%2FminiDatasheet.pdf?alt=media\&token=3713ae3f-3bd8-40f1-8f5a-2e6e553e2f3b)

## Controller description

The figure shows the CONTROLLINO MINI with its components labeled. It is based on an ATmega328 microcontroller. It has eight inputs without galvanic isolation: four combined analog/digital inputs, two digital-only inputs and two analog-only inputs. It also has eight digital outputs without galvanic isolation and six relay outputs in parallel with digital outputs. Its compact, flexible design supports small automation and control projects.

<figure><img src="../../.gitbook/assets/image (22).png" alt="Controllino MINI" width="375"><figcaption><p>Controllino MINI</p></figcaption></figure>

## Electrical wiring

Connect the controller to its power supply, digital inputs and digital outputs.

### PLC power supply

The PLC requires a power supply; this example uses 24 V DC. The supply terminals are shown below.

<figure><img src="../../.gitbook/assets/image (24).png" alt="Connecting the power supply" width="375"><figcaption><p>Connecting the power supply</p></figcaption></figure>

The **12V/24V** label indicates the positive supply terminal, and **GND** indicates supply ground.

### Digital inputs

Digital inputs monitor devices such as limit switches, pressure switches and other digital sensors. The figure shows an example switch connection.

<figure><img src="../../.gitbook/assets/image (25).png" alt="Connecting a digital signal to PLC input A2" width="337"><figcaption><p>Connecting a digital signal to PLC input A2</p></figcaption></figure>

### Digital outputs

Digital outputs operate devices such as lamps, relays, motors and pumps. The figure shows a load connected to a digital relay output.

<figure><img src="../../.gitbook/assets/image (26).png" alt="Connecting a load to relay output D0" width="234"><figcaption><p>Connecting a load to relay output D0</p></figcaption></figure>

The relay output switches the load through its contact. Connect the positive supply (24 V) to one contact terminal and the load to the other. Connect the load's other terminal to the negative supply (0 V).

### User interface

Built-in LEDs indicate the states of the input and output devices.

<figure><img src="../../.gitbook/assets/image (27).png" alt="LEDs indicating input and output states"><figcaption><p>LEDs indicating input and output states</p></figcaption></figure>

The interface allows input and output states to be monitored but does not directly control them.

## Programming software

Controllino MINI can be programmed in several environments. Arduino IDE supports programming in C.

### Arduino environment setup

* [Environment setup instructions](https://github.com/CONTROLLINO-PLC/CONTROLLINO_Library#installation-guide)

### Communication interface setup

### Uploading the program to the controller

### Program monitoring

### Common issues

1. Upload error

{% code lineNumbers="true" %}
```c
avrdude: stk500_recv(): programmer is not responding
```
{% endcode %}

To resolve this issue:

* Press and hold the reset button on the Controllino.
* Connect the USB cable while holding reset, so the existing program does not start.
* Start uploading the sketch in Arduino IDE. Keep holding reset during compilation. When the status changes to "uploading", release reset immediately so the upload can complete.
* If the upload fails, repeat the procedure.

