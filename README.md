**Floating Point multipler**

1 bit: Sign
5 bits: Exponent (biased by 15)
6 bits: Fraction (with implied leading 1)


**Simulation Design (Single-cycle):**
Your first version computes the multiplication combinationally in one clock cycle:

- Unpacks the sign, exponent, and fraction from both inputs

- Detects if either operand is zero
- XORs the signs, adds the exponents (adjusting for bias)

- Multiplies the 7-bit mantissas (with implied leading 1)

- Normalizes if the product ≥ 2.0 (bit 13 is set)

- Handles underflow (E < 2) and overflow (E > 30)

- Registers the result on the next clock edge

**Synthesis Design (3-stage pipeline):**
**Your optimized version breaks the work across three pipeline stages:**

- Stage 1: Unpacks inputs, detects zeros, prepares mantissas

- Stage 2: Performs the 7×7 multiplication

- Stage 3: Normalizes, handles special cases, packs the result

**Simualtion vs Synthesis**:

There needs to be pipeline so errors dont occur with everything trying to be crammed into one clockcycle
3 stage pipeline was implemented
**Where can this be used **
A floating point multipler can be used in DSP applicaitons and AI applicaitons where Floating Point Operatiosn are executed aka FLOPs.
