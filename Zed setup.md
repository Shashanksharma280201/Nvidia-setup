3. ZED SDK Installation

3.1 Prerequisites

Verify Jetpack version (Required: 5.1.1)

Confirm CUDA version installation

3.2 Installation Steps

Download SDK from Stereolabs SDK

Select the version matching your Jetpack version.

Install and set up the SDK:

chmod +x ZED_SDK_Ubuntu20_cuda11.4_v*zstd.run
./ZED_SDK_Ubuntu20_cuda11.4_v*zstd.run

Clone the SDK repository:

git clone https://github.com/stereolabs/zed-sdk

Install dependencies and test sample programs.

4. Sensor Setup

4.1 RPLidar Setup

Create a workspace:

mkdir -p lidar_ws/src
cd lidar_ws/src

Clone repository:

git clone -b dev-ros1 https://github.com/Slamtec/rplidar_ros/tree/dev-ros1

Setup workspace:

cd ../
source ./devel/setup.bash

Launch Lidar visualization:

roslaunch rplidar_ros view_rplidar_s2.launch

View 2D Lidar map in RViz.