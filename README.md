# Installing-and-launching-robot-arm-packages
This repository shows the steps taken to install  and run robot arm packages.

These packages were tested under ROS Melodic  and Ubuntu 18.04.

# Dependencies

1.Make sure you already have a running VM with ubuntu 18.04 .

2.type in the commands down below in the terminal

**1-Install of ROS Melodic** 
   - 1-1 Setup your sources.list
```
$ sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```
   - 1-2 Set up your keys
```
$ sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
```
   - 1-3 Installation
```
$ sudo apt-get update
$ sudo apt-get install ros-melodic-desktop-full
```
   - 1-4 Environment setup
  ```
$ echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc
$ source ~/.bashrc
```
   -  1-5 Dependencies for building packages
   ```
$ sudo apt install python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential
$ sudo apt install python-rosdep
$ sudo rosdep init
$ rosdep update
```

**2-Preparing ROS**
 ```     
$ source /opt/ros/noetic/setup.bash
$ mkdir -p ~/catkin_ws/src
$ cd ~/catkin_ws/
$ echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc
$ source ~/.bashrc
```
**3-Installing the package arduino_robot_arm**

  - 3-1 Add the “arduino_robot_arm” package to “src” folder
  ```
$ cd ~/catkin_ws/src
$ sudo apt install git
$ git clone https://github.com/smart-methods/arduino_robot_arm
```
  - 3-2 Install all the dependencies 
  ```
$ cd ~/catkin_ws
$ rosdep install --from-paths src --ignore-src -r -y
$ sudo apt-get install ros-melodic-moveit
$ sudo apt-get install ros-melodic-joint-state-publisher ros-melodic-joint-state-publisher-gui
$ sudo apt-get install ros-melodic-gazebo-ros-control joint-state-publisher
$ sudo apt-get install ros-melodic-ros-controllers ros-melodic-ros-control
```
 - 3-3 Compile the package
```
$ catkin_make
```


**4-Controlling the motors in simulation**
```
$ roslaunch robot_arm_pkg check_motors.launch
$ roslaunch robot_arm_pkg check_motors_gazebo.launch
$ rosrun robot_arm_pkg joint_states_to_gazebo.py
```

**5-Results**
![1](https://user-images.githubusercontent.com/86648269/124048182-68611900-da1e-11eb-982f-5c2eec57fad8.png)


![2](https://user-images.githubusercontent.com/86648269/124048194-6f882700-da1e-11eb-8f34-92205e544cfe.png)


![3](https://user-images.githubusercontent.com/86648269/124048200-744cdb00-da1e-11eb-9f89-c2024b4ff3e9.png)









