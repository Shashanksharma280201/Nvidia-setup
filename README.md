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

# 3. Edge Device Connection Setup

### 3.1 Overview
- Before running any robot control programs, establish a secure SSH connection.

### 3.2 Connection Process

#### 3.2.1 Network Configuration
- Connect your development laptop to the same WiFi network as the edge device.
- Verify network connectivity.
- Ensure the edge device is powered on and connected to the network.

#### 3.2.2 Find Edge Device IP Address
- **Method 1 - Using hostname:**
  ```sh
  hostname -I
  ```
- **Method 2 - Using ifconfig:**
  ```sh
  ifconfig
  ```
  Look for the `wlan0` interface for WiFi connection.
  Example output:
  ```sh
  wlan0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST> mtu 1500
  inet 192.168.1.100 netmask 255.255.255.0 broadcast 192.168.1.255
  ```

#### 3.2.3 Establish SSH Connection
- From your development laptop, execute:
  ```sh
  ssh -X GMR@192.168.1.100  # For Orin NX
  ssh -X GMR@<device_ip_address>  # For Jetson Nano
  ```
- When prompted, enter the password:
  ```
  123456
  ```

#### 3.2.4 Verification
- After successful connection, the terminal prompt should indicate connection to the edge device.
- Test the connection by running:
  ```sh
  nvidia-smi
  ```
  This should display the GPU information.

---

### **Notes:**
- Ensure that Jetpack and CUDA versions are compatible with your hardware.
- Always verify device connections using `lsusb` and `ifconfig`.
- If SSH connection fails, check firewall settings and network configurations.
