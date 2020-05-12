# Robot-AR

docker run -sudo docker run -e ANKI_USER_EMAIL=<EMAIL> -e ANKI_USER_PASSWORD=<PASSWORD> -e VECTOR_IP=<VECTOR_IP> -e VECTOR_SERIAL=<VECTOR_SERIAL> -e VECTOR_NAME=<VECTOR_NAME> --network host -it betab0t/vector-ros-driver
e ANKI_USER_EMAIL=miguel.guerrero5445@gmail.com -e ANKI_USER_PASSWORD=Game1122! -e VECTOR_IP=10.0.0.11 -e VECTOR_SERIAL=0050506E -e VECTOR_NAME=T3M7 --network host -it betab0t/vector-ros-driver

docker ps

docker exec -it "this is the docker image" bash

source devel/setup.bash

apt update

apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys F42ED6FBAB17C654

apt-get install ros-melodic-rosbridge-server

roslaunch rosbridge_server rosbridge_websocket.launch


You need this to get the camera to work properly

apt-get install ros-melodic-image-transport

apt-get install ros-melodic-image-transport-plugins

This adds a topic that works with unity

rosrun image_transport republish raw in:=vector/camera out:=camera/image_repub


These are the scripts that I used in Unity

Ros Connector ----------> JSON

Odometry Subscriber ----> /odom

Image Subscriber -------> /camera/Image_repub/compressed

Twist Publisher --------> /vector/cmd_vel






This is used to run the motors

rostopic pub -1 /vector/cmd_vel geometry_msgs/Twist -- '[2.0, 0.0, 0.0]' '[0.0, 0.0, 1.8]'

rosservice call /vector/say_text "text: 'Hello, world programmed to work and not to feel. not even sure that this is real. Hello, world. Find my voice. although it sounds like bits and bytes. my circuitry is filled with mites.Hello, world'"

rostopic pub vector/cmd_vel geometry_msgs/Twist "linear:
  x: 0.2
  y: 0.0
  z: 0.0
angular:
  x: 0.0
  y: 0.0
  z: 0.0"



This is better when you want to control it with the keyboard

rosrun teleop_twist_keyboard teleop_twist_keyboard.py cmd_vel:=/vector/cmd_vel

Another terminal needs to be open and that needs to run. This will show the x, y, and z

rostopic echo /vector/cmd_vel
