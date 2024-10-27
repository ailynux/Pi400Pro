# Cyberdeck Hat for Raspberry Pi

![image](https://github.com/user-attachments/assets/9f75f074-8960-40a9-b7cc-d157b4ab280a)


## Table of Contents

1. [Introduction](#introduction)
2. [Features](#features)
3. [Hardware Required](#hardware-required)
4. [Software Setup](#software-setup)
5. [Assembly Instructions](#assembly-instructions)
6. [Usage](#usage)
7. [Troubleshooting](#troubleshooting)
8. [Contributing](#contributing)
9. [License](#license)

## Introduction

The **Cyberdeck Hat** is an add-on board designed to work with Raspberry Pi devices, bringing compact connectivity and functionality to your portable builds. Whether you're building a mobile workstation or a retro-inspired cyberdeck, this hat adds the ports and customization needed to bring your project to life.

## Features

- **Compact Design**: Fits snugly on top of Raspberry Pi.
- **Multiple Ports**: Includes USB, HDMI, and GPIO breakout.
- **OLED Display**: Mini display for system stats or custom outputs.
- **Built-in Power Management**: Efficient power control for your setup.

## Hardware Required

| Component               | Quantity |
|-------------------------|----------|
| Cyberdeck Hat            | 1        |
| Raspberry Pi 4           | 1        |
| OLED Display             | 1        |
| USB-C Power Supply       | 1        |
| Micro SD Card (32GB+)    | 1        |
| STEMMA QT / Qwiic JST SH 4-pin to Premium Male Headers Cable - 150mm Long    | 1        |
| JST PH 2mm 3-pin Plug-Plug Cable - 100mm long    | 1        |
| STEMMA JST PH 2mm 3-Pin to Male Header Cable - 200mm    | 1        |
| Pimoroni HyperPixel - 4.0" Hi-Res Display for Raspberry Pi   | 1        |


## Software Setup

### 1. Download Raspberry Pi OS

- To get started, download the latest version of Raspberry Pi OS from the [official Raspberry Pi website](https://www.raspberrypi.org/software/operating-systems/). Use the **Raspberry Pi Imager** to write the OS to your SD card.

### 2. Install Dependencies

- Once you have Raspberry Pi OS installed, follow these steps to install the necessary dependencies.

### *Update your system*
- Run the following commands to update your Raspberry Pi OS:
```bash
sudo apt-get update
sudo apt-get -y upgrade
```
- Install I2C tools and Python SMBus
- Install the required packages for interacting with I2C devices:
```bash
sudo apt-get install -y i2c-tools python3-smbus
```
- These packages will allow you to use I2C and interact with connected devices through Python 12.

### 3. Enable the I2C Interface
- To enable I2C on your Raspberry Pi:
- Open the Raspberry Pi configuration tool:
```bash
sudo raspi-config
```
- Navigate to Interfacing Options.
- Select I2C and enable it.
- Reboot your Raspberry Pi:
```bash
sudo reboot
```

### 4. Verify I2C Setup
- After rebooting, you can check that your I2C connections are working correctly by running the following command to scan the I2C bus:
```bash
sudo i2cdetect -y 1
```

## Assembly Instructions
- Mount the Cyberdeck Hat
- Carefully align the GPIO pins of the Raspberry Pi with the Cyberdeck Hat and press down gently until secure.
- Connect the OLED Display
- Attach the OLED display to the I2C pins on the Cyberdeck Hat.
- Power Up
- Connect the USB-C power supply to the Raspberry Pi and power it up.

## Usage

**After setting up the Cyberdeck Hat on your Raspberry Pi, you can begin interacting with the connected I2C devices and using the OLED display for system stats.**

### 1. Display System Stats on the OLED Screen
To display your system stats (such as CPU temperature, RAM usage, etc.) on the attached OLED display, use the following script:
```bash
python3 display_stats.py
```
- Make sure that the Python script display_stats.py is configured to read system information and output it to the OLED. You can modify the script to show other useful information, like network status or custom messages.

### 2. I2C Device Interaction
Once you have I2C tools installed, you can scan for connected I2C devices and interact with them. To list the addresses of all connected I2C devices, use:

```bash
sudo i2cdetect -y 1
```
- This command scans the I2C bus and lists the devices detected on the bus. You can use the i2cget and i2cset commands to read from and write to the registers of those devices.
For example, to read a byte from an I2C device at address 0x60, run:
```bash
sudo i2cget -y 1 0x60
```
- You can modify this depending on the device's address and the register you're interacting with.

### 3. 📜 Script.py 🚀

🖥️ Don't worry about the code just yet — I've got **big plans** for these screens! I'm working on several scripts that will bring the display to life. Whether you're tracking system stats, showing cool animations, or running custom visualizations, it's all coming soon! 🎉

You'll be able to:

- 🖥️ Monitor CPU performance
- 🌡️ Track temperature and system health
- 📶 Check network status
- 🔧 Create custom alerts or messages

Stay tuned for **tons of features** as I keep building and improving this project! 😎

```bash
# Example placeholder
python3 display_stats.py
```
















