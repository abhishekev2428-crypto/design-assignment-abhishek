Digital IC Design Internship

This repository contains the assignments and projects completed during my Digital IC Design Internship. All designs are implemented using **Verilog HDL** and verified through simulation using dedicated testbenches.

The assignments cover both **combinational** and **sequential digital circuits**, providing practical experience in RTL design, functional verification, simulation, and digital system development.

Repository Structure

```text
digital-ic-design-internship/
│
├── day1/
│   ├── BCD_Adder/
│   │   ├── design/
│   │   │   └── design_bcd.v
│   │   ├── tb/
│   │   │   └── BCD_tb.v
│   │   └── bcd.md
│   │
│   └── Ripple_Carry_Adder/
│       ├── design/
│       │   └── design_rca.v
│       ├── tb/
│       │   └── RCA_tb.v
│       └── rca.md
│
└── day2/
    ├── 2x4_Decoder/
    │   ├── design/
    │   │   └── design_decoder.v
    │   ├── tb/
    │   │   └── decoder_tb.v
    │   └── decoder.md
    │
    ├── DFF/
    │   ├── design/
    │   │   └── design_dff.v
    │   ├── tb/
    │   │   └── DFF_tb.v
    │   └── dff.md
    │
    ├── SR_FF/
    │   ├── design/
    │   │   └── design_srff.v
    │   ├── tb/
    │   │   └── srff_tb.v
    │   └── srff.md
    │
    └── USR/
        ├── design/
        │   └── design_usr.v
        ├── tb/
        │   │   └── USR_tb.v
        └── usr.md
```

Implemented Designs

 Day 1

BCD Adder

* Designed and implemented a BCD Adder.
* Performed decimal correction when the sum exceeded valid BCD range.
* Verified functionality using a dedicated testbench.

Ripple Carry Adder (RCA)

* Designed a 4-bit Ripple Carry Adder using Full Adders.
* Studied carry propagation across stages.
* Verified the design through simulation.

Day 2

2×4 Decoder

* Implemented a 2-to-4 Decoder using combinational logic.
* Verified all possible input combinations.

 D Flip-Flop (DFF)

* Designed an edge-triggered D Flip-Flop.
* Verified data capture and storage behavior.

 SR Flip-Flop

* Implemented an SR Flip-Flop with Set and Reset operations.
* Simulated all valid operating conditions.

Universal Shift Register (USR)

* Designed a Universal Shift Register supporting:

  * Hold
  * Shift Left
  * Shift Right
  * Parallel Load
* Verified functionality through simulation waveforms.

 Skills and Tools

* Verilog HDL
* RTL Design
* Functional Verification
* Testbench Development
* Digital Logic Design
* Waveform Analysis
* Git & GitHub

 Learning Outcomes

Through these assignments, I gained hands-on experience in:

* Combinational Circuit Design
* Sequential Circuit Design
* RTL Coding and Simulation
* Testbench Creation
* Debugging and Verification
* Digital System Design Methodologies
* Version Control using Git and GitHub

# Day 3 – Assignment: Sequence Detector (1110) Design and Verification

## 1. Objective

To design and verify a Sequence Detector for detecting the binary sequence **1110** using Verilog HDL and simulate its functionality using Xilinx Vivado.

---

## 2. Introduction

A Sequence Detector is a sequential logic circuit used to identify a specific pattern of bits in a serial input stream. When the desired sequence is detected, the circuit generates an output signal indicating successful detection.

In this assignment, a sequence detector was designed to detect the binary sequence:

**1110**

Sequence detectors are widely used in:

* Digital communication systems
* Pattern recognition circuits
* Error detection systems
* Data transmission protocols
* Control systems

---

 3. Theory

A Sequence Detector is generally implemented using a Finite State Machine (FSM). The FSM transitions between different states depending on the incoming serial input.

For the target sequence **1110**, the detector keeps track of previously received bits and generates a HIGH output when the complete sequence is detected.

### State Description

