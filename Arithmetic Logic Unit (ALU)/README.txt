# 8-Bit Arithmetic Logic Unit (ALU) in Verilog HDL

## Overview

This project implements an **8-bit Arithmetic Logic Unit (ALU)** using Verilog HDL. The ALU performs a variety of arithmetic, logical, shift, and rotate operations based on a **4-bit selection signal (`sel`)**.

The design supports **16 different operations**, making it suitable for educational processor design, digital systems, FPGA implementations, and computer architecture projects.

---

# Features

- 8-bit input operands
- 16-bit output result
- 4-bit operation select
- Carry/Borrow output (`e_bit`)
- Arithmetic operations
- Logical operations
- Shift operations
- Rotate operations
- Comparison operation
- Two's complement operation
- Synthesizable Verilog RTL

---

# Module Description

## Module Name

```
ALU
```

The ALU receives two 8-bit operands (`a` and `b`) and performs one of sixteen operations selected by the 4-bit control input.

---

# Inputs and Outputs

## Inputs

| Signal | Width | Description |
|--------|------:|-------------|
| `a` | 8 bits | Operand A |
| `b` | 8 bits | Operand B |
| `sel` | 4 bits | Operation selector |

---

## Outputs

| Signal | Width | Description |
|--------|------:|-------------|
| `result` | 16 bits | ALU result |
| `e_bit` | 1 bit | Carry/Borrow or extra status bit |

---

# Supported Operations

| Select | Operation | Description |
|:------:|-----------|-------------|
| `0000` | Addition | `a + b` |
| `0001` | Subtraction | `a - b` |
| `0010` | Multiplication | `a × b` |
| `0011` | Division | `a ÷ b` |
| `0100` | Left Shift | `a << 1` |
| `0101` | Right Shift | `a >> 1` |
| `0110` | Left Rotate | Rotate left by one bit |
| `0111` | Right Rotate | Rotate right by one bit |
| `1000` | AND | `a & b` |
| `1001` | OR | `a \| b` |
| `1010` | NAND | `~(a & b)` |
| `1011` | NOR | `~(a \| b)` |
| `1100` | XOR | `a ^ b` |
| `1101` | XNOR | `a ~^ b` |
| `1110` | Greater Than | `(a > b)` |
| `1111` | Two's Complement | `-a` |

---

# Working Principle

The ALU continuously monitors its inputs. Whenever `a`, `b`, or `sel` changes, the corresponding operation is executed using a combinational `case` statement.

---

# Arithmetic Operations

## Addition

```
result = a + b
```

Carry-out is stored in:

```
e_bit
```

---

## Subtraction

```
result = a - b
```

Borrow information is captured in `e_bit`.

---

## Multiplication

```
result = a × b
```

Since two 8-bit numbers can produce a 16-bit product, the full product is stored in `result`.

---

## Division

```
result = a / b
```

Only the quotient is returned. The remainder is discarded.

---

# Shift Operations

## Left Shift

```
a << 1
```

Equivalent to multiplying by 2 (ignoring overflow).

---

## Right Shift

```
a >> 1
```

Equivalent to dividing by 2 for unsigned values.

---

# Rotate Operations

## Left Rotate

Moves every bit one position left while wrapping the MSB to the LSB.

Example:

```
10110010

↓

01100101
```

---

## Right Rotate

Moves every bit one position right while wrapping the LSB to the MSB.

Example:

```
10110010

↓

01011001
```

---

# Logical Operations

## AND

```
result = a & b
```

---

## OR

```
result = a | b
```

---

## NAND

```
result = ~(a & b)
```

---

## NOR

```
result = ~(a | b)
```

---

## XOR

```
result = a ^ b
```

---

## XNOR

```
result = a ~^ b
```

---

# Comparison Operation

```
(a > b)
```

Returns:

```
1
```

if `a` is greater than `b`, otherwise:

```
0
```

> **Note:** Although the display message says **"Equality operation"**, the implemented logic actually performs a **greater-than comparison**.

---

# Two's Complement

```
-a
```

Implemented as:

```
~a + 1
```

---

# Example Operations

| A | B | Operation | Result |
|---:|---:|-----------|--------:|
| 25 | 15 | Addition | 40 |
| 25 | 15 | Subtraction | 10 |
| 10 | 5 | Multiplication | 50 |
| 40 | 5 | Division | 8 |
| 12 | 10 | AND | 8 |
| 12 | 10 | OR | 14 |
| 12 | 10 | XOR | 6 |

---

# Block Diagram

```
            +----------------------+
A --------->|                      |
B --------->|        8-bit ALU     |
SEL ------->|                      |
            +----------------------+
                |            |
                |            |
                v            v
            Result        e_bit
```

---

# Applications

## 1. Processor Design

- CPU datapath
- Arithmetic unit
- Logic unit

---

## 2. Embedded Systems

- Digital controllers
- Signal processing
- Arithmetic computation

---

## 3. FPGA Projects

- Soft-core processors
- Educational CPU design
- Hardware accelerators

---

## 4. Computer Architecture

- Instruction execution
- ALU datapath
- Register-transfer operations

---

# Advantages

- Supports sixteen operations
- Simple combinational implementation
- Full 16-bit multiplication result
- Parameter-free and easy to understand
- Synthesizable for FPGA and ASIC

---

# Limitations

- No protection against **division by zero**.
- Rotate operations are not implemented correctly because multiple non-blocking assignments (`<=`) update `result` and `e_bit` in the same block; the rotated bit may not be inserted as intended.
- The comparison operation checks **`a > b`**, not equality, despite the message text.
- `$display` statements are intended for simulation and are ignored during synthesis.

---

# Coding Improvements

### 1. Use Blocking Assignments in Combinational Logic

Replace:

```verilog
result <= a * b;
```

with:

```verilog
result = a * b;
```

Similarly, use `=` throughout the `always @(*)` block.

---

### 2. Handle Division by Zero

```verilog
if (b != 0)
    result = a / b;
else
    result = 16'h0000;
```

or define another suitable error behavior.

---

### 3. Correct Rotate Operations

Left rotate:

```verilog
result = {8'b0, {a[6:0], a[7]}};
e_bit = a[7];
```

Right rotate:

```verilog
result = {8'b0, {a[0], a[7:1]}};
e_bit = a[0];
```

---

### 4. Correct the Comparison Message

If keeping the current logic:

```verilog
$display("15-Greater Than operation");
```

If equality is intended, change the logic to:

```verilog
result = (a == b);
```

---

### 5. Initialize Outputs

Assign default values at the beginning of the combinational block:

```verilog
result = 16'd0;
e_bit = 1'b0;
```

This helps prevent unintended latch inference if new cases are added later.

---

# Project Files

```
ALU.v
```

---

## Author

**Dileep Kumar Maddineni**