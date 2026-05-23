# SF-09: Modulo-10 Counter
This module is a decade counter that counts incoming clock pulses. The current count is output in BCD binary format on the data line. It features an active-low reset input to clear the count back to zero.

To enable cascading multiple counters for multi-digit decimal counting, the board forwards a control line containing the following signals:
* **Carry (Riporto):** Active on the falling edge, indicating the counter has reached 10.
* **Reset:** Propagates the incoming reset pulse to the next cascaded module.

The board is designed to receive clock and reset pulses with an **active-low** configuration. Input lines are held high by default, dropping to a low logic level only during an active pulse.

![sf-built](sf-09_built.jpg)

## Schematic Diagram
![sf-schematic](sf-09_sch.jpg)

## PCB Layout
![sf-pcb](sf-09_pcb.jpg)

## Bill of Materials (BOM)
* [x] 1x Perfboard (4x6 cm)
* [x] 1x Resistor (100Ω, Biasing)
* [x] 2x Resistors (47kΩ, Biasing)
* [x] 1x General-purpose NPN Transistor
* [x] 1x IC 74LS90 (Decade Counter)
* [x] 1x Ceramic Capacitor (100nF)
* [x] 3x 2-pin Connectors (Molex-KK or KF2510 type)
* [x] 1x 4-pin Connector (Molex-KK or KF2510 type, Data Lines)