| State | Description    |
| ----- | -------------- |
| S0    | Initial State  |
| S1    | Detected '1'   |
| S2    | Detected '11'  |
| S3    | Detected '111' |

When the next input is **0** after reaching S3, the sequence **1110** is detected and the output becomes HIGH.

---

## 4. Working Principle

The detector continuously monitors the serial input bit stream.

### State Transitions

* S0 → S1 when input = 1
* S1 → S2 when input = 1
* S2 → S3 when input = 1
* S3 → Detection State when input = 0

At this point, the sequence **1110** has been received and the output signal is asserted.

After detection, the FSM returns to an appropriate state depending on the design requirements.

---

## 5. Design Methodology

The Sequence Detector was implemented using a Finite State Machine (FSM).

### Inputs

* `clk` : Clock signal
* `rst` : Reset signal
* `din` : Serial input data

### Outputs

* `detected` : Sequence detection output

### Internal Components

* Present State Register
* Next State Logic
* Detection Logic

The FSM updates its state on every positive edge of the clock and compares incoming bits with the target sequence.

---

## 6. RTL Analysis

The RTL schematic generated in Vivado shows:

* State register (`ps_reg`)
* Next-state logic implemented using multiplexers
* Detection logic for output generation
* Clock and reset circuitry

The synthesized design confirms the implementation of a Finite State Machine for sequence detection.

<img width="1562" height="699" alt="image" src="https://github.com/user-attachments/assets/e27311bd-ef98-4af8-98d8-55e7e250af85" />


---

## 7. Verilog Implementation

The design was coded in Verilog HDL using:

* State encoding
* Sequential state register
* Combinational next-state logic
* Output detection logic

The FSM tracks the incoming serial data and asserts the output whenever the sequence **1110** is detected.

---

## 8. Simulation and Verification

A testbench was developed to verify the operation of the Sequence Detector.

### Test Input Stream

```text
1110
```

### Expected Result

| Sequence Received | Detected Output |
| ----------------- | --------------- |
| 1110              | 1               |

### Observed Result

From the simulation waveform:

* Input stream successfully transitions through all FSM states.
* Upon receiving the sequence **1110**, the output `detected` becomes HIGH.
* The output pulse confirms successful sequence detection.

**Result:** PASS ✅

<img width="1544" height="761" alt="image" src="https://github.com/user-attachments/assets/e6c0e2c2-91ea-4caa-807f-5ba2660e6811" />


---

## 9. Observations

* The FSM correctly tracked the incoming serial bits.
* State transitions occurred as expected on each clock edge.
* The output was asserted only when the sequence **1110** was received.
* Reset operation initialized the FSM to the starting state.
* Simulation results matched the expected sequence detection behavior.

---

## 10. Conclusion

A Sequence Detector for detecting the binary sequence **1110** was successfully designed, implemented, and verified using Verilog HDL. The FSM correctly identified the target sequence and generated the detection output. Functional simulation and RTL analysis confirmed the correctness of the design. This assignment provided practical experience in Finite State Machine design, sequential logic implementation, and hardware verification using Vivado.

# Day 4– Task 1: BLOCK MEMORY GENERATOR

## Objective

To design and verify an **8-bit Single-Port RAM** using Verilog HDL and simulate its read and write operations using Xilinx Vivado.

---

## Introduction

Random Access Memory (RAM) is a storage device used to temporarily store data that can be accessed directly using memory addresses. Unlike sequential storage devices, RAM allows data to be written to and read from any memory location independently.

A **Single-Port RAM** uses one communication port for both read and write operations. The memory location is selected using an address input, and data can either be stored or retrieved depending on the control signals.

### Applications

* Data Storage Systems
* Embedded Systems
* Digital Signal Processing
* Microcontrollers
* FPGA-Based Designs
* Buffer Memory

---

## Theory

A Single-Port RAM consists of memory locations addressed through an address bus.

### Inputs

