## ROS & namespace & 多机



在c++程序中，命名空间是一组描述逻辑分组的机制。例如：

```
namespace uav1{//定义
	pose p;
	....
}
uav1::p = xxx//使用using namespace uav1 可以在程序中省略命名空间名称

```

在ros中编写c++程序时命名空间。

在launch文件中，使用group标签为其中运行的节点设定命名空间

```
<group ns="uav1">
	....
</group>
```

或者在launch文件运行节点时，通过ns参数来设定节点的命名空间

```
<node pkg="publish_node" type="publish_node_A" name="fusionA" output="screen" ns="uav1">
```

在cpp文件中，有四种命名方式：

基础名称，此时话题名称输出/fly_pos

```
 ros::init(argc, argv, "gazebo_ground_truth");
 ros::NodeHandle nh;
drone_pos_pub = nh.advertise<geometry_msgs::PoseStamped>("/fly_pos", 100);
```

全局名称，此时话题名称输出/gazebo_ground_truth/fly_pos

```
 ros::init(argc, argv, "gazebo_ground_truth");
 ros::NodeHandle nh;
drone_pos_pub = nh.advertise<geometry_msgs::PoseStamped>("/gazebo_ground_truth/fly_pos", 100);
```

相对名称，此时话题名称前带默认命名空间，通过launch文件设置ns

```
 ros::init(argc, argv, "gazebo_ground_truth");
 ros::NodeHandle nh;
drone_pos_pub = nh.advertise<geometry_msgs::PoseStamped>("gazebo_ground_truth/fly_pos", 100);
```

私有名称，此时话题在节点名称的后面

```
 ros::init(argc, argv, "gazebo_ground_truth");
 ros::NodeHandle nh("~");
drone_pos_pub = nh.advertise<geometry_msgs::PoseStamped>("/gazebo_ground_truth/fly_pos", 100);
```

使用多机时，在不同的命名空间中运行对应个体的节点即可

