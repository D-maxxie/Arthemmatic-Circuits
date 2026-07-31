# 4-bit Divider using Repeated Subtraction (Verilog)

## 📖 Overview

This project implements a **4-bit unsigned divider** using the **Repeated Subtraction Algorithm** in Verilog HDL. The module calculates both the **quotient** and **remainder** by repeatedly subtracting the divisor from the dividend until the remaining value becomes smaller than the divisor.

Unlike hardware divider architectures such as restoring or non-restoring division, this implementation focuses on demonstrating the basic concept of integer division using procedural constructs.

The design is intended primarily for **educational purposes** and demonstrates the use of:

- Combinational procedural logic
- `while` loops
- Arithmetic operations
- Quotient and remainder generation

---

## ✨ Features

- 4-bit unsigned division
- Computes both quotient and remainder
- Uses repeated subtraction algorithm
- Pure combinational implementation
- Simple and easy-to-understand RTL
- Fully synthesizable for bounded inputs (tool-dependent)
- Educational implementation

---

## 📋 Specifications

| Parameter | Description |
|-----------|-------------|
| Language | Verilog HDL |
| Module Name | `divide` |
| Dividend Width | 4 bits |
| Divisor Width | 4 bits |
| Quotient Width | 4 bits |
| Remainder Width | 4 bits |
| Algorithm | Repeated Subtraction |

---

## 🏗️ Block Diagram

```
              +--------------------------+
Dividend ---->|                          |
              |      Divider Module      |
Divisor ------>|                          |
              | Repeated Subtraction     |
              +-----------+--------------+
                          |
          +---------------+---------------+
          |                               |
      Quotient                      Remainder
```

---

## ⚙️ Functional Description

Whenever the dividend or divisor changes, the module performs integer division using repeated subtraction.

### Step 1

Initialize:

```text
Quotient = 0
Remainder = Dividend
```

---

### Step 2

While:

```
Remainder ≥ Divisor
```

Perform:

```
Remainder = Remainder − Divisor

Quotient = Quotient + 1
```

---

### Step 3

Stop when:

```
Remainder < Divisor
```

Final outputs:

```
Quotient
Remainder
```

---

## 📊 Algorithm Flow

```
Start

↓

Quotient = 0

↓

Remainder = Dividend

↓

Is Remainder ≥ Divisor ?

      Yes
       |
       v

Remainder = Remainder − Divisor

Quotient++

       |
       |
      Repeat

       |
      No
       |
       v

Output Quotient & Remainder

↓

End
```

---

## 🔢 Example Calculations

### Example 1

```
Dividend = 12

Divisor = 3
```

```
12 - 3 = 9

9 - 3 = 6

6 - 3 = 3

3 - 3 = 0
```

Result

```
Quotient = 4

Remainder = 0
```

---

### Example 2

```
Dividend = 13

Divisor = 5
```

```
13 - 5 = 8

8 - 5 = 3
```

Result

```
Quotient = 2

Remainder = 3
```

---

## 📊 Sample Results

| Dividend | Divisor | Quotient | Remainder |
|-----------|----------|----------|-----------|
| 8 | 2 | 4 | 0 |
| 9 | 2 | 4 | 1 |
| 10 | 3 | 3 | 1 |
| 13 | 5 | 2 | 3 |
| 15 | 4 | 3 | 3 |

---

## ⏱️ Timing Behavior

- Pure combinational logic
- Output updates whenever either input changes
- No clock required
- Computation completes after the subtraction loop finishes

---

## 💡 Applications

- Educational digital design
- Arithmetic unit demonstrations
- Simple integer division
- FPGA learning projects
- Digital arithmetic laboratories
- Functional verification examples

---

## ✅ Advantages

- Easy to understand
- Simple RTL implementation
- Simultaneously computes quotient and remainder
- Demonstrates procedural loops in Verilog
- Suitable for learning arithmetic algorithms

---

## 🧪 Simulation

### Recommended Simulators

- Xilinx Vivado Simulator
- ModelSim
- QuestaSim
- Icarus Verilog
- GTKWave

### Sample Test Cases

| Dividend | Divisor | Expected Quotient | Expected Remainder |
|-----------|----------|-------------------|--------------------|
| 8 | 2 | 4 | 0 |
| 7 | 3 | 2 | 1 |
| 15 | 5 | 3 | 0 |
| 14 | 4 | 3 | 2 |
| 13 | 6 | 2 | 1 |

---

## 🔧 Synthesis

- Simple RTL implementation ✅
- FPGA Compatible (tool-dependent) ⚠️
- ASIC Compatible (tool-dependent) ⚠️
- Pure combinational design

> **Note:** This implementation does **not** handle the case where the divisor is **0**. If `divisor = 0`, the condition `remainder >= divisor` is always true, causing the `while` loop to run indefinitely during simulation. A divide-by-zero check should be added before entering the loop. Also, while some synthesis tools may support bounded loops, repeated-subtraction implementations are generally inefficient for hardware compared to restoring, non-restoring, or pipelined divider architectures.

---

## 📁 Project Structure

```text
divider/

├── rtl/
│   └── divide.v
│
├── tb/
│   └── divide_tb.v
│
├── docs/
│   ├── algorithm_flowchart.png
│   ├── timing_diagram.png
│   └── waveform.png
│
└── README.md
```

---

## 🚀 Future Improvements

- Add divide-by-zero protection
- Parameterize input/output widths
- Implement signed division support
- Design restoring and non-restoring divider architectures
- Add pipelined divider implementation
- Develop a self-checking SystemVerilog testbench
- Compare resource utilization with hardware divider implementations

---

## 👨‍💻 Author

**Maddineni Dileep Kumar**

---
