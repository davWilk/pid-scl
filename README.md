# pid-scl

## Table of Contents
* [General Info](#general-info)
* [Technologies](#technologies)
* [Usage](#usage)

## General Info
This repo contains the SCL files I developed for use within Factory IO, specifically for controlling tank level.

The function_blocks subdirectory houses various files used in conjunction with each other.
- PI_Block.scl [FB] - This is a PI controller, which takes a Real input signal and outputs a Real.
                     	Also accepts a Boolean Reset flag which resets integral error summation.
- Hysteresis.scl [FB] - Passes input signal only if change between current and previous signal state are significant, as described by the UpperPct and LowerPct inputs.
                       This must be embedded in a Function Block to allow for self-encapsulating Hysteresis operation (previous state must be saved as static var).
- Saturate.scl [FC] - Passes input signal only if signal value is between upper and lower thresholds, else saturates the signal at corresponding threshold value.
  
## Technologies 
This SCL code is to be used within a Siemens TIA Portal Project.

## Usage
The PI Controller block can be used in main, however this does not guarantee a fixed sample rate.
</br>
Using the PI block in a Cyclic Interrupt Program Block overcomes this issue.


![Embedding blocks within a Cyclic Interrupt](/imgs/CyclicInterrupt.PNG?raw=true)

Here is the Main Cycle for my TIA Portal Project:

![Main Cycle](/imgs/Main.PNG?raw=true)
