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
2. Set up your compiler-prefix like this `export CCPREFIX=/opt/rpi-tools/arm-bcm2708/gcc-linaro-arm-linux-gnueabihf-raspbian-x64/bin/arm-linux-gnueabihf-`
3. Open the menuconfig of the kernel configuration and adjust the settings `make ARCH=arm CROSS_COMPILE=${CCPREFIX} menuconfig`
4. Build the kernel `make ARCH=arm CROSS_COMPILE=${CCPREFIX} zImage modules dtbs -j5`
5. Flash the kernel onto the SD card and you're ready to go.

## Real-Time performance
I made some rt tests with *cyclictest* on the same time executing *hackbench* to determine the worst-case latencies under high system load. My worst-case latencies were 99 microseconds with the following settings:

```
cyclictest -p98 -n -t
hackbench -l5000000
```
