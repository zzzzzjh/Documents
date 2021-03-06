

# Brief introduction

It includes several realizations of simulation/experience of the drone swarm.

## 1. General prerequisites

- Test environment: Ubuntu 18.04, ROS Melodic.
- Simulator: Gazebo
- Visualization tool: Rviz

## 2. Build on ROS

```
    cd ~/catkin_ws/src
    //necessary packages
    git clone https://github.com/zzzzzjh/drone_msg.git
    git clone https://github.com/zzzzzjh/pf_swarm.git
    
    //optional packages
    git clone https://github.com/zzzzzjh/drone_swarm.git
    git clone https://github.com/zzzzzjh/fake_drone_swarm.git
    
    //external localizetion packages
    git clone https://github.com/ros-drivers/vrpn_client_ros.git
    git clone https://github.com/nooploop-dev/nlink_parser.git
    
    //socket package
    git clone https://github.com/zzzzzjh/mavlink_socket.git
    cd ../
    catkin_make
    source ~/catkin_ws/devel/setup.bash
```

## 3. Design

- ##### drone_msg 包（[repo](https://github.com/zzzzzjh/drone_msg)）

  包含了无人机集群所需的ROS消息文件

- ##### pf_swarm 包（[repo](https://github.com/zzzzzjh/pf_swarm)）

  对文章模型的复现和修改:

  [Vásárhelyi G, Virágh C, Somorjai G, et al. Optimized flocking of autonomous drones in confined environments[J]. Science Robotics, 2018, 3(20).](https://www.science.org/doi/10.1126/scirobotics.aat3536)

- ##### drone_swarm 包（[repo](https://github.com/zzzzzjh/drone_swarm)）

  基于ROS和PX4开发，效果如下

  避撞与队形变换

  <img src=".\vedio\222.gif" alt="222" width="300;" /><img src=".\vedio\333.gif" alt="333" width="300;" />

  

  牵制控制

  ![111](https://github.com/zzzzzjh/Documents/blob/master/vedio/111.gif)

  

  实机飞行：

  <img src=".\images\506b7ce191ec159366f11ca56db7376.png" width="300;" /><img src=".\images\d5b22ed8e8334c72ebd951717aa0a90.png" alt="d5b22ed8e8334c72ebd951717aa0a90" width="300;" />

- ##### fake_drone_swarm 包（[repo](https://github.com/zzzzzjh/fake_drone_swarm)）

  简化了飞机的动力学模型，实现大规模集群的仿真：

  ![444](https://github.com/zzzzzjh/Documents/blob/master/vedio/444.gif)

- #####  nlink_parser包（[repo](https://github.com/nooploop-dev/nlink_parser)）   

  对nooploop公司UWB消息解析包

- ##### vrpn_client_ros 包（[repo](https://github.com/zzzzzjh/vrpn_client_ros)）

  对Optitrack光学动捕定位消息解析包

- ##### mavlink_socket 包（[repo](https://github.com/zzzzzjh/mavlink_socket)）

  与定制的Mcontroller飞控板通信的mavlink消息包
  
## 4. Todo

- ##### Mcontroller控制程序包
- ##### 室外gps/rtk定位下的集群程序
- ##### 人机交互界面程序
- ##### ....

