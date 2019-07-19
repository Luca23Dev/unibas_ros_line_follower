# unibas_ros_line_follower
Questo ros project è basto sui ROS package di ROBOTIS-GIT per il Turtlebot 3 


## Requisiti ##
Ubuntu 16.04 con ROS Kinetic installato.

Il primo passo necessario è installare pacchetti dipendenti per il controllo del TurtleBot3.
Eseguire il comando seguente per installarlo.

```
sudo apt-get install ros-kinetic-joy ros-kinetic-teleop-twist-joy ros-kinetic-teleop-twist-keyboard ros-kinetic-laser-proc ros-kinetic-rgbd-launch ros-kinetic-depthimage-to-laserscan ros-kinetic-rosserial-arduino ros-kinetic-rosserial-python ros-kinetic-rosserial-server ros-kinetic-rosserial-client ros-kinetic-rosserial-msgs ros-kinetic-amcl ros-kinetic-map-server ros-kinetic-move-base ros-kinetic-urdf ros-kinetic-xacro ros-kinetic-compressed-image-transport ros-kinetic-rqt-image-view ros-kinetic-gmapping ros-kinetic-navigation ros-kinetic-interactive-markers
```

- Spostati nella cartella  
```src``` 
del package 
```catkin_ws``` 

```bash
cd ~/catkin_ws/src/
```

-Download di queste repository

```bash
git clone https://github.com/ROBOTIS-GIT/turtlebot3_msgs.git
git clone https://github.com/ROBOTIS-GIT/turtlebot3.git
git clone https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
git clone https://github.com/ROBOTIS-GIT/turtlebot3_autorace.git
```
-Download di unibas_ros_line_follower
-esegui il comando:
```bash
cd $HOME/catkin_ws
catkin_make
```
- copiare i file degli ambienti all'interno della directory dei modelli gazebo. 
Per fare ciò, esegui i seguenti comandi:

```bash
roscd unibas_ros_line_follower

cp -r ./world/turtlebot3_autorace_track_lg $HOME/.gazebo/models

cp -r ./world/flag $HOME/.gazebo/models

cp ./urdf/turtlebot3_lg_burger_pi* $HOME/catkin_ws/src/turtlebot3/turtlebot3_description/urdf/.

cp -r ./world/*_logo $HOME/.gazebo/models
cp -r ./world/scottsdale_right_01 $HOME/.gazebo/models
cp -r ./world/scottsdale_left_01 $HOME/.gazebo/models
```
Questo repository utilizza un modello personalizzato di turtlebot3, il burger turtlebot3 pi. Per averlo dentro l'ambiente di simulazione deve essere aggiunto in ```turtlebot3_descripion```.

Il modello 3D e la descrizione del robot si trovano nella cartella ```urdf```. 
Quindi esegui i seguenti comandi:
```bash
cp ./urdf/turtlebot3_burger_pi* $HOME/catkin_ws/src/turtlebot3/turtlebot3_description/urdf/.
```

## Avvio Project ##
```bash
export TURTLEBOT3_MODEL=burger_pi
```
Per avviare l'ambiente di simulazione Gazebo, viene fornito un launch file ROS. 
```bash
roslaunch unibas_ros_line_follower gazebo_project.launch
```
Per avviare l'autoguida e il riconoscimento immagini digitare in una latro terminale il comando:

```bash
roslaunch unibas_ros_line_follower start_project.launch 
```

