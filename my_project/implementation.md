---
title: Implementation
layout: default
parent: eyeBox
nav_order: 1
---


# Implementation

Eventough the steps were implemented in a whatever-came-up and i-have-time-for-this-now order, the iterations describe the design and rough implementation process. 

## Iteration 1
**Hardware**

While simultaneously working on the face detection running in python the first prototype for the project were designed and built. Initially the entire pipeline should work on an arduino uno as this would have made it possible to incorporate all four servos without a servo driver. It became eveident very quickly that face detection would not run smooth on an arduino uno, thus other options had to be explored.
![sketch](assets/first_sketch_medium.png)
While a rasberry pi would also be a viable option, a cross-device solution was chosen. 

**Facetracking**

Facetracking worked on single images and only if the user smiled in an exaggerated manner. Processing of one Face and printing the coordinates to the console took more than one second and the delay only added up. Different options have to be explored yet.

## Iteration 2
**Hardware**

The switch to the ESP32 feather board allowed for remote control of the servos which was tested with a small webpage hosted on the esp32 where the user could manually rotate the motor. Alongside this step, also a pca driver board was acquired to enable the control of up to 16 servos. Additionally, the design process for the mechanics began. A very crude one eyed version was 3D printed and the movement tested. The controls were really fragile and the eye cracked in the process of moving the upper lid with the servo. A more stable eye, lid and servo mount was needed.

**Facetracking**

Facetracking is more stable and can detect all Faces on a video stream in almost realtime. The time and coordinates were written to a file and the coordinates mapped from 0 to 180 degrees. In a simple script for the esp, with this data an 'animation' was reated to test the movement of the eye. The framerate was too quick and the motors could not react quick enough to big changes and just started quivering and breaking the joints of the eye. In order to allow for quicker exchange of parts, the eye was seprataed from the connector and can now be 'clicked' on a moint. In case of a joint break, only the joint has to be reprinted. 

## Iteration 3

**Facetracking**

The update rate was slowed down for sending data to the client. In the same python script a connection to a yet non-existant server was *theoretically* established and the detected face converted to x and y coordinates within the captured image.
