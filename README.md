# ros_catkin_ws
This is the source for ros on raspbian, use commands from https://neverbenever.wordpress.com/2017/12/20/install-ros-and-opencv-in-raspberry-piraspbian-stretch/

```
sudo /etc/dphys–swapfile
```
edit 
```
# set size to absolute value, leaving empty (default) then uses computed value
# you most likely don't want this, unless you have an special disk situation
# CONF_SWAPSIZE=100
CONF_SWAPSIZE=1024
```

```
sudo apt-get install dirmngr
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 421C365BD9FF1F717815A3895523BAEEB01FA116
sudo apt-get update
cd ~/
git clone https://github.com/lbaitemple/ros_catkin_ws/
cd ros_catkin_ws
unzip src.zip
rosdep install --from-paths src --ignore-src --rosdistro kinetic -y
sudo mkdir -p /opt/ros/kinetic
sudo chown pi:pi /opt/ros/kinetic
./src/catkin/bin/catkin_make_isolated -j2 --install --install-space /opt/ros/kinetic -DCMAKE_BUILD_TYPE=Release
```
