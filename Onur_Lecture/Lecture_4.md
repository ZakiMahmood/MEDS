# Lecture 4: Sequential Logic Design, FSMs, and FPGAs

### Sequential Circuits & Memory
- Output depends on:
  - The output depends on present as well as on past state and its a memory element.
- Use memory elements:
  - Flip-Flops
  - Latches

---

## 1. Asynchronous vs. Synchronous
| Asynchronous | Synchronous |
| :--- | :--- |
| State transition occurs at the same time. | State transition occurs after fixed unit of time. |

**Clock signal** is used to keep track of time. 

---
## 2. Sequential Circuits

### D Flip-Flop
- Edge-triggered state element
- Captures input **D** on the **rising edge** of the clock
- Retain the output **Q** for the entire clock cycle

---

### Finite State Machine (FSM) Structure

An FSM consists of three main components:

1. **State Register**
   - Implemented using flip-flops
   - Stores the current state

2. **Next State Logic**
   - Combinational logic
   - Determines next state based on:
     - Current state
     - Inputs

3. **Output Logic**
   - Generates outputs

---

### Moore vs. Mealy FSMs

#### Moore Machine
- Outputs depend **only on current state**

#### Mealy Machine
- Outputs depend on the **current state** AND the **current inputs**

---

### FSM Design Steps

1. Determine how many states are required
2. Create a **state transition diagram**
3. Create a **state transition table**
4. Create a **Truth table**
5. Derive logic expression
6. Draw the circuit diagram

---

## 3. State Encoding Schemes

#### Binary (Fully Encoded)
- Uses `log2(number_of_states)` bits
- Advantage:
  - Less no of flip-flops
- Disadvantage:
  - Logic is in complex form

#### One-Hot Encoding
- Uses `number_of_states` bits
- Only one bit is `1` at a time
- Advantage:
  - Simple logic
- Disadvantage:
  - More no of flip-flops

#### Output Encoding
- Outputs encoded directly in state bits
- Used in **Moore machines only**
- Minimizes output logic

---

## 4. FPGA

### What is an FPGA?
- **Field-Programmable Gate Array**
- A **reconfigurable hardware device**
- It can be programmed to implement custom circuits

---

### Building Blocks
- **Programmable switches** -> Connect components
- **Look-Up Tables (LUTs)** -> Implement logic -> Memory array

---

### Advantages & Disadvantages

#### Advantages
- High performance 
- Energy efficient
- Low development charges
- Reconfigurable 

#### Disadvantages
- Slower than custom ASICs
- Higher area usage

---

### FPGA Applications
- Deep learning (Microsoft Brainwave)
- Cloud acceleration (AWS F1)
- Genomics (DRAGEN)
- Climate modeling
- Memory research (RowHammer, RowPress)
- Architecture prototyping (PiDRAM, MetaSys)

## 5. Hardware Description Languages (HDL) & Verilog

### HDL
- Languages:
  - Verilog
  - VHDL
- UseS:
  - Describe hardware
  - Simulate designs
  - Synthesize circuits

---

### Structural vs. Behavioral Modeling

#### Structural (Gate-Level)
- Connects:
  - Gates
  - Lower-level modules

#### Behavioral
- Describes functionality using:
  - `case`
  - `if`
  - `assign`

---

### Blocking vs Non-Blocking operator

-   **Blocking (=):**
    Assignments are made immediately. Process waits until the first is complete, step-by-step.
    Used for **Combinational** logic (inside always @(*)).

-   **Non-Blocking (<=):**
    Assignments are made in parallel at the end of the block.
    Used for **Sequential** logic (inside always @(posedge clk)).