# Parameterized N-bit Comparator (Verilog)

## 📖 Overview

This project implements a **parameterized N-bit Comparator** using Verilog HDL. The comparator compares two unsigned binary numbers and determines whether the first input is **less than**, **greater than**, or **equal to** the second input.

The design is parameterized, allowing the comparator width to be easily configured for different applications without modifying the RTL code. By default, the comparator operates on **8-bit** inputs.

This module is a fundamental combinational circuit widely used in processors, ALUs, sorting circuits, digital control systems, and decision-making logic.

---

## ✨ Features

- Parameterized data width
- Default 8-bit comparator
- Performs unsigned comparison
- Generates three comparison outputs
- Pure combinational logic
- Fully synthesizable Verilog HDL
- FPGA and ASIC compatible

---

## 📋 Specifications

| Parameter | Description |
|-----------|-------------|
| Language | Verilog HDL |
| Module Name | `N_bit_comparator` |
| Default Width | 8 bits |
| Parameter | `N` |
| Inputs | `a[N-1:0]`, `b[N-1:0]` |
| Outputs | `Lesser`, `Greater`, `Equal` |
| Logic Type | Combinational |

---

## 🏗️ Block Diagram

```
               A[N-1:0]
                  │
                  │
                  ▼

        +----------------------+
        |  N-bit Comparator    |
        |                      |
        +----------+-----------+
                   ▲
                   │
               B[N-1:0]

                   │
                   ▼

        +----------------------+
        | Lesser   Greater     |
        | Equal                |
        +----------------------+
```

---

## ⚙️ Functional Description

The comparator continuously evaluates the relationship between the two input values.

### Case 1

If:

```
A < B
```

Outputs

```
Lesser  = 1

Greater = 0

Equal   = 0
```

---

### Case 2

If:

```
A > B
```

Outputs

```
Lesser  = 0

Greater = 1

Equal   = 0
```

---

### Case 3

If:

```
A = B
```

Outputs

```
Lesser  = 0

Greater = 0

Equal   = 1
```

---

## 📊 Comparison Flow

```
          Inputs

       A[N-1:0]

       B[N-1:0]

            │

            ▼

     Compare A and B

            │

      ┌─────┼─────┐

      │     │     │

     A<B   A>B   A=B

      │     │     │

      ▼     ▼     ▼

 Lesser Greater Equal
```

---

## 🔢 Example Comparisons

### Example 1

```
A = 25

B = 40
```

Result

```
Lesser = 1

Greater = 0

Equal = 0
```

---

### Example 2

```
A = 70

B = 15
```

Result

```
Lesser = 0

Greater = 1

Equal = 0
```

---

### Example 3

```
A = 55

B = 55
```

Result

```
Lesser = 0

Greater = 0

Equal = 1
```

---

## 📊 Sample Results

| A | B | Lesser | Greater | Equal |
|---|---|:------:|:-------:|:-----:|
| 5 | 9 | 1 | 0 | 0 |
| 20 | 10 | 0 | 1 | 0 |
| 15 | 15 | 0 | 0 | 1 |
| 0 | 255 | 1 | 0 | 0 |
| 128 | 64 | 0 | 1 | 0 |

---

## ⏱️ Timing Behavior

- Pure combinational logic
- No clock required
- Outputs update immediately when either input changes
- Delay depends on comparator implementation after synthesis

---

## 💡 Applications

- Arithmetic Logic Units (ALUs)
- CPUs and microcontrollers
- Digital decision-making circuits
- Address comparison
- Sorting and searching hardware
- Digital controllers
- FPGA-based systems
- Data validation logic

---

## ✅ Advantages

- Parameterized and reusable design
- Easy to scale for wider data buses
- Simple RTL implementation
- Fully synthesizable
- Suitable for FPGA and ASIC implementation
- Generates mutually exclusive comparison outputs

---

## 🧪 Simulation

### Recommended Simulators

- Xilinx Vivado Simulator
- ModelSim
- QuestaSim
- Icarus Verilog
- GTKWave

### Sample Test Cases

| A | B | Expected Lesser | Expected Greater | Expected Equal |
|---|---|:---------------:|:----------------:|:--------------:|
| 0 | 0 | 0 | 0 | 1 |
| 5 | 8 | 1 | 0 | 0 |
| 12 | 7 | 0 | 1 | 0 |
| 100 | 100 | 0 | 0 | 1 |
| 255 | 1 | 0 | 1 | 0 |

---

## 🔧 Synthesis

- FPGA Compatible ✅
- ASIC Compatible ✅
- Fully Synthesizable RTL ✅
- Pure combinational implementation
- Parameterized architecture for flexible bit widths

> **Note:** This module performs **unsigned comparisons** because the inputs are declared as standard vectors (`[N-1:0]`). If signed comparisons are required, declare the inputs as `signed` or use the `$signed()` system function. The parameterized width (`N`) allows the same module to be reused for 4-bit, 8-bit, 16-bit, 32-bit, or larger comparators without changing the core logic.

---

## 📁 Project Structure

```text
n_bit_comparator/

├── rtl/
│   └── N_bit_comparator.v
│
├── tb/
│   └── N_bit_comparator_tb.v
│
├── docs/
│   ├── block_diagram.png
│   ├── comparison_flow.png
│   ├── truth_table.png
│   └── waveform.png
│
└── README.md
```

---

## 🚀 Future Improvements

- Add signed comparison support
- Parameterize output encoding (binary or one-hot)
- Include less-than-or-equal and greater-than-or-equal outputs
- Develop a self-checking SystemVerilog testbench
- Compare synthesis results across different FPGA families
- Extend the design with pipelined comparison for high-speed applications

---

## 👨‍💻 Author

**Maddineni Dileep Kumar**
---
