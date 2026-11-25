# WALLE
MAE/ECE 148 Final Project, Team 14

Building an Autonmously Field Inspection Robot. 
Using ROS2 Jazzy Docker Image given in class. 
_________

Package will accomplish the following: 
Autonomous navigation by following predefined GPS waypoints across field
AI based detection on OAK-D camera: train model to identify upright cones, fallen cones, golf ball
Condition mapping: start with empty map; associate detections with GPS locations and update a spatial grid with numbers corresponding to object & condition
if cone obstructs planned path, record condition and return to starting point as route cannot be safely completed. 
At the end of trip, returns grid map with values correctly describing the condition of the field
_________

To do so, package will:
process image data from OAD-D Lite camera and when object of interest is detected, return a specific number. e.g.
- Upright cone: return 1
- Fallen cone: return 2
- Golf ball: return 3
Robocar starts at the corner of a square field and divide the field into grids. Initialize all grid cell value at 0. Within each grid cell that the robocar visits, it will save a number for that grid cell depending on what the camera detected. 
Robocar makes it way through all grid cells through a predetermined path. At the last grid cell, it will return a "condition map" in which all grid cells have updated values.
_________

Example of a 2x2 grid with the field divided into 4:
_________
Initial condition map:
_________
|_0_|_0_|   
|_0_|_0_|  

_________
Final condition map:
_________
|_1_|_2_|   
|_3_|_1_|
_________

Where upright cone is detected in 2 places, 1 fallen cone is detected in top right, and a golf ball detected in bottom left.   



References: 
Package used in completing ROS laps (PID control + camera to ensure car stays to the right of center yellow line on track): docker pull ghcr.io/ucsd-silberman-classes-and-projects/ucsd_robocar:stable
YOLO AI Detection model trained on RoboFlow

