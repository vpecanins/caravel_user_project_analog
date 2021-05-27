# Noise-shaping TDC

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0) [![UPRJ_CI](https://github.com/efabless/caravel_user_project_analog/actions/workflows/user_project_ci.yml/badge.svg)](https://github.com/efabless/caravel_user_project_analog/actions/workflows/user_project_ci.yml) [![Caravan Build](https://github.com/efabless/caravel_user_project_analog/actions/workflows/caravan_build.yml/badge.svg)](https://github.com/efabless/caravel_user_project_analog/actions/workflows/caravan_build.yml)

This project aims to implement a noise-shaping time to digital converter (TDC) inspired by [1] with Google/Skywater/Efabless SKY130 process technology.

[1] A. Elshazly, S. Rao, B. Young and P. K. Hanumolu, "A Noise-Shaping Time-to-Digital Converter Using Switched-Ring Oscillators—Analysis, Design, and Measurement Techniques," in IEEE Journal of Solid-State Circuits, vol. 49, no. 5, pp. 1184-1197, May 2014, doi: 10.1109/JSSC.2014.2305651. https://ieeexplore.ieee.org/document/6748928

## Brief explanation

This noise-shaping TDC works by accumulating time differences into the phase of a free-running ring oscillator. By reading out the phase of the ring oscillator and differentiating in the digital domain, successive quantization errors are cancelled and its energy is moved towards high frequency, where it can be filtered out by averaging.

Due to noise shaping, the resolution increases by 1.5 bits for every 2x increase in oversampling ratio, as opposed to just 0.5 bits for a non-noise-shaping TDC. This allows to obtain resolution of less than 1ps using just a modest clock frequency of 500MHz.

## Possible applications

- Time-of-flight
- LIDAR 
- Accudate distance sensing for autonomous cars / drones / robots
- As building block for All-Digital PLL (ADPLL)

## Status

Currently just getting started with Skywater PDK and getting familiar with the various open source tools used in this work flow.

## Information

- Cloned from caravel_user_project_analog - "CaraVAN" basis chip 
- Bare analog pads required for high-speed clock signal.
- Planned transistor-level implementation:
  - Ring oscillator
  - Sense amplifier Flip Flop
  - Switch
  - Time difference generator (TDG) - Will use RS latch
- Planned standard cell implementation
  - Phase decoder
  - Differentiator modulo 16
  - Accumulator
  - RAM Memory (FIFO)
  - Wishbone interface

---

Refer to [README](docs/source/index.rst) for sample project documentation. 
