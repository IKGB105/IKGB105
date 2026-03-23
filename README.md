# hey, soy estudiante de electrónica 👋

mira, esto es basicamente todo lo que he estado haciendo en la universidad. empecé obsesionado con entender cómo funcionan realmente las cosas a nivel de hardware, y bueno... aquí estamos.

## qué hago

- diseño CPUs (simulé una RISC-V completa en Python porque los simuladores existentes no me mostraban lo que realmente quería ver)
- programo microcontroladores en C + Assembly (cuando quiero controlar exactamente qué hace el hardware)
- sintetizo cosas en FPGAs (Xilinx + Gowin, porque porqué limitarse a una)
- debuggeo a nivel de registros (OpenOCD + GDB es mi mejor amigo)
- automatizo cosas cuando estoy cansado de hacer lo mismo manual

## proyectos principales

### RISC-V Simulator
ok aquí es donde todo empezó. quería entender la arquitectura completa, no solo memorizar instrucciones. entonces armé:
- un decodificador que extrae opcode, rd, funct3, rs1, rs2, todo
- una ALU con 16+ operaciones (ADD, MUL, DIV, MULH... los que realmente necesitas)
- un RegisterFile 32x32 que valida según especificación IEEE
- generación de VCD para ver exactamente qué pasa en GTKWave

```python
# el decodificador parsea instrucciones RISC-V y te dice exactamente qué es cada cosa
decoder = RISCVDecoder(instruction=0x12345678)
opcode, rd, funct3, rs1, rs2 = decoder.extract()
```

está en Python/Amaranth HDL. cuando lo terminé tuve ese momento de "aaah, ahora entiendo por qué se hace así"

### ALU + RegisterFile en Verilog
después quise sintetizar esto en hardware real. 20+ test vectors, cobertura exhaustiva. vi exactamente dónde fallan las cosas a nivel de timing

### Multiplicador Booth (VHDL)
este fue interesante porque tuve que entender la matemática detrás. más lento conceptualmente que los multiplicadores convencionales, pero si lo optimizas bien... funciona. sintetizé en Xilinx, jugué con trade-offs entre velocidad y área

### Sistema RFID (STM32F446)
esto fue el primer proyecto "real" que hice. lectura de tags RFID, validación de permisos, control de relé para una cerradura. suena simple pero involucra drivers personalizados, manejo de interrupts, y asegurar que no explote en producción

### FreeRTOS en STM32
agregué un RTOS. multi-tasking, sincronización con mutexes, semáforos. la parte confusa fue entender context switching y por qué a veces se deadlockea todo si no tienes cuidado

### 13+ Programas en ARM Assembly
esto es donde realmente entiendes el hardware. GPIO, timers, UART, interrupt handlers. escribí bubble sort en Assembly puro porque... bueno, por qué no. fue dolor pero aprendí mucho

### Arduino + C++ (23+ ejercicios de C, 30+ de C++)
base sólida de programación. no es fancy pero es importante saber qué estás haciendo

### FFT en Python
procesamiento de señales. espectrograma, análisis, visualización. útil cuando necesitas saber qué frecuencias está generando algo

### Suite de diseño de amplificadores (Python)
automatizó el diseño de amplificadores BJT/MOSFET/JFET. cálculo de punto Q, cargas AC/DC. lo empaquetté como ejecutable con PyInstaller. está feo pero funciona

## lenguajes que dominé (para bien o mal)

| lenguaje | qué onda | experiencia |
|----------|---------|-------------|
| **Verilog** | para sintetizar en hardware, testbenches que funcionan | bastante |
| **VHDL** | más verbose que Verilog pero Xilinx lo prefiere | bastante |
| **Python** | simuladores, automatización, DSP, es mi "duct tape" | mucha |
| **ARM Assembly** | bajo nivel puro, duele pero necesitas saberlo | bastante |
| **C** | STM32, HAL, cosas embebidas | bastante |
| **AVR Assembly** | microcontroladores simples, menos potencia | algo |
| **C++** | OOP, Arduino sketches | básico pero va |

## herramientas que usé

- **Xilinx ISE/Vivado** - síntesis FPGA (curva de aprendizaje pero vale la pena)
- **Gowin EDA** - alternativa más accesible, Tang Nano 1K
- **OpenOCD + GDB** - debugging a nivel de registros (esto es crítico)
- **GTKWave** - analizar trazas VCD cuando algo no funciona
- **KiCAD** - diseño de esquemáticos, aunque prefiero trabajar con FPGAs
- **STM32CubeIDE** - HAL, USB, interrupts, lo estándar
- **Multisim** - simulación SPICE cuando necesito verificar electrónica analógica
- **LaTeX** - documentación, presentaciones Beamer

## plataformas donde me metí

- **STM32F411** (Blackpill) - mi primer ARM serio
- **STM32F446RETx** - cuando necesitaba más poder
- **Arduino** - para prototipear rápido
- **ESP32** - IoT, WiFi, cuando necesitas wireless
- **AVR ATmega8515** - lo antiguo pero es un buen aprendizaje
- **Xilinx Spartan-6** (Mimas) - mi FPGA de laboratorio
- **Gowin Tang Nano 1K** - FPGA chiquita pero poderosa

## lo que aprendí (la versión honesta)

- entender la arquitectura de una CPU es uno de los mejores cursos de ciencias de la computación que puedes tomar
- debugging con OpenOCD/GDB te salva cuando algo explota a nivel de registros
- VHDL no es tan malo una vez que entiendes por qué es tan verbose
- Assembly es dolor pero cuando lo dominas, ves el código en C diferente
- la documentación de datasheets es tu mejor amiga (lee cada sección)
- testing exhaustivo previene dolores de cabeza después
- Python es "good enough" para simuladores (startup time no importa si tu lógica es correcta)

## stats rápidas

```
14+ proyectos finalizados
10,000+ líneas de código (más si cuentas ejercicios)
6 lenguajes dominados más o menos
2 fabricantes FPGA (Xilinx, Gowin)
5 familias de microcontroladores diferentes
13+ programas en Assembly
Cambridge B2 Advanced en inglés
```

## contacto

📧 **email:** [tu.email@uaa.edu.mx](mailto:tu.email@uaa.edu.mx)  
💼 **linkedin:** [linkedin.com/in/tu_usuario](https://linkedin.com/)  
☎️ **teléfono:** +52 XXXXXXXXX  
📍 **ubicación:** Aguascalientes, México 🇲🇽  

## lo raro

si explorás el repo vas a ver archivos con nomenclatura fea, carpetas desorganizadas, y código que probablemente no te enamore. es que fueron proyectos universitarios, no un producto pulido. pero cada uno de esos archivos tiene algo que aprendí. si algo no tiene sentido, probablemente fue porque en su momento estaba aprendiendo

## disclaimer

no soy ingeniero aún (todavía estoy en 6to semestre 😅). pero he metido horas serias entendiendo hardware, y eso cuenta para algo. si ves algo que está mal explicado o código cuestionable, es porque en su momento parecía buen idea

⭐ si algo te parece útil, dale una estrella. significa que alguien más piensa que no fue pérdida de tiempo

happy hacking 🚀
