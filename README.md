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


Iniciar simulacion GundamRobot
==============================

**Preparar a Gundam Robot para caminar**
```
$ roslaunch gundam_rx78_gazebo gundam_rx78_walk.launch
```

![image2](https://user-images.githubusercontent.com/61398373/146424713-ed34cf68-3669-4dd8-9ffd-f151c7c0e042.jpg)
Posicion del Gundam Robot listo para caminar.

**Importar modelo 3d de la ciudad de Panama**



**Comandos para darle movimento al GundamRobot**
```
# Caminar hacia adelante
$ rosrun gundam_rx78_control joint_trajectory_client_csv.py `rospack find gundam_rx78_control`/sample/csv/walk-forward.csv

# Caminar hacia atras
$ rosrun gundam_rx78_control joint_trajectory_client_csv.py `rospack find gundam_rx78_control`/sample/csv/walk-backward.csv

# Moverse a la derecha
$ rosrun gundam_rx78_control joint_trajectory_client_csv.py `rospack find gundam_rx78_control`/sample/csv/walk-to-right.csv

# Moverse a la izquierd
$ rosrun gundam_rx78_control joint_trajectory_client_csv.py `rospack find gundam_rx78_control`/sample/csv/walk-to-left.csv

# Girar a la derecha
$ rosrun gundam_rx78_control joint_trajectory_client_csv.py `rospack find gundam_rx78_control`/sample/csv/turn-right.csv

# Girar a la izquierda
$ rosrun gundam_rx78_control joint_trajectory_client_csv.py `rospack find gundam_rx78_control`/sample/csv/turn-left.csv
```



