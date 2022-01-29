# PID_SCL

This repo contains the SCL files I developed for use within Factory IO, specifically for controlling tank level.

The function_blocks subdirectory houses various files used in conjunction with each other.
 PI_Block.scl [FB] - This is a PI controller, which takes a Real input signal and outputs a Real.
                     Also accepts a Boolean Reset flag which resets integral error summation.
 Hysteresis.scl [FB] - Passes input signal only if change between current and previous signal state are significant, as described by the UpperPct and LowerPct inputs.
                       This must be embedded in a Function Block to allow for self-encapsulating Hysteresis operation (previous state must be saved as static var).
 Saturate.scl [FC] - Passes input signal only if signal value is between upper and lower thresholds, else saturates the signal at corresponding threshold value.
  
 
