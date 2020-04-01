# ROS Interface plugin for CoppeliaSim

This is a modified package that make interaction between CoppeliaSim and ROS for EspeleoRobô simulations.
After this tutorial, please see https://github.com/victorRFmiranda/espeleo_Coppelia_Sim.git

### Install CoppeliaSim
1. Download CoppeliaSim EDU version 4.0 from official website: https://www.coppeliarobotics.com/downloads

2. Extract into your preference folder. Example:
```
$ cd ~/Downloads
$ tar -xf CoppeliaSim_Edu_V4_0_0_Ubuntu16_04.tar.xz
```

3. Add these lines in '.bashrc':
```
export COPPELIASIM_ROOT_DIR=~/Downloads/CoppeliaSim_Edu_V4_0_0_Ubuntu16_04
alias coppeliaSim=~/Downloads/CoppeliaSim_Edu_V4_0_0_Ubuntu16_04/coppeliaSim.sh
```
If you are using a differente folder, change `/Downloads/` for `/your_folder/`.


### Compiling this package

1. Install required packages for [libPlugin](https://github.com/CoppeliaRobotics/libPlugin): 
  ```
  $ sudo apt-get install xsltproc -y
  ```
2. Install required package https://github.com/ITVRoC/ros_eposmcd. Follow `Installation to RUGGED`.

Don't forget of remove `ros_eposmcd_driver` from ros_eposmcd folder
 
3. Clone this package in your ROS Workspace
```
$ cd ~/catkin_ws/src
$ git clone --recursive https://github.com/victorRFmiranda/sim_ros_interface.git sim_ros_interface
```
4. Compile
```
$ catkin build
```

5. Copy the file `../catkin_ws/devel/lib/libsimExtROSInterface.so` to you CoppeliaSim root.

6. Run the ROS master, open CoppeliaSim (type coppeliaSim on terminal), load any EspeleoRobô model, play the scene and check if the topics have appeared, indicating that you are good to go!
