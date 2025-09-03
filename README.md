# 32-bit RISC-V CPU Core  

![Build](https://img.shields.io/badge/build-passing-brightgreen)  
![Simulation](https://img.shields.io/badge/simulation-verified-blue)  
![FPGA](https://img.shields.io/badge/fpga-tested-orange)  
![License](https://img.shields.io/badge/license-MIT-lightgrey)  

A custom 32-bit pipelined RISC-V CPU core designed and implemented in SystemVerilog. This project demonstrates the full lifecycle of CPU design, from RTL development and simulation to FPGA prototyping and debugging, with emphasis on hazard handling, timing closure, and verification. 

---

## 🚀 Features  
- **Instruction Set**: Implements the RV32I base instruction set  
- **Pipeline**: Classic 5-stage pipeline (IF → ID → EX → MEM → WB)  
- **Hazard Handling**:  
  - Data forwarding  
  - Stall insertion for load-use hazards  
  - Branch hazard detection and flush  
- **Verification**:  
  - UVM-style testbench in SystemVerilog  
  - Directed and constrained-random tests  
  - SystemVerilog Assertions (SVA) for protocol and timing checks  
- **FPGA Support**: Synthesized and validated on Xilinx FPGA with Integrated Logic Analyzer (ILA) for real-time debug  

---

## 🛠️ Tools & Technologies  
- **RTL & Verification**: SystemVerilog  
- **Simulation**: Synopsys VCS / Verilator  
- **Lint/CDC**: SpyGlass / Verible  
- **Synthesis**: Synopsys Design Compiler / Vivado (FPGA)  
- **Timing Analysis**: Synopsys PrimeTime  
- **FPGA Prototyping**: Xilinx Vivado + ILA  
- **Documentation**: Markdown, WaveDrom (pipeline/timing diagrams)  

---

## 📂 Repository Structure  
├── rtl/ # CPU RTL source code (SystemVerilog)

│ ├── core/ # Pipeline stages, ALU, regfile, hazard unit

│ └── top/ # Top-level integration

├── tb/ # Testbench environment

│ ├── uvm/ # UVM-style components (drivers, monitors, scoreboards)

│ └── directed/ # Directed unit tests

├── sim/ # Simulation scripts and configs

├── synth/ # Synthesis & FPGA build files

├── docs/ # Documentation, diagrams, and notes

└── README.md # This file



---

## ⚡ Getting Started  

### Prerequisites  
- Verilator (for open-source sim) or Synopsys VCS (for industry tools)  
- Xilinx Vivado (for FPGA prototyping)  
- Make, Python 3.x (for automation scripts)  

### Running Simulation  
```bash
cd sim
make verilator     # Run simulation with Verilator
make vcs           # Run simulation with Synopsys VCS
```

---

Running FPGA Build
```bash
Copy code
cd synth/fpga
vivado -mode batch -source build.tcl
```

---

✅ Verification Strategy


Directed Tests: Cover basic ALU ops, memory access, and branching

Randomized Tests: Instruction streams with assertions for corner cases

Coverage: Instruction, functional, and code coverage metrics collected in simulation

FPGA Validation: Real programs executed with outputs checked via on-chip debug probes

---

📊 Pipeline Diagram
mermaid
Copy code
graph LR
    IF[Instruction Fetch] --> ID[Instruction Decode]
   
    ID --> EX[Execute]
   
    EX --> MEM[Memory Access]
    
    MEM --> WB[Write Back]

---
    
🔮 Future Work


Implement RV32M (Multiply/Divide) extension

Add instruction & data caches

Support branch prediction

Enhance FPGA demo with a small SoC (UART, GPIO)

---

## 👤 Author  
**Gavin DeZoysa**  
- [LinkedIn](https://www.linkedin.com/in/gavindezoysa)  
- [Portfolio](https://gavindezoysa.github.io)  

---

## 📜 License  

MIT License  

Copyright (c) 2025 Gavin DeZoysa  

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:  

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.  

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.  
