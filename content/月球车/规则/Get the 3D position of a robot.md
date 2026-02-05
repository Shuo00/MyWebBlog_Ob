There are different functions depending whether this information must be accessed in a normal controller, in a [Supervisor](https://www.cyberbotics.com/doc/reference/supervisor) controller or in a physics plugin. All the functions described below will return the 3D position in meters and expressed in the global (world) coordinate system.

Clearly, the position of a robot can also be apGproximated by using odometry or SLAM techniques. This is usually more realistic because most robots don't have a [GPS](https://www.cyberbotics.com/doc/reference/gps) and therefore have no mean of precisely determining their position. You will find more info about odometry and SLAM techniques in Cyberbotics' Robot Curriculum.

# Get Position in Controller Code

To get the position of a robot in the robot's controller code: add a [GPS](https://www.cyberbotics.com/doc/reference/gps) node to the robot, then use the wb_robot_get_device, wb_gps_enable and wb_gps_get_values functions. Note that the [GPS](https://www.cyberbotics.com/doc/reference/gps)'s resolution field must be 0 (the default), otherwise the results will be noisy. You will find more info about the [GPS](https://www.cyberbotics.com/doc/reference/gps) node and functions in the [Reference Manual](https://www.cyberbotics.com/doc/reference/gps). Note that the [GPS](https://www.cyberbotics.com/doc/reference/gps) can also be placed on a robot's part (arm, foot, etc.) to get the world/global coordinates of that particular part.

# Get Position in Supervisor Code

-   To get the 3D position of any [Transform](https://www.cyberbotics.com/doc/reference/transform) (or derived) node using the [Supervisor API](https://www.cyberbotics.com/doc/reference/supervisor): you can use the wb_supervisor_node_get_position function. Please check this function's description in the [Reference Manual](https://www.cyberbotics.com/doc/reference/supervisor).
-   To get the 3D position of any [Transform](https://www.cyberbotics.com/doc/reference/transform) (or derived) node placed at the root of the Scene Tree (the nodes visible when the Scene Tree is completely collapsed), you can use the wb_supervisor_field_get_sf_vec3f function. Here is an [example](https://www.cyberbotics.com/doc/guide/supervisor-programming#tracking-the-position-of-robots).

A simulation example that shows both the [GPS](https://www.cyberbotics.com/doc/reference/gps) and the [Supervisor](https://www.cyberbotics.com/doc/reference/supervisor) APIs techniques is included in the Webots installation, you just need to open this world: "[WEBOTS_HOME/projects/samples/devices/worlds/gps.wbt](https://github.com/cyberbotics/webots/tree/released/projects/samples/devices/worlds/gps.wbt)".

# Get Position in Physics Plugin Code

In the physics plugin you can use ODE's dBodyGetPosition function. Note that this function returns the position of the center of mass of the body: this may be different from the center of the [Solid](https://www.cyberbotics.com/doc/reference/solid). Please find a description of ODE functions [here](http://ode.org/wiki/index.php?title=Manual).