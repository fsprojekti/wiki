# FlexDrive

<figure><img src="../../.gitbook/assets/image (5).png" alt="FlexDrive laboratory rig"><figcaption><p>FlexDrive laboratory rig</p></figcaption></figure>

## 1. Rig description

FlexDrive is a laboratory rig for studying the mechanics of elastically coupled drive systems. Its mechanical assembly consists of two shafts connected by an elastic coupling. A flywheel is rigidly mounted on the load shaft, while an electric motor drives the drive shaft and the entire assembly. The block diagram shows the components and their connecting signals.

<figure><img src="../../.gitbook/assets/image (4).png" alt="Block diagram of the rig"><figcaption><p>Block diagram of the rig</p></figcaption></figure>

Rig components:

* mechanical assembly
* angular encoder on the drive shaft
* angular encoder on the load shaft
* DC motor
* motor driver
* microcontroller
* computer

Rig signals:

* $$U_{DC}$$: continuous voltage signal driving the DC motor
* $$M(t)$$: torque supplied by the motor to the drive shaft
* $$\phi_1(t)$$: load shaft rotation
* $$\phi_2(t)$$: drive shaft rotation
* $$AB(t)$$: quadrature encoder signal
* $$U_{an}$$: analog encoder signal (load shaft only)
* $$PWM(t)$$: digital control signal to the motor driver

### 1.1 Mechanical assembly

The mechanical assembly is a rotating dynamic system, shown schematically below.

<figure><img src="../../.gitbook/assets/image (6).png" alt="Diagram of the rig's mechanical assembly"><figcaption><p>Diagram of the rig's mechanical assembly</p></figcaption></figure>

The load shaft has moment of inertia $$J_2$$ and carries a rigidly attached flywheel with inertia $$J_1$$. Two bearings support the shaft, with combined damping $$B_1$$. Its motion is described by angle $$\phi_2(t)$$. A spring coupling with stiffness $$k$$ connects it to the drive shaft, whose inertia is $$J_3$$. The drive shaft is rigidly connected to a motor with damping $$B_2$$. Its motion is described by angle $$\phi_1(t)$$, and the electric motor supplies torque $$M(t)$$.

* System variables

| Symbol | Description | Unit |
| -------------------------------------------- | ---------------------------------- | ------ |
| <p><span class="math">M(t)</span></p><p></p> | Torque produced by the electric motor | $$Nm$$ |
| $$\phi_1$$ | Drive shaft rotation angle | &deg; |
| $$\phi_2$$ | Load shaft rotation angle | &deg; |

* System parameters

| Symbol | Description | Value | Unit |
| ------- | ----------------------------- | -------- | -------------- |
| $$B_1$$ | Load shaft damping | | $$kg/s$$ |
| $$B_2$$ | Drive shaft damping | | $$kg/s$$ |
| $$J_1$$ | Flywheel moment of inertia | 0.612 | $$g \cdot m^2$$ |
| $$J_2$$ | Load shaft moment of inertia | 0.0902 | $$g \cdot m^2$$ |
| $$J_3$$ | Drive shaft moment of inertia | \~0 | $$g \cdot m^2$$ |
| $$k$$ | Spring stiffness | | $$N/m$$ |

### 1.2 Drive shaft angular encoder

