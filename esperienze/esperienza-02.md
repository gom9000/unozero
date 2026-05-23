# Experience 02: High/Low Logic State Representation via BCD Display

## 1. Preparation

### Required Functional Boards (BOM)
* [ ] **1x [SF-01](../schede/sf-01/)**: Board Power Supply Module
* [ ] **1x [SF-03](../schede/sf-03/)**: Permanent Logic Line Generator
* [ ] **1x [SF-05](../schede/sf-05/)**: 7-Segment BCD Display Module
* [ ] **1x [SF-08](../schede/sf-08/)**: Data Line Distribution Module

### Wiring Blueprint
> [!IMPORTANT]  
> Always ensure the main power switch on the Power Supply Module (SF-01) is turned OFF before making or changing any electrical connections.

1. **Power Distribution:** Connect the +5V regulated power output from **SF-01** to the power input lines of **SF-03** and **SF-05** using standard 2-pin power cables.
2. **Signal Bus Setup:** Connect the 4-pin data output of the Permanent Generator (**SF-03**) to one of the input ports on the Distribution Hub (**SF-08**).
3. **Decoder Connection:** Connect a 4-pin data cable from an output port of the Distribution Hub (**SF-08**) to the BCD binary input port of the 7-Segment Display Module (**SF-05**).

---

## 2. Execution

### Operational Procedure
1. Double-check all wiring configurations against the blueprint, verifying that the 4 data lines (D1, D2, D3, D4) match the corresponding BCD inputs (A, B, C, D) respectively.
2. Turn ON the main power switch on **SF-01**.
3. Set all 4 toggle switches on **SF-03** to the **OFF** position. Observe the character or symbol displayed on **SF-05**.
4. Actuate the toggle switches on **SF-03** to generate different binary combinations (from `0000` to `1111`) and document what appears on the 7-segment display for each state.
5. Identify which switch combinations correspond to standard decimal numbers (0 through 9).

### Expected Behavior
* **Active-Low Inversion:** Because the generator (**SF-03**) is active-low, when all switches are **OFF**, they output high states (`1111`). The 7-segment decoder will interpret this specific input and blank the display or show a unique non-decimal symbol depending on the 74LS47 behavior.
* **Decimal Representation:** Flipping the switches to force a traditional low state (ground) allows you to feed the proper BCD patterns into **SF-05**. For example, setting the lines to represent a valid BCD code for 0 will turn on segments to form the number `0`. Valid combinations will cleanly map decimal values from `0` to `9`.

---

## 3. Conclusions

### Technical Analysis
This laboratory highlights how raw binary signals are translated into human-readable data:
* **Binary Coded Decimal (BCD):** A 4-bit digital bus can represent 16 distinct combinations ($2^4$). BCD utilizes the first ten combinations (`0000` to `1001`) to map directly to the decimal numbers 0–9.
* **The Role of the Decoder:** The 74LS47 IC on **SF-05** acts as a hardwired truth-table engine. It samples the 4-bit BCD input, determines the intended decimal digit, and immediately sinks current from the specific anodes of the common-anode TDSL5150 display to light up the correct segments. 

### Further Challenges / Insights
* **Invalid BCD States:** Look closely at what happens when you input binary combinations greater than 9 (from `1010` to `1111`). Why doesn't it show normal numbers, and how does the 74LS47 datasheet define these odd symbols?
* **Next Steps:** Think about how we could automate the generation of these numbers. Instead of manually flipping 4 switches to cycle through 0–9, what kind of digital circuit block could automatically step through these states sequentially?