# Experience 04: Cascaded Pulse Counter Systems

## 1. Preparation

### Required Functional Boards (BOM)
* [ ] **1x [SF-01](../schede/sf-01/)**: Board Power Supply Module
* [ ] **2x [SF-05](../schede/sf-05/)**: 7-Segment BCD Display Module
* [ ] **1x [SF-06](../schede/sf-06/)**: Pulse Generator
* [ ] **2x [SF-08](../schede/sf-08/)**: Data Line Distribution Module
* [ ] **2x [SF-09](../schede/sf-09/)**: Modulo-10 Counter

### Wiring Blueprint
> [!IMPORTANT]  
> Always ensure the main power switch on the Power Supply Module (SF-01) is turned OFF before making or changing any electrical connections.

1. **Power Distribution:** Connect the +5V power output from **SF-01** to the power input lines of all active modules (**SF-05** units, **SF-06**, and **SF-09** units).
2. **First Stage (Units Digit):**
   * Connect a 2-pin signal cable from the Pulse Generator (**SF-06**) output to the clock input port of the first Counter (**SF-09**, Stage 1).
   * Connect the 4-pin BCD output of this first counter to the first Distribution Hub (**SF-08**, Stage 1).
   * Route a 4-pin data cable from that hub to the BCD input of the Units Display (**SF-05**, Stage 1).
3. **Cascading the Control Line:** Connect a 2-pin signal cable from the control output port (specifically the **Carry** line) of the first Counter (**SF-09**, Stage 1) to the clock input port of the second Counter (**SF-09**, Stage 2).
4. **Second Stage (Tens Digit):**
   * Connect the 4-pin BCD output of the second counter to the second Distribution Hub (**SF-08**, Stage 2).
   * Route a 4-pin data cable from that hub to the BCD input of the Tens Display (**SF-05**, Stage 2).

---

## 2. Execution

### Operational Procedure
1. Verify the dual-stage wiring paths carefully, ensuring the Carry from Stage 1 feeds the Clock of Stage 2.
2. Turn ON the main power switch on **SF-01**. 
3. If the displays do not show `00`, trigger a manual reset to clear both staging counters simultaneously.
4. Begin pressing the manual push button on **SF-06** repeatedly. Watch the interaction between the Units display and the Tens display.
5. Cycle through the counts to observe the transition when the system shifts from `09` to `10`, and finally from `99` back to `00`.

### Expected Behavior
* **Units Increment:** For every manual press on **SF-06**, the Units display increments cleanly from `0` to `9`.
* **The Carry Event:** On the 10th pulse (when the Units counter rolls over from `9` back to `0`), the falling edge of the Carry signal triggers the Tens counter, incrementing it by one. The display smoothly changes from `09` to `10`.
* **Maximum Capacity:** The system will count sequentially all the way up to `99`. On the 100th pulse, both stages roll over at the same time, resetting the entire dual-display setup back to `00`.

---

## 3. Conclusions

### Technical Analysis
This experience demonstrates how a synchronous local event can propagate asynchronously as a control signal to expand system capacity:
* **Asynchronous Cascading:** The second stage counter does not know about the master clock pulses coming from **SF-06**. It is entirely dependent on the first stage. 
* **The Falling Edge Trigger:** The 74LS90 IC increments on a high-to-low voltage transition (falling edge). The Carry output remains high during counts 0 through 8, goes low when reaching 9, and then transitions back from low to high upon rolling over to 0. This precise behavior ensures that the next stage advances exactly at the right moment.

### Further Challenges / Insights
* **Synchronized Resetting:** Look at the shared Reset propagation line. If you apply a reset signal to the input of the first counter, how does the architecture guarantee that the second stage clears at the exact same instant?
* **Next Steps:** Manually pushing a button 99 times to test the full scale is tedious. How can we replace the manual input module (**SF-06**) with an automated subsystem that injects continuous, high-speed clock pulses into our dual-stage counter?