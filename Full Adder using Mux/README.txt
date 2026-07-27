# Full Adder Testbench in Verilog

## Overview

This project contains a **testbench** for verifying the functionality of a **1-bit Full Adder** module in Verilog HDL. The testbench automatically applies every possible combination of the three input signals (`a`, `b`, and `cin`) and monitors the resulting **Sum** and **Carry** outputs.

The design is intended for simulation only and is commonly used to validate the correctness of the Full Adder before synthesis or hardware implementation.

## Features

- Verifies a 1-bit Full Adder
- Tests all possible input combinations (8 test cases)
- Automatically changes inputs using simulation delays
- Displays input and output values in the simulation console
- Ends the simulation automatically after all test cases are executed
- Compatible with most Verilog simulators

## Inputs and Outputs

### Testbench Inputs

| Signal | Width | Description |
|--------|------:|-------------|
| `a` | 1 bit | First input |
| `b` | 1 bit | Second input |
| `cin` | 1 bit | Carry input |

### Outputs from DUT

| Signal | Width | Description |
|--------|------:|-------------|
| `sum` | 1 bit | Sum output |
| `carry` | 1 bit | Carry output |

## Device Under Test (DUT)

The testbench instantiates the Full Adder module as the **Device Under Test (DUT)**.

```verilog
full_adder dut(a, b, cin, sum, carry);
```

All input combinations are applied to this instance during simulation.

## How It Works

The testbench contains two `initial` blocks.

### Test Vector Generation

The first `initial` block applies all eight possible combinations of the three input signals.

Each test case is separated by a simulation delay of **10 ns**, allowing enough time to observe the outputs before the next input combination is applied.

### Output Monitoring

The second `initial` block uses the `$monitor` system task to continuously display the current values of the inputs and outputs whenever any signal changes.

Example output:

```text
a = 0, b = 1, cin = 0, sum = 1, carry = 0
```

After all test cases have been executed, the simulation automatically terminates using:

```verilog
$finish;
```

## Project File

```
test_bench.v
```

## Test Cases

| A | B | Cin | Expected Sum | Expected Carry |
|:-:|:-:|:---:|:------------:|:--------------:|
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 0 |
| 0 | 1 | 0 | 1 | 0 |
| 0 | 1 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 | 0 |
| 1 | 0 | 1 | 0 | 1 |
| 1 | 1 | 0 | 0 | 1 |
| 1 | 1 | 1 | 1 | 1 |

## Requirements

- Verilog HDL
- A Full Adder module (`full_adder.v`)
- Any Verilog simulator such as Vivado Simulator, ModelSim, or Icarus Verilog

## Applications

- Functional verification of combinational circuits
- Learning Verilog simulation concepts
- Digital electronics laboratory experiments
- FPGA and ASIC design verification
- Educational demonstrations of Full Adder operation

## Future Improvements

- Add waveform generation using `$dumpfile` and `$dumpvars`.
- Implement self-checking test cases that automatically compare outputs with expected values.
- Extend the testbench to support random stimulus generation.
- Reuse the testbench structure for verifying larger arithmetic circuits.

## Author

**Dileep Kumar Maddineni**