| Signal         | Description                   |
| -------------- | ----------------------------- |
| clk            | Clock Signal                  |
| arstn          | Active-Low Asynchronous Reset |
| wrenb          | Write Enable                  |
| wraddress[7:0] | Write Address                 |
| rdaddress[7:0] | Read Address                  |
| d_in[7:0]      | Input Data                    |

### Output

| Signal        | Description |
| ------------- | ----------- |
| data_out[7:0] | Output Data |

### Memory Organization

* Data Width = 8 bits
* Address Width = 8 bits
* Number of Locations = 256
* Memory Type = Single-Port RAM

---

## Working Principle

The RAM operates in two modes:

### Write Operation

When the write enable signal is HIGH:

```text
wrenb = 1
```

The input data is stored at the memory location specified by the write address.

```text
Memory[wraddress] ← d_in
```

### Read Operation

When a read address is provided, the data stored at the specified memory location is retrieved.

```text
data_out ← Memory[rdaddress]
```

The output reflects the contents of the selected memory location.

---

## Design Methodology

The RAM was implemented using:

* Memory Register Array
* Address Decoding Logic
* Read Multiplexer
* Write Control Logic
* Asynchronous Reset Circuit

### Functional Blocks

1. Memory Array
2. Write Address Decoder
3. Read Address Selection Logic
4. Output Register
5. Reset Logic

---

## RTL Analysis

The RTL schematic generated in Vivado shows:

* Multiple memory registers representing RAM locations.
* Address decoding logic for write operations.
* Multiplexer-based read logic.
* Output register for data retrieval.
* Reset circuitry for memory initialization.

The RTL structure confirms the implementation of a memory block with independent read and write addressing.

### RTL Diagram

<img width="1052" height="524" alt="image" src="https://github.com/user-attachments/assets/ce647c7f-ef3d-457c-bbab-3e954c037747" />


---

## Verilog Implementation

The design was implemented using Verilog HDL.

### Features

* 8-bit Data Storage
* 256 Addressable Locations
* Independent Read and Write Addresses
* Write Enable Control
* Asynchronous Reset
* Registered Output

---

## Simulation and Verification

A Verilog testbench was developed to verify memory operations.

### Test Case 1: Write Data

| Write Address | Data Written |
| ------------- | ------------ |
| 01            | 55           |
| 02            | AA           |

Expected Result:

```text
Memory[01] = 55
Memory[02] = AA
```

Result: PASS ✅

---

### Test Case 2: Read Data

| Read Address | Expected Output |
| ------------ | --------------- |
| 01           | 55              |
| 02           | AA              |

Observed Output:

| Address | Data Out |
| ------- | -------- |
| 01      | 55       |
| 02      | AA       |

Result: PASS ✅

---

### Test Case 3: Additional Data Access

| Address | Data |
| ------- | ---- |
| 02      | F0   |

The output correctly reflected the data stored at the selected memory location.

Result: PASS ✅

---

## Simulation Observation

The waveform confirms that:

* Reset initializes the memory system.
* Data values are written successfully when `wrenb` is asserted.
* Different memory locations store independent data values.
* Read operations correctly retrieve stored data.
* Address changes result in the expected output data.
* Memory contents are preserved until overwritten.

### Sample Memory Transactions

| Address | Data Stored |
| ------- | ----------- |
| 01      | 55          |
| 02      | AA          |
| 02      | F0          |

The output data matched the contents of the addressed memory location.

### Simulation Waveform

<img width="1551" height="711" alt="image" src="https://github.com/user-attachments/assets/fd1087a3-ce0f-4941-8a81-1855b7b3238f" />


---

## Observations

* Data was successfully written to the specified memory addresses.
* Read operations returned the correct stored values.
* Address decoding functioned properly.
* Memory contents remained intact after storage.
* Reset initialized the memory and output correctly.
* Simulation results matched expected RAM behavior.

---

## Conclusion

An **8-bit Single-Port RAM** was successfully designed, implemented, and verified using Verilog HDL. The memory correctly performed write and read operations based on the supplied addresses and control signals. Functional simulation and RTL analysis confirmed the correctness of the design. This task provided practical experience in memory design, address decoding, read/write control logic, and hardware verification using Xilinx Vivado.


