# Full Adder using NAND Gates (Verilog)

## 📖 Overview

This project implements a **1-bit Full Adder** using **only NAND gates** in Verilog HDL. Since the NAND gate is a **universal logic gate**, any combinational or sequential logic circuit can be constructed using only NAND gates.

The design accepts three inputs:

- **A**
- **B**
- **Carry-in (Cin)**

and produces:

- **Sum (Sout)**
- **Carry-out (Cout)**

This project demonstrates gate-level digital design and illustrates how complex arithmetic circuits can be built using a single universal gate.

---

## ✨ Features

- 1-bit Full Adder
- NAND-only implementation
- Universal gate realization
- Pure gate-level design
- Fully synthesizable Verilog HDL
- FPGA and ASIC compatible
- Educational implementation

---

## 📋 Specifications

| Parameter | Description |
|-----------|-------------|
| Language | Verilog HDL |
| Module Name | `fa_nand` |
| Inputs | A, B, Cin |
| Outputs | Sout, Cout |
| Logic Style | Gate-Level |
| Universal Gate | NAND |

---

## 🏗️ Block Diagram

```
             A
             │
             │
             ▼

          NAND Network

             ▲
             │
             │

             B

             │

            Cin

             │

             ▼

      +----------------+
      | Full Adder     |
      | using NANDs    |
      +-------+--------+
              |
      +-------+-------+
      |               |
    Sout           Cout
```

---

## ⚙️ Functional Description

The Full Adder computes:

### Sum

```
S = A ⊕ B ⊕ Cin
```

### Carry

```
Cout = AB + ACin + BCin
```

Instead of directly using XOR, AND, and OR gates, the design realizes both equations exclusively through interconnected **NAND gates**.

---

## 📊 NAND Network

The circuit uses intermediate signals:

```
w0

↓

w1

↓

w2

↓

w3

↓

w4

↓

w5

↓

w6
```

These intermediate signals implement the XOR and carry-generation logic required for the Full Adder.

---

## 🔢 Truth Table

| A | B | Cin | Sout | Cout |
|---|---|-----|------|------|
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 0 |
| 0 | 1 | 0 | 1 | 0 |
| 0 | 1 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 | 0 |
| 1 | 0 | 1 | 0 | 1 |
| 1 | 1 | 0 | 0 | 1 |
| 1 | 1 | 1 | 1 | 1 |

---

## 🔄 Logic Flow

```
Inputs

A

B

Cin

↓

NAND Gate Network

↓

Intermediate Signals

↓

Sum

Carry
```

---

## ⏱️ Timing Behavior

- Pure combinational logic
- No clock required
- Output changes immediately when any input changes
- Propagation delay depends on the depth of the NAND gate network

---

## 💡 Applications

- Arithmetic Logic Units (ALUs)
- Digital processors
- FPGA learning projects
- Gate-level digital design
- Computer architecture
- Educational digital electronics
- Arithmetic circuit implementation
- ASIC standard-cell design

---

## ✅ Advantages

- Uses only NAND gates
- Demonstrates universal gate implementation
- Fully synthesizable RTL
- Modular and reusable design
- Suitable for FPGA and ASIC implementation
- Excellent educational example of gate-level optimization

---

## 🧪 Simulation

### Recommended Simulators

- Xilinx Vivado Simulator
- ModelSim
- QuestaSim
- Icarus Verilog
- GTKWave

### Sample Test Cases

| A | B | Cin | Expected Sout | Expected Cout |
|---|---|-----|---------------|---------------|
| 0 | 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 1 | 0 |
| 1 | 0 | 1 | 0 | 1 |
| 1 | 1 | 0 | 0 | 1 |
| 1 | 1 | 1 | 1 | 1 |

---

## 🔧 Synthesis

- FPGA Compatible ✅
- ASIC Compatible ✅
- Fully Synthesizable RTL ✅
- Gate-level implementation
- Uses only universal NAND gates

> **Note:** NAND gates are universal, meaning any Boolean function can be implemented using only NAND gates. Although this implementation is educational and demonstrates gate-level construction, modern synthesis tools automatically optimize higher-level RTL descriptions into efficient gate-level netlists, often resulting in better area, timing, and power characteristics than manually constructed NAND-only logic.

---

## 📁 Project Structure

```text
full_adder_nand/

├── rtl/
│   └── fa_nand.v
│
├── tb/
│   └── fa_nand_tb.v
│
├── docs/
│   ├── block_diagram.png
│   ├── nand_network.png
│   ├── truth_table.png
│   └── waveform.png
│
└── README.md
```

---

## 🚀 Future Improvements

- Implement Half Adder using NAND gates
- Design Ripple Carry Adder using NAND-based Full Adders
- Compare NAND-only and behavioral implementations
- Analyze propagation delay and gate count
- Develop a self-checking SystemVerilog testbench
- Extend the design to 4-bit and 8-bit adders

---

## 👨‍💻 Author

**Maddineni Dileep Kumar**

---
