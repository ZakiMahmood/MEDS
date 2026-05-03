# Lecture_5: HDL, Timing, and Verification

## 1. Design 

- There are two main approaches to digital design:

| Approach | Direction | Flow |
|----------|-----------|------|
| **Bottom-Up** | Low → High | Leaf cells → Sub-modules → Top Module |
| **Top-Down** | High → Low | Top Module → Sub-modules → Leaf cells |

- **Leaf cells** are the basic gates at the loweR level of abstraction.

---

## 2. Module in Verilog

A **module** is the basic building block in Verilog.

```verilog
module exercise (d, e, f, z);
    input d;
    input e;
    input f;
    output z;

endmodule
```


### Bits Manipulation

| Operation | Syntax | Description |
|-----------|--------|-------------|
| Multi-bit definition | [3:0] c | Creates a 4-bit data |
| Bit slicing | a[3:1] | Selecting a portion of data |
| Bit concatenation | a[2], b[0] | Combines two separate data |
| Bit duplication | 4{d[0]} | Create copies of data |

###  Number Representation

Follow format of Number: **N'Bxx**

| Symbol | Meaning |
|--------|---------|
| N | No of bits |
| B | Base (b binary, h hex, d decimal, o octal) |
| xx | The actual value |

**Example:**
4'hA   // 4-bit hexadecimal number (value = 10)
4'b0111   // 4-bit binary number (value = 7)
---

## 3. HDL Implementation Styles

| Style | Description |
|-------|-------------|
| **Structural** | In this sub-modules are instantiated and then connected via wires. **Gate-level**  |
| **Behavioral** | In behavioral coding operators are used rather than explicit gates. **Functional** |

---

## 4. Workflow for HDL

Code  ──►  Synthesis  ──►  Simulation

## 5. Parameterized Modules

Through parameterized module variables are resize easily without interuption in code,it can aslo change in the testbench code :

**Example:**
#(parameter width = 4)

---

## 6. Sequential Logic in Verilog

Sequential logic has **memory** and relies on clock transitions.

- State transitions are triggered by the clk signal
- Uses the 'always' construct with posedge (rising edge) or negedge (falling edge)

### Sync vs. Async Reset

| Reset Type | Behavior |
|------------|----------|
| **Synchronous** | Reset happen at the edge of the clock( positive or negitave edge) |
| **Asynchronous** | Reset happen exactly at the same time reset is high or low not depend on clock |

### The `always` Block

- Sequential statements must go inside an 'always' block
- The block is triggered by a change in its **sensitivity list**
- Any signal assigned inside an 'always' block must be declared as 'reg'
- The 'assign' keyword not used inside an 'always' block

---

## 7. Circuit Timing Basics
- Gates take time to process signals.

| Term | Symbol | Definition |
|------|--------|------------|
| **Contamination Delay** | $t_{cd}$ | When the output *starts changing* (min delay). |
| **Propagation Delay** | $t_{pd}$ |  When the output is *finally done changing* (max delay). |
 
---

## 8. Glitches & Skew (the annoying stuff)

- **Glitches:**
  - Output randomly flickers before settling
  - Usually harmless -> ignore unless it causes real issues

- **Clock Skew:**
  - Clock doesn’t hit all flip-flops at the same time
  - Makes timing harder to satisfy
---

## 9. Timing in Sequential Circuits

Flip-flops require stable data to function correctly.

| Parameter | Definition |
|-----------|------------|
| **Setup Time** ($t_{setup}$) | Time data must be stable **before** the clock edge |
| **Hold Time** ($t_{hold}$) | Time data must be stable **after** the clock edge |

If data changes during either of these windows, **metastability** occurs — the output gets stuck between 0 and 1.

## 10. The Two Timing Rules 

### Rule 1: Setup Time (don’t be late)

- Flip-flop needs data **before** the clock edge.
- If data comes late -> boom, wrong value.

- Formula:
  `Clock Period > tpcq + tpd + tsetup`

- If it breaks:
  - slow down clock  
  - or simplify your logic (shorten path)

---

### Rule 2: Hold Time (don’t be too fast)

- Data changes *too quickly* and messes up the next flip-flop.

- Formula:
  `tccq + tcd > thold`

- If it breaks:
  - add buffers (literally slow things down)

---

- **Golden rule:**  
    - Setup = max delay issue  
    - Hold = min delay issue 

## 11. Verification

| Type | Description | Method |
|------|-------------|--------|
| **Functional Verification** | Checks if logic is correct (ignoring physical timing) | **Testbenches** — feed test vectors into the Device Under Test (DUT) and check outputs |
| **Timing Verification** | Checks setup, hold, and skew constraints | Done mostly by **synthesis tools** |