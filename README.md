# Raspberry Pi OS ROS2

Build ROS2 for Raspbian

![](./images_for_readme//rviz_rpi.jpg)

<br>

## Support

### Latest : ros2-0.3.2

[ros2-0.3.2](https://github.com/Ar-Ray-code/rpi-bullseye-ros2/releases/tag/ros2-0.3.2)

| Distro | Debian | arm64-desktop | arm64-full |
| --- | --- | --- | --- |
| jazzy | bookworm | [URL](https://s3.ap-northeast-1.wasabisys.com/download-raw/dpkg/ros2-desktop/debian/bookworm/ros-jazzy-desktop-0.3.2_20240525_arm64.deb) |
| iron | bullseye | [URL](https://s3.ap-northeast-1.wasabisys.com/download-raw/dpkg/ros2-desktop/debian/bullseye/ros-iron-desktop-0.3.2_20230611_arm64.deb)
| iron | bookworm | [URL](https://s3.ap-northeast-1.wasabisys.com/download-raw/dpkg/ros2-desktop/debian/bookworm/ros-iron-desktop-0.3.2_20231028_arm64.deb)
| humble | bullseye | [URL](https://s3.ap-northeast-1.wasabisys.com/download-raw/dpkg/ros2-desktop/debian/bullseye/ros-humble-desktop-0.3.1_arm64.deb)

### Install (bullseye)

- OS   : RaspberryPi OS bullseye arm64
- ROS2 : ROS2 Humble

```bash
wget https://github.com/Ar-Ray-code/rpi-bullseye-ros2/releases/download/ros2-0.3.1/ros-humble-desktop-0.3.1_20221218_arm64.deb
sudo apt install ./ros-humble-desktop-0.3.1_20221218_arm64.deb
sudo pip install vcstool colcon-common-extensions
```

### Install (bookworm)

- OS   : RaspberryPi OS bookworm arm64
- ROS2 : ROS2 jazzy

```bash
wget https://s3.ap-northeast-1.wasabisys.com/download-raw/dpkg/ros2-desktop/debian/bookworm/ros-jazzy-desktop-0.3.2_20240525_arm64.deb
sudo apt install ./ros-jazzy-desktop-0.3.2_20240525_arm64.deb
sudo pip install --break-system-packages vcstool colcon-common-extensions
```

> When using Rviz2, switch the display server from Wayland to X11.
```bash
sudo raspi-config
```
![image](https://github.com/nathanshankar/rpi-bullseye-ros2/assets/66565433/19937c56-2655-4d4d-8d58-45b7d03fd36e)

> After rebooting follow these steps to get rviz working on your Pi if you are using VNC
```bash
sudo apt install xserver-xorg-video-dummy
cd /etc/X11/xorg.conf.d/
sudo nano screen.conf
```

> screen.conf: and after pasting the below code press Ctrl+X and Y
```bash
Section "Monitor"
  Identifier "Monitor0"
  HorizSync 28.0-80.0
  VertRefresh 48.0-75.0
  Modeline "1920x1080_60.00" 172.80 1920 2040 2248 2576 1080 1081 1084 1118 -HSync +Vsync
EndSection

Section "Device"
  Identifier "Card0"
  Driver "dummy"
  VideoRam 256000
EndSection

Section "Screen"
  DefaultDepth 24
  Identifier "Screen0"
  Device "Card0"
  Monitor "Monitor0"
  SubSection "Display"
    Depth 24
    Modes "1920x1080_60.00"
  EndSubSection
EndSection
```
> Reboot the Raspberry Pi

## Uninstall

```bash
sudo apt remove ros-${DISTRO}-desktop
# e.g. sudo apt remove ros-humble-desktop
```

<br>

### Load ROS2

```bash
source /opt/ros/${DISTRO}/setup.bash
# e.g. source /opt/ros/humble/setup.bash
```

<br>

<details><summary>ros2-0.2.0</summary>

[ros2-0.2.0](https://github.com/Ar-Ray-code/rpi-bullseye-ros2/releases/tag/ros2-0.2.0)

| Distro | aarch64 |
| --- | --- |
| humble | ✔ |
| galactic | |

### Install

- OS   : RaspberryPi OS bullseye aarch64
- ROS2 : ROS2 Humble

```bash
# (humble, aarch64)
curl -O https://raw.githubusercontent.com/Ar-Ray-code/rpi-bullseye-ros2/main/install.bash
# bash install.bash <distro> <arch> <version> <install-dir>
bash install.bash humble aarch64 0.2.0 /opt/ros
```

<br>

</details>

<details><summary>ros2-0.1.0</summary>

<br>

[ros2-0.1.0](https://github.com/Ar-Ray-code/rpi-bullseye-ros2/releases/tag/ros2-0.1.0)


### ❌ Excluded packages ❌

- RViz
- rosbag
- rqt

<br>

| Distro | aarch64 | arm7l |
| --- | --- | --- |
| humble | ✔ | ✔ |
| galactic | | ✔ |

### Install

- OS   : RaspberryPi OS bullseye aarch64
- ROS2 : ROS2 Humble

```bash
# (humble, aarch64)
wget https://raw.githubusercontent.com/Ar-Ray-code/rpi-bullseye-ros2/main/install.bash
bash install.bash humble aarch64 0.1.0 /opt/ros

# galactic, arm7l
# bash install.bash galactic arm7l 0.1.0 /opt/ros
```

### Load ROS2

```bash
source /opt/ros/humble/setup.bash
```

<br>

</details>

<br>


## Build ROS2

- [README](./build/README.md)

<br>

## Cross compile 🛠️

- [Ar-Ray-code/rpi-bullseye-ros2-xcompile](https://github.com/Ar-Ray-code/rpi-bullseye-ros2-xcompile)

<br>

## Cases

If rpi-bullseye-ros2 has made your project work, please let me know!✨

<br>

## About author

- author : [Ar-Ray](https://github.com/Ar-Ray-code)
- compatibility setup along with rviz: [Nathan](https://github.com/nathanshankar)

<br>
