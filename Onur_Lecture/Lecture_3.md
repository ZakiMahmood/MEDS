# Lecture_3: Sequential Logic and FSMs

## 1. Logic Simplification
**Simplification?** reduce the number of gates for lower cost.

-   **The Uniting Theorem:** Eliminate the expression which is not affecting. If the input changes its value but the output stays the same, that input can be eliminated.
-   **Karnaugh Maps (K-Maps):** to minimize the expression by drawing the map of outputs depends on input.

---

## 2. Basic Storage Elements

### 1. Cross-Coupled Inverters
- Two stable states: Q = 0 or 1
- No control input -> not practical alone

---

### 2. R-S Latch 
- Built from NAND gates

| S | R | Q |
|--|--|--|
| 0 | 1 | 1 (Set) |
| 1 | 0 | 0 (Reset) |

- When R=0 the value is reset and when S=0 the value is set

---

### 3. Gated D Latch
- Controlled by Enable 

| WE | D | Q(next) |
|----|---|---------|
| 0 | X | Q(prev) |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

- WE = 1 -> it become transparent
- WE = 0 -> it holds value

---

### 4. D Flip-Flop
- Built from two back-to-back latches
- Changes occur at clock edge
- Stable output during clock cycle
- Flip-flop: edge-triggered

---

## 3. Registers and Memory

### Register
- Multiple flip-flops in parallel form register
- How many bits of register depend on no of flip flops
- Stores multiple bits

### Memory Array
- Organized as locations * bits

Key concepts:
- Address space = number of locations
- Addressability = bits per location

Operations:
- Decoder selects location
- Multiplexer outputs data

---

## 4. Finite State Machines (FSM)

### Components
- State Register (flip-flops)
- Next State Logic
- Output Logic

### Structure
- Inputs -> Next State Logic -> State Register -> Outputs

---

## State Diagrams
- Circles represent states
- Arrows(arc) represent transitions
- Labels show input conditions

---

| FSM Type | Output Logic Behavior | Difference |
| :--- | :--- | :--- |
| **Moore Machine** | Outputs depend only on the **current state**. | output after some delay |
| **Mealy Machine** | Outputs depend on the **current state** AND the **current inputs**. | output exit at time |
