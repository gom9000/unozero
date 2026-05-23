# Experience 03: Pulse Counter Circuit

## 1. Preparation

### Required Functional Boards (BOM)
* [ ] **1x [SF-01](../schede/sf-01/)**: Board Power Supply Module
* [ ] **1x [SF-05](../schede/sf-05/)**: 7-Segment BCD Display Module
* [ ] **1x [SF-06](../schede/sf-06/)**: Pulse Generator
* [ ] **1x [SF-08](../schede/sf-08/)**: Data Line Distribution Module
* [ ] **1x [SF-09](../schede/sf-09/)**: Modulo-10 Counter

### Wiring Blueprint
> [!IMPORTANT]  
> Always ensure the main power switch on the Power Supply Module (SF-01) is turned OFF before making or changing any electrical connections.

1. **Power Distribution:** Connect the +5V regulated power output from **SF-01** to the power input lines of **SF-05**, **SF-06**, and **SF-09** using standard 2-pin power cables.
2. **Clock Pulse Routing:** Connect a 2-pin signal cable from one of the pulse outputs on the Pulse Generator (**SF-06**) to the clock input port of the Modulo-10 Counter (**SF-09**).
3. **Count Data Bus:** Connect the 4-pin BCD data output of the Counter (**SF-09**) to an input port on the Distribution Hub (**SF-08**).
4. **Display Data Bus:** Connect a 4-pin data cable from an output port of the Distribution Hub (**SF-08**) to the input port of the BCD Display Module (**SF-05**).

---

## 2. Execution

### Operational Procedure
1. Verify all connections match the wiring blueprint, ensuring proper orientation of the data and power cables.
2. Turn ON the main power switch on **SF-01**.
3. Observe the initial value displayed on **SF-05**. If the display does not show `0`, momentarily trigger the reset mechanism to clear the counter.
4. Press and release the manual push button on **SF-06** that is linked to your clock input. Observe the number shown on the 7-segment display.
5. Continue pressing the button repeatedly, tracking the numerical sequence from `0` up to `9`, and note what happens on the next consecutive pulse after `9`.

### Expected Behavior
* **Sequential Counting:** Every time you press the push button on **SF-06**, the counter increments by exactly one unit, and the 7-segment display cleanly transitions to the next number (e.g., `0 -> 1 -> 2...`).
* **Automatic Roll-Over:** When the display reaches `9` and you apply one more pulse, the counter automatically resets its internal state and rolls back to `0`, starting the cycle over again.

---

## 3. Conclusions

### Technical Analysis
This experience showcases a complete, closed-loop digital subsystem integrating input, processing, and output stages:
* **The Necessity of Debouncing:** Mechanical switches suffer from contact bounce, generating rapid, erratic voltage spikes when pressed. If you connected a raw switch directly to the counter,