# Full Subtractor using NAND Gates (Verilog)

## 📖 Overview

This project implements a **1-bit Full Subtractor** using **only NAND gates** in Verilog HDL. A Full Subtractor performs the subtraction of two binary bits while considering a **borrow-in (Bin)** and generates both the **difference (Sout)** and the **borrow-out (Cout)**.

The design demonstrates how a complete arithmetic circuit can be realized using **only NAND gates**, highlighting the universality of the NAND gate in digital logic design.

This implementation is useful for learning gate-level modeling, Boolean logic optimization, and arithmetic circuit construction.

---

## ✨ Features

- 1-bit Full Subtractor
- NAND-only implementation
- Borrow-in and Borrow-out support
- Pure gate-level design
- Fully synthesizable Verilog HDL
- FPGA and ASIC compatible
- Educational implementation

---

## 📋 Specifications

| Parameter | Description |
|-----------|-------------|
| Language | Verilog HDL |
| Module Name | `fs_nand` |
| Inputs | A, B, Bin |
| Outputs | Sout (Difference), Cout (Borrow Out) |
| Logic Style | Gate-Level |
| Universal Gate | NAND |

---

## 🏗️ Block Diagram

```
               A
               │
               │
               ▼

          NAND Gate Network

               ▲
               │
               │

               B

               │

             Bin

               │

               ▼

      +----------------------+
      |   Full Subtractor    |
      |    using NAND Gates  |
      +----------+-----------+
                 |
        +--------+--------+
        |                 |
   Difference         Borrow Out
     (Sout)             (Cout)
```

---

## ⚙️ Functional Description

The Full Subtractor performs the operation:

```
A − B − Bin
```

It produces:

### Difference

```
Difference = A ⊕ B ⊕ Bin
```

### Borrow Out

```
Borrow = (¬A · B) + (Bin · ¬(A ⊕ B))
```

Instead of using XOR, AND, OR, and NOT gates directly, the circuit realizes both outputs exclusively through interconnected **NAND gates**.

---

## 📊 NAND Logic Network

The implementation generates intermediate signals:

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

These intermediate signals are combined to generate the final **Difference** and **Borrow Out** outputs.

---

## 🔢 Truth Table

| A | B | Bin | Difference | Borrow Out |
|---|---|-----|------------|------------|
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 1 |
| 0 | 1 | 0 | 1 | 1 |
| 0 | 1 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 | 0 |
| 1 | 0 | 1 | 0 | 0 |
| 1 | 1 | 0 | 0 | 0 |
| 1 | 1 | 1 | 1 | 1 |

---

## 🔄 Logic Flow

```
Inputs

A

B

Bin

↓

NAND Gate Network

↓

Intermediate Signals

↓

Difference

Borrow Out
```

---

## ⏱️ Timing Behavior

- Pure combinational logic
- No clock required
- Outputs update immediately when any input changes
- Propagation delay depends on the NAND gate network depth

---

## 💡 Applications

- Arithmetic Logic Units (ALUs)
- Binary subtraction circuits
- Digital processors
- FPGA educational projects
- Gate-level digital design
- Computer arithmetic units
- ASIC standard-cell implementations
- Digital electronics laboratories

---

## ✅ Advantages

- Uses only NAND gates
- Demonstrates universal gate implementation
- Fully synthesizable RTL
- Modular and reusable design
- Suitable for FPGA and ASIC implementation
- Excellent educational example of arithmetic circuit construction

---

## 🧪 Simulation

### Recommended Simulators

- Xilinx Vivado Simulator
- ModelSim
- QuestaSim
- Icarus Verilog
- GTKWave

### Sample Test Cases

| A | B | Bin | Expected Difference | Expected Borrow |
|---|---|-----|---------------------|-----------------|
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 1 |
| 0 | 1 | 0 | 1 | 1 |
| 1 | 0 | 1 | 0 | 0 |
| 1 | 1 | 1 | 1 | 1 |

---

## 🔧 Synthesis

- FPGA Compatible ✅
- ASIC Compatible ✅
- Fully Synthesizable RTL ✅
- Gate-level implementation
- Uses only universal NAND gates

> **Note:** This implementation realizes the Full Subtractor entirely with NAND gates, demonstrating that NAND is a universal gate capable of implementing any Boolean function. Although this approach is valuable for learning digital logic, modern synthesis tools typically optimize behavioral RTL into more efficient gate-level implementations with better timing, area, and power characteristics.

---

## 📁 Project Structure

```text
full_subtractor_nand/

├── rtl/
│   └── fs_nand.v
│
├── tb/
│   └── fs_nand_tb.v
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

- Implement Half Subtractor using NAND gates
- Design a 4-bit Ripple Borrow Subtractor
- Compare NAND-only and behavioral implementations
- Analyze gate count and propagation delay
- Develop a self-checking SystemVerilog testbench
- Extend the design to parameterized multi-bit subtractors

---

## 👨‍💻 Author

**Maddineni Dileep Kumar**
