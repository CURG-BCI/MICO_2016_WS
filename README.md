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