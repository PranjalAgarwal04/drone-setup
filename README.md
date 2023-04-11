# Setup Documentation

## Setting up Ardupilot ✈️

- Clone the [ardupilot](https://github.com/ArduPilot/ardupilot) repository. [Read docs](https://ardupilot.org/dev/docs/building-setup-linux.html)

```bash
git clone https://github.com/ArduPilot/ardupilot.git
```

- Enter the ardupilot directory

```bash
cd ardupilot
```

- Install submodules

```bash
git submodule update --init --recursive
```

- Install required packages

```bash
Tools/environment_install/install-prereqs-ubuntu.sh -y
```

- `Logout` and `Login` again.

- Reload path

```bash
. ~/.profile
```

- Build the code. [Read more](https://github.com/ArduPilot/ardupilot/blob/master/BUILD.md)

```bash
./waf configure --board sitl
```

- Build copter

```bash
./waf copter
```

## Running SITL 💻️

- Enter the copter directory

```bash
cd ArduCopter
```

- Run the simulator

```bash
sim_vehicle.py -w
```

![SITL](./assets/sim.png?raw=true "SITL")

## Installing GCS 📡️

- Remove a package

```bash
sudo apt-get remove modemmanager -y
```

- Install dependencies. [Read Docs](https://docs.qgroundcontrol.com/master/en/getting_started/download_and_install.html)

```bash
sudo apt install gstreamer1.0-plugins-bad gstreamer1.0-libav gstreamer1.0-gl -y
```

- Install a dependency

```bash
sudo apt install libqt5gui5 -y
```

- Install a dependency

```bash
sudo apt install libfuse2 -y
```

- Download [QGroundControl](https://d176tv9ibo4jno.cloudfront.net/latest/QGroundControl.AppImage).

- Make the file executable

```bash
chmod +x ./QGroundControl.AppImage
```

- Add the alias to the `~/.bash_aliases` file

```bash
alias qgc="~/Documents/vs-code/py-python/projects/drone-setup/src && ./QGroundControl.AppImage"
```

- Reload the aliases

```bash
source ~/.bashrc
```

- Launch the application

```bash
qgc
```

## Visualize SITL 📺️

- Launch qgc

```bash
qgc
```

- Run the simulator

```bash
cd ArduCopter && sim_vehicle.py
```

![QGroundControl](./assets/qgc.png?raw=true "QGroundControl")

## Installing Gazebo 🖥️

- Install dependencies

```bash
sudo apt update
sudo apt install lsb-release wget gnupg
```

- Add the repository. [Read Docs](https://staging.gazebosim.org/docs/garden/install_ubuntu)

```bash
sudo wget https://packages.osrfoundation.org/gazebo.gpg -O /usr/share/keyrings/pkgs-osrf-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/pkgs-osrf-archive-keyring.gpg] http://packages.osrfoundation.org/gazebo/ubuntu-stable $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/gazebo-stable.list > /dev/null
```

- Update the package list

```bash
sudo apt update
```

- Install gazebo

```bash
sudo apt install gz-garden
```

- Install arduino_gazebo [plugin](https://github.com/ArduPilot/ardupilot_gazebo)

```bash
git clone https://github.com/ArduPilot/ardupilot_gazebo.git
```

- Install dependencies

```bash
sudo apt install libgz-sim7-dev rapidjson-dev
```

- Enter the directory

```bash
cd ardupilot_gazebo
```

- Install the plugin

```bash
mkdir build && cd build
cmake .. -DCMAKE_BUILD_TYPE=RelWithDebInfo
make -j4
```

- Add the plugin to the `~/.bashrc` file

```bash
echo 'export GZ_SIM_SYSTEM_PLUGIN_PATH=$HOME/Documents/vs-code/py-python/projects/drone-setup/src/ardupilot_gazebo/build:${GZ_SIM_SYSTEM_PLUGIN_PATH}' >> ~/.bashrc
echo 'export GZ_SIM_RESOURCE_PATH=$HOME/Documents/vs-code/py-python/projects/drone-setup/src/ardupilot_gazebo/models:$HOME/Documents/vs-code/py-python/projects/drone-setup/src/ardupilot_gazebo/worlds:${GZ_SIM_RESOURCE_PATH}' >> ~/.bashrc
```

- Reload the bashrc

```bash
source ~/.bashrc
```

## Launching SITL in Gazebo 🚀️

- Run gazebo

```bash
gz sim -v4 -r iris_runway.sdf
```

- Enter the dirctory

```bash
cd ardupilot/ArduCopter
```

- Run the simulator

```bash
sim_vehicle.py -v ArduCopter -f gazebo-iris --model JSON --map --console
```

![Gazebo](./assets/gzb.png?raw=true "Gazebo")

## Installing ROS 🦾

- Add repository

```bash
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```

- Set up your keys

```bash
sudo apt install curl # if you haven't already installed curl
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
```

- Update pkg manager

```bash
sudo apt update
```

- Installing ROS: Everything in ROS-Base plus tools like rqt and rviz

```bash
sudo apt install ros-noetic-desktop
```

## Authors

- [@pranjal](https://github.com/PranjalAgarwal04)
- [@prajesh](https://github.com/prajeshElEvEn)
