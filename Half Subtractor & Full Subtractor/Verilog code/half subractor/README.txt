# Half Subtractor Using Dataflow Modeling in Verilog

## Overview

This project implements a **1-bit Half Subtractor** using Verilog HDL with **dataflow modeling**. A half subtractor is a basic combinational circuit that subtracts one binary digit (`b`) from another (`a`) and produces two outputs: the **Difference** (`diff`) and the **Borrow** (`bout`).

The design uses continuous assignment (`assign`) statements, making it simple, efficient, and easy to understand for beginners learning digital logic and Verilog HDL.

## Features

- Implements a 1-bit Half Subtractor
- Uses dataflow modeling with continuous assignments
- Generates Difference and Borrow outputs
- Pure combinational logic with no clock dependency
- Fully synthesizable for FPGA and ASIC implementations

## Inputs and Outputs

### Inputs

| Signal | Width | Description |
|--------|------:|-------------|
| `a` | 1 bit | Minuend input |
| `b` | 1 bit | Subtrahend input |

### Outputs

| Signal | Width | Description |
|--------|------:|-------------|
| `diff` | 1 bit | Difference output |
| `bout` | 1 bit | Borrow output |

## How It Works

The half subtractor performs the subtraction of input `b` from input `a`.

The outputs are calculated using the following logic:

- **Difference (`diff`)** is generated using the XOR (`^`) operation.
- **Borrow (`bout`)** is generated using the expression `~a & b`, indicating that a borrow is required only when `a` is `0` and `b` is `1`.

The implementation is shown below:

```verilog
assign diff = a ^ b;
assign bout = ~a & b;
```

Since the design is purely combinational, the outputs change immediately whenever either input changes.

## Project File

```
half_subtractor.v
```

## Truth Table

| A | B | Difference (`diff`) | Borrow (`bout`) |
|:-:|:-:|:-------------------:|:---------------:|
| 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 1 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 0 |

## Requirements

- Verilog HDL
- Any Verilog simulator such as Vivado Simulator, ModelSim, or Icarus Verilog

## Applications

- Binary subtraction circuits
- Arithmetic Logic Units (ALUs)
- Digital arithmetic operations
- FPGA and ASIC design
- Digital electronics education

## Future Improvements

- Create a testbench to verify all possible input combinations.
- Extend the design to a Full Subtractor by adding a borrow input.
- Implement multi-bit subtraction by cascading subtractor modules.
- Compare the implementation with gate-level and behavioral modeling techniques.

## Author

**Dileep Kumar Maddineni**