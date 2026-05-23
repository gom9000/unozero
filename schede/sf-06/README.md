# SF-06: Pulse Generator
This module generates single logic pulses via manual switches. The pulse initiates upon pressing the switch and terminates approximately 15ms later, regardless of whether the switch remains pressed or is released. 

The 15ms duration is long enough to completely absorb and debounce any spurious switch contacts, yet short enough to prevent any perceived delay when the switch is pressed repeatedly in rapid succession.

The board is designed with an **active-low** configuration. The output line is held at a high logic level by default, dropping to a low logic level only for the duration of the active pulse.

![sf-built](sf-06_built.jpg)

## Schematic Diagram
![sf-schematic](sf-06_sch.jpg)

## PCB Layout
![sf-pcb](sf-06_pcb.jpg)

## Bill of Materials (BOM)
* [x] 1x Perfboard (4x6 cm)
* [x] 2x SPST Tactile Push Button Switches (Normally Open)
* [x] 2x Resistors (47kΩ, Pull-up)
* [x] 2x Resistors (22kΩ, Pull-up)
* [x] 2x Resistors (100Ω, Pull-down)
* [x] 2x IC 74LS02 (Quadruple 2-input NOR Gate)
* [x] 4x Ceramic Capacitors (100nF)
* [x] 2x Capacitors (1µF)
* [x] 2x 2-pin Connectors (Molex-KK or KF2510 type)