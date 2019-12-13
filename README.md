# Enterprise Project

A line following robot with a button to start or stop its programming.

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

        Tsensor = TouchSensor(Port.S1)
        Csensor = ColorSensor(Port.S2)
        Csensor.mode='COL-REFLECT'

        while not Tsensor.pressed():
            wait(10)

        while True:

        color = Csensor.color()
        print(color) 

        while color is not None and color < 5:
            wait(1)
            robot.drive(100, 0)
            color = Csensor.color()
            print(color) 

        while color is not None and color >= 5:
            wait(1)
            test_motor1.run(500)
            color = Csensor.color()
            print(color) 

        
        brick.sound.beep(1000, 500)

