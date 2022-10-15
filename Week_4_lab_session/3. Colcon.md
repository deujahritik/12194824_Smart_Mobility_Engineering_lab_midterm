# ROS2 COLCON
## Using Colcon to build packages
*The ROS build tools colcon is an iteration of include catkin make, catkin make isolated, catkin tools, and ament tools.*
## Prerequisites
## 1.Install colcon
```
sudo apt install python3-colcon-common-extensions
```
![image](https://user-images.githubusercontent.com/92029196/195608151-0d3ce969-c8a4-4723-8ead-6e61c258d57d.png)


## 2.Install ROS 2
*Make a directory called ros2 ws to house our workspace first:*

```
mkdir -p ~/ros2_ws/src
cd ~/ros2_ws
```
<img width="333" alt="Screenshot_1" src="https://user-images.githubusercontent.com/92029196/195607847-66530ed9-221b-4a70-9be9-7d9e912dbd0e.png">


*I modified ros2_ws to ros2_ws1 because I had built a workspace and package with a directory named ros2_ws.*

*Currently, the workspace only has the empty directory src:*

```
.
└── src

1 directory, 0 files
```
## 3.Add some sources
*Let's clone the examples repository and place it in the workspace's src directory:*

```
git clone https://github.com/ros2/examples src/examples -b foxy
```

*The source code for the ROS 2 examples should now be in the workspace:*

<img width="358" alt="Screenshot_2" src="https://user-images.githubusercontent.com/92029196/195607738-51d32a1a-eb1f-42a8-977b-ef6bbc0c6d07.png">

```
.
└── src
    └── examples
        ├── CONTRIBUTING.md
        ├── LICENSE
        ├── rclcpp
        ├── rclpy
        └── README.md

4 directories, 3 files
```
## 4.Build the workspace
```
colcon build --symlink-install
```

<img width="355" alt="Screenshot_3" src="https://user-images.githubusercontent.com/92029196/195607627-0a54e5be-0562-490f-b743-4382e4dc5d0a.png">


*After the build is finished, we should see the build, install, and log directories:*

```
.
├── build
├── install
├── log
└── src

4 directories, 0 files
```
## 5.Run tests
*Run the following tests to run the packages we just built:*
```
colcon test
```
<img width="303" alt="Screenshot_4" src="https://user-images.githubusercontent.com/92029196/195607540-635be7f3-c1a4-430c-a298-bd94bbb60b4e.png">

## Try a demo
*Excutables created by Colcon can be run using the environment supplied. Run a subscriber node using the following examples:*

```
ros2 run examples_rclcpp_minimal_subscriber subscriber_member_function
```
<img width="425" alt="Screenshot_5" src="https://user-images.githubusercontent.com/92029196/195610207-45e0cc00-7acd-405c-a042-cae6e959852c.png">

*Let's launch a publisher node in a different terminal (remember to source the setup script):*
```
ros2 run examples_rclcpp_minimal_publisher publisher_member_function
```
![image](https://user-images.githubusercontent.com/92029196/195612035-74ec4912-218c-4197-bf9b-1cf8420cb515.png)

# Create your own package
## 1.Setup colcon_cd

```
echo "source /usr/share/colcon_cd/function/colcon_cd.sh" >> ~/.bashrc
echo "export _colcon_cd_root=/opt/ros/foxy/" >> ~/.bashrc
```
## 2.Setup colcon tab completion

```
echo "source /usr/share/colcon_argcomplete/hook/colcon-argcomplete.bash" >> ~/.bashrc
```

