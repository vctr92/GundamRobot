# GundamRobot

Simulaion de una caminata en la ciudad de Panama

Recursos Necesarios
===================
1. Tener instalado ROS (Robot Operating System)
2. Configurar el espacio del Gundam Robot del repositorio: https://github.com/gundam-global-challenge/gundam_robot.git
3. Pasos para la instalacion usados

```
$ mkdir -p catkin_ws/src
$ cd  catkin_ws
$ sudo apt install python-wstool
$ wstool init src
$ wstool merge -t src https://github.com/gundam-global-challenge/gundam_robot/raw/master/.gundam.rosinstall
$ wstool update -t src
$ source /opt/ros/$ROS_DISTRO/setup.bash
$ rosdep install -y -r --from-paths src --ignore-src
$ catkin build
$ source devel/setup.bash
```

Modelo 3d de la ciudad de Panama
================================

![Screenshot from 2021-12-16 12-42-08](https://user-images.githubusercontent.com/61398373/146422856-50b3904e-3feb-47b1-bea1-9e77ea6c6ba2.jpg)
La carpeta **PanamaCity** de este repositorio contiene este modelo3d de la ciudad de Panama exportado en formato **.dae** para poder ser utilzado en gazebo.


How to run gazebo simulation
============================

To run a gazebo dynamics simulation, you can start `gundam_rx78_world.launch`.

```
$ roslaunch gundam_rx78_gazebo gundam_rx78_world.launch
```

If the gazebo simulation GUI is launched, You must start `start` button on the bottom of the gazebo UI to start dynamics calculation.

To control joint angles, try a sample script.

```
$ rosrun gundam_rx78_control joint_position_client_example.py
```

Note that currently, we have several limitation on this simulation, the robot is pinned to the world, we only have position controller etc.

You can also find sample motion control files in the `gundam_rx78_control/sample` directory.


