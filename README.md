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

