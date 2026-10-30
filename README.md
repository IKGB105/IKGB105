# Hardware Systems Engineering  
[My webpage](https://ikgb105.github.io/) 

Electronics student at UAA (7th semester), building toward complete hardware systems — not isolated pieces. Working across FPGA/RTL design, PCB design, embedded systems, and production hardware/firmware/software integration.

**Aguascalientes, Mexico**

---

## What I'm doing

Focused on building complete hardware systems — PCB design, embedded firmware, and the digital logic underneath, not just one layer in isolation. Most of my recent work is physical: I've designed and routed boards from schematic to fabrication-ready Gerbers, from an ARM Cortex-M platform to a handful of power electronics projects (SCR control, buck conversion, a Class D amplifier).

That systems-first instinct came from building a production safety-interlock system — a hardware relay wired into a real machine, driven by firmware and a web API, actually running at a food manufacturing plant. Before that I went deep on computer architecture (built a RISC-V simulator, synthesized it on real FPGAs) to understand why CPUs are designed the way they are — that depth still shows up in how I approach hardware, it's just not the main focus anymore.

Spend most of my time on:
- PCB design in KiCad — schematic capture through fabrication-ready routing
- Power electronics: SCR control, buck conversion, Class D amplification — validated with LTspice and COMSOL thermal FEM
- Embedded systems (STM32, FreeRTOS, custom drivers) and production hardware/firmware/software integration
- FPGA design and RISC-V architecture when a project calls for it
- Debugging with OpenOCD/GDB when things don't work (which is often)

---

## Main projects

**These line up most with where I'm headed — complete systems, not isolated pieces:**

### ARM Processor PCB Design (KiCad)
[PCB-ARM-Kicad](https://github.com/IKGB105/PCB-ARM-Kicad)

Designed and routed a 2-layer PCB around an ARM Cortex-M MCU (QFP package), from schematic capture through final routing. Board includes:
- USB connector for power and programming
- 4 user pushbuttons plus a dedicated reset
- 8 status LEDs
- Expansion headers for BOOT mode selection, a camera interface, and general I/O

Used a ground pour across the stackup to keep return paths short on a design that doesn't have the luxury of a dedicated internal ground plane. Fully routed with fabrication-ready Gerbers and drill files — this one is designed to actually be built, not just simulated.

My only real complex physical-hardware project so far, which is exactly the piece a pure-RTL background doesn't prove on its own.

### Adjustable LM317 Power Supply — SPICE, PCB & Thermal FEM
[LM317-Adjustable-PowerSupply](https://github.com/IKGB105/LM317-Adjustable-PowerSupply)

Full power-supply design loop documented as an honest engineering logbook: 
  * LTspice simulation of the adjustable topology
  * KiCad PCB layout
  * COMSOL thermal FEM study of the regulator's worst-case temperature

The simulation step caught a real 76mV arithmetic error in an earlier hand calculation before it propagated into the thermal analysis.

### Adjustable LM2596 Buck Converter — PCB & Thermal FEM
[LM2596-Adjustable-Buck-Converter](https://github.com/IKGB105/LM2596-Adjustable-Buck-Converter)

Companion project to the LM317 supply above, built mainly for hands-on KiCad layout practice (trace sizing, ground-plane strategy, via stitching) before moving into multiphase VRM work. A COMSOL thermal sweep across the full adjustable range found the real thermal limit wasn't the regulator IC — it was the catch diode, exceeding its rated junction temperature at the low-output-voltage extreme. Root-caused to an isolated ground via at the diode's anode; fix proposed, not yet built. Same "honest logbook" standard as the LM317 project: every result marked calculated, simulated, or pending.

### Hot-Swap eFuse (LTC4215) — SPICE, PCB & Thermal FEM
[EFUSE-LTC4215-HotSwap](https://github.com/IKGB105/EFUSE-LTC4215-HotSwap)

12V hot-swap/eFuse front-end: controlled inrush, latching overcurrent shutdown, and auto-retry undervoltage lockout, validated in LTspice against the IC's own internal startup-delay behavior. A coupled electrical-thermal COMSOL model (current in the copper solved together with the heat) found the copper pours themselves were the dominant heat source at the rated 15A — not the MOSFET or sense resistor alone — driving a lower, thermally-safe continuous-current recommendation. Same "honest logbook" standard as the LM317/LM2596 projects: every result marked calculated, simulated, or pending.

### Power Electronics PCBs
[PCBs-POWER-ELECTRONICS](https://github.com/IKGB105/PCBs-POWER-ELECTRONICS)

Four physical PCBs from power electronics coursework, each with its own schematic, layout, and 3D render:
- SCR/thyristor firing controller
- Buck converter
- STM32-controlled Class D amplifier
- Two-board protected voltage supply with short-circuit protection

All four designed, routed, and rendered; the protected power supply's power stage is fully routed with fabrication-ready Gerbers. Simpler single-purpose boards than the ARM PCB above, but real practice across control, power-conversion, and audio topologies.

### IoT Safety Checklist & Hardware Interlock System (Raspberry Pi / Node.js)
[IOT-Safety-Checklist](https://github.com/IKGB105/IOT-Safety-Checklist)

Production system deployed at a food manufacturing plant. Digitizes pre-shift machine safety checklists and physically interlocks machine startup — a Shelly smart relay wired into the start-button circuit only closes after the checklist is approved. Runs fully offline on a Raspberry Pi acting as its own:
- WiFi access point
- Web server
- REST API

Also includes:
- Photo evidence capture
- Automatic WhatsApp alerts
- Audited supervisor override flow

This is my strongest example of full-stack integration — hardware, firmware, and software, actually deployed and running, not a class exercise. It's the project that made me want to keep working across the whole stack instead of picking just one.

### IK-Dron — 5" FPV Racing Drone
[IK-Dron](https://github.com/IKGB105/IK-Dron)

Team project (with [Orlando Contreras](https://github.com/DasReyxr)): diagnosed and flew a 5" racing drone after its original flight controller suffered an unrecoverable hardware failure. Migrated to a SpeedyBee F405 V4 stack on BetaFlight, then root-caused a "won't lift off, then disarms on takeoff" failure via the flight controller's CLI to a propeller/motor-rotation mismatch tripping BetaFlight's runaway-takeoff protection. Full day-by-day build log and a formal technical report included — real hardware/firmware debugging under a hard constraint (it has to actually fly).

### Outsider — Blackstar Amp Control (AI-Assisted Fork) — [Outsider-AI-FIX](https://github.com/IKGB105/Outsider-AI-FIX)
* An AI-assisted round of bug fixes and feature completions on a Linux GUI for controlling Blackstar ID-series guitar amplifiers over USB, forked from Jonathan Underwood's original, validated against a real Blackstar ID:15 TVP over the reverse-engineered USB protocol.


**Strong systems/embedded fundamentals — good supporting evidence:**
 * **RFID Access Control System (STM32F446)** — [RFID-Access-Control-using-STM32F446RETx](https://github.com/IKGB105/RFID-Access-Control-using-STM32F446RETx)

 * **RISC-V Simulator** — [RISC-V-CPU-Designs](https://github.com/IKGB105/RISC-V-CPU-Designs)

 * **FreeRTOS on STM32** — part of [UNI-CODES](https://github.com/IKGB105/UNI-CODES).

 * **ARM Assembly** (13+ programs) — also in [UNI-CODES](https://github.com/IKGB105/UNI-CODES).


**More academic / isolated-piece exercises — solid work, but narrower in scope than the above:**

 * **Booth Multiplier** (VHDL) — Part of the [VHDL-LABS](https://github.com/IKGB105/VHDL-LABS/tree/main/xilinx-labs/P7) coursework.

 * **IEEE-754 Floating-Point Calculator** (VHDL) — [IEEE-754-Calc-VHDL](https://github.com/IKGB105/IEEE-754-Calc-VHDL)

 * **FFT in Python** — [Py-FFT-Upscaling](https://github.com/IKGB105/Py-FFT-Upscaling)

 * **Transistor Amplifier Suite** (Python) — [transistor-designer-calculator](https://github.com/IKGB105/transistor-designer-calculator)

---

## Languages & Tools

**PCB & Power:** KiCad (schematic to fabrication-ready Gerbers), LTspice, COMSOL (thermal FEM)  
**Embedded Platforms:** STM32F411, STM32F446, Arduino, ESP32, AVR ATmega8515  
**Programming:** Python (simulators, automation), C (embedded), ARM Assembly, C++ (a bit), AVR Assembly  
**HDL & FPGA:** Verilog, VHDL, Amaranth HDL, Xilinx (ISE/Vivado, Spartan-6), Gowin EDA (Tang Nano 1K)  
**Tools & Debug:** Git, LaTeX, OpenOCD/GDB, GTKWave 

---

## Stats (if that matters)

- 20+ completed projects
- 10+ PCBs designed and routed in KiCad
- 1 production system deployed and actually running
- ~10,000 lines of actual code (not counting exercises)
- 6 programming languages
- 2 FPGA vendors (Xilinx and Gowin)
- Cambridge English B2 certified
