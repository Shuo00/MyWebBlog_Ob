wb_supervisor_node_get_position
wb_supervisor_node_get_orientation
wb_supervisor_node_get_pose
wb_supervisor_node_enable_pose_tracking
wb_supervisor_node_disable_pose_tracking
CC++PythonJavaMATLABROS
#include <webots/supervisor.h>

const double *wb_supervisor_node_get_position(WbNodeRef node);
const double *wb_supervisor_node_get_orientation(WbNodeRef node);
const double *wb_supervisor_node_get_pose(WbNodeRef node, WbNodeRef from_node);
void wb_supervisor_node_enable_pose_tracking(WbNodeRef node, int sampling_period, WbNodeRef from_node);
void wb_supervisor_node_disable_pose_tracking(WbNodeRef node, WbNodeRef from_node);
Description
get the global (world) position/orientation of a node

The wb_supervisor_node_get_position function returns the position of a node expressed in the global (world) coordinate system. The node argument must be a Transform node (or a derived node), otherwise the function will print a warning message and return 3 NaN (Not a Number) values. This function returns a vector containing exactly 3 values.

The wb_supervisor_node_get_orientation function returns a matrix that represents the rotation of the node in the global (world) coordinate system. The node argument must be a Transform node (or a derived node), otherwise the function will print a warning message and return 9 NaN (Not a Number) values. This function returns a matrix containing exactly 9 values that shall be interpreted as a 3 x 3 orthogonal rotation matrix:

[ R[0] R[1] R[2] ]
[ R[3] R[4] R[5] ]
[ R[6] R[7] R[8] ]
Each column of the matrix represents where each of the three main axes (x, y and z) is pointing in the node's coordinate system. The columns (and the rows) of the matrix are pairwise orthogonal unit vectors (i.e., they form an orthonormal basis). Because the matrix is orthogonal, its transpose is also its inverse. So by transposing the matrix you can get the inverse rotation. Please find more info here.

By multiplying the rotation matrix on the right with a vector and then adding the position vector you can express the coordinates of a point in the global (world) coordinate system knowing its coordinates in a local (node) coordinate system. For example:

p' = R * p + T
Where p is a point whose coordinates are given with respect to the local coordinate system of a node, R the rotation matrix returned by the wb_supervisor_node_get_orientation function, T is the position returned by the wb_supervisor_node_get_position function and p' represents the same point but this time with coordinates expressed in the global (world) coordinate system.

The wb_supervisor_node_get_pose function returns an array of 16 values. The array shall be interpreted as a 4 x 4 transformation matrix that represents an absolute transform of the node. The function returns the relative pose of the node with respect to the node specified in from_node. If from_node is null, it returns the absolute pose of the node in the global coordinate system. The resulting matrix looks as following:

[ M[0] = R[0,0]    M[1] = R[0,1]    M[2] = R[0,2]     M[3] = T[0] ]
[ M[4] = R[1,0]    M[5] = R[1,1]    M[6] = R[1,2]     M[7] = T[1] ]
[ M[8] = R[2,0]    M[9] = R[2,1]    M[10] = R[2,2]    M[11] = T[2]]
[ M[12] = 0        M[13] = 0        M[14] = 0         M[15] = 1   ]
Where M[i] is the result of the wb_supervisor_node_get_pose function at index i. The matrix is composed of a rotation matrix R and a translation vector T.

The wb_supervisor_node_enable_pose_tracking function forces Webots to stream poses to the controller. It improves the performance as the controller by default uses a request-response pattern to get pose data. The sampling_period argument determines how often the pose data should be sent to the controller.

The wb_supervisor_node_disable_pose_tracking function disables pose data tracking.

The "WEBOTS_HOME/projects/robots/neuronics/ipr/worlds/ipr_cube.wbt" simulation shows how to use these functions to achieve this (see the controller).

Note: The returned pointers are valid during one time step only as memory will be deallocated at the next time step.