# Introduction

The goal of this project is to implement a controller for a 3D Quadrotor. The state is determined by nine variables. From those variables, only four are independent which are the body rates and the altitude, controlled directly by the torques and collective thrust respectively. A reasonable approach is to start tuning the controllers for those and later focus on the other degrees of fredom. The validation of the controller 

## Body Rates Controller
When implementing a controller for the quad body rates, the goal is to demonstrate that the quad rotation rate can be estabilized to zero under the effect of any rotational speed. In this case, a small rotational speed is applied to the the roll axis. This is done by tuning the gain KpPQR. As a result, the quad rates are kept to zero.

### Roll/Pitch Controller
Then, the next step is to control the vehicle angle. This is done by tuning the parameter kpBank.


## Lateral Position Controller


## Non-idealities and robustness
