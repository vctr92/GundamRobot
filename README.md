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


Iniciar simulacion Gundam Robot
==============================

**Preparar a Gundam Robot para caminar**
```
$ roslaunch gundam_rx78_gazebo gundam_rx78_walk.launch
```

![image2](https://user-images.githubusercontent.com/61398373/146424713-ed34cf68-3669-4dd8-9ffd-f151c7c0e042.jpg)
Posicion del Gundam Robot listo para caminar.


Importar modelo 3d de la ciudad de Panama
=========================================
1. Seleccionar en el Gazebo la pestana Edit y la Opcion Model Editor.


2. Abrira la una ventana nueva donde se elige la opcion Add.
![add](https://user-images.githubusercontent.com/61398373/146429069-0de84448-ffd6-4a1b-90f0-812feb3116ae.jpg)


3. Se busca el modelo 3d de la Ciudad de Panama descargado de este repositorio, para ser importado.
![dae](https://user-images.githubusercontent.com/61398373/146429342-31f400a8-0e9b-46e5-a507-89bc4e66f197.jpg)


4. Una vez importado el modelo 3d se ajusta en una posicion donde no coincida con el Gundam Robot y se procede a guardar el nombre del modelo.
![save](https://user-images.githubusercontent.com/61398373/146429530-9cce062f-9094-4610-938d-84e0612bbc9d.jpg)


5. Ahora en el gazebo debe aparecer el modelo 3d de la Ciudad de Panama junto al Gundam Robot.
![gazebo](https://user-images.githubusercontent.com/61398373/146430675-39921b90-88f9-488d-a2e0-02b5b59b58b9.jpg)



En una nueva terminal ejecutar los siguientes comandos 
============================================================================================

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

Ejemplo de caminata hacia adelante del Gundam Robot
===================================================

**Por cuestiones de rendimiento del equipo usado, se realiza sin el modelo3d de la Ciudad de Panama**

![ezgif com-gif-maker](https://user-images.githubusercontent.com/61398373/146469155-633e8fe4-6999-4841-85f8-7a9d50ed0ae9.gif)
