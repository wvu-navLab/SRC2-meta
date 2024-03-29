# SRC2-meta
SRC2 competition metarepository

## Dependencies
Install [wstool](http://wiki.ros.org/wstool).

Install [catkin_tools](https://catkin-tools.readthedocs.io/en/latest/installing.html) (if using catkin build).

**vo.rosinstall:** ROS Melodic or greater (with `ros-(version)-ros-base`, `ros-(version)-cv-bridge`, `ros-(version)-gazebo-msgs`, `ros-(version)-image-transport`, `ros-(version)-tf`, OpenCV 3.2.0 or greater, and C++11. ~~To install OpenCV, an install script is provided [here](https://github.com/wvu-irl/wvu_vo/blob/master/scripts/install_opencv.sh).~~ OpenCV no longer needs installed separately as OpenCV 3.2.0 is installed by default along with the ROS packages. To check OpenCV version, run `pkg-config --modversion opencv` to check if version 3.2.0 is installed.

**solution.rosinstall:** ROS Melodic (with `ros-(version)-ros-base`, `ros-(version)-cv-bridge`, `ros-(version)-gazebo-msgs`, `ros-(version)-image-transport`, `ros-(version)-tf`, `ros-(version)-pcl-conversions`, `ros-(version)-costmap-2d`, `ros-(version)-pcl-ros`, `ros-(version)-nav-core`, `ros-(version)-base-local-planner`, `ros-(version)-tf2-geometry-msgs`, `ros-(version)-tf2-sensor-msgs`, `ros-(version)-navfn`, `ros-(version)-realtime-tools`, `ros-(version)-move-base-msgs`, `ros-(version)-map-server`, `ros-(version)-move-base`, OpenCV 3.2.0, and C++11. The require version of OpenCV is installed automatically along with ROS melodic. To check OpenCV version, run `pkg-config --modversion opencv` to check if version 3.2.0 is installed. Also, execute the following commands: `sudo apt install python-pip`, `pip install scipy`, `python2.7 -m pip install Pillow`, `python2.7 -m pip install setuptools`, `python2.7 -m pip install tensorflow`, `python2.7 -m pip install keras==2.3.1`.

## Install 
This is an example of how to install packages and setup a new workspace. 
   
**Create workspace**  

First, create the workspace directory:  
 
 `$ mkdir ~/my_ws`  
 `$ cd ~/my_ws`  
  
**Download repository containing .rosinstall files**

Now, download the repository containing the `.rosinstall`. The following command will create the `src` folder (not yet created) and clone the meta repository inside the created `src` folder.   
`$ cd ~/my_ws`  
`$ git clone https://github.com/wvu-navLab/SRC2-meta src`
  
**Install with wstool (from file)**  

 Now, install packages using `wstool`:  
 
 `$ cd ~/my_ws/src`  
 `$ wstool init . meta.rosinstall`  
   
 where the arguments `$ wstool init /folder/to/init /path/to/.rosinstall`  
   
**Install with wstool (from URL)**  

 Instead of cloning the repository containing the .rosinstall file (or downloading). The workspace can be installed using the url for the raw file. For example:  
 
 `$ mkdir ~/my_ws`  
 `$ cd ~/my_ws`  
 `$ mkdir src`  
 `$ wstool init src/ https://raw.githubusercontent.com/...` 

You can find the raw url by going to the file in GitHub and clicking raw near the top right of the file.  
   
**Build packages**  

 If using catkin_make:
 
  `$ cd ~/my_ws`  
  `$ catkin_make`  
  
 If using catkin build:
 
  `$ cd ~/my_ws`  
  `$ catkin build`  
  
**Ignoring packages**  

To ignore a package, add an empty file called   `CATKIN_IGNORE` in the package directory, and delete the file to stop ignoring. For example, to ignore the `wvu_vo_ros` package:  

  `$ cd ~/my_ws/src/wvu_vo_ros`  
  `$ touch CATKIN_IGNORE`    

If using catkin build, blacklist packages to ignore. For example, to ignore `wvu_vo_ros`:  

  `$ cd ~/my_ws`  
  `$ catkin config --blacklist wvu_vo_ros`  
  
To ignore all packages except a specific list, whitelist packages to compile. For example, to only compile `wvu_vo_ros`:  

  `$ cd ~/my_ws`  
  `$ catkin config --whitelist wvu_vo_ros`  
  
  To remove all packages from the blacklist or whitelist use the following commands:
  
   `$ catkin config --no-blacklist`  
   `$ catkin config --no-whitelist`  

**Credential Helpers**  

If the .rosinstall contains many packages, either SSH keys can be used or a credential helper. To cache credentials, use the following command:  

  `$ git config --global credential.helper cache`   

This tells git to keep the username and password in memory for 15 minutes (by default), but the timeout or other seetings can be modified. See [Credential Storage](https://git-scm.com/book/en/v2/Git-Tools-Credential-Storage) for more details.  
