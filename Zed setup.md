## 3. ZED SDK Installation Guide  

### 3.1 Prerequisites  
Before installing the ZED SDK, make sure you have:  
- **JetPack 5.1.1** installed.  
- **CUDA** installed and properly set up.  

### 3.2 Installation Steps (General)  
1. **Download the SDK** from [Stereolabs Developers](https://www.stereolabs.com/developers/).  
2. **Choose the version** that matches your JetPack version.  
3. **Install the SDK** by running the following commands:  
   ```sh
   chmod +x ZED_SDK_Ubuntu20_cuda11.4_v*zstd.run
   ./ZED_SDK_Ubuntu20_cuda11.4_v*zstd.run
   ```  
4. **Clone the ZED SDK repository** (optional but useful for sample programs):  
   ```sh
   git clone https://github.com/stereolabs/zed-sdk
   ```  
5. **Install dependencies and test the sample programs** to ensure everything is working.  

---  

### 3.3 Installation for Jetson Orin NX  
#### Option 1: Transfer and Install from Another Machine  
1. **Download the SDK** from [this link](https://drive.google.com/drive/folders/196RAmjltYhkYCpIDo6fPaXH0Fv8bp7P8?usp=sharing) to your local computer.  
2. **Transfer the file** to your Jetson Orin NX using `scp`:  
   ```sh
   scp /path/to/ZED_SDK_Ubuntu20_cuda11.4_v*zstd.run GMR@192.168.18.52:/home/GMR
   ```  
3. **Install the SDK** on Jetson Orin NX:  
   ```sh
   chmod +x ZED_SDK_Ubuntu20_cuda11.4_v*zstd.run
   ./ZED_SDK_Ubuntu20_cuda11.4_v*zstd.run
   ```  

#### Option 2: Direct Download on Jetson Orin NX  
If your Jetson Orin NX has a graphical interface, you can directly download the SDK file using the provided link and follow the installation steps above.  


