# Lecture_1: Introduction, Fundamentals, Transistors, Gates

## 1.The Problem-to-Electron Pipeline

A computer solves problems by navigating a multi-layered as following,

## Transformation Hierarchy:  

    Problem -> Algorithm -> Program/Language -> System Software(VM, OS, MM) -> SW/HW Interfaces (ISA) -> Micro-Architechture -> logic(Gates etc) -> Devices -> Electrons

### Software Layer: 
*    It begins with a **Problem** that is structured into an **Algorithm** , which is then coded into a specific **Program/Language**.  

### The Bridge:
*   System Software communicates with the **Instruction Set Architecture (ISA)** this serves as the vital contract or interface between the software and the physical hardware.  

### Hardware Layer: 
*    The **Micro-architecture** (the specific way an ISA is built) utilizes Logic and electronic **Devices** to finally direct the flow of **Electrons**.

## 2. Components of Computer:
Every computer system relies on three components to function: 

  1. **Computation:** The processing unit that performs calculations.
  2. **Communication:** The units that move data between different parts of the system.
  3. **Storage:** The memory and storage systems that hold data both temporarily and permanently.

## 3. Comparsion:

| Feature | General Purpose (CPU) | Special Purpose (ASIC) |
| :--- | :--- | :--- |
| **Versatility** | High; can execute any program | Low; restricted to specific tasks|
| **Usability** | Easier to program and manage| Harder to design and program |
| **Efficiency** | Balanced; not optimized for one task | Maximum efficiency and performance |

## 4. Transistor:
Transistors serve as electronic **switches** used to build logic gates.

### MOS Transistor Types
*   **n-type MOS**:
    *   Turns **ON** when Gate is High (3V).
    *   Optimized for pulling signals **DOWN** to 0V.
*   **p-type MOS**:
    *   Turns **ON** when Gate is Low (0V).
    *   Optimized for pulling signals **UP** to 3V.

## 5. CMOS Logic Construction

**CMOS** (Complementary MOS) technology combines nMOS and pMOS to create efficient logic gates.

*   **p-MOS Pull-up Network**: Connects output to 3V.
*   **n-MOS Pull-down Network**: Connects output to 0V.
**Configuration:** 

*   **Series Configuration**: Requires every transistor in the path to be ON for the network to conduct
*   **Parallel Configuration**: Requires only one transistor in the path to be ON for the network to conduct.

## Common CMOS Gates

### 1. NOT Gate (Inverter)
* 1 nMOS + 1 pMOS  
* Y = ~A  

### 2. NAND Gate
* pMOS in parallel, nMOS in series  
* Y = ~(A . B)

### 3. AND Gate
* NAND + NOT  

### 4. NOR Gate
* pMOS in series, nMOS in parallel  
* Y = ~(A + B)

## Truth Table

| A | B | A.B (AND) | A+B (OR) | NAND | NOR | ~A |
|--|--|-----------|----------|------|-----|----|
| 0 | 0 | 0 | 0 | 1 | 1 | 1 |
| 0 | 1 | 0 | 1 | 1 | 0 | - |
| 1 | 0 | 0 | 1 | 1 | 0 | - |
| 1 | 1 | 1 | 1 | 0 | 0 | 0 |



