FIFO Design in Verilog

Overview
This project implements a First-In First-Out (FIFO) memory buffer using Verilog HDL.  
A FIFO is a queue-based memory structure used for temporary data storage where the first data written is the first data read. It is widely used in digital systems such as data buffering, clock domain crossing, and communication interfaces.

Features
- Supports configurable **data width** and **depth**.
- Implements **synchronous / asynchronous FIFO** design.
- Handles **overflow** and **underflow** conditions.
- Uses **circular buffer** technique with read and write pointers.
- Parameterized design for flexible reuse.

Modules

| `fifo.v` | Main FIFO module implementing memory, control logic, and flags. 
| `fifo_tb.v` | Testbench used to verify FIFO functionality. 

Parameters

| `DATA_WIDTH` | Width of each data word | 8 |
| `DEPTH` | Number of words in FIFO | 16 |

How It Works
1. Write Operation
   Data is written into the FIFO when `wr_en` is asserted and the FIFO is not full.  
   The write pointer increments with each valid write.

2. Read Operation 
   Data is read from the FIFO when `rd_en` is asserted and the FIFO is not empty.  
   The read pointer increments with each valid read.

3. Status Flags 
   - `full` indicates FIFO is full (no more writes possible).  
   - `empty` indicates FIFO is empty (no more reads possible).  
   - `count` provides the current number of stored elements.

## Simulation
Run the simulation using ModelSim / QuestaSim / Icarus Verilog:

```bash
vlog fifo.v fifo_tb.v
vsim fifo_tb
run -all
