# SF-01: Board Power Supply Module
This module provides the regulated voltage required to power all the functional boards in the system. It accepts any external power supply with an output voltage between $+9V$ and $+12V$ (regulated or unregulated) and delivers a stable $+5V$ output with a maximum current of approximately $250mA$.

![sf-built](sf-01_built.jpg)


## Schematic Diagram
![sf-schematic](sf-01_sch.jpg)

## PCB Layout
![sf-pcb](sf-01_pcb.jpg)


## Bill of Materials
- [x] 1x Perfboard (4x6 cm)
- [x] 1x DC Power Jack (5.1mm)
- [x] 1x Voltage Regulator (7805, TO-220 package)
- [x] 1x Diode Bridge Rectifier (1A)
- [x] 1x Electrolytic Capacitor (1000µF, 50V)
- [x] 2x Ceramic Capacitors (0.1µF, 50V)
- [x] 1x Resistor (1kΩ, LED current limiting)
- [x] 1x Green LED (ON/OFF status indicator)
- [x] 1x Microswitch (SPST or DPST, ON/OFF toggle)
- [x] 4x 2-pin Connectors (Molex-KK or KF2510 type)
