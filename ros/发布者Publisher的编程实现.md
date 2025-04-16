创建工作空间
创建功能包
```
cd ~/catkin_ws/src
catkin_create_pkg learning_topic roscpp rospy std_msgs geometry_msgs turtlesim 
```
创建发布者代码
> 实现发布者
> 1、初始化ros节点
> 2、向ROS Master注册节点信息，包括发布的话题名和话题中的消息类型
> 3、创建消息数据
> 4、按照一定频率循环发布信息

配置发布者代码编译规则
> 配置CMakeLists.txxt的编译规则
> 1、设置需要编译的代码和生成的可执行文件
> 2、设置链接库
> ```
> add_executable(velocity_publisher src/velocity_publisher.cpp)
> target_link_libraries(velocity_publisher ${catkin_LIBRARIES})
> ```

编译并运行发布者
```
cd ~/catkin_ws
catkin_make
source devel/setup.bash
roscore
rosrun turtlesim turtlesim_node
rosrun learning_topic velocity_publisher
```
