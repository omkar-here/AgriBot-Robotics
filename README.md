# AgriBot

![](Agribot.png)

AgriBot is one of the themes in 10th edition of [E-Yantra Robotics Competition](https://portal.e-yantra.org/) 2021-2022 , an international robotics outreach program funded by the Ministry of Education and hosted at the [Indian Institute of Technology, Bombay](https://www.iitbombay.org/)

This repository explains our approach to the tasks for the AgriBot theme. 

Our team consisting of 3 members(myself Team Leader) from the Father Conceicao Rodrigues College of Engineering,Bandra has secured an overall 12th position among 255 international teams in the theme. 

## Theme description
Commercial harvesting necessitates expert labour. The picker must swiftly identify any ripe tomatoes on a plant, select them,pick and place them into basket all at the same time. This is labour for the employees as well as bad for the farm's overall efficiency. 

The aim is to train an AgriBot for picking tomatoes from a greenhouse environment and placing them into its basket. A total of 6 incremental tasks starting from the installation to the final solution to the problem are detailed here.

## Software Specifications
We will use Gazebo simulator, a robotics simulator, where the simulated greenhouse and Agribot will dwell, the MoveIt Motion Planning Framework for controlling the Robotic Arm, and ROS for integrating the many parts of autonomy required in the solution.
### 1. [Ubuntu 20.04 LTS](https://releases.ubuntu.com/20.04/)
- Ubuntu 20.04, a Linux environment is used for running all the packages and programmes such as Gazebo 11 etc.

### 2. [ROS Noetic](http://wiki.ros.org/noetic)
- The Robot Operating System (ROS) is a set of software libraries and tools that help one build robot applications.
 **Note:** ROS is strongly version specific middleware. Thus, Ubuntu 20.04 (Focal) is used with ROS Noetic.

### 3. [Gazebo](https://gazebosim.org/home)
- Gazebo 11, a physical engine (used for simulation) is tightly integrated with ROS Noetic and so it comes pre-installed when      ```ros-noetic-desktop-full``` is installed.

### 4. [MoveIt](https://moveit.ros.org/)
- MoveIt is an open-source robotic manipulation platform that allows you to develop complex manipulation applications using ROS.
- It is a free-space motion planning framework for ROS.

### 5. [Rviz](http://wiki.ros.org/rviz/UserGuide#Move_Camera_.28Keyboard_shortcut:_m.29)
- rviz (short for “ROS visualization”) is a 3D visualization software tool for robots, sensors, and algorithms. 
- It uses sensor data to try to create an accurate depiction of what is going on in the robot’s environment..

### 6. [Python3](https://www.python.org/download/releases/3.0/)
- All the programs interfacing with ROS Noetic framework are written in Python3. 
- It comes preinstalled with ROS Noetic.


## Tasks
- <b>Task 0 - Getting familiar with ROS and Ubuntu 
- Task 1 - ROS navigation in the green house environment
- Task 2 - Getting started with Arm Manipulation (Forward kinematics)
- Task 3.1 - Detection and Extraction of tomato pose co-ordinates and broadcasting them in Rviz 
- Task 3.2 - Autonomous Detection and performing Pick and Place with Robotic Arm (Inverse Kinematics)
- Task 4 - Theme Implementation
- Task 5 - Final Theme Implementation</b>
## Flow
The competition was carried out in a step-wise manner. The whole theme implementation was divided into several subtasks and then the algorithms and techniques of individual tasks were to be skillfully merged to accomplish the Final Task. I have tried to explain our preparation,approach and implementation in each of the individual tasks properly. Its my request to read this entire repo to get the complete feel of our work. Hope its joyful!

## Task 0
The aim of this task is to get you started with installation of required software components like ROS Melodic and Gazebo. An small assignment was given to get hands-on ROS and other tools.


<img src="https://github.com/Omkar-here/Agri-Bot/blob/main/Gazebo.PNG" width="400" height="300"><img src="https://github.com/Omkar-here/Agri-Bot/blob/main/ROS%20Melodic.png" width="400" height="300">

## Task 1 - Autonomous Navigation in the GreenHouse
The aim of this task is to make the AgriBot move in the Entire GreenHouse Environment in the shortest time possible. 
A LIDAR sensor is present in the Agribot vehicle at its center. With the help of LIDAR sensor data, we programmed our Agribot to navigate properly without collisions with the troughs. We incorporated smooth turnings at endpoints to save on time.Rospy was mainly used as the programming language including other python libraries.

<!-- <img src="" width="400" height="300" style="margin-right: 30px"><img src="https://github.com/Omkar-here/Agri-Bot/blob/main/Agribot_greenhouse.png" width="400" height="300">
<p>                  AgriBot                      </p> -->
<table><th><img src="https://github.com/Omkar-here/Agri-Bot/blob/main/agribot.png" width="400" height="300" style="margin-right: 30px"></th>
    <th><img style="margin-right: 50px" src="https://github.com/Omkar-here/Agri-Bot/blob/main/Agribot_greenhouse.png" width="400" height="300px" ></th><tr>
    <td>
    AgriBot-A csv vehicle with 6-DOF Robotic Arm mounted.
</td>
  <td align='center'>
    GreenHouse Environment
</td></tr></table>
To watch our implementation:- <a href="https://youtu.be/OgofVdM-6HM">Video</a>

## Task 2- Robotic Arm Manipulation
In this task the Bot was supposed to perform pick_N_place of tomatoes in the basket.In this task we were provided with tomato poses.Hence knowing where the tomato is, wasn't a difficulty. We build the Robotic Arm for training on MoveIt Motion Planning FrameWork. As we were knowing the tomato pose coordinates, we found the values of joint angles of final orientation with the help of simulator. This approach is called as Forward Kinematics where the joint angles are provided as input. This task gave us good exposure for dealing with robotic arm.
<table><th><img src="https://github.com/Omkar-here/Agri-Bot/blob/main/Agribot_trough.png" width="350" height="250" style="margin-right: 30px"></th><th><img src="https://github.com/Omkar-here/Agri-Bot/blob/main/Picking_task_2.PNG" width="350" height="250" style="margin-right: 30px"></th>
   <tr>
    <td align='center'>
    Tomato Plant
</td>
  <td align='center'>
    End effector grabbing the tomato -(A glance from the implementation!!)
</td></tr></table>

To watch our implementation:- <a href="https://youtu.be/BIcqByAgQaM">Video</a>

## Task 3.1- Detection,Perception & broadcasting of tomato poses on Rviz
The aim of this task was to detect ripe tomatoes and broadcast its poses on Rviz. To broadcast a point in Rviz, coordinate positions are required.In our case, origin was center of Agribot.A camera is located near the end-effector from which live feed is recieved. We used OpenCv to detect ripe tomatoes and noted their pixel coordinates. To estimate the depth of tomato we used Depth image(Distance in plane parallel to the ground). We could trace the X and Y coordinates dynamically with respect to the origin with help of focal length of camera and pixel coordinates of center of tomato. Our bot was supposed to traverse around troughs and broadcast all tomatoes in Rviz.

To watch our implementation:- <a href="https://www.youtube.com/watch?v=oFbbvw6vOtk">Video</a>

<img src="https://github.com/Omkar-here/Agri-Bot/blob/main/Task3_1.png" >

## Task 3.2- Autonomous pick_N_place of tomatoes(Perception and Inverse Kinematics)
The aim of this task was to detect and pick_N_place ripe tomatoes in the basket.No collision of the robotic arm with the leaves,branches or other tomatoes was allowed.The most challenging part of this task was programming of the robotic arm.We were able to extract coordinates, and the end effector/gripper was supposed to reach till there from its initial position. We incorporated checkpoints to make sure that the gripper is exactly infront of the tomato before covering it and avoid clashing to breaking it from the stem. MoveIt Motion Planning Framework was used for visualization and training, we tried different path planning algorithms for smooth movement of the arm from initial to final state. The algorithms were able to formulate a path to the final state but these trajectories were highly complex and time consuming. Sometimes the arm would collide with the plant and other tomatoes.To overcome this, we limited the movement of joint angles only to certain degrees to avoid complex trajectories.This enabled us to perform pick and place properly.

<img src="https://github.com/Omkar-here/Agri-Bot/blob/main/Cut_minimized.gif" width="1000px" height="550px"    >

To watch our implementation:- <a href="https://youtu.be/C8fYwzjLWnY">Video</a>

## Task 4- Theme Implementation
The Task-4 was our final task in which we had to merge all the things learnt in the subtasks and accomplish the goal of bagging all the tomatoes in the shortest time possible. Initially, the orientation of the bot was getting distorted due to the inertia produced by the Robotic Arm.However, after writing the code for auto-alignment that issue was solved. We made sure that the Bot stopped before every aruco marker and analysed if the tomato infront of it is approachable or not. The pose coordinates of all tomatoes of a single plant were saved at the first detection cycle to save time on orientation and processing. After executing our code this whole task ran completely autonomous without our intervention required at any point.

<img src="https://github.com/Omkar-here/Agri-Bot/blob/main/Task%204.png" width="1000px" height="550px"  >

To watch our implementation:- <a href="https://youtu.be/0TVvBM_daSA">Video</a>

## Task 5- Final Theme Implementation
After our Final task, this was an evaluation task where a new environment in which the tomato positions were changed was given and it was asked to make the code more robust. We tried to increase the velocity of the bot.To avoid distortion due to inertia of the bot we incorporated variable velocity. A different path for navigation was chosen to increase speed and shorten the completion time. Our execution time was improved by almost 5.30 minutes compared to our previous task!!.

<img src="https://github.com/Omkar-here/Agri-Bot/blob/main/real_final.gif" width="1000px" height="550px"  >

To watch our implementation:- <a href="https://youtu.be/gyZdeAM0CXU">Video</a>

## Results :partying_face:	 
**After the Five Month Long Competition, my team was entitled to be in the Top 12 teams out of 255 teams participated <br>internationally**	:partying_face:	:raised_hands:.<br>
_My Certificate of Completion EYRC_:- <a href="https://drive.google.com/file/d/1NZF9tYL1Ba9Bu3cPE3qV5xRsI4C6IvSW/view?usp=sharing" >Certificate</a>
