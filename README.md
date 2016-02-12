# PREEMPT_RT Linux Kernel for the Raspberry PI

This repository contains a version of the Linux kernel for the Raspberry PI2 already patched and configured with PREEMPT_RT.
The only thing you have to do is to build the kernel and flash it on the microcontroller's SD card.

## Current configuration
The kernel config (.config) is already set up fully-preemptible.

* bcm2709_defconfig done
* Fully Preemptible Kernel (RT)
* No old dyntics (CONFIG_NO_HZ not set)
* Default CPUFreq governor (performance)
* CAN bus subsystem support
   - Microchip MCP251x SPI CAN controllers 
   - PEAK PCAN-USB/USB Pro interfaces

## Build and Run

1. Clone the repository `git clone --depth=1 https://github.com/dtuchsch/rpi-linux-preempt_rt.git`.
2. Open the menuconfig of the kernel configuration
