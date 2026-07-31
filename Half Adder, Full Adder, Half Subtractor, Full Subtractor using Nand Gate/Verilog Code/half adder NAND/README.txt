# Half Adder using NAND Gates (Verilog)

## 📖 Overview

This project implements a **1-bit Half Adder** using **only NAND gates** in Verilog HDL. A Half Adder performs the addition of two single-bit binary inputs and produces a **Sum** and a **Carry** output.

The design demonstrates how a complete arithmetic circuit can be constructed using only **NAND gates**, one of the fundamental universal logic gates capable of implementing any Boolean function.

This project is ideal for learning gate-level modeling, digital arithmetic, and universal gate implementations.

---

## ✨ Features

- 1-bit Half Adder
- NAND-only implementation
- Pure gate-level design
- Generates Sum and Carry outputs
- Fully synthesizable Verilog HDL
- FPGA and ASIC compatible
- Educational implementation

---

## 📋 Specifications

| Parameter | Description |
|-----------|-------------|
| Language | Verilog HDL |
| Module Name | `ha_nand` |
| Inputs | A, B |
| Outputs | Sout (Sum), Cout (Carry) |
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

            ▼

      +------------------+
      |   Half Adder     |
      | using NAND Gates |
      +--------+---------+
               |
      +--------+--------+
      |                 |
    Sout             Cout
```

---

## ⚙️ Functional Description

The Half Adder performs the addition of two binary inputs:

```
A + B
```

It generates:

### Sum

```
Sum = A ⊕ B
```

### Carry

```
Carry = A · B
```

The XOR and AND operations are implemented exclusively using interconnected **NAND gates**, eliminating the need for any other logic gate.

---

## 📊 NAND Logic Network

The design generates intermediate signals:

```
w0

↓

w1

↓

w2
```

The final outputs are produced as:

- **Sum** from the NAND-based XOR network
- **Carry** by inverting the NAND output using another NAND gate

---

## 🔢 Truth Table

| A | B | Sum (Sout) | Carry (Cout) |
|---|---|------------|--------------|
| 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 1 |

---

## 🔄 Logic Flow

```
Inputs

A

B

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
- Outputs update immediately when any input changes
- Propagation delay depends on the NAND gate network depth

---

## 💡 Applications

- Arithmetic Logic Units (ALUs)
- Binary arithmetic circuits
- Ripple Carry Adders
- FPGA educational projects
- Gate-level digital design
- Computer arithmetic
- ASIC standard-cell implementations
- Digital electronics laboratories

---

## ✅ Advantages

- Uses only NAND gates
- Demonstrates universal gate implementation
- Fully synthesizable RTL
- Compact and modular design
- Suitable for FPGA and ASIC implementation
- Excellent educational example of gate-level arithmetic design

---

## 🧪 Simulation

### Recommended Simulators

- Xilinx Vivado Simulator
- ModelSim
- QuestaSim
- Icarus Verilog
- GTKWave

### Sample Test Cases

| A | B | Expected Sum | Expected Carry |
|---|---|--------------|----------------|
| 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 1 |

---

## 🔧 Synthesis

- FPGA Compatible ✅
- ASIC Compatible ✅
- Fully Synthesizable RTL ✅
- Gate-level implementation
- Uses only universal NAND gates

> **Note:** The Half Adder is implemented entirely using NAND gates, illustrating the universality of the NAND gate. While this implementation is excellent for understanding digital logic, synthesis tools generally optimize higher-level RTL descriptions into more efficient gate-level circuits with improved timing, area, and power characteristics.

---

## 📁 Project Structure

```text
half_adder_nand/

├── rtl/
│   └── ha_nand.v
│
├── tb/
│   └── ha_nand_tb.v
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

- Implement Full Adder using NAND gates
- Design a multi-bit Ripple Carry Adder
- Compare NAND-only and behavioral implementations
- Analyze propagation delay and gate count
- Develop a self-checking SystemVerilog testbench
- Extend the design to parameterized arithmetic circuits

---

## 👨‍💻 Author

**Maddineni Dileep Kumar**

---