# Day 5 – Task 1: BCD Adder Verification Using SystemVerilog Interface

## Objective

To verify the previously designed **BCD Adder** using a **SystemVerilog Interface** and demonstrate how interfaces simplify communication between the DUT (Design Under Test) and the testbench.

---

# Introduction

In traditional Verilog testbenches, all DUT signals must be connected individually. As designs become larger, managing numerous signals becomes difficult and error-prone.

SystemVerilog introduces the concept of an **Interface**, which groups related signals into a single construct. This improves readability, scalability, and maintainability of verification environments.

In this task, the same **BCD Adder design developed on Day 1** was verified using a SystemVerilog Interface-based testbench.

---

# Theory

## What is an Interface?

An Interface is a collection of signals bundled together into a single entity.

Instead of connecting signals individually:

```text
a
b
cin
sum
carry
```

all signals are grouped inside one interface.

### Advantages

* Reduces wiring complexity
* Improves code readability
* Simplifies DUT-Testbench connections
* Supports reusable verification environments
* Widely used in UVM-based verification

---

# BCD Adder Overview

A BCD Adder adds two BCD digits and generates a valid BCD result.

If the binary sum exceeds decimal 9, a correction value of **0110 (decimal 6)** is added.

### Inputs

| Signal | Description       |
| ------ | ----------------- |
| a[3:0] | First BCD Number  |
| b[3:0] | Second BCD Number |
| cin    | Carry Input       |

### Outputs

| Signal   | Description  |
| -------- | ------------ |
| sum[3:0] | BCD Sum      |
| carry    | Carry Output |

---

# Interface Declaration

The interface groups all DUT signals into a single structure.

### Signals Included

| Signal   | Description  |
| -------- | ------------ |
| a[3:0]   | Operand A    |
| b[3:0]   | Operand B    |
| cin      | Carry Input  |
| sum[3:0] | Sum Output   |
| carry    | Carry Output |

### Example Interface Structure

```systemverilog
interface bcd_if;

logic [3:0] a;
logic [3:0] b;
logic cin;

logic [3:0] sum;
logic carry;

endinterface
```

---

# Design Methodology

The verification environment consists of:

### 1. Interface

Stores all BCD Adder signals.

### 2. DUT

BCD Adder implemented on Day 1.

### 3. Testbench

Applies stimulus through the interface and observes outputs.

### Verification Flow

```text
Testbench
    ↓
Interface
    ↓
BCD Adder DUT
    ↓
Output Observation
```

---

# RTL Analysis

The RTL schematic remains identical to the Day 1 BCD Adder because only the verification methodology changed.

The design still contains:

* Ripple Carry Adder
* BCD Correction Logic
* Final BCD Addition Stage

### RTL Diagram

*(Insert RTL Schematic Image Here)*

---

# Simulation and Verification

A SystemVerilog testbench was developed using the interface.

### Test Case 1

| Input | Value |
| ----- | ----- |
| A     | 4     |
| B     | 3     |
| Cin   | 0     |

Expected Result:

```text
4 + 3 = 7
```

Observed Output:

| Signal | Value |
| ------ | ----- |
| Sum    | 7     |
| Carry  | 0     |

Result: PASS ✅

---

### Test Case 2

| Input | Value |
| ----- | ----- |
| A     | 5     |
| B     | 6     |
| Cin   | 0     |

Expected Result:

```text
5 + 6 = 11
BCD Output = 0001 0001
```

Observed Output:

| Signal | Value |
| ------ | ----- |
| Sum    | 1     |
| Carry  | 1     |

Result: PASS ✅

---

# Simulation Observation

From the waveform:

### First Input Set

| A | B | Sum | Carry |
| - | - | --- | ----- |
| 4 | 3 | 7   | 0     |

### Second Input Set

| A | B | Sum | Carry |
| - | - | --- | ----- |
| 5 | 6 | 1   | 1     |

