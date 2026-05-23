# UnoZero - Digital Logic Experiences
A collection of educational hands-on experiences in digital electronics, built using a custom ecosystem of modular logic boards.

![image](overview.jpg)


## Introduction
This project represents a workbench for exploring digital electronics through a modular, hardware-first approach. It has a dual objective: building the functional boards themselves and learning the core logic of digital systems—all without needing to dive into the underlying physics and complex mathematics of solid-state components.

This kit gives you a hands-on way to build and experiment with real hardware.


## Functional Boards
A **Functional Board** (*Scheda Funzione* / **SF**) is a minimal circuit designed to perform a single, specific logic or utility function. By interconnecting these boards, simpler blocks can be composed into increasingly complex digital systems.

Each board type is tracked with the prefix **SF** followed by a progressive identifier:
* **[SF-01](schede/sf-01/)**: Board Power Supply Module
* **[SF-02](schede/sf-02/)**: Momentary Logic Line Generator
* **[SF-03](schede/sf-03/)**: Permanent Logic Line Generator
* **[SF-04](schede/sf-04/)**: LED Logic Level Indicator
* **[SF-05](schede/sf-05/)**: 7-Segment BCD Display Module
* **[SF-06](schede/sf-06/)**: Pulse Generator
* **[SF-07](schede/sf-07/)**: Clock Generator
* **[SF-08](schede/sf-08/)**: Data Line Distribution Module
* **[SF-09](schede/sf-09/)**: Modulo-10 Counter


## Laboratory Experiences
Every experience in this repository is structured into 3 distinct phases to guide the workflow:
1.  **Preparation**: The bill of materials (required SF boards) and the complete wiring blueprint needed to set up the circuit.
2.  **Execution**: The step-by-step procedure to operate the system and observe its behavior.
3.  **Conclusions**: A brief analysis of the results, paired with deeper technical insights or further challenges.


### Current Experiments Inventory
* **[Experience 01](esperienze/esperienza-01.md)**: High/Low Logic State Representation via LEDs
* **[Experience 02](esperienze/esperienza-02.md)**: High/Low Logic State Representation via BCD Display
* **[Experience 03](esperienze/esperienza-03.md)**: Pulse Counter Circuit
* **[Experience 04](esperienze/esperienza-04.md)**: Cascaded Pulse Counter Systems
* **[Experience 05](esperienze/esperienza-05.md)**: Clock-Driven Pulse Counter Applications


## Changes
See the [CHANGES.md](CHANGES.md) file for a detailed version history and changelog of the hardware and documentation updates.


## About & License
**Author:** Alessandro Fraschetti (gom9000). <br/>
**Acknowledgments**: A special thanks goes to D.G. Larsen and P.R. Rony. In the late 1970s, they conceived and wrote the legendary *Bugbook* series, which directly inspired the modular architecture and educational spirit of this project.<br/>
**Technical Notes:** All hardware design, schematics, and layouts were developed using the free **ExpressPCB** CAD suite, supported by the custom **[expresspcb-goslib](https://github.com/gom9000/expresspcb-goslib)** asset library.<br/>
**License:** This project is licensed under the [MIT License](LICENSE). You are free to use, modify, and distribute it. Credit in your derivative documentation is highly appreciated.