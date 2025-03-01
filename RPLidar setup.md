### 4.1 RPLidar Setup
- Create a workspace:
  ```sh
  mkdir -p lidar_ws/src
  cd lidar_ws/src
  ```
- Clone repository:
  ```sh
  git clone -b dev-ros1 https://github.com/Slamtec/rplidar_ros/tree/dev-ros1
  ```
- Setup workspace:
  ```sh
  cd ../
  source ./devel/setup.bash
  ```
- Launch Lidar visualization:
  ```sh
  roslaunch rplidar_ros view_rplidar_s2.launch
  ```
- View 2D Lidar map in RViz.
