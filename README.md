# MICO_2016_WS
Running the Mico project using block recognition and tf filtering

## Dependencies
- You need to have the following packages installed
```bash
$ sudo apt-get install ros-indigo-desktop-full
$ sudo apt-get install ros-indigo-moveit
$ sudo apt-get install ros-indigo-ar-track-alvar
```
- Also libassimp3-dev won't work - so you'll need the 3.0 version of assimp (here)[https://sourceforge.net/projects/assimp/files/assimp-3.0/]
- For building we use gitman. Make sure you have at least python3.5 installed (for trusty users see (here)[https://gist.github.com/larainema/a05d2f28cc7d944da6f6] and then rerun (get-pip.py)[https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=3&cad=rja&uact=8&ved=0ahUKEwioqIrc6NfWAhUJSyYKHXUKD-oQFggxMAI&url=https%3A%2F%2Fbootstrap.pypa.io%2Fget-pip.py&usg=AOvVaw0zKVO_zW0nkF7s0zdjWFNj] with python3.5).
```bash
$ pip install gitman --user
```

## Install
```bash
$ gitman install
```

## Running
```bash
$ source devel/setup.bash
$ roslaunch launcher everything.launch
$ roslaunch graspit_bci_plugin graspit_bci_plugin.launch
```

## Installing Dependencies on 16.04
```bash
cd
pip3 install gitman --user

sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 421C365BD9FF1F717815A3895523BAEEB01FA116

wget https://developer.nvidia.com/compute/cuda/9.0/Prod/local_installers/cuda-repo-ubuntu1604-9-0-local_9.0.176-1_amd64-deb
sudo dpkg -i cuda-repo-ubuntu1604-9-0-local_9.0.176-1_amd64.deb
sudo apt-key add /var/cuda-repo-9-0-local/7fa2af80.pub
sudo apt-get update

sudo apt install build-essential libturbojpeg libtool autoconf libudev-dev cmake mesa-common-dev freeglut3-dev libxrandr-dev doxygen libxi-dev libjpeg-turbo8-dev pkg-config beignet-dev libglfw3-dev   libusb-1.0-0-dev libva-dev libjpeg-dev libopenni2-dev ros-kinetic-desktop-full ros-kinetic-moveit ros-kinetic-ar-track-alvar ros-kinetic-manipulation-msgs ros-kinetic-pcl-ros ocl-icd-libopencl1 cuda libqt4-dev libqt4-opengl-dev libqt4-sql-psql libcoin80-dev libsoqt4-dev libblas-dev liblapack-dev libqhull-dev libeigen3-dev ros-kinetic-trac-ik*

pip2 install ipdb --user

sudo rosdep init
rosdep update

git clone https://github.com/OpenKinect/libfreenect2.git
cd libfreenect2
mkdir build
cd build
cmake .. -DCMAKE_INSTALL_PREFIX=$HOME/freenect2
sudo make -j$(nproc) install

cd

mkdir ros
cd ros
git clone git@github.com:CURG-BCI/MICO_2016_WS.git
cd MICO_2016_WS

mkdir dependencies
cd dependencies
git clone https://github.com/assimp/assimp.git
cd assimp
mkdir build
cd build
cmake ..
make -j$(nproc)
sudo make install
cd port/PyAssimp
python setup.py install --user
sudo rm -rf /usr/lib/python2.7/dist-packages/pyassimp
cd ../../../..

gitman install
catkin_make
```
