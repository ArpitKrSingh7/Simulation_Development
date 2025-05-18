# Simulation Development

This repository contains Husarion_ws. This repo will help the image processing and Navigation team to implement there algos and other things properly , Basically a testing envirnoment.

## 📦 Current Development
- `components.yaml` : Added 4 Zed X camera as per mentioned in ERC Docx.
- `husarion_gz_worlds`: Custom Compressed Mars World simulation world with aruco markers and anomaly objects.
- `aruco_markers`, `aruco_markers_msgs`: ArUco marker detection.
- `stereolabs_zed.urdf.xacro` : Solved the pc2 vertical inverison thing , Optimized it further to support in medium range PCs.
- `gz_ros2_control` : Issue solved which was coming due to this particular thing.
- Differential dirve working fine while visualizing all 4 cam Pc2 data.
- Properly configured for Jazzy (Ubuntu 24.04).

## 🛠️ Let's Get Started

### Prerequisites

- ROS 2 Jazzy
- `gazebo Harmonic` : Visit [Gazebo Harmonic installition Guide](https://gazebosim.org/docs/harmonic/install_ubuntu/) to get the right thing for this package.

### Intall Instructions
```
Install the Zip file , and extract it - remember it's a workspace
Remove the install , build and log from the husarion_ws directory
There will be a `bas.sh` file don't remove it
```

### Build Instructions

```bash
# I assume that you have already sourced your Ros2 and all
# Build workspace
export HUSARION_ROS_BUILD_TYPE=simulation

vcs import src < src/husarion_ugv_ros/husarion_ugv/${HUSARION_ROS_BUILD_TYPE}_deps.repos

sudo rosdep init
rosdep update --rosdistro $ROS_DISTRO
rosdep install --from-paths src -y -i

source /opt/ros/$ROS_DISTRO/setup.bash
colcon build --symlink-install --packages-up-to husarion_ugv --cmake-args -DCMAKE_BUILD_TYPE=Release -DBUILD_TESTING=OFF

source install/setup.bash

```
Previous Step will build the husarion related packages , now to build and run  Aruco package follow my colleague [Harshini's](https://github.com/harshinisrisavitha/remote/blob/main/README.md) Repo.

## Running Husarion Bot
```
#To run the bot Enter this command
ros2 launch husarion_ugv_gazebo simulation.launch.py

```

After this thing for running the bot everytime , you can directly hit `./bas.sh` , it will rebuild the workspace + source it and run the bot automatically.


### Extra Info Related to the Package