The outputs match the expected BCD arithmetic results.

### Simulation Waveform

<img width="1600" height="835" alt="image" src="https://github.com/user-attachments/assets/b4d159eb-25f7-4cf9-b1f3-4b8721145ab4" />


---

# Comparison with Traditional Testbench

| Traditional Verilog           | Interface-Based Verification |
| ----------------------------- | ---------------------------- |
| Individual signal connections | Single interface connection  |
| More wiring                   | Less wiring                  |
| Difficult to scale            | Easily scalable              |
| Less reusable                 | Highly reusable              |
| Basic verification style      | Modern verification style    |

---

# Observations

* Interface successfully grouped all DUT signals.
* DUT and testbench communication became simpler.
* The BCD Adder functionality remained unchanged.
* Simulation results matched Day 1 results.
* Interface reduced signal connection complexity.
* Verification code became cleaner and easier to maintain.

---

# Conclusion

The BCD Adder designed on Day 1 was successfully verified using a **SystemVerilog Interface-based testbench**. The interface simplified signal management and improved testbench organization without affecting the functionality of the DUT. Simulation results confirmed correct BCD addition behavior, demonstrating the advantages of using interfaces in modern verification environments.

---


# Day 5 – Task 1: BCD Adder Verification Using SystemVerilog Interface

## Objective

To verify the previously designed **BCD Adder** using a **SystemVerilog Interface** and demonstrate how interfaces simplify communication between the DUT (Design Under Test) and the testbench.

---

# Introduction

In traditional Verilog testbenches, all DUT signals must be connected individually. As designs become larger, managing numerous signals becomes difficult and error-prone.

SystemVerilog introduces the concept of an **Interface**, which groups related signals into a single construct. This improves readability, scalability, and maintainability of verification environments.

In this task, the same **BCD Adder design developed on Day 1** was verified using a SystemVerilog Interface-based testbench.

---

# Theory

## What is an Interface?

An Interface is a collection of signals bundled together into a single entity.

Instead of connecting signals individually:

```text
a
b
cin
sum
carry
```

all signals are grouped inside one interface.

### Advantages

* Reduces wiring complexity
* Improves code readability
* Simplifies DUT-Testbench connections
* Supports reusable verification environments
* Widely used in UVM-based verification

---

# BCD Adder Overview

A BCD Adder adds two BCD digits and generates a valid BCD result.

If the binary sum exceeds decimal 9, a correction value of **0110 (decimal 6)** is added.

### Inputs

| Signal | Description       |
| ------ | ----------------- |
| a[3:0] | First BCD Number  |
| b[3:0] | Second BCD Number |
| cin    | Carry Input       |

### Outputs

| Signal   | Description  |
| -------- | ------------ |
| sum[3:0] | BCD Sum      |
| carry    | Carry Output |

---

# Interface Declaration

The interface groups all DUT signals into a single structure.

### Signals Included

| Signal   | Description  |
| -------- | ------------ |
| a[3:0]   | Operand A    |
| b[3:0]   | Operand B    |
| cin      | Carry Input  |
| sum[3:0] | Sum Output   |
| carry    | Carry Output |

### Example Interface Structure

```systemverilog
interface bcd_if;

logic [3:0] a;
logic [3:0] b;
logic cin;

logic [3:0] sum;
logic carry;

endinterface
```

---

# Design Methodology

The verification environment consists of:

### 1. Interface

Stores all BCD Adder signals.

### 2. DUT

BCD Adder implemented on Day 1.

### 3. Testbench

Applies stimulus through the interface and observes outputs.

### Verification Flow

```text
Testbench
    ↓
Interface
    ↓
BCD Adder DUT
    ↓
Output Observation
```

---

# RTL Analysis

The RTL schematic remains identical to the Day 1 BCD Adder because only the verification methodology changed.

The design still contains:

* Ripple Carry Adder
* BCD Correction Logic
* Final BCD Addition Stage

### RTL Diagram

