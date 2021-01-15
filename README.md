# sl_robot
 一个 基于gezabo的机器人仿真，用于演示和参考，目前适用包括以下几个模式，使用gmapping测试建图，使用amcl+gmapping(蒙特卡洛)建图导航，使用move_base+gmapping建图导航，使用move_base+gmapping自适应导航，以及一个真实的机器人搭建的源码

1.在home目录中克隆后，在/sl_robot/下使用 catkin_make 编译即可
（在安装ros使使用sudo apt-get install ros-kinetic-desktop-full安装ros的所有安装包，否则要单独安装其他安装包）

2.演示模式：
（1）单独启动gmapping演示
  roslaunch mbot_gazebo mbot_laser_nav_gazebo.launch
  roslaunch mbot_navigation gmapping_demo.launch
  roslaunch mbot_teleop mbot_teleop.launch 
  注：克隆后,python文件要手动将其属性设置成可执行,下同
  
  (2) 使用已有地图演示amcl（蒙特卡洛导航框架）
   roslaunch mbot_gazebo mbot_laser_nav_gazebo.launch
   roslaunch mbot_navigation nav_cloister_demo.launch

  (3) 使用gmapping 和 move_base 导航框架实现一边建图，一边导航
  roslaunch mbot_gazebo mbot_laser_nav_gazebo.launch
  roslaunch mbot_navigation exploring_slam_demo.launch

  (4) 使用gmapping 和move_base 导航框架自己自主建图
  roslaunch mbot_gazebo mbot_laser_nav_gazebo.launch
  roslaunch mbot_navigation exploring_slam_demo.launch
  rosrun mbot_navigation exploring_slam.py

  (5)真实机器人参考启动
  roslaunch mbot_bringup mbot_with_laser.launch(机器人端)
  roslaunch mbot_navigation gmapping_demo.launch(PC端)
  roslaunch mbot_teleop mbot_teleop.launch (PC端)

注意：ros工程文件必须在全英文目录下才能运行成功
删除src目录下的CMmakeLists.txt,再使用caktin_make,编译。
