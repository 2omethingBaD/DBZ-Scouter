# DBZ Scouter User Guide

This project is a working **screen module for a Dragon Ball scouter cosplay**, featuring animated scanning graphics, button controls, and rechargeable battery power.

![DBZ Scouter banner](https://github.com/2omethingBaD/DBZ-Scouter/blob/main/img/20260715_165016.jpg?raw=true)

---

## 📋 Table of Contents

- [Assembly](#-assembly)
- [Using the Scouter](#-using-the-scouter)
- [Charging](#-charging)
- [Tech Notes](#-tech-notes)

---

## 🧰 Assembly

<details>
<summary><strong>Connecting the Battery</strong></summary>

The scouter is powered by the included **3.7V rechargeable lithium polymer battery**.

1. Locate the white **JST battery connector** on the PCB.
2. Check the small **`+` polarity marking** beside the connector.
3. Line up the battery plug so that the **red wire matches the `+` marking**.
4. Carefully push the connector into place until it is fully seated.

> [!WARNING]
> Check the wire orientation before connecting the battery. Reversing the battery polarity may damage the PCB, microcontroller, display, or battery.

Do not force the connector into place. If it does not fit easily, remove it and check its orientation.

![DBZ Scouter JST plugged in](https://github.com/2omethingBaD/DBZ-Scouter/blob/main/img/20260715_164435.jpg?raw=true)

![DBZ Scouter JST plug](https://github.com/2omethingBaD/DBZ-Scouter/blob/main/img/20260715_165133.jpg?raw=true)

</details>

---

## 🎮 Using the Scouter

<details>
<summary><strong>Animations and Button Controls</strong></summary>

### Starting the Scouter

After the scouter is turned on:

1. The **SomethingBAD Studios splash screen** appears.
2. The scouter plays its first **scanning animation**.
3. It switches to the second animation.
4. After approximately **30 seconds**, the screen and backlight turn off and the module enters its standby state.

### Restarting the Animation

Press and hold the input button for at least **2 seconds** and release to restart the animation sequence from the scanning screen.

The animation can be restarted:

- while the scanning animation is playing
- while the second animation is playing
- while the screen is in standby

### Button-Cap Extender

An optional **button-cap extender** is included. It can be fitted over the input button if the button is difficult to reach after installing the module inside the scouter housing.

![DBZ Scouter input button](https://github.com/2omethingBaD/DBZ-Scouter/blob/main/img/20260715_165102.jpg?raw=true)

![DBZ Scouter button-cap extender](https://github.com/2omethingBaD/DBZ-Scouter/blob/main/img/20260715_165237.jpg?raw=true)

</details>

---

## 🔋 Charging

<details>
<summary><strong>Charging the Included Battery</strong></summary>

The included lithium polymer battery can be charged through the **USB-C port on the XIAO ESP32C6** while the battery remains connected to the PCB.

1. Make sure the battery is correctly connected to the PCB.
2. Connect a USB-C cable to the USB-C port on the microcontroller.
3. Connect the other end of the cable to a standard USB power source.
4. Watch the red charging LED on the microcontroller.

The red LED indicates the current charging state:

- **Flashing red:** The battery is charging.
- **Red LED off:** The battery is fully charged.

Disconnect the USB-C cable once charging is complete.

> [!CAUTION]
> Do not charge or use the battery if it is punctured, swollen, leaking, or otherwise damaged.

![DBZ Scouter charging](https://github.com/2omethingBaD/DBZ-Scouter/blob/main/img/20260715_165617.jpg?raw=true)

</details>

---

## 🧠 Tech Notes

<details>
<summary><strong>Hardware and Firmware Information</strong></summary>

### Main Hardware

The screen module uses:

- **Seeed Studio XIAO ESP32C6** microcontroller
- **Waveshare 2.4-inch SPI LCD**
- **ILI9341 display controller**
- **320 × 240 pixel display resolution**
- **3.7V rechargeable lithium polymer battery**
- momentary input button
- custom PCB

### Firmware

The firmware is written in **Arduino C++** and uses:

- **Adafruit GFX Library**
- **Adafruit ILI9341 Library**
- **AnimatedGIF Library**
- the ESP32 SPI interface

The GIF animations are stored directly inside the firmware as byte arrays, allowing the module to play them without an SD card.

### Animation Timing

The current firmware uses the following timing:

- **Splash screen:** approximately 2 seconds
- **Scanning animation:** approximately 5 seconds
- **Total active sequence:** approximately 30 seconds
- **Button hold required to restart:** 2 seconds

### Standby Behavior

The current standby mode is a **display-only standby state**.

When standby begins, the firmware:

- fills the display with black
- switches off the display backlight
- waits for the input button to be held
- restarts the animation sequence after a valid 2-second hold

This mode does **not** currently place the ESP32C6 into light sleep or deep sleep. The microcontroller continues running while it waits for the button input.

### Source Code

The complete Arduino firmware can be found here:

[View ScouterCode.ino](https://github.com/2omethingBaD/DBZ-Scouter/blob/main/ScouterCode.ino)

### Additional Documentation

More information about the microcontroller and its battery-charging system is available in the official documentation:

[Seeed Studio XIAO ESP32C6 Getting Started Guide](https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/)

</details>

---

💡 *Created by [SomethingBAD Studios](https://github.com/2omethingBaD) — “BAD ideas, genius built.”*
