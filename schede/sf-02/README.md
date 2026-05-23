# SF-02: Momentary Logic Line Generator

This module generates 4 momentary logic lines that remain active only while their corresponding switches (labeled SW1, SW2, SW3, and SW4) are pressed. Each switch controls its respective data line, labeled D1, D2, D3, and D4.

The lines operate in one of two states:
* **Low logic level (L or "0"):** A voltage of 0V.
* **High logic level (H or "1"):** A voltage of +5V.

The board is designed with an **active-low** configuration. When a switch is pressed (SW=ON), the level of the corresponding data line is pulled low:

```text
SWn = OFF -> Dn = H
SWn = ON  -> Dn = L
```

![sf-built](sf-02_built.jpg)

## Schematic Diagram
![sf-schematic](sf-02_sch.jpg)

## PCB Layout
![sf-pcb](sf-02_pcb.jpg)

## Bill of Materials (BOM)
* [x] 1x Perfboard (4x6 cm)
* [x] 4x SPST Tactile Push Button Switches (Normally Open)
* [x] 4x Resistors (47kΩ, Pull-up)
* [x] 4x Resistors (100Ω, Pull-down)
* [x] 1x IC 74LS00 (Quadruple 2-input NAND Gate)
* [x] 1x Ceramic Capacitor (100nF)
* [x] 1x 2-pin Connector (Molex-KK or KF2510 type, Board Power)
* [x] 1x 4-pin Connector (Molex-KK or KF2510 type, Data Lines)
