---
title: Color Sensor
weight: 8
---
*adapted from [PyBricks](https://docs.pybricks.com/en/stable/robotics.html)*
{{< figure src="https://pybricks.com/ev3-micropython/_images/sensor_ev3_color.png" title="Color Sensor" >}}

{{< hint info >}}
In almost all programming, American spellings are used. So as programmers we use **colors**, even though we would normally spell the word **colours**.
{{< /hint >}}

A sensor lets an EV3 program measure and collect data about is surroundings. The Color Sensor can detect color and reflected light.

Three modes: **Color**, **Reflected Light** intensity and **Ambient Light** intensity.

– **Color Mode**: Recognizes 7 colors (black, brown, blue, green, yellow, red, white) and No Color

– **Reflected Light**: Measures the intensity of the light reflected back from a lamp that emits a red light. (0=very dark and 100=very light)

– **Ambient Light**: Measures the strength of the light that enters the sensor from the environment. (0=very dark and 100=very light)

## Example Code
{{< highlight python "lineNos=table,lineNoStart=1" >}}
#!/usr/bin/env pybricks-micropython
from pybricks.hubs import EV3Brick
from pybricks.ev3devices import Motor
from pybricks.parameters import Port, Stop
from pybricks.robotics import DriveBase
from pybricks.tools import wait
from pybricks.ev3devices import (Motor, TouchSensor, ColorSensor, InfraredSensor, UltrasonicSensor, GyroSensor)

# Initialize the EV3 Brick.
ev3 = EV3Brick()

# Initialize the motors.
left_motor = Motor(Port.B)
right_motor = Motor(Port.C)

# Initialize the drive base.
robot = DriveBase(left_motor, right_motor, wheel_diameter=55.5, axle_track=104)

{{< /highlight >}}

Here we initialize what sensors we would like by telling the EV3 what port it is plugged into and what we would like to call it when referring to it in our code.
{{< highlight python "lineNos=table,lineNoStart=18,hl_lines=2" >}}
# Initialize the sensors.
line_sensor = ColorSensor(Port.S1)

# Go forward while reflected light is less than 10.
ev3.speaker.beep()
robot.drive(100,0)
while line_sensor.reflection() < 10:
    wait(10)
robot.stop()
{{< /highlight >}}