*(Insert RTL Schematic Image Here)*

---

# Simulation and Verification

A SystemVerilog testbench was developed using the interface.

### Test Case 1

| Input | Value |
| ----- | ----- |
| A     | 4     |
| B     | 3     |
| Cin   | 0     |

Expected Result:

```text
4 + 3 = 7
```

Observed Output:

| Signal | Value |
| ------ | ----- |
| Sum    | 7     |
| Carry  | 0     |

Result: PASS ✅

---

### Test Case 2

| Input | Value |
| ----- | ----- |
| A     | 5     |
| B     | 6     |
| Cin   | 0     |

Expected Result:

```text
5 + 6 = 11
BCD Output = 0001 0001
```

Observed Output:

| Signal | Value |
| ------ | ----- |
| Sum    | 1     |
| Carry  | 1     |

Result: PASS ✅

---

# Simulation Observation

From the waveform:

### First Input Set

| A | B | Sum | Carry |
| - | - | --- | ----- |
| 4 | 3 | 7   | 0     |

### Second Input Set

| A | B | Sum | Carry |
| - | - | --- | ----- |
| 5 | 6 | 1   | 1     |

The outputs match the expected BCD arithmetic results.

### Simulation Waveform

<img width="1600" height="835" alt="image" src="https://github.com/user-attachments/assets/b4d159eb-25f7-4cf9-b1f3-4b8721145ab4" />


---

# Comparison with Traditional Testbench

| Traditional Verilog           | Interface-Based Verification |
| ----------------------------- | ---------------------------- |
| Individual signal connections | Single interface connection  |
| More wiring                   | Less wiring                  |
| Difficult to scale            | Easily scalable              |
| Less reusable                 | Highly reusable              |
| Basic verification style      | Modern verification style    |

---

# Observations

* Interface successfully grouped all DUT signals.
* DUT and testbench communication became simpler.
* The BCD Adder functionality remained unchanged.
* Simulation results matched Day 1 results.
* Interface reduced signal connection complexity.
* Verification code became cleaner and easier to maintain.

---

# Conclusion

The BCD Adder designed on Day 1 was successfully verified using a **SystemVerilog Interface-based testbench**. The interface simplified signal management and improved testbench organization without affecting the functionality of the DUT. Simulation results confirmed correct BCD addition behavior, demonstrating the advantages of using interfaces in modern verification environments.

---
# Day 6 – Task 1: Creating a Transaction Class for FIFO Verification

## Objective

To create a SystemVerilog **Transaction Class** for FIFO verification and generate randomized stimulus using constraints. This task introduces Object-Oriented Programming (OOP) concepts in SystemVerilog and serves as the foundation for building a verification environment.

---

# Introduction

In modern verification methodologies, transactions are used to represent data packets exchanged between the testbench and the Design Under Test (DUT).

A **Transaction Class** groups all FIFO-related signals into a single object and allows random generation of stimulus using constraints. This approach improves code reusability, readability, and scalability compared to traditional signal-by-signal testbench coding.

---

# Theory

## What is a Transaction?

A transaction is a collection of input and output signals represented as a class object.

For FIFO verification, a transaction contains:

- Reset signal
- Write enable signal
- Read enable signal
- Input data
- Output data
- Full flag
- Empty flag

Instead of handling these signals individually, they are bundled into a single transaction object.

---

## Randomization

SystemVerilog supports constrained random stimulus generation using the `rand` keyword.

### Advantages

- Automatic test generation
- Better coverage
- Reduced manual effort
- Helps uncover corner-case bugs

---

## Constraint-Based Verification

Constraints control how random values are generated.

In this task:

### Reset Distribution

```systemverilog
rst_tb dist {0:=8, 1:=2};
```

Meaning:

- Reset inactive (0) → 80%
- Reset active (1) → 20%

---

### Write Enable Distribution

```systemverilog
wrenb_tb dist {0:=2, 1:=8};
```

Meaning:

- Write disabled → 20%
- Write enabled → 80%

