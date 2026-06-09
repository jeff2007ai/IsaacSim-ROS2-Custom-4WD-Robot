# IsaacSim-ROS2-Custom-4WD-Robot
A completely custom-made four-wheel differential drive robot built from scratch in NVIDIA Isaac Sim 5.1 with ROS 2 Jazzy integration, camera and RTX LiDAR support.


🚀 IsaacSim-ROS2-Custom-4WD-Robot
Completely Custom-Made Four-Wheel Differential Drive Robot Built from Scratch in NVIDIA Isaac Sim 5.1 with ROS 2 Jazzy

## Highlights

- ✅ 100% custom-made robot
- ✅ Built from primitive cube and cylinder meshes
- ✅ Four-wheel differential drive
- ✅ ROS 2 Jazzy integration
- ✅ `/cmd_vel` control
- ✅ Camera support
- ✅ RTX LiDAR support
- ✅ Ready for SLAM Toolbox and Nav2
- ✅ No TurtleBot or URDF imports

This repository presents a **completely custom-built four-wheel differential-drive robot** designed from scratch in **NVIDIA Isaac Sim 5.1** using primitive shapes (cube chassis and cylinder wheels). Unlike imported URDF models, every component, articulation, wheel joint, controller, and ROS 2 interface was manually designed and configured inside Isaac Sim.

The robot is controlled through ROS 2 `/cmd_vel` messages and serves as a foundation for perception, SLAM, navigation, and autonomous robotics applications.

## Demo

<p align="center">
  <img src="/home/jeffin-g-joseph/Downloads/custom_ros2_robot.gif" width="700">
</p>

---

## Features

* Fully **custom-made robot**
* Built from scratch using primitive objects
* Four-wheel differential drive (4WD)
* Revolute wheel joints
* Articulation-based robot model
* ROS 2 Jazzy integration
* `/cmd_vel` control
* Differential Controller
* Articulation Controller
* Camera support
* RTX LiDAR support
* Ready for SLAM Toolbox and Nav2
* Expandable for AI and autonomous navigation

---

## Demo Video

https://github.com/jeff2007ai/IsaacSim-ROS2-Custom-4WD-Robot/blob/main/custom_ros2_robot.mp4

## Robot Structure

```text
World
├── base_link
├── front_left_wheel
├── front_right_wheel
├── rear_left_wheel
├── rear_right_wheel
└── ActionGraph
```

---

## Wheel Parameters

| Parameter           | Value   |
| ------------------- | ------- |
| Wheel Radius        | 0.06 m  |
| Wheel Width         | 0.04 m  |
| Front Wheel X       | 0.17 m  |
| Rear Wheel X        | -0.17 m |
| Left Wheel Y        | 0.36 m  |
| Right Wheel Y       | -0.36 m |
| Wheel Center Height | 0.06 m  |

---

## Joint Names

```text
front_left_joint
front_right_joint
rear_left_joint
rear_right_joint
```

---

## Action Graph Architecture

```text
ROS2 Subscribe Twist
        ↓
Break Vector
        ↓
Differential Controller
        ↓
Get Array Index (0)
Get Array Index (1)
        ↓
Make Array
        ↓
Articulation Controller
        ↓
Wheel Joints
```

### Velocity Array

```text
[
 left_speed,
 right_speed,
 left_speed,
 right_speed
]
```

---

## ROS2 Motion Commands

### Forward

```bash
ros2 topic pub /cmd_vel geometry_msgs/msg/Twist \
"{linear: {x: 0.3}, angular: {z: 0.0}}" -r 10
```

### Backward

```bash
ros2 topic pub /cmd_vel geometry_msgs/msg/Twist \
"{linear: {x: -0.3}, angular: {z: 0.0}}" -r 10
```

### Rotate Left

```bash
ros2 topic pub /cmd_vel geometry_msgs/msg/Twist \
"{linear: {x: 0.0}, angular: {z: 1.0}}" -r 10
```

### Rotate Right

```bash
ros2 topic pub /cmd_vel geometry_msgs/msg/Twist \
"{linear: {x: 0.0}, angular: {z: -1.0}}" -r 10
```

### Forward Left

```bash
ros2 topic pub /cmd_vel geometry_msgs/msg/Twist \
"{linear: {x: 0.3}, angular: {z: 0.5}}" -r 10
```

### Forward Right

```bash
ros2 topic pub /cmd_vel geometry_msgs/msg/Twist \
"{linear: {x: 0.3}, angular: {z: -0.5}}" -r 10
```

---

## Camera Integration

Camera hierarchy:

```text
base_link
└── camera_link
```

Published topics:

```text
/rgb
/camera_info
```

---

## RTX LiDAR Integration

LiDAR hierarchy:

```text
base_link
└── lidar_link
```

Published topic:

```text
/scan
```

---

## Software Stack

* NVIDIA Isaac Sim 5.1
* Ubuntu 24.04
* ROS 2 Jazzy
* Python 3

---

## Highlights

* **100% custom-made robot**
* No URDF import
* No prebuilt TurtleBot models
* Entire robot created manually in Isaac Sim
* Designed for learning robot modeling, ROS 2 integration, and autonomous navigation


## Contribution

- 🌐 **Robocademy** – Robotics and ROS tutorials: [robocademy.com](https://robocademy.com)


---

## License

MIT License

