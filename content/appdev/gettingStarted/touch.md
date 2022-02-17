---
title: Touch Sensor
weight: 6
---
*adapted from [PyBricks](https://docs.pybricks.com/en/stable/robotics.html)*
{{< figure src="https://pybricks.com/ev3-micropython/_images/sensor_ev3_touch.png" title="Touch Sensor" >}}

A sensor lets an EV3 program measure and collect data about is surroundings. The Touch Sensor can detect when the sensor’s red button
has been pressed or released.

# Example Code
{{< highlight python "lineNos=table,lineNoStart=1" >}}
#!/usr/bin/env pybricks-micropython
from pybricks import ev3brick as brick
from pybricks.ev3devices import (Motor, TouchSensor, ColorSensor,
InfraredSensor, UltrasonicSensor, GyroSensor)
from pybricks.parameters import (Port, Stop, Direction, Button, Color,
SoundFile, ImageFile, Align)
from pybricks.tools import print, wait, StopWatch
from pybricks.robotics import DriveBase

# Initialize Touch Sensor
touch_sensor = TouchSensor(Port.S1)

# Initialize two motors and a drive base
left = Motor(Port.B)
right = Motor(Port.C)
robot = DriveBase(left, right, 56, 114)


# Drive forward until touch sensor is pressed
robot.drive(1000, 0)
while not touch_sensor.pressed():
    wait(1)
robot.stop()


