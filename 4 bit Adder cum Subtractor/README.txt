# 4-Bit Adder/Subtractor Using Full Adders in Verilog

## Overview

This project implements a **4-bit Adder/Subtractor** using Verilog HDL. The design performs both addition and subtraction on two 4-bit binary numbers using a single circuit. An enable signal (`en`) determines whether the module performs addition or subtraction.

The circuit is built by cascading four **1-bit Full Adders** in a ripple carry configuration. Subtraction is achieved using the **2's complement** method, where the bits of operand `B` are inverted and an initial carry of `1` is added.

## Features

- Performs both 4-bit addition and subtraction
- Uses a single control signal to select the operation
- Built using four Full Adder modules
- Ripple Carry Adder architecture
- Implements subtraction using 2's complement
- Pure combinational logic
- Fully synthesizable for FPGA and ASIC designs

## Modules Included

### 1. Full Adder

The `full_adder` module adds two input bits and a carry input to produce a sum and carry output.

### 2. Adder/Subtractor

The `add_sub` module combines four full adders to perform arithmetic operations on two 4-bit operands.

- **`en = 0`** → Addition (`A + B`)
- **`en = 1`** → Subtraction (`A - B`)

## Inputs and Outputs

### Inputs

| Signal | Width | Description |
|--------|------:|-------------|
| `A` | 4 bits | First operand |
| `B` | 4 bits | Second operand |
| `en` | 1 bit | Operation select (0 = Add, 1 = Subtract) |

### Outputs

| Signal | Width | Description |
|--------|------:|-------------|
| `sdout` | 4 bits | Sum or Difference output |
| `cbout` | 1 bit | Carry Out (Addition) or Borrow Indicator (Subtraction) |

## How It Works

The design uses four Full Adder modules connected in series.

For **addition** (`en = 0`):

- Operand `B` passes through unchanged.
- The initial carry input is `0`.
- The circuit computes:

```
A + B
```

For **subtraction** (`en = 1`):

- Each bit of `B` is XORed with `en`, effectively inverting all bits of `B`.
- The initial carry input becomes `1`.
- This performs:

```
A + (~B + 1)
```

which is equivalent to:

```
A - B
```

Using the same hardware for both operations minimizes logic and demonstrates an efficient arithmetic circuit design.

## Project Files

```
full_adder.v
add_sub.v
```

## Example Operations

### Addition (`en = 0`)

| A | B | Result |
|---|---|--------|
| 0101 | 0011 | 1000 |
| 0110 | 0010 | 1000 |

### Subtraction (`en = 1`)

| A | B | Result |
|---|---|--------|
| 1001 | 0011 | 0110 |
| 0111 | 0010 | 0101 |

## Requirements

- Verilog HDL
- Any Verilog simulator such as Vivado Simulator, ModelSim, or Icarus Verilog

## Applications

- Arithmetic Logic Units (ALUs)
- Digital processors
- FPGA and ASIC design
- Embedded systems
- Digital electronics and computer architecture laboratories

## Future Improvements

- Extend the design to 8-bit, 16-bit, or 32-bit arithmetic units.
- Add overflow detection for signed arithmetic.
- Implement a Carry Lookahead Adder (CLA) to improve performance.
- Create a comprehensive testbench covering both addition and subtraction cases.

## Author

**Dileep Kumar Maddineni**