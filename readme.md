# Introduction

The goal of this project is to implement a controller for a 3D quadrotor. Ultimately, we want control over the position in X, Y, Z and yaw so we can move the quad anywhere in the space. The collective thrust is the immediate control knob for Z. Any desired motion in X and Y has to be linked to an attitude controller of the vehicle. This leads to a cascaded control structure for the attitude controller which includes a roll/pitch controller and a body rates controller. Since yaw is a byproduct of the reactive moment in Z, its controller can be treated outside of the attitude controller. A reasonable approach is to tune the controllers starting from the inner loops first. The next sections explains details of implementation.

## Body Rates Controller
The body rate controller is at the core of the attitude controller. It takes p, q, r commands and produces the required rotational moments in X, Y, Z. This is a first order system that is going to be implemented using a P-controller. The following equation shows this:

The simulator applies a small rotational speed on the roll axis of the vehicle and the goal is to demonstrate that the quad body rates can be estabilized to zero. The key is to adjust kpPQR so we can achieve a short rising time and avoid overshooting at most.

## Roll/Pitch Controller
Unlike the body rates controller, the control knobs for this controller are more complex. This controller takes the desired acceleration at x and y as inputs and passes pitch and roll rates commands to the body rate controller. The equation to get body rate commands is...

This is a P-controller in which we aim to have a short settling time along with a little oscillation. The parameter kpBank is set to...


## Position Controller and Yaw Control
The role of the altitude controller is to keep the quad close the desired position and velocity in Z by setting a thrust value. The equation is

Controlling X and Y includes 

## Non-idealities and robustness
In this validation scenario, the goal is to show that the controllers respond to the following non ideal conditions:
- When the center of mass is shifted
- When the vehicle is heavier than expected

## Tracking trajectories
