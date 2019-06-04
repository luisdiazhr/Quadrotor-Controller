# Introduction

The goal of this project is to implement a controller for a 3D Quadrotor. As we plan to control, a reasonable approach is to start tuning the body rates controller since they are independently controlled. The lateral position control depends on the body rates.

## Body Rate Controller
In this step the focus is on implementing a function to control the body rates p, q, r of the quad. A small rotation speed is aplied on the roll axis of simulated quad. The purpose is to estabilize the quad attitude by keeping the roll angle to zero. This is done by experimenting with the gain KpPQR.

## Roll/Pitch Controller


## Lateral Position Controller

