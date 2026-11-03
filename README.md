# Fluid in a Box

Real-time simulation of sand and water using cellular automata. The application runs on a Raspberry Pi and combines an interactive graphical interface with accelerometer input and a physical LED-matrix display.

## Features

- Separate cellular-automaton behaviours for sand and water.
- Gravity direction controlled by an ADXL345 accelerometer or keyboard input.
- Multithreaded C implementation using POSIX threads and FIFO scheduling.
- Periodic-task utilities and deadline monitoring.
- Allegro graphical interface.
- 24 × 32 LED display driven by MAX7219 devices.

## Hardware and dependencies

The original setup uses a Raspberry Pi 4 Model B running Raspberry Pi OS, an ADXL345 accelerometer and the LED matrix. Building requires GCC, Make, POSIX threads, the real-time library, WiringPi and Allegro 4 with `allegro-config` available.

Enable the SPI and I²C interfaces and connect the hardware according to the [project report](Report/Report.pdf). The implementation uses WiringPi APIs and Allegro 4, so a compatible software environment is required.

## Build and run

```bash
git clone https://github.com/MattiaTinfena/Fluid-in-a-box.git
cd Fluid-in-a-box/Code
make
./Main
```

Run from `Code/` so the bitmap resources are found. The process needs access to the hardware interfaces and permission to use the configured real-time scheduling policy.

## Controls

| Key | Action |
| --- | --- |
| `S` / `W` | Select sand / water. |
| `P` | Pause or resume. |
| Arrow keys | Adjust the simulated gravity direction manually. |
| `A` | Enable accelerometer control. |
| `T` / `Y` | Increase / decrease the time-scale setting. |
| `G` / `H` | Increase / decrease gravity strength. |
| `Esc` | Exit. |

## Source and documentation

- `Code/Main.c`: application tasks, simulation and interaction.
- `Code/ptask.*`: periodic-task support.
- `Code/hwlib.*`: hardware interfaces.
- `Code/auxlib.*`: simulation and GUI utilities.
- [Report](Report/Report.pdf): design, hardware and implementation details.
