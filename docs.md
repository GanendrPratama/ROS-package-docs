# 1. Launch Gazebo simulation
roslaunch hexapod_gazebo reignblaze_gazebo.launch

# 2. Launch hexapod controller
roslaunch hexapod_bringup hexapod_simple.launch

# 3. Launch keyboard control
roslaunch hexapod_bringup key_teleop.launch

2. Keyboard Controls
Basic Movement
↑: Move forward
↓: Move backward
←: Strafe left
→: Strafe right
q: Rotate left
e: Rotate right
SPACE: Stop movement
Robot State
s: Toggle stand/sit
CTRL+C: Emergency stop
Speed Control
x: Increase linear speed
z: Decrease linear speed
c: Increase angular speed
v: Decrease angular speed

# Movement speeds
MAX_METERS_PER_SEC: 0.19    # Linear speed
MAX_RADIANS_PER_SEC: 17.629 # Angular speed

# Launch RViz visualization
roslaunch hexapod_bringup rviz.launch

. Common Issues
If robot doesn't stand:

Check if state is published: rostopic echo /state
Manually publish stand command: rostopic pub /state std_msgs/Bool "data: true"
If no movement:

Verify controller node is running: rosnode list
Check topics: rostopic echo /cmd_vel
6. Safety Notes
Always start in a safe position with enough clearance
Keep finger on Space key for emergency stop
Monitor servo temperatures during extended use
Start with slow speeds when testing new movements