# 4-bit Binary Multiplier using Shift-and-Add (Verilog)

## 📖 Overview

This project implements a **4-bit unsigned binary multiplier** using the **Shift-and-Add multiplication algorithm** in Verilog HDL. The multiplier generates an **8-bit product** by examining each bit of the multiplier and conditionally adding shifted versions of the multiplicand.

The design demonstrates one of the most fundamental hardware multiplication techniques used in digital systems and serves as an introduction to arithmetic circuit design.

Unlike the built-in multiplication (`*`) operator, this implementation explicitly performs multiplication using **partial products** and **binary addition**, making it useful for learning RTL design concepts.

---

## ✨ Features

- 4-bit unsigned multiplication
- Produces an 8-bit product
- Shift-and-Add multiplication algorithm
- Partial product generation
- Pure combinational logic
- Fully synthesizable Verilog HDL
- FPGA and ASIC compatible

---

## 📋 Specifications

| Parameter | Description |
|-----------|-------------|
| Language | Verilog HDL |
| Module Name | `multiplier` |
| Multiplicand Width | 4 bits |
| Multiplier Width | 4 bits |
| Output Width | 8 bits |
| Algorithm | Shift-and-Add |
| Logic Type | Combinational |

---

## 🏗️ Block Diagram

```
                +---------------------------+
A[3:0] -------->|                           |
                |  Shift-and-Add Multiplier |
B[3:0] -------->|                           |
                +------------+--------------+
                             |
                             |
                        Product[7:0]
```

---

## ⚙️ Functional Description

The module generates four partial products based on the bits of the multiplier (`b`).

### Partial Products

```
If b[0] = 1

t1 = a << 0
```

```
If b[1] = 1

t2 = a << 1
```

```
If b[2] = 1

t3 = a << 2
```

```
If b[3] = 1

t4 = a << 3
```

The final product is obtained by summing all partial products:

```
Product = t1 + t2 + t3 + t4
```

---

## 📊 Multiplication Flow

```
             Multiplier Bits

          b3  b2  b1  b0

           │   │   │   │
           ▼   ▼   ▼   ▼

        Shift Multiplicand

        <<3 <<2 <<1 <<0

           │   │   │   │

           ▼   ▼   ▼   ▼

      Partial Products

           │
           ▼

      Binary Addition

           │
           ▼

      Final Product
```

---

## 🔢 Example Calculation

### Example

```
A = 5

B = 6
```

Binary

```
A = 0101

B = 0110
```

Partial products

```
b0 = 0 → 00000000

b1 = 1 → 00001010

b2 = 1 → 00010100

b3 = 0 → 00000000
```

Final product

```
00001010

+00010100

-----------

00011110
```

Result

```
30
```

---

## 📊 Sample Results

| A | B | Product |
|---|---|---------|
| 2 | 3 | 6 |
| 4 | 5 | 20 |
| 7 | 3 | 21 |
| 8 | 8 | 64 |
| 15 | 15 | 225 |

---

## ⏱️ Timing Behavior

- Pure combinational logic
- No clock required
- Output updates immediately when either input changes
- Delay depends on shift and addition logic

---

## 💡 Applications

- Arithmetic Logic Units (ALUs)
- Digital Signal Processing (DSP)
- FPGA arithmetic modules
- Embedded processors
- Digital calculators
- Educational RTL projects
- Hardware arithmetic units

---

## ✅ Advantages

- Easy to understand
- Demonstrates hardware multiplication principles
- Uses explicit partial products
- Fully synthesizable RTL
- Suitable for FPGA and ASIC implementation
- Good educational example of combinational arithmetic design

---

## 🧪 Simulation

### Recommended Simulators

- Xilinx Vivado Simulator
- ModelSim
- QuestaSim
- Icarus Verilog
- GTKWave

### Sample Test Cases

| A | B | Expected Product |
|---|---|------------------|
| 0 | 5 | 0 |
| 3 | 4 | 12 |
| 5 | 6 | 30 |
| 9 | 7 | 63 |
| 15 | 15 | 225 |

---

## 🔧 Synthesis

- FPGA Compatible ✅
- ASIC Compatible ✅
- Fully Synthesizable RTL ✅
- Pure combinational implementation
- Efficient for small operand widths

> **Note:** This design implements a straightforward **shift-and-add multiplier**, which is suitable for small bit-widths. For larger operands, more efficient architectures such as **Booth Multipliers**, **Wallace Tree Multipliers**, or **Dadda Multipliers** are typically used to improve performance and reduce hardware delay.

---

## 📁 Project Structure

```text
multiplier/

├── rtl/
│   └── multiplier.v
│
├── tb/
│   └── multiplier_tb.v
│
├── docs/
│   ├── block_diagram.png
│   ├── multiplication_flow.png
│   ├── timing_diagram.png
│   └── waveform.png
│
└── README.md
```

---

## 🚀 Future Improvements

- Parameterize operand widths
- Add signed multiplication support
- Implement Booth multiplier architecture
- Implement Wallace Tree multiplier
- Add pipelined multiplier version
- Develop a self-checking SystemVerilog testbench
- Compare resource utilization with the built-in multiplication operator

---

## 👨‍💻 Author

**Maddineni Dileep Kumar**

---
