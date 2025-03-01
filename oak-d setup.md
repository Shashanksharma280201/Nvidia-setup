4.2 OAK-D Setup

Install DepthAI SDK and ROS2 wrapper:

sudo apt update
python3 -m pip install depthai
sudo apt install ros-humble-depthai-ros

Create a workspace:

mkdir -p ~/oakd_ws/src
cd ~/oakd_ws/src

Clone repository:

git clone https://github.com/luxonis/depthai-ros.git

Build and source the workspace:

cd ~/oakd_ws
colcon build --symlink-install
source install/setup.bash

Launch OAK-D node:

ros2 launch depthai_ros depthai.launch.py

View output in RViz:

ros2 run rviz2 rviz2

Verify topics:

ros2 topic list

Key Topics:

/color/image_raw – RGB image

/stereo/depth – Depth map

/pointcloud – 3D point cloud

Troubleshooting:

Check if OAK-D is detected:

lsusb | grep Luxonis

Restart node if no image appears:

ros2 node list
ros2 launch depthai_ros depthai.launch.py --debug

