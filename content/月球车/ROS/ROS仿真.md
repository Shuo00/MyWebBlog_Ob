[(58条消息) ROS下的机器人建模与仿真_飞天地板流的博客-CSDN博客](https://blog.csdn.net/sinat_39528691/article/details/105560600)

---

## 1 创建工作空间及功能包

### 1.1 创建工作空间

```bash
$ mkdir -p ~/catkin_ws/src       #在home目录下创建两个文件夹/catkin_ws/src
$ cd ~/catkin_ws/src             #转移到/catkin_ws/src目录下                                
$ catkin_init_workspace          #初始化工作空间
```

### 1.2编译工作空间

```bash
$ cd ~/catkin_ws/ 	#返回/catkin_ws目录下
$ catkin_make    	#编译工作空间
```

### 1.3 设置环境变量

```bash
$ gedit ~/.bashrc       #打开home目录下的.bashrc文件
```

在.bashrc最后一行添加“source ~/catkin_ws/devel/setup.bash”  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200416161930153.png)

### 1.4 机器人模型功能包

```bash
$ cd ~/catkin_ws/src	#转移到/catkin_ws/src目录下
$ catkin_create_pkg mbot_description urdf xacro   gazebo_plugins  gazebo_ros gazebo_ros_control  roscpp  rospy    #创建“mbot_description”功能包，依赖“urdf xacro…...”
$ cd ~/catkin_ws	#返回到/catkin_ws目录下
$ catkin_make 		#编译工作空间
```

完成上述步骤后，home下会有“catkin_ws”  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200416162133713.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzM5NTI4Njkx,size_16,color_FFFFFF,t_70)

“catkin_ws”中有“build”、“devel”、“src”：  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200416162145601.png)

“src”中有“mot_description”和“CMakeLists.txt”：  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200416162229211.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzM5NTI4Njkx,size_16,color_FFFFFF,t_70)

### 1.5完善机器人描述功能包

在“mbot_description”中创建以下文件夹：“urdf”、“meshes”、“launch”、“config”  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200416162244608.png)

## 2 完成机器人的URDF模型

### 2.1创建机器人启动文件

display_mbot_base_urdf.launch  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200416162311229.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzM5NTI4Njkx,size_16,color_FFFFFF,t_70)

### 2.2 创建机器人urdf模型

#### 2.2.1机器人车体

在mbot_description/urdf下创建“mbot_base.urdf”文件，并写入以下内容  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200416162403968.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzM5NTI4Njkx,size_16,color_FFFFFF,t_70)

运行

```bash
$ roslaunch mbot_description display_mbot_base_urdf.launch
```

若RVIZ没有显示机器人模型

（1）在“Fixed Frame”下选择“base_link”

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200416162503865.png)

(2)点击“add”添加“RobotModel”  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200416162509671.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzM5NTI4Njkx,size_16,color_FFFFFF,t_70)

(3)若要观察坐标关系，还可以添加“TF”

#### 2.2.2机器人添加车轮

在mbot_description/urdf的“mbot_base.urdf”文件添加车轮相关描述代码，并运行launch文件显示  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200416162533318.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzM5NTI4Njkx,size_16,color_FFFFFF,t_70)

2.2.3机器人添加前后支撑轮

在mbot_description/urdf的“mbot_base.urdf”文件添加支撑轮相关描述代码，并运行launch文件显示  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200416162551622.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzM5NTI4Njkx,size_16,color_FFFFFF,t_70)

2.2.4机器人添加kinect传感器

在mbot_description/urdf的“mbot_base.urdf”文件添加kinect传感器相关描述代码，并运行launch文件显示，需要将课程例程的“meshes”文件夹中的kinect描述文件添加到功能包的“meshes”下。  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200416162607429.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzM5NTI4Njkx,size_16,color_FFFFFF,t_70)

2.2.5检查URDF模型的整体结构

运行  
`$ urdf_to_graphiz mbot_base.urdf`  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200416162640687.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzM5NTI4Njkx,size_16,color_FFFFFF,t_70)

## 3机器人仿真

### 3.1 创建仿真相关文件

在“mbot_description/urdf”下创建“mbot_base_gazebo.urdf”，并把“mbot_base.urdf”的内容复制到“mbot_base_gazebo.urdf”中。在“mbot_description/launch”下创建“gazebo_mbot_base_urdf.launch” 。  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200416162717812.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzM5NTI4Njkx,size_16,color_FFFFFF,t_70)

### 3.2 为机器人模型添加惯性参量和碰撞参量

车身base_link:  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200416162744129.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzM5NTI4Njkx,size_16,color_FFFFFF,t_70)

左右轮right、left_wheel_link：  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200416162754294.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzM5NTI4Njkx,size_16,color_FFFFFF,t_70)

前后支撑轮front、back_caster_link

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200416162804195.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzM5NTI4Njkx,size_16,color_FFFFFF,t_70)

### 3.3设置kinect传感器

#### 3.3.1为kinect传感器配置碰撞属性和惯性属性（可选）

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200416162831735.png)

3.3.2 新建一个虚拟link来解决坐标变换的问题  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200416162846775.png)

3.3.3插入kinect传感器插件

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200416162857632.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzM5NTI4Njkx,size_16,color_FFFFFF,t_70)

传感器插入后可运行

```bash
$ roslaunch mbot_description gazebo_mbot_base_urdf.launch
```

来查看传感器的效果，运行后，在RVIZ 的“add”中添加点云图像

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200416162929666.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzM5NTI4Njkx,size_16,color_FFFFFF,t_70)

然后在gazebo中放入任意物体

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200416162942558.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzM5NTI4Njkx,size_16,color_FFFFFF,t_70)

然后在rviz的点云信息中显示  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200416162953363.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzM5NTI4Njkx,size_16,color_FFFFFF,t_70)

3.4 添加控制器插件  
3.4.1为左右轮添加传动机构  
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020041616304578.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzM5NTI4Njkx,size_16,color_FFFFFF,t_70)

3.4.2添加差速运动控制器

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200416163059487.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzM5NTI4Njkx,size_16,color_FFFFFF,t_70)

3.4.3测试控制程序

首先，把附件的mbot_teleop功能包添加到工作空间源文件目录（~/catkin_ws/src）下,然后

```bash
$ cd ~/catkin_ws/              #返回/catkin_ws目录下
$ catkin_make		      #编译工作空间
$ roslaunch mbot_description gazebo_mbot_base_urdf.launch      #运行仿真程序
```

打开一个新的终端：

```bash
$ roslaunch mbot_teleop mbot_teleop.launch 
```

如图所示，通过键盘对应按键就能控制机器人运动

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200416163722872.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzM5NTI4Njkx,size_16,color_FFFFFF,t_70)

## 4 查看整个系统的计算图

运行$rqt_graph

可以看到整个系统的计算图，/mbot_teleop发送控制命令/cmd_vel给仿真环境/gazebo的车，/gazebo经过计算之后把坐标变换输出，而/joint_state_publisher则控制机体内部关节的坐标变换。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200416163811405.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzM5NTI4Njkx,size_16,color_FFFFFF,t_70)

