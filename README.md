# LoonE-URDF

URDF/xacro robot description package for **LE1000-URDF-T4**, part of [Humber ASV](https://github.com/HumberASV)'s Loon E project.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![ROS](https://img.shields.io/badge/ROS-2%20%28ament__cmake%29-22314E?logo=ros&logoColor=white)](https://docs.ros.org/en/rolling/)
[![Platform](https://img.shields.io/badge/platform-linux-lightgrey)](#prerequisites)
[![Code of Conduct](https://img.shields.io/badge/Code%20of%20Conduct-CODE__OF__CONDUCT.md-blueviolet)](CODE_OF_CONDUCT.md)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

## Overview

This package holds the robot description for **LE1000-URDF-T4**, generated from a SolidWorks assembly via the [`sw_urdf_exporter`](http://wiki.ros.org/sw_urdf_exporter) plugin. It contains the xacro/URDF model, collision/visual meshes, joint configuration, and a launch file for visualizing the robot in RViz.

## Repository structure

```text
├── config/          # Controller joint name mappings and RViz config
├── launch/          # RViz launch file (display.launch.py)
├── meshes/          # Visual/collision STL meshes for each link
├── urdf/            # Xacro robot description and exporter-generated CSV
├── CMakeLists.txt   # ament_cmake build rules
└── package.xml      # ament package manifest
```

## Prerequisites

- ROS 2 (colcon workspace)
- [`robot_state_publisher`](https://index.ros.org/p/robot_state_publisher/)
- [`joint_state_publisher_gui`](https://index.ros.org/p/joint_state_publisher_gui/)
- [`rviz2`](https://index.ros.org/p/rviz2/)
- [`xacro`](https://index.ros.org/p/xacro/)

## Building

Clone this package into the `src` folder of a colcon workspace and build:

```sh
cd ~/ros2_ws/src
git clone https://github.com/HumberASV/LoonE-URDF.git
cd ~/ros2_ws
colcon build --packages-select le1000_urdf_t4
source install/setup.bash
```

## Usage

Launch RViz with the robot model, `joint_state_publisher_gui`, and `robot_state_publisher`:

```sh
ros2 launch le1000_urdf_t4 display.launch.py
```

The xacro file is processed automatically by the launch file; there's no need to pre-generate a `.urdf` file. To view a different model or RViz config, override the launch arguments:

```sh
ros2 launch le1000_urdf_t4 display.launch.py model:=/path/to/other.urdf.xacro rvizconfig:=/path/to/other.rviz
```

## Contributing

Contributions are welcome — please read [CONTRIBUTING.md](CONTRIBUTING.md) before opening a pull request, and follow our [Code of Conduct](CODE_OF_CONDUCT.md).

## License

Licensed under the [MIT License](LICENSE).
