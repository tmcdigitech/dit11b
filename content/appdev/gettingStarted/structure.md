---
title: Structure of program
weight: 4
---
For obscure, historical reasons, the first line must look **exactly** like this.
If it doesn't, your program won't work at all.
Accidentally adding a blank line above or a space before is a common reason your code will break.

{{< highlight python "lineNos=table,lineNoStart=1" >}}
#!/usr/bin/env pybricks-micropython 

{{< /highlight >}}

The next lines are some explanatory text about what the program in this file does.
It is a good habit to do this in Python, but your program will work if you don't.

{{< highlight python "lineNos=table,lineNoStart=3" >}}
""" 
Example LEGO® MINDSTORMS® EV3 Robot Educator Driving Base Program 
----------------------------------------------------------------- 

This program requires LEGO® EV3 MicroPython v2.0. 
Download: https://education.lego.com/en-us/support/mindstorms-ev3/python-for-ev3 

Building instructions can be found at: 
https://education.lego.com/en-us/support/mindstorms-ev3/building-instructions#robot 
""" 

{{< /highlight >}}

Now we need to import some extra code from the library, so that the computer knows
how to drive the various parts of the EV3. Libraries are collections of useful code
which are used by lots of different people, but not all the time.

{{< highlight python "lineNos=table,lineNoStart=14" >}}
from pybricks.hubs import EV3Brick 
from pybricks.ev3devices import Motor 
from pybricks.parameters import Port, Stop
from pybricks.robotics import DriveBase 
from pybricks.tools import wait 
from pybricks.ev3devices import (Motor, TouchSensor, ColorSensor, InfraredSensor, UltrasonicSensor, GyroSensor) 

{{< /highlight >}}

We need to tell the computer that we're using an EV3 brick (which might seem a bit weird, since the computer is
itself trapped in an EV3 brick, but never mind), and what we've connected to it.

If this part differs from what you've actually wired up, your code won't work.

{{< highlight python "lineNos=table,lineNoStart=21" >}}
# Initialize the EV3 Brick. 
ev3 = EV3Brick() 

# Initialize the motors. 
left_motor = Motor(Port.B) 
right_motor = Motor(Port.C) 

# Initialize the Touch Sensor. 
touch_sensor = TouchSensor(Port.S1) 

# Initialize the Colour Sensor. 
color_sensor = ColorSensor(Port.S3) 

# Initialize the ultrasonic sensor.  
ultrasonic_sensor = UltrasonicSensor(Port.S4) 

{{< /highlight >}}

`DriveBase` is a handy addition which allows us to drive two motors as though they were a car.
We need to tell the computer:
- which motor is the **left** motor,
- which motor is the **right** motor,
- what the **diameter of the wheels** is, so it can work out how many
times to turn the wheels to go a given distance,
- what the **track** (the distance between the wheels) is, so it can work out how far to turn
the wheels to rotate the robot a given angle.

{{< highlight python "linenos=table,lineNoStart=37" >}}
# Initialize the drive base. 
robot = DriveBase(left_motor, right_motor, wheel_diameter=55.5, axle_track=104)

{{< /highlight >}}

The robot is now set up and ready to go. You can add your code to the bottom of the file.

{{< highlight python "linenos=table,lineNoStart=40" >}}
# Write your program here.
{{< /highlight >}}

### Complete program

Finally, here is the complete code, to make copying it easier:

{{< highlight python "linenos=table" >}}
#!/usr/bin/env pybricks-micropython 

""" 
Example LEGO® MINDSTORMS® EV3 Robot Educator Driving Base Program 
----------------------------------------------------------------- 

This program requires LEGO® EV3 MicroPython v2.0. 
Download: https://education.lego.com/en-us/support/mindstorms-ev3/python-for-ev3 

Building instructions can be found at: 
https://education.lego.com/en-us/support/mindstorms-ev3/building-instructions#robot 
""" 

from pybricks.hubs import EV3Brick 
from pybricks.ev3devices import Motor 
from pybricks.parameters import Port 
from pybricks.robotics import DriveBase 
from pybricks.tools import wait 
from pybricks.ev3devices import (Motor, TouchSensor, ColorSensor, InfraredSensor, UltrasonicSensor, GyroSensor) 

# Initialize the EV3 Brick. 
ev3 = EV3Brick() 

# Initialize the motors. 
left_motor = Motor(Port.B) 
right_motor = Motor(Port.C) 

# Initialize the Touch Sensor. 
touch_sensor = TouchSensor(Port.S1) 

# Initialize the Colour Sensor. 
color_sensor = ColorSensor(Port.S3) 

# Initialize the ultrasonic sensor.  
ultrasonic_sensor = UltrasonicSensor(Port.S4) 

# Initialize the drive base. 
robot = DriveBase(left_motor, right_motor, wheel_diameter=55.5, axle_track=104)

# Write your program here.
{{< /highlight >}}
