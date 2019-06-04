# Introduction

The goal of this project is to implement a controller for a 3D Quadrotor. The state is determined by nine variables. From those variables, only four are independent which are the body rates and the altitude, controlled directly by the torques and collective thrust respectively. A reasonable approach is to start tuning the controllers for those and later focus on the other degrees of fredom. The validation of the controller 

## Body Rates Controller
When implementing a controller for the quad body rates, the goal is to demonstrate that the quad rotation rates can be estabilized to zero under the effect of any rotational speed. The equation for the body rates is the following: 


In order to control the rates, a P-controller is chosen as the best kind of controller.
In order to validate how efficient the controller is, the simulator applies a small rotational speed to the quad roll axis. After a small shooting time, the controller estabilizes the quad rates to zero.

### Roll/Pitch Controller
The next step is to control the vehicle angle. This is done by tuning the parameter kpBank.


## Position Controller
Position includes altitude and lateral. Altitude control involves the application of thrust to reach desired position in z. The equation for finding z is...

Lateral position control is achieved by using the knobs...

## Non-idealities and robustness
