# What's that?

Config for linuxcnc driven machine using DigitalDream EC500 CNC controller board (based on: https://github.com/scottalford75/Remora-RT1052-cpp/tree/main/LinuxCNC/remora-ec500-DMA )

This is WORK IN PROGRESS
I'm using:
- remora 3.1.3 for EC500 RT1052 board ( https://github.com/scottalford75/Remora-RT1052-cpp )
- LinuxCNC 2.9.3

# Machine capabilities:
- Axes: X Y Z + A, driven by DM556T stepper drivers
- Spindle, driven by VFD controlled by 0-10V signal + FWD/REV I/O.


# Bugs
- sometimes NVMPG will SELECT ON IT'S OWN next axis, and selecting previous one doesn't work. You have to manually cycle to previous exis by selecting next.

# Troubleshooting

## following joint error

### Problem

Axis moves on slower speed but when movement is sharper and/or direction change it will error with `following joint error`

### Cause

[guess] linuxcnc or remora can't keep up with position tracking.

### Solution

Lower `MAX_VELOCITY` for particular axis in `.ini` file


## Wrong axis direction

### Solution
Prepend/remove `-` in `SCALE` value for particular axis in `.ini` file
