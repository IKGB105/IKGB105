# Electronics Engineering - Hardware & Architecture

Electronics student at UAA (6th semester). Working on CPU design, FPGA synthesis, embedded systems, and whatever else doesn't fit in a neat category.

**Aguascalientes, Mexico** | ikergarcia450@gmail.com | +52 477 691 4456

---

## What I'm doing

Started with basic microcontroller projects but got obsessed with understanding why CPUs are designed the way they are. So I built a RISC-V simulator to work through the decode logic, instruction execution, register files, everything. After that, synthesizing hardware modules felt like the next logical step.

Spend most of my time on:
- RISC-V architecture and ISA implementation
- FPGA design on Xilinx and Gowin platforms
- Embedded systems (STM32, FreeRTOS, custom drivers)
- Low-level ARM Assembly when I need precise hardware control
- Debugging with OpenOCD/GDB when things don't work (which is often)

---

## Main projects

### RISC-V Simulator
Built a complete CPU simulator to actually understand what's happening at the instruction level. Not just a testbench—a working model with:
- Full instruction decoder (extracts opcode, registers, immediate values)
- 32-bit ALU with all the standard operations
- Register file with proper RISC-V semantics (x0 is always zero)
- VCD output to trace execution in GTKWave

Started in Python/Amaranth, but after that I also implemented the ALU and RegisterFile in Verilog so I could see how it synthesizes on actual hardware.

### Booth Multiplier (VHDL)
Spent time understanding Booth's algorithm and how to implement it efficiently on an FPGA. Trade-offs are interesting—it's not the fastest algorithm in theory, but if you optimize the layout and synthesis, it actually performs well.

### IEEE-754 Floating-Point Calculator (VHDL)
Built a single-precision floating-point unit because the math behind IEEE-754 is more complex than I expected. Separate datapath modules for mantissa and exponent, proper rounding, exception flags. It works but the testbench took longer than the actual design.

### RFID Access Control System (STM32F446)
First real project that wasn't just an assignment. Reading RFID tags, validating against a list, controlling a relay for a door lock. Involved custom drivers, interrupt handling, making sure it doesn't randomly fail in production. Nothing fancy but it works.

### FreeRTOS on STM32
Added an RTOS to understand scheduling and synchronization. Multi-tasking, task priorities, mutexes, semaphores. The confusing part was understanding why everything deadlocks sometimes if you're not careful with resource sharing.

### ARM Assembly (13+ programs)
This is where you actually learn architecture. GPIO configuration, timers, UART at the register level, interrupt handlers. Wrote bubble sort in pure Assembly because I wanted to understand the pain.

### FFT in Python
Signal processing project—computing frequency domain representation, visualization. Nothing groundbreaking but it's useful to understand when working with actual signals instead of abstractions.

### Transistor Amplifier Suite (Python)
Automated design of BJT/MOSFET amplifiers. Q-point calculation, load lines, SOA margins. Built it as a standalone executable because I was tired of running Python scripts for every design. It's not pretty but it works.

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

---

**Email:** ikergarcia450@gmail.com  
**GitHub:** [@IKGB105](https://github.com/IKGB105)  
**LinkedIn:** [Iker Garcia](https://linkedin.com/)  

Last update: March 2026
