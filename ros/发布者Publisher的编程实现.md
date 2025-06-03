### 导入 Twist 消息类型
```python
from geometry_msgs.msg import Twist
```
Twist 用于表示速度指令，常用于控制小车、机器人或乌龟的运动，例如通过 /cmd_vel 话题。

### python 代码实现
```python
#!/usr/bin/env python3

import rospy
from geometry_msgs.msg import Twist

def velocity_publisher():
    # 初始化节点
    rospy.init_node('vliocity_publisher', anonymous=True)
    # 
    turtle_vel_pub = rospy.Publisher('/turtle1/cmd_vel', Twist, queue_size = 10)
    rate = rospy.Rate(10)
    while not rospy.is_shutdown():
        vel_msg = Twist()
        vel_msg.linear.x = 0.5
        vel_msg.angular.z = 0.2
        turtle_vel_pub.publish(vel_msg)
        rospy.loginfo("Publish turtle velocity command[%0.2f m/s, %0.2f rad/s]", vel_msg.linear.x, vel_msg.angular.z)
        rate.sleep()
if __name__ == '__main__':
    try:
        velocity_publisher()
    except rospy.ROSInterruptException:
        pass
```


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
