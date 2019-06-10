# Introduction

The goal of this project is to implement a controller for a 3D quadrotor. In this case, we want control over the position in X, Y, Z and yaw so we can move the quad anywhere in the space. The collective thrust is the immediate control knob for Z. Any desired motion in X and Y has to be linked to a vehicle attitude controller. This leads to a cascaded control structure for the attitude controller which includes a roll/pitch controller and a body rates controller. Since yaw is a byproduct of the reactive moment in Z, its controller can be treated outside of the attitude controller. A reasonable approach is to tune the controllers starting from the inner loops first. The next sections explains details of implementation.

## Body Rates Controller
The body rate controller is at the core of the attitude controller. Any desired attitude is controlled by commanding body rates to the vehicle. Ultimately, these body rate commands set the torques. This is a first order system that is going to be implemented using a P-controller. The following equation shows this:

The simulator applies a small rotational speed on the roll axis of the vehicle and the goal is to demonstrate that the quad body rates can be estabilized to zero. The key is to adjust kpPQR so we can achieve a short rising time and avoid overshooting at most.

## Roll/Pitch Controller
The next controller is for the roll and pitch angles. Unlike the body rates controller, the control knobs for this controller are more complex. This controller takes the desired acceleration at x and y as inputs and outputs pitch and roll rates command that are passed to the body rate controller. The equation to get body rate commands is...

This is a P-controller in which we aim to have a short settling time along with a little oscillation. The parameter kpBank is set to...


## Position Controller and Yaw Control
Position includes altitude and lateral. Altitude control involves the application of thrust to reach desired position in z. The equation for finding z is...

Lateral position control is achieved by using the knobs...

## Non-idealities and robustness
In this validation scenario, the goal is to show that the controllers respond to the following non ideal conditions:
- When the center of mass is shifted
- When the vehicle is heavier than expected

## Tracking trajectories
