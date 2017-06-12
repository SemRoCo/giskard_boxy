# giskard_boxy
Robot-specific configuration and launch-files to use giskard controllers on the Boxy robot.

## Installation
### ROS Indigo and Ubuntu 14.04
Using ```catkin_tools``` and ```wstool``` in a new workspace, please run:
```
source /opt/ros/indigo/setup.bash          # start using ROS Indigo
mkdir -p ~/giskard_ws/src                  # create directory for workspace
cd ~/giskard_ws                            # go to workspace directory
catkin init                                # init workspace
cd src                                     # go to source directory of workspace
wstool init                                # init rosinstall
wstool merge https://raw.githubusercontent.com/SemRoCo/giskard_boxy/master/rosinstall/catkin_indigo.rosinstall
                                           # update rosinstall file
wstool update                              # pull source repositories
rosdep install --ignore-src --from-paths . # install dependencies available through apt
cd ..                                      # go to workspace directory
catkin build                               # build packages
source ~/giskard_ws/devel/setup.bash       # source new overlay
```
## Playthings
### Boxy upper-body Cartesian Position Control: Using Interactive Markers

![rviz view](https://raw.githubusercontent.com/SemRoCo/giskard_boxy/master/docs/interactive_markers_upper_body.png)

To get a quick intuition of the performance of the upper-body Cartesian control, you can run

```bash
roslaunch giskard_boxy interactive_markers.launch sim:=true
```
That should bring up a kinematics-only simulation of Boxy, the giskard controller, and rviz with interactive markers displayed. Pull on the markers to move the left or the right arm, respectively.