The drive shaft has a magnetic incremental [RLS AM4096](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOjZ1XG64rvc2AeRBUH5H%2Fuploads%2FyzCheUulIy3s2L2ZKiW7%2FAM4096D02_09.pdf?alt=media\&token=98176deb-bbd0-47c8-8e04-4e16f1c4bee7) encoder from the Slovenian company [RLS d.o.o.](https://www.rls.si/). It is mounted on an [RMK-AM4096](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOjZ1XG64rvc2AeRBUH5H%2Fuploads%2FbyXYN1jzgBNJ6AE5CL2T%2FRMK4D01_02.pdf?alt=media\&token=79a8c043-1cb3-4de8-b4c9-b0015d1d1cb4) development board. The encoder measures relative shaft motion and sends a digital signal to the microcontroller.

### 1.3 Load shaft angular encoder

The load shaft has an optical incremental encoder from [POLOLU](https://www.pololu.com/). See the [POLOLU-4883 datasheet](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOjZ1XG64rvc2AeRBUH5H%2Fuploads%2FFI9ruRMcNiLlxmRKPVba%2Fpololu-25d-metal-gearmotors.pdf?alt=media\&token=f1a4c430-3dc9-469c-b787-b65e03a61922).

{% hint style="info" %}
A 20.4:1 gear train connects the encoder to the load shaft. Account for this ratio when calculating the rotation angle!
{% endhint %}

### 1.4 Electric motor drive

An electric motor drives the shaft. The rig uses a [POLOLU-4883](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOjZ1XG64rvc2AeRBUH5H%2Fuploads%2FFI9ruRMcNiLlxmRKPVba%2Fpololu-25d-metal-gearmotors.pdf?alt=media\&token=f1a4c430-3dc9-469c-b787-b65e03a61922) motor from [POLOLU](https://www.pololu.com/) with a 20.4:1 gear ratio.

### 1.5 Motor driver

An [MD10C R3](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOjZ1XG64rvc2AeRBUH5H%2Fuploads%2FsN0uYqGXUT1pKGO2iOuc%2FA1TemgvjKjL.pdf?alt=media\&token=e0621c34-4375-4835-b94b-6c76b18cf1ee) motor driver from [Cytron](https://www.cytron.io/) drives the DC motor. Two digital signals control it: $$power$$ is a PWM (Pulse Width Modulation) signal, and $$direction$$ sets the output current direction and therefore the motor's direction of rotation.

## 2. Electrical hardware

The circuit connects the Arduino microcontroller to two incremental encoders and a DC motor driver. The serial connection between the microcontroller and single-board computer is not shown. The table lists the digital connections to the Arduino.

| Device | Pin | Arduino pin | Signal label | Input/Output |
| ---------------- | --- | ----------- | --------------- | ---------- |
| Magnetic encoder | A | 32 | A1 | Input |
| Magnetic encoder | B | 33 | B1 | Input |
| Optical encoder | A | 36 | A2 | |
| Optical encoder | B | 37 | B2 | |
| Motor driver | DIR | 25 | DIR | Output |
| Motor driver | PWM | 26 | PWM | Output |

### 2.1 Electrical components

List of electrical components used:

<table><thead><tr><th>Component</th><th width="174">Part number</th><th>Manufacturer</th><th>Datasheet</th></tr></thead><tbody><tr><td>Magnetic encoder</td><td>RLS AM4096</td><td><a href="https://www.rls.si/">RLS d.o.o.</a></td><td><a href="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOjZ1XG64rvc2AeRBUH5H%2Fuploads%2FbyXYN1jzgBNJ6AE5CL2T%2FRMK4D01_02.pdf?alt=media&#x26;token=79a8c043-1cb3-4de8-b4c9-b0015d1d1cb4">file</a></td></tr><tr><td>Optical encoder</td><td>POLOLU</td><td><a href="https://www.pololu.com/">POLOLU</a></td><td><a href="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOjZ1XG64rvc2AeRBUH5H%2Fuploads%2FFI9ruRMcNiLlxmRKPVba%2Fpololu-25d-metal-gearmotors.pdf?alt=media&#x26;token=f1a4c430-3dc9-469c-b787-b65e03a61922">file</a></td></tr><tr><td>Motor driver</td><td>MD10C R3</td><td><a href="https://www.cytron.io/">Cytron</a></td><td><a href="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOjZ1XG64rvc2AeRBUH5H%2Fuploads%2FsN0uYqGXUT1pKGO2iOuc%2FA1TemgvjKjL.pdf?alt=media&#x26;token=e0621c34-4375-4835-b94b-6c76b18cf1ee">file</a></td></tr><tr><td>Microcontroller</td><td>ESP32 - LILYGO</td><td><a href="https://www.espressif.com/en/products/modules/esp32">Espressif</a></td><td><a href="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FOjZ1XG64rvc2AeRBUH5H%2Fuploads%2Fzm4t7rH9GXGytU5nTjB7%2FESP-32%20Dev%20Kit%20C%20V2_EN.pdf?alt=media&#x26;token=bf2beae7-b3bd-435d-b155-cd2a164210b9">file</a></td></tr></tbody></table>



## 3. Software: CLI

***

This section explains how to communicate directly with the rig over a serial connection. It covers the CLI commands, their functions, examples and measurement visualization in Arduino Serial Plotter.

### **3.1 Command structure (CLI)**

FlexDrive provides a simple text-based command-line interface (CLI) for communication with the ESP32 controller through Arduino Serial Monitor or another terminal, such as PuTTY, CoolTerm or RealTerm.

Enter commands as plain text lines, for example:

```
mode 1
ref 0.5
kp 5
run
```

Each command has the following basic form:

```
<command> <parameter>
```

Some commands have no parameters and are used on their own:

```
run
stop
list
```

### **3.2 Open-loop control**

In open-loop mode, the system does not use speed feedback. You control the motor directly by setting its PWM value and direction. This mode is useful for testing, diagnostics and learning the system's basic operation.

Common open-loop commands are:

```
mode 0
pwm 1200
dir 1
run
```

Command meanings:

* **mode 0**\
  Select open-loop operation without feedback control.
* **pwm**\
  Set PWM between 0 and `pwm_max` (4000 by default).\
  This command controls the motor drive level.
* **dir <0|1>**\
  Set the direction of rotation:
  * 0 = forward
  * 1 = reverse
* **run**\
  Start the motor using the latest PWM and direction settings.

Quick motor test example:

```
mode 0
pwm 800
run
```

Changing direction during operation:

```
dir 1
pwm 1000
```

To stop the system:

```
stop
```

### **3.3 Closed-loop control (PID)**

In closed-loop mode, FlexDrive uses encoder feedback to control motor speed.\
The system automatically adjusts PWM to reach the requested reference speed.

Closed-loop mode provides:

* stable speed,
* load compensation,
* repeatability,
* an introduction to PID control.

To enable closed-loop mode, use:

```
mode 1
```

Main speed-control commands:

* **ref**\
  Set the reference speed in _rev/s_ (revolutions per second).\
  For example, `ref 0.6` requests 0.6 revolutions per second.
* **kp**\
  Set the proportional gain (-1000 to +1000).\
  A higher Kp gives a faster response but may cause oscillation.
* **ki**\
  Set the integral gain (0 to 100).\
  It reduces steady-state error but can cause integral windup.
* **kd**\
  Set the derivative gain (0 to 100).\
  It damps rapid changes and reduces oscillation.

After setting the PID parameters, start closed-loop control with:

```
run
```

Complete PID configuration example:

```
mode 1
ref 0.5
kp 8
ki 0.2
kd 0.05
run
```

Changing the reference speed during operation:

```
ref 1.2
```

Adjusting PID parameters in real time:

```
kp 12
ki 0.3
kd 0.1
```

Stopping closed-loop operation:

```
stop
```

Tip: If the motor vibrates, accelerates abruptly or changes speed erratically, reduce Kp or increase Kd.

### **3.4 Reading position and speed**

FlexDrive provides serial monitoring and settings that affect measurement stability, controller response and the data display rate.

This group includes commands for:

* speed filtering (alpha),
* control-loop sample time (ts),
* the legacy raw plot,
* Arduino Serial Plotter output,
* plot interval settings (plot\_period).

***

**SPEED FILTERING (LOW-PASS FILTER)**

Parameter **alpha** sets the smoothing applied to the measured encoder speed.

A larger alpha, such as 0.4, gives a faster response with less smoothing.\
A smaller alpha, such as 0.05, gives a slower response and smoother speed measurements.

Setting:

```
alpha 0.1
```

Valid values: 0.00 to 1.00

***

**SETTING THE SAMPLE TIME (ts)**

Command **ts** sets the time between control cycles in milliseconds.

A smaller ts gives faster sampling and control updates.\
A larger ts gives slower control updates and reduces processor load.

Example:

```
ts 10
```

***

**RAW PLOT (COMPATIBLE WITH SIMPLE TERMINALS)**

This legacy data-output mode makes the ESP32 periodically print:

* encoder positions
* speeds

Enable:

```
plot 1
```

Disable:

```
plot 0
```

***

**SERIAL PLOTTER: OPEN LOOP**

For Arduino Serial Plotter, the output can include:

* pwm
* actual speed

Enable:

```
plotSerialOpen
```

Open-loop plotting example:

```
mode 0
pwm 1200
run
plotSerialOpen
```

***

**SERIAL PLOTTER: CLOSED LOOP**

In closed-loop mode, Serial Plotter displays three signals:

* pwm
* reference speed
* actual speed

Enable:

```
plotSerialClosed
```

Example:

```
mode 1
ref 0.8
kp 10
run
plotSerialClosed
```

***

**SETTING THE PLOT INTERVAL (plot\_period)**

This parameter outputs data only once every _plot\_period_ control cycles.

Example:\
ts = 10 ms\
plot\_period = 5\
Plot output is therefore produced every 50 ms.

Setting:

```
plot_period 5
```

Minimum value:

```
plot_period 1
```

***

**QUICK TEST CONFIGURATION**

```
alpha 0.15
ts 10
plot_period 3
plotSerialClosed
```

### **3.5 Advanced commands: diagnostics, limits and system information**

These commands display the system state, configure operating limits and retrieve system information. They are useful for diagnostics, learning and configuring FlexDrive.

***

**DISPLAYING THE CURRENT SYSTEM STATE (list)**

Command **list** shows the complete device state:

* operating mode (open or closed loop)
* state (run or stop)
* PWM value and direction
* PID parameters
* reference speed
* filtering (alpha)
* sample time (ts)
* plot mode
* encoder speeds and positions

Example:

```
list
```

This is the main diagnostic command.

***

**FIRMWARE INFORMATION (version)**

This command prints the installed firmware version:

```
version
```

***

**LIMITING THE MAXIMUM PWM VALUE (pwm\_max)**

This sets the maximum PWM value the ESC can reach, helping limit excessive motor and power-supply current.

Example:

```
pwm_max 3000
```

The minimum permitted setting is 100.

***

**SETTING THE ROTATION DIRECTION (dir)**

Set the motor's rotation direction:

* 0 = forward
* 1 = reverse

Example:

```
dir 0
```

***

**MANUAL CONTROL (pwm + dir): DIAGNOSTIC MODE**

In open-loop mode, the motor can be controlled manually:

```
mode 0
dir 1
pwm 1500
run
```

***

**INITIAL SYSTEM SETUP (init)**

Initialize the internal variables, which is useful for starting a fresh test:

```
init
```

***

**STOPPING AND STARTING THE SYSTEM (stop / run)**

Stop the motor:

```
stop
```

Restart using the existing settings:

```
run
```

***

**DIAGNOSTIC COMMAND SUMMARY**

```
list        # display state
version     # firmware version
pwm_max 4000 # PWM limit
dir 0       # direction
init        # reset internal values
stop        # stop the motor
run         # start the motor
```

### 3.6 CLI command reference

The table summarizes all FlexDrive commands, their parameters, allowed values and functions.

| Command | Parameter | Value range | Description |
| ---------------- | ------------- | --------------------- | --------------------------------------------- |
| mode | 0 / 1 | 0 = open, 1 = closed | Select operating mode |
| run | - | - | Start the motor or controller |
| stop | - | - | Stop the motor |
| ref | value | -10.0 to 10.0 (rev/s) | Set reference speed |
| pwm | value | 0 to pwm\_max | Set PWM manually in open-loop mode |
| pwm\_max | value | >= 100 | Limit maximum PWM |
| dir | 0 / 1 | 0 = forward, 1 = reverse | Set motor rotation direction |
| kp | value | -1000 to 1000 | PID proportional gain |
| ki | value | 0 to 100 | PID integral gain |
| kd | value | 0 to 100 | PID derivative gain |
| alpha | value | 0.0 to 1.0 | Speed low-pass filter |
| ts | value (ms) | >= 1 | Control-loop sample time |
| plot | 0 / 1 | 0 = off, 1 = on | Legacy raw data output |
| plotSerialOpen | - | - | Plot PWM and speed in open-loop mode |
| plotSerialClosed | - | - | Plot PWM, reference and speed in closed-loop mode |
| plot\_period | value | >= 1 | Output data every _n_ cycles |
| list | - | - | Display the complete current system state |
| version | - | - | Display firmware version |
| init | - | - | Reset internal system values |

***

#### 2. MATLAB connection

This section describes how MATLAB communicates with FlexDrive, reads data, sends commands and records measurements for laboratory exercises.

**2.1. Establishing serial communication in MATLAB**

**2.2. Sending commands from MATLAB**

**2.3. Reading data in real time**

**2.4. Recording time responses: steps, sine waves and noise**

**2.5. Processing data and plotting graphs**

**2.6. MATLAB script examples for laboratory exercises**

**2.7. Analyzing and exporting data for PID tuning**
