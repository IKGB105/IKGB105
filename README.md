# Hardware Systems Engineering

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

### IoT Safety Checklist & Hardware Interlock System (Raspberry Pi / Node.js)
Production system deployed at a food manufacturing plant. Digitizes pre-shift machine safety checklists and physically interlocks machine startup — a Shelly smart relay wired into the start-button circuit only closes after the checklist is approved. Runs fully offline on a Raspberry Pi acting as its own:
- WiFi access point
- Web server
- REST API

Also includes:
- Photo evidence capture
- Automatic WhatsApp alerts
- Audited supervisor override flow

This is my strongest example of full-stack integration — hardware, firmware, and software, actually deployed and running, not a class exercise. It's the project that made me want to keep working across the whole stack instead of picking just one.

### ARM Processor PCB Design (KiCad)
Designed and routed a 2-layer PCB around an ARM Cortex-M MCU (QFP package), from schematic capture through final routing. Board includes:
- USB connector for power and programming
- 4 user pushbuttons plus a dedicated reset
- 8 status LEDs
- Expansion headers for BOOT mode selection, a camera interface, and general I/O

Used a ground pour across the stackup to keep return paths short on a design that doesn't have the luxury of a dedicated internal ground plane. Fully routed with fabrication-ready Gerbers and drill files — this one is designed to actually be built, not just simulated.

My only real complex physical-hardware project so far, which is exactly the piece a pure-RTL background doesn't prove on its own. I've also built simpler single-purpose PCBs for power electronics coursework (SCR firing controller, buck converter, Class D amplifier, protected voltage supply) — see [PCBs-POWER-ELECTRONICS](https://github.com/IKGB105/PCBs-POWER-ELECTRONICS) for those.

### Adjustable LM317 Power Supply — SPICE, PCB & Thermal FEM
Full power-supply design loop documented as an honest engineering logbook: LTspice simulation of the adjustable topology, KiCad PCB layout, and a COMSOL thermal FEM study of the regulator's worst-case junction temperature that drove two rounds of heatsink selection. The simulation step caught a real 76mV arithmetic error in an earlier hand calculation before it propagated into the thermal analysis — [LM317-Adjustable-PowerSupply](https://github.com/IKGB105/LM317-Adjustable-PowerSupply)

### Outsider — Blackstar Amp Control (AI-Assisted Fork)
An AI-assisted round of bug fixes and feature completions on a Linux GUI for controlling Blackstar ID-series guitar amplifiers over USB, forked from Jonathan Underwood's original, validated against a real Blackstar ID:15 TVP over the reverse-engineered USB protocol:
- Amplifier front-panel control
- Effects control
- Preset save/restore
- Full 128-preset backup/restore

Real communication with external hardware over a real bus, not a simulated peripheral — the same kind of protocol-level debugging that comes up in any board with a USB or serial interface.

### RFID Access Control System (STM32F446)
First real project that wasn't just an assignment:
- Reading RFID tags and validating against a list
- Controlling a relay for a door lock
- Custom drivers and interrupt handling
- Making sure it doesn't randomly fail in production

Nothing fancy but it works — real hardware/firmware integration, not just a simulated peripheral.

**Strong systems/embedded fundamentals — good supporting evidence:**

### RISC-V Simulator
Built a complete CPU simulator to actually understand what's happening at the instruction level. Not just a testbench—a working model with:
- Full instruction decoder (extracts opcode, registers, immediate values)
- 32-bit ALU with all the standard operations
- Register file with proper RISC-V semantics (x0 is always zero)
- VCD output to trace execution in GTKWave

Started in Python/Amaranth, but after that I also implemented the ALU and RegisterFile in Verilog so I could see how it synthesizes on actual hardware. Strong on computer architecture depth, though it's a CPU core on its own rather than a full system.

### FreeRTOS on STM32
Added an RTOS to understand scheduling and synchronization:
- Multi-tasking and task priorities
- Mutexes and semaphores

The confusing part was understanding why everything deadlocks sometimes if you're not careful with resource sharing.

### ARM Assembly (13+ programs)
This is where you actually learn architecture:
- GPIO configuration
- Timers and UART at the register level
- Interrupt handlers

Wrote bubble sort in pure Assembly because I wanted to understand the pain.

**More academic / isolated-piece exercises — solid work, but narrower in scope than the above:**

### Booth Multiplier (VHDL)
Spent time understanding Booth's algorithm and how to implement it efficiently on an FPGA. Trade-offs are interesting—it's not the fastest algorithm in theory, but if you optimize the layout and synthesis, it actually performs well. Part of the [VHDL-LABS](https://github.com/IKGB105/VHDL-LABS/tree/main/xilinx-labs/P7) coursework.

### IEEE-754 Floating-Point Calculator (VHDL)
Built a single-precision floating-point unit because the math behind IEEE-754 is more complex than I expected:
- Separate datapath modules for mantissa and exponent
- Proper rounding
- Exception flags (NaN, overflow, underflow)

It works but the testbench took longer than the actual design.

### FFT in Python
Signal processing project—computing frequency domain representation, visualization. Nothing groundbreaking but it's useful to understand when working with actual signals instead of abstractions.

### Transistor Amplifier Suite (Python)
Automated design of BJT/MOSFET amplifiers:
- Q-point calculation
- Load lines
- SOA margins

Built it as a standalone executable because I was tired of running Python scripts for every design. It's not pretty but it works.

---

## Languages & Tools

**HDL:** Verilog, VHDL, Amaranth HDL  
**Programming:** Python (simulators, automation), C (embedded), ARM Assembly, C++ (a bit), AVR Assembly  
**Platforms:** STM32F411, STM32F446, Arduino, ESP32, AVR ATmega8515  
**FPGA:** Xilinx (Spartan-6), Gowin (Tang Nano 1K)  
**Tools:** OpenOCD/GDB, GTKWave, Xilinx ISE/Vivado, KiCAD, COMSOL, LaTeX

---

## Stats (if that matters)

- 14+ completed projects
- ~10,000 lines of actual code (not counting exercises)
- 6 programming languages
- 2 FPGA vendors
- 13+ programs in Assembly
- Cambridge English B2 certified

---

## What I learned

The obvious stuff: understanding CPU architecture teaches you more about programming than most computer science courses. Debugging with OpenOCD/GDB saves you when things break at the register level. VHDL is verbose for a reason. Assembly hurts but afterward you read C code differently.

Less obvious: datasheets have all the answers if you actually read them. Exhaustive testing prevents disasters. Python is good enough for hardware simulation if your logic is correct. Real hardware teaches lessons that simulation can't.

---

## Code quality disclaimer

Some of this is university coursework, some is learning-by-doing. If you see code that looks questionable, it probably seemed like the right approach at the time. Each project has something useful in it, even if the implementation isn't perfect.

Open to feedback. If something is confusing or broken, let me know.
