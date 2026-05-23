# Experience 01: High/Low Logic State Representation via LEDs

## 1. Preparation

### Required Functional Boards (BOM)
* [ ] **1x [SF-01](../schede/sf-01/)**: Board Power Supply Module
* [ ] **1x [SF-02](../schede/sf-02/)**: Momentary Logic Line Generator
* [ ] **1x [SF-03](../schede/sf-03/)**: Permanent Logic Line Generator
* [ ] **1x [SF-04](../schede/sf-04/)**: LED Logic Level Indicator
* [ ] **1x [SF-08](../schede/sf-08/)**: Data Line Distribution Module

### Wiring Blueprint
> [!IMPORTANT]  
> Always ensure the main power switch on the Power Supply Module (SF-01) is turned OFF before making or changing any electrical connections.

1. **Power Distribution:** Connect the +5V regulated power output from **SF-01** to the power input lines of **SF-02**, **SF-03**, and **SF-04** using standard 2-pin power cables.
2. **Signal Bus Setup:** Connect the 4-pin data output of the Permanent Generator (**SF-03**) to one of the input ports on the Distribution Hub (**SF-08**).
3. **Indicator Connection:** Connect a 4-pin data cable from an output port of the Distribution Hub (**SF-08**) to the input port of the LED Indicator (**SF-04**).

---

## 2. Execution

### Operational Procedure
1. Double-check all wiring configurations against the blueprint.
2. Turn ON the main power switch on **SF-01**. Verify that its green onboard power LED lights up.
3. Observe the 4 LEDs on the LED Indicator module (**SF-04**) while all toggle switches on **SF-03** are in the **OFF** position.
4. One by one, flip the toggle switches on **SF-03** to the **ON** position and observe the state of the corresponding LEDs on **SF-04**.
5. Turn OFF the power on **SF-01**. Replace the data connection from **SF-03** with the 4-pin data output of the Momentary Generator (**SF-02**).
6. Turn the power back ON. Press and release the tactile push buttons on **SF-02** one at a time, noting the behavior of the LEDs on **SF-04**.

### Expected Behavior
* **With SF-03 (Toggle Switches):** When a switch is **OFF**, its corresponding LED on **SF-04** stays **ON** (High level / "1"). When you flip a switch to **ON**, the corresponding LED turns **OFF** (Low level / "0").
* **With SF-02 (Push Buttons):** All LEDs on **SF-04** are normally **ON**. Pressing a push button immediately turns its corresponding LED **OFF**. Releasing the button instantly turns the LED back **ON**.

---

## 3. Conclusions

### Technical Analysis
This experience practically demonstrates the concept of **active-low logic** used throughout this architecture:
* When a switch or button is open (**OFF**), the data line is pulled up to +5V via the internal resistors on the generator boards, representing a digital **High (1)** state. The indicator circuit (**SF-04**) interprets this high voltage and drives the LED.
* When a switch is closed (**ON**), the line is shorted directly to ground (0V), forcing an **active-low** state. The data line drops to digital **Low (0)**, causing the LED on the indicator module to turn off.
