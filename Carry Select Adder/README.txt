# 4-bit Carry Select Adder (CSLA) using Verilog

## 📖 Overview

This project implements a **4-bit Carry Select Adder (CSLA)** using Verilog HDL. A Carry Select Adder is a high-speed adder architecture that improves performance over the traditional Ripple Carry Adder by **precomputing two possible sums and carry outputs**—one assuming the carry-in is `0` and the other assuming it is `1`.

Once the actual carry input becomes available, multiplexers select the correct sum and carry output. This significantly reduces carry propagation delay and increases arithmetic performance.

The design consists of:

- **Full Adder modules**
- **2:1 Multiplexer modules**
- **Carry Select Adder top module**

---

## ✨ Features

- 4-bit binary addition
- High-speed Carry Select architecture
- Parallel computation for carry-in = 0 and carry-in = 1
- Multiplexer-based output selection
- Modular design using Full Adders and Multiplexers
- Fully synthesizable Verilog HDL
- FPGA and ASIC compatible

---

## 📋 Specifications

| Parameter | Description |
|-----------|-------------|
| Language | Verilog HDL |
| Top Module | `carry_select` |
| Submodules | `full_adder`, `mux` |
| Input Width | 4 bits |
| Output Width | 4-bit Sum + Carry |
| Architecture | Carry Select Adder |
| Logic Type | Combinational |

---

## 🏗️ Block Diagram

```
                A[3:0]
                   │
                   │
                B[3:0]
                   │
                   ▼

         +-------------------------+
Carry=0->| Ripple Carry Adder #1   |
         +-------------------------+
                   │
                   │

         +-------------------------+
Carry=1->| Ripple Carry Adder #2   |
         +-------------------------+
                   │
                   │
                   ▼

             2:1 Multiplexers
                   ▲
                   │
             Carry Input
                   │
                   ▼

             Sum[3:0], Cout
```

---

## ⚙️ Functional Description

The Carry Select Adder performs two additions simultaneously:

### Path 1

Assumes:

```
Carry In = 0
```

Generates:

```
Sum0

Carry0
```

---

### Path 2

Assumes:

```
Carry In = 1
```

Generates:

```
Sum1

Carry1
```

---

### Multiplexer Selection

Once the actual carry input arrives,

```
Carry = 0

↓

Select Sum0
```

or

```
Carry = 1

↓

Select Sum1
```

The same logic selects the correct carry output.

---

## 📊 Data Flow

```
          Carry = 0

        Ripple Adder

             │

             ▼

          Sum0 Cout0

             │

             │

          Multiplexers

             ▲

             │

          Carry Input

             │

             ▼

          Sum Cout

             ▲

             │

        Ripple Adder

          Carry = 1

             │

             ▼

          Sum1 Cout1
```

---

## 🔢 Example Calculation

### Example

```
A = 0101 (5)

B = 0011 (3)

Carry = 0
```

Adder assuming Carry = 0

```
5 + 3 = 8
```

Adder assuming Carry = 1

```
5 + 3 + 1 = 9
```

Multiplexer selects

```
8
```

Final Result

```
Sum = 1000

Carry = 0
```

---

## 📊 Sample Results

| A | B | Carry In | Sum | Carry Out |
|---|---|----------|-----|-----------|
| 0101 | 0011 | 0 | 1000 | 0 |
| 0101 | 0011 | 1 | 1001 | 0 |
| 1111 | 0001 | 0 | 0000 | 1 |
| 1111 | 1111 | 1 | 1111 | 1 |

---

## ⏱️ Timing Behavior

- Pure combinational logic
- No clock required
- Two additions execute in parallel
- Multiplexer delay determines the final selection
- Faster than a Ripple Carry Adder for larger bit widths

---

## 💡 Applications

- Arithmetic Logic Units (ALUs)
- High-speed processors
- Digital Signal Processing (DSP)
- FPGA arithmetic units
- Embedded processors
- Address generation
- High-performance computing
- Computer architecture

---

## ✅ Advantages

- Faster than Ripple Carry Adder
- Parallel computation reduces carry propagation delay
- Modular and scalable architecture
- Fully synthesizable RTL
- Suitable for FPGA and ASIC implementation
- Improved arithmetic performance

---

## ⚠️ Limitation

The Carry Select Adder achieves higher speed by duplicating adder hardware for both carry possibilities. This increases **area and power consumption** compared to a Ripple Carry Adder.

---

## 🧪 Simulation

### Recommended Simulators

- Xilinx Vivado Simulator
- ModelSim
- QuestaSim
- Icarus Verilog
- GTKWave

### Sample Test Cases

| A | B | Carry In | Expected Sum | Expected Carry |
|---|---|----------|--------------|----------------|
| 0000 | 0000 | 0 | 0000 | 0 |
| 0101 | 0011 | 0 | 1000 | 0 |
| 0101 | 0011 | 1 | 1001 | 0 |
| 1111 | 0001 | 0 | 0000 | 1 |
| 1111 | 1111 | 1 | 1111 | 1 |

---

## 🔧 Synthesis

- FPGA Compatible ✅
- ASIC Compatible ✅
- Fully Synthesizable RTL ✅
- Pure combinational implementation
- Hierarchical modular design

> **Note:** This implementation computes two complete 4-bit ripple-carry additions in parallel—one assuming `carry = 0` and the other assuming `carry = 1`. While this reduces the carry propagation delay, it approximately doubles the adder hardware. Carry Select Adders are generally more beneficial for larger bit widths, where the speed improvement outweighs the additional area.

---

## 📁 Project Structure

```text
carry_select_adder/

├── rtl/
│   ├── full_adder.v
│   ├── mux.v
│   └── carry_select.v
│
├── tb/
│   └── carry_select_tb.v
│
├── docs/
│   ├── block_diagram.png
│   ├── csla_architecture.png
│   ├── timing_diagram.png
│   └── waveform.png
│
└── README.md
```

---

## 🚀 Future Improvements

- Parameterize the adder width
- Implement square-root Carry Select Adder (SQRT-CSLA)
- Optimize area using Binary-to-Excess-1 Converter (BEC)
- Compare timing with Ripple Carry and Carry Lookahead Adders
- Add overflow detection
- Develop a self-checking SystemVerilog testbench
- Analyze FPGA resource utilization and timing performance

---

## 👨‍💻 Author

**Maddineni Dileep Kumar**

---
