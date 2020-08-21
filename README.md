# Chessbot
This simulation will program a NASA/GM Robonaut 2 robot.  NASA has released a Gazebo model of an R2, which we can install.

## Dependencies

The following commands will install some necessary ROS packages for the Noetic distribution from the build farm

```
sudo apt-get install ros-noetic-ros-control ros-noetic-gazebo-ros-control ros-noetic-joint-state-controller \
ros-noetic-effort-controllers ros-noetic-joint-trajectory-controller ros-noetic-octomap* ros-noetic-object-recognition*
```

There is also a dependency on the ROS MoveIt Motion Planning Framework.  [MoveIt 1.1 Noetic](https://moveit.ros.org/#release-versions) is the imminent release for Noetic that is still in development at the time of this writing.  Once it is available it can be installed using:

```
sudo apt-get install ros-noetic-moveit*
```

To check out the latest version of the R2 simulaiton model for Gazebo and the R2 controllers:
```
cd src
git clone -b melodic https://github.com/plskeggs/nasa_r2_simulator.git
git clone -b melodic https://github.com/plskeggs/nasa_r2_common.git
```

To make the catkin workspace:
```
cd ..
catkin_make
```

>__WARNING:__
After executing the following lines:
```
cd ..
source devel/setup.bash
roslaunch r2_gazebo r2_gazebo.launch 
```
The following errors are generated:
```
RLException: Invalid <param> tag: Cannot load command parameter [robot_description]: no such command [['/opt/ros/noetic/share/xacro/xacro.py', '~/chessbot/src/nasa_r2_simulator/r2_gazebo/robots/r2.sim.urdf.xacro']]. 

Param xml is <param name="robot_description" command="$(find xacro)/xacro.py '$(find r2_gazebo)/robots/r2.sim.urdf.xacro'"/>
The traceback for the exception was written to the log file
```
This looks to be related to a missing parameter that is determined by a sourceforge.net page no longer in use.

## Links
* https://github.com/osrf/rosbook/issues/24
* https://github.com/plskeggs/nasa_r2_simulator
* https://github.com/plskeggs/nasa_r2_common