
# Lecture_6: Timing and Verification (2)

## 1. Combinational Circuit Timing
In real circuits, outputs do not change instantly. Delays occur due to some technical resons:
-   Capacitance & resistance in the circuit
-   Life of the circuit
-   Temperature changes
-   Finite speed of light

### Types of Delay
*   **Contamination Delay ($t_{cd}$):** When the output *starts changing* (min delay).
*   **Propagation Delay ($t_{pd}$):** When the output is *finally done changing* (max delay). 
*   **Critical Path:** The path in the circuit that causes the longest delay (determined by $t_{pd}$).

### Output Glitches
*   **Glitch:** When one input transition causes multiple unwanted output transitions (incorrect triggering).
*   **Cause:** Differences in timing across different paths in the circuit.

---

## Sequential Circuit Timing
For sequential circuits (like a D Flip-Flop) to work correctly, the input `D` must be stable when the clock samples it.

### Timing Constraints
-   **Setup Time ($t_{setup}$):** The time data must be stable *before* the clock edge.
-   **Hold Time ($t_{hold}$):** The time data must be stable *after* the clock edge.
-   **Aperture Time ($t_a$):** The total time around the clock edge ($t_{setup} + t_{hold}$).
-   **Metastability:** If data changes during the aperture time, the output gets stuck between 0 and 1 non-deterministically.

### Timing Variables & Formulas
-   $t_{ccq} / t_{pcq}$ = clock-to-q delay (Flip-Flop contamination/propagation delay).
-   $t_{cd} / t_{pd}$ = combinational logic delay (contamination/propagation).
-   $T_c$ = clock period.

**To ensure safe operation between two flip-flops:**
1.  **Setup Time Constraint (Max Delay):** 
    $T_c > t_{pcq} + t_{pd} + t_{setup}$
2.  **Hold Time Constraint (Min Delay):** 
    $t_{ccq} + t_{cd} > t_{hold}$

###  Clock Skew
- Clock does **not** arrive at all flip-flops simultaneously.
- **Skew** = time difference between two clock edges.
- Skew **increases effective `tsetup` and `thold`** -> more sequencing overhead.
- Managed by careful clock network design (e.g., clock trees, meshes).

---

## 2. Circuit Verification
Testing functionality and timing constraints is very time-consuming. 
**Solution:** Split the process into two steps:
1.  Check functionality at a high level (fast).
2.  Check timing and power at a low level (slow).

### Functional Verification
*   Tests logical correctness only. Timing delays are ignored.
*   Uses **Testbenches** to analyze logic. 
*   Runs in simulation, not physical synthesis.

**Types of Testbenches:**

| Type | Input Generation | Error Checking |
|------|----------------|----------------|
| Simple | Manual | Manual (waveforms) |
| Self-Checking | Manual | Automatic |
| Testvector-based | File | Automatic |
| Automatic | Generated | Automatic (vs golden model) |

-   **Golden Model:** 
-  high-level, simpler, verified-correct version of DUT.
- Test pattern generator feeds same inputs to DUT and golden model.
- Comparator checks mismatch.
- **Pros:** fully automated, high coverage, good separation of roles.
- **Cons:** golden model may be hard to write; input generation still challenging.


### Timing Verification
*   **High-Level Simulation:** Timing is modeled artificially using delay statements (e.g., `#5` in Verilog). Not as accurate as real physical circuits.
*   **Circuit-Level Simulation:** Extremely accurate. Requires you to synthesize the design first. The process is heavily dependent on your specific design flow and tools (like Vivado).

---