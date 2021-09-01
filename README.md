**multi_robot**

**Depends on the Turtlebot3 package, you can install following this tutorial:**
https://emanual.robotis.com/docs/en/platform/turtlebot3/quick-start/#install-dependent-ros-packages

**Launch multiple robots**
```
$ roslaunch multi_robot main.launch
```

**Run teleoperation node**
```
$ rosrun teleop_twist_keyboard teleop_twist_keyboard.py /cmd_vel:=robot1/cmd_vel
$ rosrun teleop_twist_keyboard teleop_twist_keyboard.py /cmd_vel:=robot2/cmd_vel
```

**Launch slam gmapping for each robot**
```
$ ROS_NAMESPACE=robot1 roslaunch turtlebot3_slam turtlebot3_gmapping.launch set_base_frame:=robot1/base_footprint set_odom_frame:=robot1/odom set_map_frame:=robot1/map
$ ROS_NAMESPACE=robot2 roslaunch turtlebot3_slam turtlebot3_gmapping.launch set_base_frame:=robot2/base_footprint set_odom_frame:=robot2/odom set_map_frame:=robot2/map
```

**Merge map data**
```
$ roslaunch multi_robot multi_map_merge.launch
```

**Launch rviz**
```
$ rosrun rviz rviz -d `rospack find multi_robot`/rviz/multi_robot_slam.rviz
```

**Launch navigation system**
```
$ roslaunch multi_robot navigation.launch
```

**Run rviz navigation**
```
$ rosrun rviz rviz -d `rospack find multi_robot`/rviz/multi_robot_navigation.rviz
```

**Launch multi_map_merge again to update map**
```
$ roslaunch multi_robot multi_map_merge.launch
```

**Save map**
```
$ rosrun map_server map_saver -f ~/map
```
