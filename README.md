# Enterprise Project

A fully autonomous robot which moves around on it's own based on the surroundings.

    #!/usr/bin/env pybricks-micropython

    from pybricks import ev3brick as brick
    from pybricks.ev3devices import (Motor, TouchSensor, ColorSensor,
                                 InfraredSensor, UltrasonicSensor, GyroSensor)
    from pybricks.parameters import (Port, Stop, Direction, Button, Color,
                                 SoundFile, ImageFile, Align)
    from pybricks.tools import print, wait, StopWatch
    from pybricks.robotics import DriveBase


    brick.sound.beep()

    test_motor1 = Motor(Port.C)
    test_motor2 = Motor(Port.A)
    robot = DriveBase(test_motor1, test_motor2, 35, 114)

    sensor1 = UltrasonicSensor(Port.S1)
    sensor2 = UltrasonicSensor(Port.S3)


    robot.drive(100, 0)
    while sensor1 or sensor2.distance() > 100:
       wait(10)
    robot.stop()

    brick.sound.beep(1000, 500)
