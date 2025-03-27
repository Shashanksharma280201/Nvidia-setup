# Nvidia-setup

# 1. Jetson Orin NX 8GB Developer Kit Setup

## 1.1 Flashing the Image
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
- Follow the official [Nvidia Guide](https://developer.nvidia.com/embedded/jetpack).
- Download the required Jetpack version (ensure compatibility).

## 1.2 Enabling All CPU Cores
By default, some CPU cores may be disabled in lower power modes. Follow these steps to enable all cores:

### **Check Active CPU Cores**
Run the following command to check how many cores are active:
```sh
lscpu
```
Or:
```sh
cat /proc/cpuinfo | grep "processor"
```

### **Enable All CPU Cores**
If only 4 cores are active, enable the remaining cores:
```sh
echo 1 | sudo tee /sys/devices/system/cpu/cpu4/online
echo 1 | sudo tee /sys/devices/system/cpu/cpu5/online
```

### **Set Jetson to Maximum Performance Mode**
If some cores are disabled due to power settings, switch to high-performance mode:
```sh
sudo nvpmodel -m 0
```
Then reboot the system:
```sh
sudo reboot
```

After rebooting, check again with `lscpu` to confirm all 6 cores are active.



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
