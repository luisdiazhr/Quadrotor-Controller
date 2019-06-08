# Introduction

The goal of this project is to implement a controller for a 3D quadrotor. The state is determined by nine variables:

![state] (http://latex.codecogs.com/gif.latex?X%20%3D%20%5Cbegin%7Bbmatrix%7D%20x%20%26%20y%20%26%20z%20%26%20%5Cdot%7Bx%7D%20%26%20%5Cdot%7By%7D%20%26%20%5Cdot%7Bz%7D%20%26%20%5Cphi%20%26%20%5Ctheta%20%26%5Cpsi%20%26%20p%20%26%20q%20%26%20r%20%5Cend%7Bbmatrix%7D)

From those variables, only four are independent which are the body rates and the altitude, controlled directly by the torques and collective thrust respectively. A reasonable approach is to start tuning the controllers for those and later focus on the other degrees of fredom. The validation of the controller 

## Body Rates Controller
When implementing a controller for the quad body rates, the goal is to demonstrate that the quad rotation rates can be estabilized to zero under the effect of any rotational speed. The equation for the body rates is the following: 


In order to control the rates, a P-controller is chosen as the most appropiate kind of controller due to the first order nature of the variable to be controlled. The simulator applies a small rotational speed to the quad roll axis. The key in this controller to is to achieve a short rising time. One would think that the body rates must be precise since they are the independent degrees of freedom. Lateral control depends on the body rates. 

### Roll/Pitch Controller
The next step is to control the vehicle angle. This is done by tuning the parameter kpBank.


## Position Controller
Position includes altitude and lateral. Altitude control involves the application of thrust to reach desired position in z. The equation for finding z is...

Lateral position control is achieved by using the knobs...

## Non-idealities and robustness
In this validation scenario, the goal is to show that the controllers respond to the following non ideal conditions:
- When the center of mass is shifted
- When the vehicle is heavier than expected

## Tracking trajectories
