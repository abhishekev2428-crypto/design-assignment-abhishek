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
