---
title: Movement
weight: 5
---
*adapted from [PyBricks](https://docs.pybricks.com/en/stable/robotics.html)*

# Set up
Having to control the two motors independently to move our robot would involve a lot of maths and be annoying and prone to error.
Instead, we can use the `DriveBase` class to make driving our robot around a lot simpler.

We still need to initialize the motors:
```python
# Initialize the motors.
left_motor = Motor(Port.B)
right_motor = Motor(Port.C)
```

But then we write this to create our DriveBase:
```python
# Initialize the drive base.
robot = DriveBase(left_motor, right_motor, wheel_diameter=55.5, axle_track=104)
```

By specifying the dimensions of your robot, this class makes it easy to drive a given distance in millimeters or turn by a given number of degrees.

**Positive** distances, radii, or drive speeds mean driving **forward**. **Negative** means **backward**.

**Positive** angles and turn rates mean turning **right**. **Negative** means **left**. So when viewed from the top, positive means clockwise and negative means counterclockwise.

Parameters:
- `left_motor`, the motor that drives the left wheel.
- `right_motor`, the motor that drives the right wheel.
- `wheel_diameter`, diameter of the wheels in *millimetres* (mm).
- `axle_track`, distance between the points where both wheels touch the ground, in *millimetres* (mm).
# Driving for a given distance or by an angle
Use the following commands to drive a given distance, or turn by a given angle.
This is measured using the internal rotation sensors. Because wheels may slip while moving, the travelled distance and angle are only estimates.

{{< hint info >}}
If you initialized your robot using the line:
```python
robot = DriveBase(left_motor, right_motor, wheel_diameter=55.5, axle_track=104)
```
you will control it using:
```python
robot.straight(300)
robot.turn(-45)
```
and so on. If instead you'd written:
```python
superchamp = DriveBase(left_motor, right_motor, wheel_diameter=55.5, axle_track=104)
```
you will control it using:
```python
superchamp.straight(300)
superchamp.turn(-45)
```
and so on.
{{< /hint >}}

---
## `straight(distance)`
Drives straight for a given distance and then stops.

Parameters:
- `distance`, distance to travel in *millimetres* (mm).

---
## `turn(angle)`
Turns in place by a given angle and then stops.

Parameters:
- `angle`, angle to turn in *degrees* (&deg;).

---
## `curve(radius, angle)`
Drives an arc along a circle of a given radius, by a given angle.

Parameters:
radius (dimension: mm) – Radius of the circle.
angle (angle: deg) – Angle along the circle.

# Drive forever
## `drive(drive_speed, turn_rate)` 
Starts driving at the specified speed and turn rate. Both values are measured at the center point between the wheels of the robot. It keeps going until you use stop() or change course by using drive() again. For example, you can drive until a sensor is triggered and then stop or turn around. 

Parameters:
- `drive_speed`, speed of the robot in millimetres per second (mm/s).
- `turn_rate`, turn rate of the robot in degrees per second (&deg;/s).

---
## `stop()`
Stops the robot by letting the motors spin freely.


```python
## Example Movement Code 

# Go forward and backwards for one metre.
robot.straight(1000)
robot.straight(-1000)

# Set the drive base speed and turn rate. It keeps going until you use stop()
robot.drive(100, 0)

# Turn clockwise by 360 degrees and back again. 
robot.turn(360)
robot.turn(-360)

# stop the motor
robot.stop()

# this stops any active movement and actively brakes the motor 
# from pybricks.parameters import Port, Stop
robot.stop(Stop.BRAKE)

# this stops any active movement and leaves the motors on coast
robot.stop(Stop.COAST)

# Stops the motor and actively holds it at its current angle. Make sure you include Stop in 
# from pybricks.parameters import Port, Stop
robot.stop(Stop.HOLD)
```