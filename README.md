# Differences-between-ROS1-and-ROS2

- rospy = rclpy
- roscpp = rclcpp
- new functionality needs to be implemented with rcl library 

## Write nodes

### import rospy 
import rclpy \
from rclpy.node import Node

### write a node in ros2

- create a class which inherits the node object (python or C++)

ROS1 :

```python
def callback_number(msg) :
      ...
```

ROS2 : 

```python 
class NumberCounterNode(Node) :
      def_init_number(self,msg)
             ...
      def callback_number(self,msg)
             ...
```

## ROS2 components (doesn't exist in ROS1)

ROS1 : Nodelets (multiple nodes in 1 executable)


![Screenshot 2023-04-07 154326](https://user-images.githubusercontent.com/118521344/230668056-3770b5e9-334d-4376-a834-67c0df8d6ba9.png)


ROS2 : components = modified node class 

![Screenshot 2023-04-07 154341](https://user-images.githubusercontent.com/118521344/230668064-b6420ddf-0501-489d-96f2-01981fe8f12d.png)


## Launch files

ROS1 : <launch> files with xlm\
ROS2 : use python to write launch files (def...)

## ROS communication 

ROS1 : start a ros master before run a node 
      
      
![Screenshot 2023-04-07 151910](https://user-images.githubusercontent.com/118521344/230667812-25a9c258-f7e4-498f-96ec-05f40a0cbca6.png)


ROS2 : no ros master (each node is independent) 

![Screenshot 2023-04-07 152018](https://user-images.githubusercontent.com/118521344/230667832-b795554c-87f4-43c5-8284-5c11874e6941.png)


If there is no ros master, there are no global parameters. That means that each parameter will be specific to a node which declares and manages its own parameters (parameters are destroyed when the node is killed).

## ROS services 
ROS1 : synchronous \
ROS2 : asynchronous (option to make them synchronous)
## ROS actions
ROS1 : built o top of ros1 topic (added later)\
ROS2 : action are a part of the ros2 core functionalities

## Messages, services  and actions

ROS1 : create definitions under folder : 
- msg
- srv
- action

ROS1 compilation, no namespace added. 

ROS2 : create definitions under folder : 
- msg
- srv
- action 

After ROS2 compilation, new namespace : 
- msg/...
- srv/...
- action/...

## Build node
ROS1 : 'catkin', compile a package with 
```python
$ catkin_make
```
ROS2 : 'ament', compile a package with
```python
$ colcon build
```

## References
[https://www.youtube.com/watch?v=yn638LmVwlw](https://www.youtube.com/watch?v=yn638LmVwlw)
