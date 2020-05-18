
# SRC2-meta
SRC2 competition metarepository

## Dependencies
TODO

## Install 
This is an example of how to install packages and setup a new workspace. 

**Download repository containing .rosinstall files**
First, download the repository containing the .rosinstall files:
`$ git clone https://github.com/wvu-navLab/SRC2-meta` 
 
**Create workspace** 
 Now, create the workspace `catkin_make`:
 `$ mkdir -p ~/my_ws/src`
 `$ cd ~/my_ws`
 `$ catkin_make`
 
Or, create the workspace using `catkin build`:
 `$ mkdir -p ~/my_ws/src`
 `$ cd ~/my_ws`
 `$ catkin build`

**Install with wstool**
 Now, install packages using `wstool`:
 `$ cd ~/my_ws`
 `$ wstool init src /path/to/meta.rosinstall`
 
 **Build packages**
 If using catkin_make:
  `$ cd ~/my_ws`
  `$ catkin_make`
  
   **Ignoring packages**
To ignore a package, add an empty file called   `CATKIN_IGNORE` in the package directory, and delete the file to stop ignoring. For example, to ignore the wvu_vo_ros package"

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
