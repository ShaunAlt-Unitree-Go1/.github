# Unitree Go1 Repository Collection
Contains all of the repositories used to work with the Unitree-Go1 robot.

## Table of Contents
- [Contributors](#contributors)
- [Repositories](#repositories)
- [Creating Ubuntu VMs](#creating-ubuntu-vms)
    - [Ubuntu 18.04 ARM Server](#ubuntu-1804-bionic-arm-server)
    - [Ubuntu 20.04 ARM Server](#ubuntu-2004-focal-arm-server)
    - [Ubuntu 22.04 ARM Server](#ubuntu-2204-jammy-arm-server)
    - [Ubuntu 24.04 ARM Server](#ubuntu-2404-noble-arm-server)
- [Installing ROS & ROS2](#installing-ros--ros2)
    - [Installing ROSDEP](#installing-rosdep)
    - [ROS1 Melodic](#ros1-melodic)
    - [ROS1 Noetic](#ros1-noetic)
    - [ROS2 Foxy](#ros2-foxy)
    - [ROS2 Galactic](#ros2-galactic)
    - [ROS2 Humble](#ros2-humble)
    - [ROS2 Iron](#ros2-iron)
    - [ROS2 Jazzy](#ros2-jazzy)
- [Installing Docker](#installing-docker)
- [Connecting to a Physical Unitree Go1 Robot](#connecting-to-a-physical-unitree-go1-robot)
    - [Turn on Physical Go1 Robot](#turn-on-physical-go1-robot)
    - [Connect to Physical Go1 Robot over Ethernet](#connect-to-physical-go1-robot-over-ethernet)
    - [Connect to Physical Go1 Robot over WiFi](#connect-to-physical-go1-robot-over-wifi)
- [Running Nav2 with a Simulated Swarm - OLD](#running-nav2-with-a-simulated-swarm---old)
- [Running Nav2 with a Simulated Swarm - NEW](#running-nav2-with-a-simulated-swarm---new)

## Contributors
Created by [Shaun Altmann](https://github.com/ShaunAlt).

## Repositories
| Repository | Purpose |
| :---: | :---: |
| [Go1-Nav2-SDK](https://github.com/ShaunAlt-Unitree-Go1/Go1-Nav2-SDK) | Software Development Kit that allows the implementation of the ROS2 Navigation Stack with a Unitree Go1 Robot. |
| [Go1-Webots-Docker](https://github.com/ShaunAlt-Unitree-Go1/Go1-Webots-Docker) | Creates a Docker to run the Unitree-Go1 robot within a Webots simulator. |
| [Reolink-Camera-ROS2](https://github.com/ShaunAlt-Unitree-Go1/Reolink-Camera-ROS2) | Wirelessly stream data from the Reolink RTC-840WA camera and publish it in ROS2. |
| [ROS-Bridge-Docker](https://github.com/ShaunAlt-Unitree-Go1/ROS-Bridge-Docker) | Creates a Docker for bridging ROS1 Noetic and ROS2 Galactic topics. |
| [ROS-Bridge-Noetic](https://github.com/ShaunAlt-Unitree-Go1/ROS-Bridge-Noetic) | ROS Noetic support packages that can be used with the ROS Bridge. |
| [Unitree-Go1-Motion-ROS2](https://github.com/ShaunAlt-Unitree-Go1/Unitree-Go1-Motion-ROS2) | Send /cmd_vel commands to the Unitree Go1 robot using ROS2. |
| [Unitree-Go1-Sim](https://github.com/ShaunAlt-Unitree-Go1/Unitree-Go1-Sim) | Unitree Go1 Robot Full Simulation with LiDAR and Camera Support. |

## Creating Ubuntu VMs
### Ubuntu 18.04 (Bionic) ARM Server
1. Install the Ubuntu 18.04 ARM Server Image from [here](https://cdimage.ubuntu.com/releases/bionic/release/).
2. Burn the image into a USB.
3. Create a new VM from this USB image.
4. Install Ubuntu Desktop on the Server.
    ``` bash
    $ sudo apt update
    $ sudo apt upgrade -y
    $ sudo apt install ubuntu-desktop-minimal
    $ sudo reboot
    ```

### Ubuntu 20.04 (Focal) ARM Server
1. Install the Ubuntu 20.04 ARM Server Image from [here](https://cdimage.ubuntu.com/releases/focal/release/).
2. Create a new VM from this .iso file.
3. Install Ubuntu Desktop on the Server.
    ``` bash
    $ sudo apt update
    $ sudo apt upgrade -y
    $ sudo apt install ubuntu-desktop-minimal
    $ sudo reboot
    ```

### Ubuntu 22.04 (Jammy) ARM Server
1. Install the Ubuntu 22.04 ARM Server Image from [here](https://cdimage.ubuntu.com/releases/jammy/release/).
2. Create a new VM from this .iso file.
3. Install Ubuntu Desktop on the Server.
    ``` bash
    $ sudo apt update
    $ sudo apt upgrade -y
    $ sudo apt install ubuntu-desktop-minimal
    $ sudo reboot
    ```

### Ubuntu 24.04 (Noble) ARM Server
1. Install the Ubuntu 20.04 ARM Server Image from [here](https://cdimage.ubuntu.com/releases/noble/release/).
2. Create a new VM from this .iso file.
3. Install Ubuntu Desktop on the Server.
    ``` bash
    $ sudo apt update
    $ sudo apt upgrade -y
    $ sudo apt install ubuntu-desktop-minimal
    $ sudo reboot
    ```

## Installing ROS & ROS2
ROS packages should only be installed on the version of Ubuntu they were designed for.
| ROS1 Version | Ubuntu Version |
| :---: | :---: |
| [Melodic](#ros1-melodic) | [18.04](#ubuntu-1804-bionic-arm-server) |
| [Noetic](#ros1-noetic) | [20.04](#ubuntu-2004-focal-arm-server) |

| ROS2 Version | Ubuntu Version |
| :---: | :---: |
| [Foxy](#ros2-foxy) | [20.04](#ubuntu-2004-focal-arm-server) |
| [Galactic](#ros2-galactic) | [20.04](#ubuntu-2004-focal-arm-server) |
| [Humble](#ros2-humble) | [22.04](#ubuntu-2204-jammy-arm-server) |
| [Iron](#ros2-iron) | [22.04](#ubuntu-2204-jammy-arm-server) |
| [Jazzy](#ros2-jazzy) | [24.04](#ubuntu-2404-noble-arm-server) |

### Installing ROSDEP
ROSDEP is a tools that allows you to easily install any dependencies required when you are trying to build a ROS package. This only needs to be done once per VM, regardless of how many versions of ROS are installed. The commands are the same for all versions of ROS and Ubuntu.
``` bash
# install ros dependency packages
$ sudo apt install \
    python3-rosdep \
    python3-rosinstall \
    python3-rosinstall-generator \
    python3-wstool \
    build-essential

# initialize rosdep
$ sudo rosdep init
```

### ROS1 Melodic
ROS Melodic can be installed on an Ubuntu 18.04 machine by opening the terminal and using the following commands (full instructions [here](https://wiki.ros.org/melodic/Installation/Ubuntu)):
``` bash
# setup sources list
$ sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

# setup keys
$ sudo apt install curl
$ curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -

# update & upgrade packages
$ sudo apt update
$ sudo apt upgrade -y

# install ros melodic desktop (full install)
$ sudo apt install ros-melodic-desktop-full

# install ros development tools
$ sudo apt install ros-dev-tools

# update rosdeps for melodic
$ rosdep update --rosdistro melodic

# (OPTIONAL) setup alias to source ROS melodic
$ echo "alias source_melodic='source /opt/ros/melodic/setup.bash'" >> ~/.bashrc

# update, upgrade, and auto-remove packages
$ sudo apt update
$ sudo apt upgrade -y
$ sudo apt autoremove -y

# restart your VM
$ sudo reboot
```

### ROS1 Noetic
ROS Noetic can be installed on an Ubuntu 20.04 machine by opening the terminal and using the following commands (full instructions [here](https://wiki.ros.org/noetic/Installation/Ubuntu)):
``` bash
# setup sources list
$ sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

# setup keys
$ sudo apt install curl
$ curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -

# update & upgrade packages
$ sudo apt update
$ sudo apt upgrade -y

# install ros noetic desktop (full install)
$ sudo apt install ros-noetic-desktop-full

# install ros development tools
$ sudo apt install ros-dev-tools

# update rosdeps for noetic
$ rosdep update --rosdistro noetic

# (OPTIONAL) setup alias to source ROS noetic
$ echo "alias source_noetic='source /opt/ros/noetic/setup.bash'" >> ~/.bashrc

# update, upgrade, and auto-remove packages
$ sudo apt update
$ sudo apt upgrade -y
$ sudo apt autoremove -y

# restart your VM
$ sudo reboot
```

### ROS2 Foxy
ROS2 Foxy can be installed on an Ubuntu 20.04 machine by opening the terminal and using the following commands (full instructions [here](https://docs.ros.org/en/foxy/Installation/Ubuntu-Install-Debians.html)):
``` bash
# ensure Ubuntu Universe Repository is enabled
$ sudo apt install software-properties-common
$ sudo add-apt-repository universe

# setup keys
$ sudo apt update
$ sudo apt install curl -y
$ sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

# add repository to sources list
$ echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

# update & upgrade packages
$ sudo apt update
$ sudo apt upgrade -y

# install ros2 foxy desktop (full install)
$ sudo apt install ros-foxy-desktop python3-argcomplete

# install ros development tools
$ sudo apt install ros-dev-tools

# update rosdeps for foxy
$ rosdep update --rosdistro foxy

# (OPTIONAL) setup alias to source ros2 foxy
$ echo "alias source_foxy='source /opt/ros/foxy/setup.bash'" >> ~/.bashrc

# update, upgrade, and auto-remove packages
$ sudo apt update
$ sudo apt upgrade -y
$ sudo apt autoremove -y

# restart your VM
$ sudo reboot
```

### ROS2 Galactic
ROS2 Galactic can be installed on an Ubuntu 20.04 machine by opening the terminal and using the following commands (full instructions [here](https://docs.ros.org/en/galactic/Installation/Ubuntu-Install-Debians.html)):
``` bash
# ensure Ubuntu Universe Repository is enabled
$ sudo apt install software-properties-common
$ sudo add-apt-repository universe

# setup keys
$ sudo apt update
$ sudo apt install curl -y
$ sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

# add repository to sources list
$ echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

# update & upgrade packages
$ sudo apt update
$ sudo apt upgrade -y

# install ros2 galactic desktop (full install)
$ sudo apt install ros-galactic-desktop

# install ros development tools
$ sudo apt install ros-dev-tools

# update rosdeps for galactic
$ rosdep update --rosdistro galactic

# (OPTIONAL) setup alias to source ros2 galactic
$ echo "alias source_galactic='source /opt/ros/galactic/setup.bash'" >> ~/.bashrc

# update, upgrade, and auto-remove packages
$ sudo apt update
$ sudo apt upgrade -y
$ sudo apt autoremove -y

# restart your VM
$ sudo reboot
```

### ROS2 Humble
ROS2 Humble can be installed on an Ubuntu 22.04 machine by opening the terminal and using the following commands (full instructions [here](https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debs.html)):
``` bash
# ensure Ubuntu Universe Repository is enabled
$ sudo apt install software-properties-common
$ sudo add-apt-repository universe

# setup keys
$ sudo apt update
$ sudo apt install curl -y
$ sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

# add repository to sources list
$ echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

# update & upgrade packages
$ sudo apt update
$ sudo apt upgrade -y

# install ros2 humble desktop (full install)
$ sudo apt install ros-humble-desktop

# install ros development tools
$ sudo apt install ros-dev-tools

# update rosdeps for humble
$ rosdep update --rosdistro humble

# (OPTIONAL) setup alias to source ros2 humble
$ echo "alias source_humble='source /opt/ros/humble/setup.bash'" >> ~/.bashrc

# update, upgrade, and auto-remove packages
$ sudo apt update
$ sudo apt upgrade -y
$ sudo apt autoremove -y

# restart your VM
$ sudo reboot
```

### ROS2 Iron
ROS2 Iron can be installed on an Ubuntu 22.04 machine by opening the terminal and using the following commands (full instructions [here](https://docs.ros.org/en/iron/Installation/Ubuntu-Install-Debs.html)):
``` bash
# ensure Ubuntu Universe Repository is enabled
$ sudo apt install software-properties-common
$ sudo add-apt-repository universe

# setup keys
$ sudo apt update
$ sudo apt install curl -y
$ sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

# add repository to sources list
$ echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

# update & upgrade packages
$ sudo apt update
$ sudo apt upgrade -y

# install ros2 iron desktop (full install)
$ sudo apt install ros-iron-desktop

# install ros development tools
$ sudo apt install ros-dev-tools

# update rosdeps for iron
$ rosdep update --rosdistro iron

# (OPTIONAL) setup alias to source ros2 iron
$ echo "alias source_iron='source /opt/ros/iron/setup.bash'" >> ~/.bashrc

# update, upgrade, and auto-remove packages
$ sudo apt update
$ sudo apt upgrade -y
$ sudo apt autoremove -y

# restart your VM
$ sudo reboot
```

### ROS2 Jazzy
ROS2 Jazzy can be installed on an Ubuntu 24.04 machine by opening the terminal and using the following commands (full instructions [here](https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debs.html)):
``` bash
# ensure Ubuntu Universe Repository is enabled
$ sudo apt install software-properties-common
$ sudo add-apt-repository universe

# setup keys
$ sudo apt update
$ sudo apt install curl -y
$ sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

# add repository to sources list
$ echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

# update & upgrade packages
$ sudo apt update
$ sudo apt upgrade -y

# install ros2 jazzy desktop (full install)
$ sudo apt install ros-jazzy-desktop

# install ros development tools
$ sudo apt install ros-dev-tools

# update rosdeps for jazzy
$ rosdep update --rosdistro jazzy

# (OPTIONAL) setup alias to source ros2 jazzy
$ echo "alias source_jazzy='source /opt/ros/jazzy/setup.bash'" >> ~/.bashrc

# update, upgrade, and auto-remove packages
$ sudo apt update
$ sudo apt upgrade -y
$ sudo apt autoremove -y

# restart your VM
$ sudo reboot
```

## Installing Docker
Many of these repositories implement docker containers. Docker can be setup by opening the terminal and using the following commands (full instructions can be found [here](https://docs.docker.com/engine/install/ubuntu/)):
``` bash
# install curl
$ sudo apt install curl -y

# install docker
$ curl -fsSL https://get.docker.com/ | sh

# validate docker is installed
$ docker --version

# create docker group and add the current user to it
$ sudo groupadd docker
$ sudo gpasswd -a $USER docker
$ sudo systemctl restart docker

# allow dockers to use host graphics (Gazebo, RViZ, etc.)
$ xhost +local:

# restart your VM
$ sudo reboot
```

## Connecting to a Physical Unitree Go1 Robot
### Turn on Physical Go1 Robot
The process to turn on the GO1 Robot can be found in this [video](https://www.youtube.com/watch?v=VbabuAhol0E).

### Connect to Physical Go1 Robot over Ethernet
The robot can be connected to via ethernet by turning it on and completing the following steps:
1. Connect the robot and laptop together via an ethernet link.
2. Get the ethernet port name on your computer.
    ``` bash
    $ sudo ifconfig
    ...
    enp0s25: ... # en* means ethernet port - this is the port we want
    ...
    ```
3. Set a static connection to the robot.
    ``` bash
    $ sudo ifconfig enp0s25 down # replace with your port name
    $ sudo ifconfig enp0s25 192.168.123.162/24
    $ sudo ifconfig enp0s25 up
    ```
4. SSH to test connection.
    ``` bash
    $ ssh pi@192.168.12.1
    Password: 123
    ```

### Connect to Physical Go1 Robot over WiFi
> [!NOTE]
> The robot produces a 5GHz wifi signal.

The robot can be connected to via wifi by turning it on and completing the following steps:
1. The robot's wifi connection name will start with `Unitree_Go`.
2. The robot's password will be `00000000` (8x zeros).
3. SSH to test connection.
    ``` bash
    # on your machine
    $ ssh pi@192.168.12.1
    Password: 123
    ```

The following steps will need to be implemented the very first time you try to connect wirelessly to the robot.
1. SSH into the robot.
    ``` bash
    # on your machine
    $ ssh pi@192.168.12.1
    Password: 123
    ```
2. Update the Robot's System Configuration File.
    ``` bash
    # inside the robot
    $ sudo vi /etc/sysctl.conf
    ```
    - Uncomment (remove the `#` character) from the `net.ipv4.ip_forward=1` line if it is not already uncommented.
3. Update the Robot's IP Tables.
    ``` bash
    # inside the robot

    # flush the ip tables
    $ sudo iptables -F

    # flash the NAT table
    $ sudo iptables -t nat -F

    # setup the NAT table routing
    $ sudo iptables -t nat -A POSTROUTING -o wlan1 -j MASQUERADE
    $ sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
    $ sudo iptables -A FORWARD -i wlan1 -o eth0 -j ACCEPT
    $ sudo iptables -A FORWARD -i eth0 -o wlan1 -j ACCEPT
    ```
4. Restart the robot (using the power button).
5. Add the robot's IP to your machine's list of hosts:
    ``` bash
    # inside your machine
    $ sudo nano /etc/hosts
    ```
    - Add the following line underneath the other IPv4 values:
        `192.168.123.161 raspberrypi`
6. Restart your machine.

The Go1 Robot has it's own `roscore` running. If you ever need to access this, source your ROS1 distribution, then set your ROS master and you will then be able to access the ROS data directly from the robot:
``` bash
# on your machine

# source ros
$ source_noetic # or whatever distribution you are using

# set ros master
$ export ROS_MASTER_URI='http://192.168.123.161:11311'

# view ros topics (or whatever other you want to do)
$ rostopic list
```

## Running Nav2 with a Simulated Swarm - OLD

> [!NOTE]
> These commands have been fully tested, however they are not as clean as the new launch files.

For this tutorial, you will need to create an Ubuntu 20.04 VM, and install ROS Humble and Docker. Once this is done, you will need to then run the following commands to clone the required repositories ([Go1-Nav2-SDK](https://github.com/ShaunAlt-Unitree-Go1/Go1-Nav2-SDK), [ROS-Bridge-Docker](https://github.com/ShaunAlt-Unitree-Go1/ROS-Bridge-Docker), and [Unitree-Go1-Sim](https://github.com/ShaunAlt-Unitree-Go1/Unitree-Go1-Sim)) and build the required docker images (you can go to each repository for a more in-depth tutorial on each):
``` bash
# clone the docker github repositories
$ cd ~/
$ git clone https://github.com/ShaunAlt-Unitree-Go1/ROS-Bridge-Docker.git
$ git clone https://github.com/ShaunAlt-Unitree-Go1/Unitree-Go1-Sim.git

# build the docker images
$ ./ROS-Bridge-Docker/docker/build_docker.bash
$ ./Unitree-Go1-Sim/docker/build_docker.bash

# make the nav2 workspace
$ mkdir -p ~/nav2_ws/src
$ cd ~/nav2_ws/src/
$ git clone https://github.com/ShaunAlt-Unitree-Go1/Go1-Nav2-SDK.git
$ cd ~/nav2_ws/
$ source /opt/ros/humble/setup.bash
$ rosdep install -y --from-paths src --ignore-src --rosdistro humble
$ colcon build
```

To get the simulation and ROS2 navigation working, you will need 3-4 terminals (3 if using a single robot, 4 if using 2 robots).
1. Open up the simulation docker and run the simulation:
    ``` bash
    # on your machine
    $ cd ~/
    $ ./Unitree-Go1-Sim/docker/run_docker.bash

    # in the simulation docker
    $ cd /home/rosuser/sim_ws/
    $ source devel/setup.bash

    # if simulating a single robot without a namespace
    $ roslaunch go1_sim_addon single.launch

    # if simulating a single robot with a namespace (r1)
    $ roslaunch go1_sim_addon single_ns.launch

    # if simulating 2 robots with namespaces (r1 and r2)
    $ roslaunch go1_sim_addon two.launch
    ```
2. Open up the ROS Bridge docker and run the bridge:
    ``` bash
    # on your machine
    $ cd ~/
    $ ./ROS-Bridge-Docker/docker/run_docker.bash

    # in the bridge docker
    $ cd /home/rosuser/bridge_ws/
    $ source install/setup.bash

    # if simulating a single robot without a namespace
    $ ./setup_params.bash

    # if simulating a single robot with a namespace (r1)
    $ ./setup_params.bash r1

    # if simulating 2 robots with namespaces (r1 and r2)
    $ ./setup_params.bash r1 r2

    # run bridge
    $ rosparam load bridge.yaml
    $ ros2 run ros1_bridge parameter_bridge
    ```
3. Run the Navigation Stack for the Robots.
    ``` bash
    # on your machine
    $ cd ~/nav2_ws/
    $ source install/setup.bash

    # if simulating a single robot without a namespace
    $ ros2 launch go1_nav2_sdk single_launch.py

    # if simulating a single robot with a namespace (r1)
    $ ros2 launch go1_nav2_sdk r1_launch.py

    # if simulating 2 robots with namespaces (r1 and r2)
    $ ros2 launch go1_nav2_sdk r1_launch.py
    $ ros2 launch go1_nav2_sdk r2_launch.py # in a new terminal
    ```

## Running Nav2 with a Simulated Swarm - NEW

> [!NOTE]
> The following commands have not been fully tested and may not work. You might have to use the `single.launch`, `single_ns.launch`, and `two.launch` commands as described in the [Unitree-Go1-Sim](https://github.com/ShaunAlt-Unitree-Go1/Unitree-Go1-Sim) documentation.

You will need to open 1 terminal to launch the simulation, 1 terminal per robot you wish to spawn into the simulation, 1 terminal to bridge ROS1 and ROS2, and 1 terminal per robot you with to control with the ROS2 navigation stack (e.g. if you wanted to simulate 3 robots, you would need 1 simulation terminal, 3 spawn terminals, 1 bridge terminal, and 3 navigation terminals, meaning 8 terminals in total).
- In the simulation terminal, run the following commands:
    ``` bash
    # on your machine
    $ cd ~/
    $ ./Unitree-Go1-Sim/docker/run_docker.bash

    # in the simulation docker
    $ cd /home/rosuser/sim_ws/
    $ source devel/setup.bash
    $ roslaunch go1_sim_addon gazebo.launch
    ```
- In each of the robot spawn terminals, run the following commands:
    ``` bash
    # on your machine
    $ cd ~/
    $ ./Unitree-Go1-Sim/docker/run_docker.bash -t

    # in the simulation docker
    $ cd /home/rosuser/sim_ws/
    $ source devel/setup.bash
    $ roslaunch go1_sim_addon spawn.launch # add arguments to each
    ```
- In the bridge terminal, run the following commands:
    ``` bash
    # on your machine
    $ cd ~/
    $ ./ROS-Bridge-Docker/docker/run_docker.bash

    # in the bridge docker
    $ cd /home/rosuser/bridge_ws/
    $ source install/setup.bash
    $ ./setup_params.bash robot_name_1 robot_name_X
    $ rosparam load bridge.yaml
    $ ros2 run ros1_bridge parameter_bridge
    ```
- In each of the navigation terminals, run the following commands:
    ``` bash
    # on your machine
    $ cd ~/nav2_ws/
    $ source install/setup.bash
    $ ros2 launch go1_nav2_sdk 
