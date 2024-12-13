# VHDL Counter Overflow Bug

This repository demonstrates a common but subtle bug in VHDL: integer overflow in a counter. The `buggy_counter.vhd` file contains a counter implementation that uses the `integer` type.  This type has a limited range, and if the counter attempts to increment beyond the maximum value, an overflow occurs. This overflow can be difficult to detect during simulation, especially if the counter doesn't reach its limit within the simulation timeframe.  The `fixed_counter.vhd` file provides a corrected version using `unsigned` for robust behavior.

## How to Reproduce

1. Simulate `buggy_counter.vhd` with a testbench that runs for a sufficiently long period to exceed the integer limit (which is implementation dependent but may be as low as 2^31). Observe the unexpected behavior.
2. Simulate `fixed_counter.vhd` and see the corrected, wrapping behavior.

## Solution

The solution is to use an unsigned type (`unsigned` from `ieee.numeric_std`) to represent the counter instead of the `integer` type. `unsigned` will correctly wrap around when it overflows.