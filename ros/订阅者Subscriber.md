1、实现一个订阅者
> 1、初始化ROS节点；
> 
> 2、订阅需要的话题
> 
> 3、循环等待话题信息，接收到消息后进入回调函数
> 
> 4、在回调函数中完成消息处理

2、配置订阅者代码编译规则
在功能包的CMakeLists.txt文件配置
```
add_executable(pose_subscriber src/pose_subscriber.cpp)
target_link_libraries(pose_subscriber ${catkin_LIBRARIES})
```

3、编译并运行订阅者（cpp）

在功能包的src下写c++源码
```
$ cd ~/catkin_ws/
$ catkin_make
$ source devel/setup.bash
$ roscore
$ rosrun turtlesim turtlesim_node
$ rosrun learning_topic pose_subscriber
```
可以一直显示位置信息

## python实现
在功能包创建scripts文件夹，把py代码拷贝到这个文件夹下

直接运行python程序
```
rosrun learning_topic pose_subscriber.py
```
如果报错
```
ImportError: No module named yaml
```

可能是因为你安装的是ROS Noetic 默认是基于 Python3

建议检查 shebang 行（建议修正）
你的脚本现在是：
```python
#!/usr/bin/env python
```
建议修改为：

```python
#!/usr/bin/env python3
```



