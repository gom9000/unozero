# SF-07: Clock Generator
This module generates a periodic square wave logic signal with a selectable frequency.

The onboard jumpers configure the output frequency:
* **Jumper JA:** Selects a frequency of approximately 1Hz.
* **Jumper JB:** Selects a frequency of approximately 0.5Hz.

![sf-built](sf-07_built.jpg)

## Schematic Diagram
![sf-schematic](sf-07_sch.jpg)

## PCB Layout
![sf-pcb](sf-07_pcb.jpg)

## Bill of Materials (BOM)
* [x] 1x Perfboard (4x6 cm)
* [x] Resistors (1kΩ, 47kΩ, and 100kΩ)
* [x] 1x Green LED
* [x] 1x IC 74LS14 (Hex Schmitt-Trigger Inverters)
* [x] Ceramic Capacitors (100nF, 10µF)
* [x] 2x 2-pin Jumper Connectors
* [x] 2x 2-pin Connectors (Molex-KK or KF2510 type)