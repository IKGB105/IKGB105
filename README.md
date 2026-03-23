# hey, i'm an electronics student 👋

so basically, this is everything i've been doing at university. started obsessed with understanding how things actually work at the hardware level, and... here we are.

## what i do

- design CPUs (built a complete RISC-V simulator in Python because existing simulators didn't show me what i actually wanted to see)
- program microcontrollers in C + Assembly (when i want to control exactly what the hardware does)
- synthesize stuff on FPGAs (Xilinx + Gowin, because why limit yourself to one)
- debug at register level (OpenOCD + GDB is my best friend)
- automate things when i'm tired of doing the same stuff manually

## main projects

### RISC-V Simulator
ok this is where it all started. i wanted to understand the complete architecture, not just memorize instructions. so i built:
- a decoder that extracts opcode, rd, funct3, rs1, rs2, everything
- an ALU with 16+ operations (ADD, MUL, DIV, MULH... the ones you actually need)
- a 32x32 RegisterFile that validates according to IEEE spec
- VCD generation to see exactly what happens in GTKWave

```python
# the decoder parses RISC-V instructions and tells you exactly what each thing is
decoder = RISCVDecoder(instruction=0x12345678)
opcode, rd, funct3, rs1, rs2 = decoder.extract()
```

it's in Python/Amaranth HDL. when i finished it i had that "aaah, now i get why it's done this way" moment

### ALU + RegisterFile in Verilog
afterwards i wanted to synthesize this on real hardware. 20+ test vectors, exhaustive coverage. i saw exactly where things fail at timing level

### Booth Multiplier (VHDL)
this was interesting because i had to understand the math behind it. slower conceptually than conventional multipliers, but if you optimize it right... it works. synthesized on Xilinx, played with speed vs area trade-offs

### RFID Access Control System (STM32F446)
this was the first "real" project i did. RFID tag reading, permission validation, relay control for a door lock. sounds simple but involves custom drivers, interrupt handling, and making sure it doesn't explode in production

### FreeRTOS on STM32
added an RTOS. multi-tasking, synchronization with mutexes, semaphores. the confusing part was understanding context switching and why everything deadlocks sometimes if you're not careful

### 13+ Programs in ARM Assembly
this is where you really understand the hardware. GPIO, timers, UART, interrupt handlers. wrote bubble sort in pure Assembly because... well, why not. it hurt but i learned a lot

### Arduino + C++ (23+ C exercises, 30+ C++)
solid programming foundation. it's not fancy but it's important to know what you're doing

### FFT in Python
signal processing. spectrogram, analysis, visualization. useful when you need to know what frequencies something's generating

### Amplifier Design Suite (Python)
automated the design of BJT/MOSFET/JFET amplifiers. Q-point calculation, AC/DC load lines. packaged it as an executable with PyInstaller. it's ugly but it works

## languages i picked up (for better or worse)

| language | what for | experience |
|----------|----------|-------------|
| **Verilog** | hardware synthesis, working testbenches | quite a bit |
| **VHDL** | more verbose than Verilog but Xilinx likes it | quite a bit |
| **Python** | simulators, automation, DSP, my "duct tape" | a lot |
| **ARM Assembly** | pure low-level stuff, hurts but you gotta know it | quite a bit |
| **C** | STM32, HAL, embedded things | quite a bit |
| **AVR Assembly** | simple microcontrollers, less power | some |
| **C++** | OOP, Arduino sketches | basic but works |

## tools i used

- **Xilinx ISE/Vivado** - FPGA synthesis (steep learning curve but worth it)
- **Gowin EDA** - more accessible alternative, Tang Nano 1K
- **OpenOCD + GDB** - debugging at register level (this is critical)
- **GTKWave** - analyze VCD traces when something doesn't work
- **KiCAD** - schematic design, though i prefer working with FPGAs
- **STM32CubeIDE** - HAL, USB, interrupts, the standard stuff
- **Multisim** - SPICE simulation when i need to verify analog electronics
- **LaTeX** - documentation, Beamer presentations

## platforms i got into

- **STM32F411** (Blackpill) - my first serious ARM
- **STM32F446RETx** - when i needed more power
- **Arduino** - for quick prototyping
- **ESP32** - IoT, WiFi, when you need wireless
- **AVR ATmega8515** - the old stuff but good learning
- **Xilinx Spartan-6** (Mimas) - my lab FPGA
- **Gowin Tang Nano 1K** - small FPGA but powerful

## what i learned (the honest version)

- understanding CPU architecture is one of the best computer science courses you can take
- debugging with OpenOCD/GDB saves you when stuff explodes at register level
- VHDL isn't that bad once you understand why it's so verbose
- Assembly is painful but once you master it, you see C code differently
- datasheet documentation is your best friend (read every section)
- exhaustive testing prevents headaches later
- Python is "good enough" for simulators (startup time doesn't matter if your logic is correct)

## quick stats

```
14+ projects finished
10,000+ lines of code (more if you count exercises)
6 languages mastered more or less
2 FPGA vendors (Xilinx, Gowin)
5 different microcontroller families
13+ programs in Assembly
Cambridge B2 Advanced English
```

## contact

📧 **email:** [your.email@uaa.edu.mx](mailto:your.email@uaa.edu.mx)  
💼 **linkedin:** [linkedin.com/in/your_user](https://linkedin.com/)  
☎️ **phone:** +52 XXXXXXXXX  
📍 **location:** Aguascalientes, Mexico 🇲🇽  

## the weird part

if you explore the repo you'll see files with ugly naming, disorganized folders, and code that probably won't impress you. that's because these were university projects, not a polished product. but each of those files has something i learned. if something doesn't make sense, it's probably because it seemed like a good idea at the time

## disclaimer

i'm not an engineer yet (still in semester 6 😅). but i've put serious hours into understanding hardware, and that counts for something. if you see something that's poorly explained or questionable code, it's because it seemed like a good idea when i wrote it

⭐ if you find something useful, give it a star. it means someone else thinks it wasn't a waste of time

happy hacking 🚀
