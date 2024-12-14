from gpiozero import OutputDevice
from time import sleep

# Pin Definitions
IN1 = OutputDevice(14)
IN2 = OutputDevice(15)
IN3 = OutputDevice(18)
IN4 = OutputDevice(23)

# Define step sequence for the motor
step_sequence = [
    [1, 0, 0, 0],
    [1, 1, 0, 0],
    [0, 1, 0, 0],
    [0, 1, 1, 0],
    [0, 0, 1, 0],
    [0, 0, 1, 1],
    [0, 0, 0, 1],
    [1, 0, 0, 1]
]

def set_step(w1, w2, w3, w4):
    IN1.value = w1
    IN2.value = w2
    IN3.value = w3
    IN4.value = w4

def step_motor(steps, direction=1, delay=0.01):
    for _ in range(steps):
        for step in (step_sequence if direction > 0 else reversed(step_sequence)):
            set_step(*step)
            sleep(delay)

try:
    while True:
        steps = int(input("Enter number of steps (e.g., 2048 for one full revolution): "))
        direction = int(input("Enter direction (1 for forward, -1 for backward): "))
        step_motor(steps, direction)
except KeyboardInterrupt:
    print("Program stopped by user")
