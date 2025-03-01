# Nvidia-setup

# Development Kit Setup and Configuration Guide

# 1. Jetson Orin NX 8GB Developer Kit Setup

### 1.1 Flashing the Image
- **Backup important files** (flashing erases all data).
- Power off the Jetson Orin NX.
- Connect a jumper cable between **ground (GND)** and **Force Recovery (REC) pins**.
- Connect the Jetson to the host PC via USB-C.
- Verify the connection using:
  ```sh
  lsusb
  ```
- Install required packages:
  ```sh
  sudo apt install qemu-user-static sshpass abootimg nfs-kernel-server libxml2-utils binutils -y
  ```
- Follow the official [Nvidia Guide](https://developer.nvidia.com/embedded/jetpack)
- Download the required Jetpack version (ensure compatibility).

# 2. Jetson Nano Setup

### 2.1 SD Card Preparation
- **Requirements:** SD card (minimum 32GB, recommended 128GB), SD card reader.
- **Download Image File:** [Jetson Nano Image](https://developer.nvidia.com/jetson-nano-sd-card-image)
- **Download Etcher Software:** [Etcher](https://www.balena.io/etcher/)

### 2.2 Installation Process
- Insert the SD card into the laptop's SD card slot or use an SD card reader.
- Open **Etcher** and select the downloaded image file.
- Select the SD card (auto-detected).
- Click **FLASH**.
- Insert the flashed SD card into the Jetson Nano.
- Connect a monitor, mouse, and keyboard for setup.

### 2.3 Ubuntu Upgrade
- Upgrade from Ubuntu 18.04 to 20.04 by following this [Ubuntu Upgrade Guide](https://ubuntu.com/tutorials/upgrading-ubuntu-desktop#1-overview).


Development Team

### **License:**
MIT License

