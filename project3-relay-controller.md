# 4-Channel Relay Controller Board — Industrial IoT PCB Design

> An optocoupler-isolated 4-channel relay controller board designed for industrial IoT applications. Accepts 3.3V/5V logic input, drives 4 independent relay channels with full electrical isolation between control and load circuits — DRC verified and Gerber-ready.

---

## Overview

This project is a **4-channel relay controller PCB** designed for real-world industrial and IoT use cases — home automation, remote switching, PLC interfacing, and load control applications. The design prioritises electrical safety and signal integrity: each relay channel is driven through a dedicated optocoupler, fully isolating the low-voltage control logic from the high-voltage load side.

This board is the kind of peripheral hardware found inside commercial IoT gateways, automation panels, and industrial controllers — making it a strong portfolio piece for clients building connected products.

---

## Specifications

| Parameter            | Value                              |
|----------------------|------------------------------------|
| Channels             | 4 independent relay channels       |
| Control Input        | 3.3V / 5V logic compatible         |
| Isolation            | Optocoupler per channel (PC817)    |
| Relay Type           | SPDT, 10A / 250VAC rated           |
| Relay Coil Voltage   | 5V DC                              |
| Flyback Protection   | 1N4007 freewheeling diode per relay|
| Indicator LEDs       | 1 per channel (relay status)       |
| Control Interface    | 2.54mm pin header (IN1–IN4, VCC, GND) |
| Load Terminals       | Screw terminals (NO, COM, NC)      |
| PCB Layers           | 2                                  |
| Board Status         | Design complete, DRC passed        |
| Tool                 | KiCad                              |

---

## Design Highlights

### Full Optocoupler Isolation
Each of the 4 channels uses a PC817 optocoupler to electrically isolate the microcontroller-side logic from the relay coil and load. This protects the MCU from voltage spikes and ensures safe operation in mixed-voltage industrial environments.

### Flyback Diode Protection
A 1N4007 freewheeling diode is placed across each relay coil to suppress the inductive voltage spike generated when the relay de-energises. This is critical for protecting the switching transistor and optocoupler from damage.

### NPN Transistor Drive Stage
Each channel uses an NPN transistor (S8050) as a driver between the optocoupler output and the relay coil, providing sufficient base current and clean switching without stressing the optocoupler output.

### High-Voltage Creepage Clearance
The PCB layout maintains generous clearance between the low-voltage control traces and the high-voltage screw terminal traces, following IPC-2221 guidelines for the relay load side. Separate ground planes for control and load sides with a clear isolation boundary.

### Status LEDs Per Channel
Each relay channel has an indicator LED that lights when the relay is energised, giving instant visual feedback of relay state — essential for debugging and field verification.

### Screw Terminal Load Connections
All relay outputs use screw terminals for secure, tool-fastened wire connections — standard practice for industrial and mains-connected equipment.

---

## Repository Structure

```
project3-relay-controller/
├── schematic/
│   └── relay_controller_4ch.kicad_sch
├── pcb/
│   └── relay_controller_4ch.kicad_pcb
├── gerbers/
│   ├── relay_controller_4ch.GTL
│   ├── relay_controller_4ch.GBL
│   ├── relay_controller_4ch.GTO
│   ├── relay_controller_4ch.GTS
│   ├── relay_controller_4ch.GBS
│   └── relay_controller_4ch.DRL
├── bom/
│   └── bom.csv
└── README.md
```

---

## Bill of Materials (Key Components)

| Ref           | Component           | Part Number      | Package      |
|---------------|---------------------|------------------|--------------|
| K1–K4         | Relay               | SRD-05VDC-SL-C   | Through-hole |
| U1–U4         | Optocoupler         | PC817            | DIP-4        |
| Q1–Q4         | NPN Transistor      | S8050            | TO-92        |
| D1–D4         | Flyback Diode       | 1N4007           | DO-41        |
| LED1–LED4     | Status LED          | Red, 2V, 20mA    | 3mm TH       |
| R1–R4         | Base Resistor       | 1kΩ              | 0402         |
| R5–R8         | LED Resistor        | 470Ω             | 0402         |
| R9–R12        | Optocoupler Resistor| 330Ω             | 0402         |
| J1            | Control Header      | 6-pin, 2.54mm    | Through-hole |
| J2–J5         | Screw Terminals     | 3-pin, 5.08mm    | Through-hole |

---

## Channel Circuit (Per Channel)

```
MCU GPIO → R (330Ω) → PC817 (optocoupler LED)
                              ↓
                     PC817 (phototransistor)
                              ↓
                     S8050 base → relay coil → GND
                              ↑
                         flyback diode (1N4007)
```

---

## Skills Demonstrated

- Optocoupler isolation circuit design
- Relay driver design (transistor + flyback protection)
- High-voltage / low-voltage PCB separation and creepage clearance
- Multi-channel board layout with screw terminal outputs
- Industrial IoT peripheral design
- KiCad DRC and Gerber export

---

## Use Cases

- Home automation (lights, fans, appliances)
- Industrial PLC output expansion
- IoT gateway relay outputs (MQTT-controlled switching)
- Lab bench load switching
- Remote power control systems

---

## Project Status

| Stage            | Status       |
|------------------|--------------|
| Schematic        | ✅ Complete  |
| PCB Layout       | ✅ Complete  |
| DRC              | ✅ Passed    |
| Gerbers Exported | ✅ Ready     |
| Fabricated       | ⬜ Not yet   |
| Tested           | ⬜ Not yet   |

---

## About the Designer

Self-taught PCB designer specializing in KiCad — IoT, embedded systems, and industrial control boards.
Available for freelance PCB design work: schematic capture, layout, DRC review, and Gerber preparation.

🔗 GitHub: [@your-username]
📧 [your.email@example.com]
🌐 [your-portfolio-link]
