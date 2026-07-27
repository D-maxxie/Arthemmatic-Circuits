# Half Adder Using Dataflow Modeling in Verilog

## Overview

This project implements a **Half Adder** using Verilog HDL with **dataflow modeling**. A half adder is a basic combinational circuit that adds two single-bit binary inputs and produces a **Sum** and a **Carry** output. It is one of the fundamental building blocks used in designing arithmetic circuits such as full adders, ripple carry adders, and arithmetic logic units (ALUs).

The design uses simple continuous assignment (`assign`) statements, making it easy to understand and suitable for beginners learning Verilog.

## Features

- Implements a 1-bit Half Adder
- Uses dataflow modeling with continuous assignments
- Generates Sum and Carry outputs
- Simple combinational logic with no clock dependency
- Fully synthesizable for FPGA and ASIC designs

## Inputs and Outputs

### Inputs

| Signal | Width | Description |
|--------|------:|-------------|
| `a` | 1 bit | First binary input |
| `b` | 1 bit | Second binary input |

### Outputs

| Signal | Width | Description |
|--------|------:|-------------|
| `sout` | 1 bit | Sum output |
| `cout` | 1 bit | Carry output |

## How It Works

The half adder performs the addition of two single-bit inputs using the following logic:

- **Sum (`sout`)** is generated using the XOR (`^`) operation.
- **Carry (`cout`)** is generated using the AND (`&`) operation.

The implementation is as follows:

```verilog
assign sout = a ^ b;
assign cout = a & b;
```

Since the design is purely combinational, the outputs update immediately whenever either input changes.

## Project File

```
half_adder.v
```

## Truth Table

| A | B | Sum (`sout`) | Carry (`cout`) |
|:-:|:-:|:------------:|:--------------:|
| 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 1 |

## Requirements

- Verilog HDL
- Any Verilog simulator such as Vivado Simulator, ModelSim, or Icarus Verilog

## Applications

- Basic digital arithmetic circuits
- Full Adder design
- Ripple Carry Adders
- Arithmetic Logic Units (ALUs)
- FPGA and ASIC development
- Digital electronics education

## Future Improvements

- Design a Full Adder by extending this module.
- Create a parameterized adder for multi-bit operations.
- Develop a testbench to verify all input combinations.
- Integrate the module into larger arithmetic circuits.

## Author

**Dileep Kumar Maddineni**