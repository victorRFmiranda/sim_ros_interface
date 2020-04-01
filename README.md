# ROS Interface plugin for CoppeliaSim

This is a modified package that makes the interaction between CoppeliaSim and ROS for EspeleoRobô simulations.

### Install CoppeliaSim

1. Download CoppeliaSim EDU version 4.0 from official website: https://www.coppeliarobotics.com/downloads

2. Extract into your preference folder. Example:
```
cd ~/Downloads
tar -xf CoppeliaSim_Edu_V4_0_0_Ubuntu16_04.tar.xz
```

3. Add these lines in `~/.bashrc`:
```
export COPPELIASIM_ROOT_DIR=~/Downloads/CoppeliaSim_Edu_V4_0_0_Ubuntu16_04
alias coppeliasim=~/Downloads/CoppeliaSim_Edu_V4_0_0_Ubuntu16_04/coppeliaSim.sh
```

You can do it wiith gedit or simply use the following terminal commands:
```
echo "export COPPELIASIM_ROOT_DIR=~/Downloads/CoppeliaSim_Edu_V4_0_0_Ubuntu16_04" >> ~/.bashrc
echo "alias coppeliasim=~/Downloads/CoppeliaSim_Edu_V4_0_0_Ubuntu16_04/coppeliaSim.sh" >> ~/.bashrc
```

After that, open a new terminal or resource your bash:
```
source ~/.bashrc 
```

If you are using a different folder, change `~/Downloads/` for `your_folder_path`.

Try typing `copeliasim` on a new terminal and see if the simulator opens. In this case, go to the next step, other case check what is wrong before proceeding.


### Compiling this package

1. Install required packages for [libPlugin](https://github.com/CoppeliaRobotics/libPlugin): 
  ```
  $ sudo apt-get install python-catkin-tools xsltproc ros-$ROS_DISTRO-brics-actuator ros-$ROS_DISTRO-tf2-sensor-msgs
  ```

2. Install required package:
  ```
  $ git clone https://github.com/ITVRoC/ros_eposmcd.
  ```

Follow `Installation to RUGGED`. Don't forget of remove `ros_eposmcd_driver` inside ros_eposmcd folder
 
3. Clone the following package in your ROS Workspace
```
$ cd ~/catkin_ws/src
$ git clone --recursive https://github.com/victorRFmiranda/sim_ros_interface.git sim_ros_interface
```

4. Compile
```
$ catkin build
```

Note: If you currently use `catkin_make` to compile install th `python_catkin_tools` to use `catkin_build` instead:
```
$ sudo apt-get install python-catkin-tools
```

5. Copy the file `~/catkin_ws/devel/lib/libsimExtROSInterface.so` to you CoppeliaSim root. You can use the following command:
```
$ cp ~/catkin_ws/devel/lib/libsimExtROSInterface.so $COPPELIASIM_ROOT_DIR
```

6. Run the ROS master (`roscore`), open CoppeliaSim (type `coppeliasim` on terminal). Check in the terminal in which you runned coppeliaSim the following lines appeared:
```
Plugin 'ROSInterface': loading...
Plugin 'RosInterface': warning: replaced variable 'simROS'
Plugin 'ROSInterface': load succeeded.

```
In the positive case, your simulator is communicating with ROS. You are ready to load a EspeleoRobô model and play with it. Please go to the `https://github.com/ITVRoC/espeleo_vrep_simulation` to get instruction on how to obtain and load the models.

## Contact

Any questions, please contact-me in ``victormrfm@gmail.com``.
