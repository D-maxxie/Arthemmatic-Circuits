# 4-Bit Carry Lookahead Adder (CLA) in Verilog

## Overview

This project implements a **4-bit Carry Lookahead Adder (CLA)** using Verilog HDL. Unlike a Ripple Carry Adder, where each carry must propagate through every stage, the Carry Lookahead Adder computes carry signals in parallel using **Generate (G)** and **Propagate (P)** logic. This significantly reduces the delay associated with carry propagation, making the CLA much faster for arithmetic operations.

The design accepts two 4-bit binary inputs and an initial carry input, then produces a 4-bit sum along with the final carry output.

## Features

- Implements a 4-bit Carry Lookahead Adder
- Uses Generate (`G`) and Propagate (`P`) signals
- Faster carry computation than Ripple Carry Adders
- Pure combinational logic
- Produces a 4-bit sum and carry output
- Fully synthesizable for FPGA and ASIC implementations

## Inputs and Outputs

### Inputs

| Signal | Width | Description |
|--------|------:|-------------|
| `a` | 4 bits | First input operand |
| `b` | 4 bits | Second input operand |
| `cin` | 1 bit | Initial carry input |

### Outputs

| Signal | Width | Description |
|--------|------:|-------------|
| `sum` | 4 bits | Sum of operands `a` and `b` |
| `carry` | 1 bit | Final carry output |

## How It Works

The Carry Lookahead Adder calculates two intermediate signals for every bit:

- **Generate (G):** Indicates whether a carry is generated at that bit.
- **Propagate (P):** Indicates whether an incoming carry is propagated to the next stage.

Using these signals, the carry values for each stage are computed directly without waiting for previous stages. Once the carry values are available, the sum bits are generated using XOR operations.

This parallel carry generation greatly improves performance compared to a Ripple Carry Adder, especially as the operand size increases.

## Project File

```
carry_look_ahead_gen.v
```

## Example

| A | B | Cin | Sum | Carry Out |
|---|---|:---:|-----|:---------:|
| 0011 | 0101 | 0 | 1000 | 0 |
| 1111 | 0001 | 0 | 0000 | 1 |
| 1001 | 0110 | 0 | 1111 | 0 |
| 1111 | 1111 | 1 | 1111 | 1 |

## Requirements

- Verilog HDL
- Any Verilog simulator such as Vivado Simulator, ModelSim, or Icarus Verilog

## Applications

- Arithmetic Logic Units (ALUs)
- High-speed digital processors
- FPGA and ASIC arithmetic circuits
- Digital signal processing systems
- Computer architecture and VLSI education

## Advantages of Carry Lookahead Adders

- Faster than Ripple Carry Adders
- Reduces carry propagation delay
- Improves overall arithmetic performance
- Suitable for high-speed computing applications

## Future Improvements

- Extend the design to 8-bit, 16-bit, or 32-bit Carry Lookahead Adders.
- Implement hierarchical CLA structures for larger bit widths.
- Add overflow detection for signed arithmetic.
- Develop a comprehensive testbench to verify all input combinations.

## Author

**Dileep Kumar Maddineni**