---

### Read Enable Distribution

```systemverilog
rdenb_tb dist {0:=8, 1:=2};
```

Meaning:

- Read disabled → 80%
- Read enabled → 20%

---

### Data Distribution

```systemverilog
data_in_tb dist {
    8'hFF := 10,
    8'hAA := 5,
    8'h55 := 5
};
```

Meaning:

| Data Value | Weight |
|------------|---------|
| FF | 10 |
| AA | 5 |
| 55 | 5 |

The value `FF` has the highest probability of being generated.

---

# Transaction Class Structure

The transaction class contains:

### Random Variables

```systemverilog
rand bit rst_tb;
rand bit wrenb_tb;
rand bit rdenb_tb;
rand bit [7:0] data_in_tb;
```

These variables are randomized during simulation.

---

### Non-Random Variables

```systemverilog
bit [7:0] data_out_tb;
bit full;
bit empty;
```

These variables store DUT outputs.

---

### Display Method

A display function is included for printing transaction contents.

```systemverilog
function void display();
```

This helps monitor generated stimulus and DUT responses.

---



# Features of the Transaction Class

✔ Uses Object-Oriented Programming

✔ Supports Constrained Random Verification

✔ Generates FIFO input stimulus

✔ Stores FIFO output responses

✔ Includes built-in transaction printing

✔ Easily reusable in Generator, Driver, and Monitor components

---

# Verification Significance

This transaction class forms the foundation for advanced verification environments.

It will later be used by:

- Generator
- Driver
- Monitor
- Scoreboard
- Environment

These components communicate using transaction objects rather than individual signals.

---

# Observations

- Successfully created a reusable FIFO transaction object.
- Random variables were declared using the `rand` keyword.
- Constraints controlled reset, read, write, and data generation.
- Distribution constraints biased stimulus toward meaningful FIFO operations.
- Display method provides easy transaction debugging.

---

# Conclusion

A SystemVerilog Transaction Class was successfully created for FIFO verification. The class encapsulates FIFO inputs and outputs into a reusable object and uses constrained randomization to generate realistic stimulus. This task introduces the core concept of transaction-based verification and serves as the first step toward building a complete SystemVerilog verification environment.

---
# Day 8 – Task 1: APB Protocol Slave Design and Verification

## Objective

To design and verify an **APB (Advanced Peripheral Bus) Slave** module using Verilog HDL and simulate its read/write operations using a testbench in Vivado.

---

# Introduction

The **Advanced Peripheral Bus (APB)** is a low-power, low-complexity bus protocol defined in the ARM AMBA architecture. APB is primarily used for connecting low-bandwidth peripherals such as:

- Timers
- UARTs
- GPIO Controllers
- Watchdog Timers
- Configuration Registers

Unlike high-performance buses such as AHB and AXI, APB provides a simple interface with minimal control signals, making it ideal for peripheral communication.

---

# Theory

## APB Transfer Phases

An APB transaction consists of two phases:

### 1. Setup Phase

During this phase:

- `PSEL` is asserted.
- Address (`PADDR`) is driven.
- Write data (`PWDATA`) is driven for write operations.
- Read/Write direction is specified using `PWRITE`.

### 2. Access Phase

During this phase:

- `PENABLE` is asserted.
- Data transfer occurs.
- Slave responds using `PREADY`.

---

# APB Signals

| Signal | Width | Direction | Description |
|----------|---------|------------|-------------|
| PCLK | 1 | Input | APB Clock |
| PRESETn / rst_n | 1 | Input | Active-Low Reset |
| PADDR | 32 | Input | Address Bus |
| PSEL | 1 | Input | Slave Select |
| PENABLE | 1 | Input | Access Enable |
| PWRITE | 1 | Input | Write Control |
| PWDATA | 32 | Input | Write Data |
| PRDATA | 32 | Output | Read Data |
| PREADY | 1 | Output | Transfer Complete |

---

# Working Principle

## Write Operation

When:

