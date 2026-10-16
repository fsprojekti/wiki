# LILYGO - ESP32

## Description

<figure><img src="../../.gitbook/assets/image (8).png" alt="LILYGO development board" width="375"><figcaption><p>LILYGO development board</p></figcaption></figure>

The TTGO development board combines an ESP32 microcontroller with a TFT display for developing Internet of Things (IoT) projects. Its main features are:

1. **ESP32 microcontroller:** The ESP32 supports Wi-Fi and Bluetooth. It combines processing capability with low power consumption for applications such as smart homes, automation and monitoring systems.
2. **TFT display:** The color TFT display can show graphics, text and user interfaces. It is suitable for applications requiring visual output, such as clocks, weather stations and interactive monitoring systems.
3. **GPIO inputs and outputs:** The board provides GPIO (General Purpose Input/Output) connections for sensors, actuators and other modules.
4. **Programming and development environments:** The TTGO board can be programmed using Arduino IDE, Espressif IDF or MicroPython, supporting both beginners and experienced developers.
5. **Power supply and battery:** The board supports different power sources, including a battery, allowing portable or remote applications.

This development board is suitable for hobby projects, education, prototyping and small to medium-sized IoT projects.

## Arduino development environment

Set up the development environment for the TTGO board as follows:

### 1. Installing board support

Add the external board-package URL in Arduino IDE because the default installation does not include support for this board.

<figure><img src="../../.gitbook/assets/image (10).png" alt="Opening Arduino IDE preferences" width="312"><figcaption><p>Opening Arduino IDE preferences</p></figcaption></figure>

Open Arduino IDE preferences and add the board-package URL under **Additional Boards Manager URLs**.

```
https://espressif.github.io/arduino-esp32/package_esp32_index.json
```

<figure><img src="../../.gitbook/assets/image (9).png" alt="Adding the external ESP32 board-package URL"><figcaption><p>Adding the external ESP32 board-package URL</p></figcaption></figure>

After adding the URL, install the board package named _esp32 by Espressif Systems_.

<figure><img src="../../.gitbook/assets/image (7).png" alt="Selecting the esp32 board package" width="563"><figcaption><p>Selecting the esp32 board package</p></figcaption></figure>

After installation, select your development board. This walkthrough uses TTGO LoRa32-OLED.

<figure><img src="../../.gitbook/assets/image (11).png" alt="Selecting the development board" width="563"><figcaption><p>Selecting the development board</p></figcaption></figure>

### 2. Installing TFT display support

The TFT display communicates with the LILYGO board over SPI. A display library handles communication and makes the display easier to use.

<figure><img src="../../.gitbook/assets/image (12).png" alt="Display library" width="423"><figcaption><p>Display library</p></figcaption></figure>

After installing the display library, select the correct configuration. The library supports different display sizes and controller interfaces, so an installed configuration file must be edited.

<figure><img src="../../.gitbook/assets/image (13).png" alt="Opening the TFT display configuration file"><figcaption><p>Opening the TFT display configuration file</p></figcaption></figure>

Find _User\_Setup\_Select.h_ in the installed Arduino libraries.

First, disable line 32 by commenting it out.

<figure><img src="../../.gitbook/assets/image (14).png" alt="Line 32"><figcaption><p>Line 32</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (15).png" alt="Disable line 32 by commenting it out"><figcaption><p>Disable line 32 by commenting it out</p></figcaption></figure>

Enable line 58 by uncommenting it.

<figure><img src="../../.gitbook/assets/image (16).png" alt="Selecting the correct TFT display and board configuration"><figcaption><p>Selecting the correct TFT display and board configuration</p></figcaption></figure>

### 3. Installing the demo program

Select one of the example programs in Arduino IDE.

<figure><img src="../../.gitbook/assets/image (17).png" alt="Selecting the digital clock example"><figcaption><p>Selecting the digital clock example</p></figcaption></figure>

Connect the board and select the correct upload port.

<figure><img src="../../.gitbook/assets/image (18).png" alt="Selecting the development board and port"><figcaption><p>Selecting the development board and port</p></figcaption></figure>

After uploading, the display shows the current time.

<figure><img src="../../.gitbook/assets/image (21).png" alt="Display after uploading the demo program"><figcaption><p>Display after uploading the demo program</p></figcaption></figure>

