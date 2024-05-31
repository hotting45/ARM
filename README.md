# ARM
Make a robot arm to play piano 

**PLANNING **

week 1:
planing the crane on ONSHAPE. Also figuring out were to put the motors and how to make them work.

week 2:
planing out the code and starting the ONSHAPE.

week 3:
starting code also wiring and polishing the ONSHAPE. Also checking with each other to make sure that we are still on time with the plan.

week 4:
Checking the wiring and making sure that it all should work if pluged into the code/doesn't break any thing.

week 5:
Making sure that everything fits on the base ONSHAPE.

week 6: 
Maybe have the ONSHAPE done and have some code put down and have some of it work.

week 7:
tune the code and make it work fully.

week 8:
have the onshape fully made and have it all cut out.

week 9:
have the code runing and maybe have it work with the onshape.

week 10:
tune the code so that it turns and stops when needed.

week11:
have the finished project.

How it will work:
The botom will turn and there will be joints that allow it to push down with two servos and the botom will turn with the steper motor.

photos:
![WIN_20240318_11_04_51_Pro](https://github.com/hotting45/ARM/assets/143732462/97e5c8e0-3081-4325-adf7-aef03e809bd5)




# Finished Project

### Description & Code Snippets 
We made a robot arm that plays the piano one key at a time.

```python
import time
import board
import pwmio
from digitalio import DigitalInOut, Direction, Pull
from adafruit_motor import servo
import asyncio
import keypad
import digitalio
from adafruit_motor import stepper

DELAY = 0.01   # Sets the delay time for in-between each step of the stepper motor.
STEPS = 100    # Sets the number of steps. 100 is half a full rotation for the motor we're using. 

# Set up the digital pins used for the four wires of the stepper motor. 
coils = (
    digitalio.DigitalInOut(board.D9),   # A1
    digitalio.DigitalInOut(board.D10),  # A2
    digitalio.DigitalInOut(board.D11),  # B1
    digitalio.DigitalInOut(board.D12),  # B2
)

# Sets each of the digital pins as an output.
for coil in coils:
    coil.direction = digitalio.Direction.OUTPUT

# Creates an instance of the stepper motor so you can send commands to it (using the Adafruit Motor library). 
motor = stepper.StepperMotor(coils[0], coils[1], coils[2], coils[3], microsteps=None)

motor.onestep()

motor.onestep(direction=stepper.BACKWARD)
motor.onestep(direction=stepper.FORWARD)

style=stepper.DOUBLE
       


# create a PWMOut object on Pin A2.
pwm = pwmio.PWMOut(board.D13, duty_cycle=2 ** 15, frequency=50)
pwm2 = pwmio.PWMOut(board.D8, duty_cycle=2 ** 15, frequency=50)

# Create a servo object, my_servo.
my_servo1 = servo.Servo(pwm)
my_servo2 = servo.Servo(pwm2)


while True:
    for step in range(STEPS):
        motor.onestep(direction=stepper.BACKWARD, style=stepper.DOUBLE)
        time.sleep(DELAY)
    
    for angle in range(0, 180, 5):  # 0 - 180 degrees, 5 degrees at a time.
        my_servo1.angle = angle
        my_servo2.angle = angle
        time.sleep(DELAY)
   
    for step in range(STEPS):
        motor.onestep(style=stepper.DOUBLE)
        time.sleep(DELAY)
    for angle in range(0, 180, 5):  # 0 - 180 degrees, 5 degrees at a time.
        my_servo1.angle = angle
        my_servo2.angle = angle
        time.sleep(DELAY)

    for step in range(STEPS):
        motor.onestep(direction=stepper.BACKWARD, style=stepper.DOUBLE)
        time.sleep(DELAY)
            
    for angle in range(0, 180, 5):  # 0 - 180 degrees, 5 degrees at a time.
        my_servo1.angle = angle
        my_servo2.angle = angle
        time.sleep(DELAY)
```

### Evidence

### ONSHAPE
![image](https://github.com/hotting45/ARM/assets/143732418/afa799de-db47-46c3-a928-b255775dd5b8)
![image](https://github.com/hotting45/ARM/assets/143732418/60fdddc6-0d54-4b6c-bc9e-897e2cd57ee1)
![image](https://github.com/hotting45/ARM/assets/143732418/48d174ab-925a-47be-b4a1-3a232fbac930)
![image](https://github.com/hotting45/ARM/assets/143732418/3efb2fbe-cbd2-4807-a1d6-47e166caa8cc)
![image](https://github.com/hotting45/ARM/assets/143732418/7bb49a5f-0308-4037-bbf1-c2fc6a4541fe)
![image](https://github.com/hotting45/ARM/assets/143732418/22b2a6a6-608b-40e8-8d85-f77785517e82)

### Wiring

![image](https://github.com/hotting45/ARM/assets/143732462/3b781aea-064f-4a27-887d-83096beacd6a)

### Problems/Miss cal
Time management wasn't done very well so we couldn't finish but we were close. Also the coding was a little hard to do at first but I learned that I should work on one peice at a time. The Onshape was going well till we relized that we had to restart because it wouldn't work. So we had to remake the whole thing rethink are plan on how to make it. Which was are down fall because we ran out of time on making it. 

### Reflection

###  Wisdom 
Work on single parts of code first to not make a mistake.

Make sure your onshape works before designing it fully.

Check wiring if your code works fine plus wiring can break a lot of things.

Make sure your bin is clean. 
















***