```text
PSEL = 1
PENABLE = 1
PWRITE = 1
```

The slave writes `PWDATA` into the memory location specified by `PADDR`.

### Example

```text
Address = 0x12C
Data    = 0xF0A3655D
```

The value is stored in the APB slave memory.

---

## Read Operation

When:

```text
PSEL = 1
PENABLE = 1
PWRITE = 0
```

The slave reads data from the memory location specified by `PADDR` and places it on `PRDATA`.

### Example

```text
Address = 0xFC
```

Output:

```text
PRDATA = Stored Data
```

---

# Design Methodology

The APB Slave module was implemented using:

### Inputs

```verilog
clk
rst_n
paddr[31:0]
psel
penable
pwrite
pwdata[31:0]
```

### Outputs

```verilog
prdata[31:0]
pready
```

### Internal Memory

A register array is used to emulate peripheral registers.

```verilog
reg [31:0] mem [0:255];
```

---

# RTL Architecture

The synthesized RTL schematic consists of:

- APB Slave Module
- Address Decoder
- Register Memory
- Read Data Path
- Write Data Path
- Ready Signal Generation

### RTL Schematic
<img width="1057" height="470" alt="image" src="https://github.com/user-attachments/assets/1e576b47-8911-4ae5-aca8-94e2b684f845" />


---




# Simulation and Verification

A testbench was created to perform multiple APB write and read transactions.

The simulation waveform verifies:

- Address generation
- Write data transfer
- Read data transfer
- Proper assertion of PSEL and PENABLE
- Correct operation of PREADY

---

# Sample Transactions

## Write Transaction 1

| Signal | Value |
|----------|---------|
| Address | 0x12C |
| Data | 0xF0A3655D |
| Operation | Write |

Result:

```text
Memory[0x12C] = 0xF0A3655D
```

PASS ✅

---

## Write Transaction 2

| Signal | Value |
|----------|---------|
| Address | 0xFC |
| Data | 0x1DF59C7B |
| Operation | Write |

Result:

```text
Memory[0xFC] = 0x1DF59C7B
```

PASS ✅

---

## Read Transaction

| Signal | Value |
|----------|---------|
| Address | 0xFC |
| Operation | Read |

Output:

```text
PRDATA = 0x1DF59C7B
```

PASS ✅

---

# Waveform Analysis


<img width="1161" height="577" alt="image" src="https://github.com/user-attachments/assets/01c4acd1-5cbb-4901-8114-06ea1985e591" />


The simulation waveform shows:

### Write Cycle

```text
PSEL    = 1
PENABLE = 1
PWRITE  = 1
```

Data from `PWDATA` is written into memory.

---

### Read Cycle

```text
PSEL    = 1
PENABLE = 1
PWRITE  = 0
```

Stored data is returned through `PRDATA`.

---

### Ready Signal

```text
PREADY = 1
```

indicates successful completion of the APB transaction.

---

# Observations

- APB write operations successfully stored data into memory.
- APB read operations returned correct stored values.
- Address decoding functioned correctly.
- PREADY correctly indicated transfer completion.
- Read and write cycles followed APB protocol timing.
- Simulation results matched expected behavior.

---

# Advantages of APB

- Simple protocol
- Low power consumption
- Easy implementation
- Suitable for peripheral devices
- Minimal hardware overhead

---

# Applications

- UART Controllers
- GPIO Controllers
- Timers
- Watchdog Modules
- Configuration Registers
- Embedded SoCs

---

# Conclusion

An APB Slave module was successfully designed and verified using Verilog HDL. The design correctly implemented APB read and write transactions, address decoding, and ready signal generation. Simulation results confirmed proper functionality according to the APB protocol specification.

---

# Tools Used

- Verilog HDL
- Vivado Simulator
- Vivado RTL Analysis

---

# Concepts Learned

- AMBA APB Protocol
- Peripheral Bus Communication
- Address Decoding
- Register-Based Memory Design
- APB Read/Write Transactions
- RTL Design and Verification
- Waveform Analysis
