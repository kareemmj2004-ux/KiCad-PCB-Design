# KiCad-PCB-Design
PCB design project developed using KiCad, including schematic capture, component placement, and PCB routing.


---

## Project: Step-Down (Buck) Converter – LM2596S-5

### Overview
A buck converter that steps a higher input voltage down to a fixed 5V using the
**LM2596S-5** regulator IC (fixed 5V version). Designed in KiCad, from schematic
capture through PCB layout and Gerber generation.

### Specifications
| Parameter           | Value                            |
|---------------------|----------------------------------|
| Input Voltage       | 7V – 40V (per datasheet)         |
| Output Voltage      | 5V (fixed)                       |
| Max Output Current  | 3A                               |
| Switching Frequency | 150 kHz                          |
| Topology            | Step-Down (Buck)                 |

### Components
| Ref | Component  | Function                              |
|-----|------------|---------------------------------------|
| U1  | LM2596S-5  | Buck regulator (switch + control)     |
| C1  | Capacitor  | Input filter                          |
| L1  | Inductor   | Stores energy and smooths the current |
| D1  | Schottky   | Freewheeling diode                    |
| C2  | Capacitor  | Output filter                         |
| J2  | Conn_01x02 | Power input                           |
| J1  | Conn_01x02 | Output                                |

### How It Works
1. When the internal switch of the IC turns on, current flows through inductor L1, charges C2, and supplies the load while the inductor stores energy.
2. When the switch turns off, the inductor keeps the current flowing to the load through diode D1.
3. The duty cycle is adjusted automatically through the FB pin (connected to the output) to hold the output at 5V.
4. C1 and C2 reduce ripple on the input and output.

### Pin Notes
- **ON/OFF** is tied to GND, so the IC is always enabled.
- **FB** is connected to the output because this is the fixed-voltage version.
- **PWR_FLAG** symbols are used so the ERC does not report power-pin errors.

### Files
- `Step-Down (Buck) Converter.kicad_sch` – Schematic
- `Step-Down (Buck) Converter.kicad_pcb` – PCB layout
- `Gerber Step-Down (Buck) Converter...` – Manufacturing files (Gerber)

### Author
**Kareem** – Mechatronics Engineering, New Cairo University
