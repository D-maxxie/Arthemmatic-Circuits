# Full Subtractor Using Dataflow Modeling in Verilog

## Overview

This project implements a **1-bit Full Subtractor** using Verilog HDL with **dataflow modeling**. A full subtractor is a combinational logic circuit that subtracts two single-bit binary numbers along with a borrow input (`bin`). It produces two outputs: the **Difference** (`diff`) and the **Borrow Out** (`bout`).

The design uses continuous assignment (`assign`) statements to implement the subtraction logic, making it simple, efficient, and easy to understand.

## Features

- Implements a 1-bit Full Subtractor
- Uses dataflow modeling with continuous assignments
- Accepts a borrow input (`bin`)
- Generates Difference and Borrow Out outputs
- Pure combinational logic with no clock dependency
- Fully synthesizable for FPGA and ASIC implementations

## Inputs and Outputs

### Inputs

| Signal | Width | Description |
|--------|------:|-------------|
| `a` | 1 bit | Minuend input |
| `b` | 1 bit | Subtrahend input |
| `bin` | 1 bit | Borrow input from the previous stage |

### Outputs

| Signal | Width | Description |
|--------|------:|-------------|
| `diff` | 1 bit | Difference output |
| `bout` | 1 bit | Borrow output |

## How It Works

The full subtractor subtracts `b` and the borrow input (`bin`) from `a`.

The outputs are calculated using the following logic:

- **Difference (`diff`)** is obtained using the XOR operation:

```verilog
assign diff = a ^ b ^ bin;
```

- **Borrow Out (`bout`)** is generated using the Boolean expression:

```verilog
assign bout = (~a & (b ^ bin)) | (b & bin);
```

The circuit continuously updates the outputs whenever any of the input signals change, making it a purely combinational design.

## Project File

```
full_subtractor.v
```

## Truth Table

| A | B | Bin | Difference | Borrow Out |
|:-:|:-:|:---:|:----------:|:----------:|
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 1 |
| 0 | 1 | 0 | 1 | 1 |
| 0 | 1 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 | 0 |
| 1 | 0 | 1 | 0 | 0 |
| 1 | 1 | 0 | 0 | 0 |
| 1 | 1 | 1 | 1 | 1 |

## Requirements

- Verilog HDL
- Any Verilog simulator such as Vivado Simulator, ModelSim, or Icarus Verilog

## Applications

- Binary subtraction circuits
- Arithmetic Logic Units (ALUs)
- Digital processors
- FPGA and ASIC design
- Digital electronics laboratory experiments

## Future Improvements

- Develop a testbench to verify all input combinations.
- Cascade multiple full subtractors to build an n-bit subtractor.
- Compare this dataflow implementation with gate-level and behavioral modeling approaches.
- Integrate the module into larger arithmetic and logic circuits.

## Author

**Dileep Kumar Maddineni**