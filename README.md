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
