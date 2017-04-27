# Main Board Design

## Input and Outputs

5V - Main
0V - Ground 
GPIO_Input - Controlling the 3v Motor Spinning Mirror
Motor1 - Power to Motor 3V
MotorGround - Connects to the Drain of the MOSFET

## 5V Input

Using a 680uf specified by the Lidar Sensor.  This creates a small buffer for power surges.  The Lidar sensor appears to work without it
but is seems that this is a good idea.  Followed by a 0.1uf again to filter power.  

## 3V Power

3V is supplied for the mirror motor.  Using a voltage convertor LM317 to convert from 5v to 3v.  This uses R1 and R2 to select the voltage.
R1 - 330 and R2 - 470.  With a small capacitor 1uf again to smooth output.  This is fed into a MOSFET to allow the GPIO to switch.

## MOSFET

We use a 100K resistor to ground from the gate (input) this is to keep the gate from floating.  Directly connecting the GPIO to the Gate of the mosfet.  The 3V Power from above is fed into the Motor1 output.  The Ground connects to the drain, that connects to the ground.  Across the Motor1 and MotorGround we have a diode to protect against voltage spikes from the motor.
