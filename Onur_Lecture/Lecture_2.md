# Lecture_2: Combinational Logic 

## 1. Building Blocks of Computers
- All computers are made from:
  - Transistors 
  - Logic Gates  
  - Combinational Circuits
- Two main transistor types:
  - **nMOS** 
  - **pMOS** 
- CMOS gates use:
  - Pull-up network (pMOS)
  - Pull-down network (nMOS)

## 2. Moore's Law
-   Number of transistors doubled on microchip after every 2 years

## 3. Logic Gates & Boolean Algebra
### Basic Gates:
- AND
- OR 
- NAND 
- NOT
- XOR
- NOR

### Boolean Laws:
- Identity
- Commutative
- Associative
- Distributive
- Complement
- Involution
- DeMorgan’s Laws

## 4. Combinational vs Sequential Logic
- **Combinational Logic:**
  - The output only depends on present state it is not a memory element.
- **Sequential Logic:**
  - The output depends on present as well as on past state and its a memory element.

## 5. Standard Functional Forms 
- **Product of Sums (POS):**
  - AND of OR terms (maxterms) represented as 0 -> A=0, A' = 1
- **Sum of Products (SOP):**
  - OR of AND terms (minterms) represented as 1 -> A=1, A' = 0

## 6. Important Combinational Building Blocks

| Block | Function |
|------|--------|
| Multiplexer (MUX) | Selects 1 of N inputs |
| Full Adder | Adds 3 bits -> sum + carry |
| Decoder | n inputs -> 2^n outputs, only one output is high at a time |
| PLA | Implements SOP using AND + OR arrays |
| ALU | Performs arithmetic & logic operations |
| Tri-State Buffer | Output = 0, 1, or Z (high impedance) |

# 9. Power 
- **Dynamic Power:**
  - P = C * V^2 * f
- **Static Power:**
  - P = V * I_leakage
- Series transistors → slower than parallel
- **Energy Consumption:** 
  - Power * Time.

