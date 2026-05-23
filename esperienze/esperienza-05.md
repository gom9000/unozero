# Experience 05: Clock-Driven Pulse Counter Applications

## 1. Preparation

### Required Functional Boards (BOM)
* [ ] **1x [SF-01](../schede/sf-01/)**: Board Power Supply Module
* [ ] **2x [SF-05](../schede/sf-05/)**: 7-Segment BCD Display Module
* [ ] **1x [SF-07](../schede/sf-07/)**: Clock Generator
* [ ] **2x [SF-08](../schede/sf-08/)**: Data Line Distribution Module
* [ ] **2x [SF-09](../schede/sf-09/)**: Modulo-10 Counter

### Wiring Blueprint
> [!IMPORTANT]  
> Always ensure the main power switch on the Power Supply Module (SF-01) is turned OFF before making or changing any electrical connections.

1. **Power Distribution:** Connect the +5V power output from **SF-01** to the power input lines of all modules (**SF-05** units, **SF-07**, and **SF-09** units).
2. **Frequency Configuration:** On the Clock Generator (**SF-07**), place a jumper on header **JA** to set the initial frequency to approximately 1Hz.
3. **Automated Clock Routing:** Connect a 2-pin signal cable from the output port of the Clock Generator (**SF-07**) directly to the clock input port of the first Counter (**SF-09**, Stage 1).
4. **Two-Digit Counting Cascade:** Maintain the exact same cascaded architecture from Experience 04:
   * Connect the **Carry** line of Stage 1 to the clock input of Stage 2.
   * Route the 4-pin BCD outputs from Stage 1 and Stage 2 through their respective Distribution Hubs (**SF-08**) to drive the Units and Tens **SF-05** display modules.

---

## 2. Execution

### Operational Procedure
1. Double-check all automated clock paths and cascading signal lines.
2. Turn ON the main power switch on **SF-01**.
3. Observe the behavior of the 7-segment displays without touching any manual buttons. The system should immediately begin cycling through numbers.
4. Use a stopwatch to time how long it takes for the Units display to advance 10 steps.
5. Turn OFF the power switch on **SF-01**. Move the jumper on **SF-07** from header **JA** to header **JB**.
6. Turn the power back ON and observe the modification in the system's counting speed.

### Expected Behavior
* **Hands-Free Automation:** The system counts entirely on its own. With jumper **JA** selected, the Units display increments precisely once every second (1Hz), meaning the Tens display advances every 10 seconds.
* **Frequency Scaling:** When swapping the jumper to **JB**, the counting speed visually cuts in half. The Units digit now increments once every 2 seconds (0.5Hz), causing the system to take 20 seconds to advance the Tens digit by one unit.

---

## 3. Conclusions

### Technical Analysis
This experience completes the evolutionary arc of your digital logic workstation by replacing manual inputs with an automated time base:
* **The Schmitt-Trigger Oscillator:** The 74LS14 IC on **SF-07** leverages an RC (Resistor-Capacitor) network to create a feedback loop that continuously charges and discharges. Because it has built-in hysteresis (Schmitt-Trigger inputs), it cleanly snaps between high and low thresholds, outputting a perfect, sharp square wave.
* **Frequency Determination:** By switching between jumper JA and JB, you alter the overall resistance ($R$) or capacitance ($C$) values active in the circuit. A larger RC time constant increases the charge/discharge duration, lowering the frequency (from 1Hz down to 0.5Hz) and slowing down the downstream counter logic.

### Further Challenges / Insights
* **Visualizing the Clock:** Look at the onboard green LED on **SF-07**. Notice how its blinking perfectly synchronizes with the stepping of the Units display. The LED is an explicit representation of the invisible active-low clock train driving the bus.
* **Ecosystem Review:** You have successfully built a fully autonomous digital clock/timer system using modular logic blocks. Think about how adding simple logic gates (like AND/NAND) between the counter lines could let you trigger external events—such as lighting a warning LED only when the counter hits a specific number like `26`.