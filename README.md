# Setup Documentation

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
