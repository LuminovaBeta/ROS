## 一、客户端Client
```python
#!/usr/bin/env python3

import sys
import rospy
from turtlesim.srv import Spawn

def turtle_spawn():
    # ROS节点初始化
    rospy.init_node('turtle_spawn')

    rospy.wait_for_service('/spawn')
    try:
        add_turtle = rospy.ServiceProxy('/spawn', Spawn)
        response = add_turtle(2.0, 2.0, 0.0, "turtle2")
        return response.name

    except rospy.ServiceException as e:
        print ("service call failed: %s"%e)


if __name__ == '__main__':
    print ("Spawn turtle successfully [name:%s]" %(turtle_spawn()))
```

## 二、
### 
```python
from std_srvs.srv import Trigger, TriggerResponse
```
从 ROS 的 std_srvs 包中导入 Trigger 服务类型，以及它的响应类型 TriggerResponse。
Trigger 是一个标准服务类型，没有请求参数，只返回一个布尔结果和字符串消息








