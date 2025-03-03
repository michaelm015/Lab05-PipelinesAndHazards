# Section 1

| PC | Opcode | src1_addr | src1_out   | src2_addr | src2_out   | dst_addr | dst_data   |
|----|--------|-----------|------------|-----------|------------|----------|------------|
| 0  | 0x23   | 0         | 0x00000000 | 2         | 0x00000000 | 0        | 0x00000000 |
| 4  | 0x23   | 0         | 0x00000000 | 2         | 0x00000000 | 0        | 0x00000000 |
| 8  | 0x00   | 2         | 0x00000000 | 2         | 0x00000000 | 0        | 0xxxxxxxxx |
| 12 | 0x2B   | 0         | 0x00000000 | 3         | 0x00000000 | 2        | 0x00000056 |
| 16 | 0x00   | 3         | 0x00000000 | 2         | 0x00000056 | 2        | 0x00000056 |
| 20 | 0x08   | 3         | 0x00000000 | 5         | 0x00000000 | 3        | 0x00000000 |
| 24 | 0x00   | 5         | 0x00000000 | 3         | 0x00000000 | 3        | 0x00000084 |
| 28 | 0x00   | 6         | 0x00000000 | 2         | 0x00000056 | 4        | 0xFFFFFFAA |
| 32 | 0x00   | 6         | 0x00000000 | 2         | 0x00000056 | 5        | 0x0000000C |
| 36 | 0x08   | 5         | 0x0000000C | 4         | 0xFFFFFFAA | 6        | 0x00000000 |
| 40 | 0x04   | 5         | 0x0000000C | 0         | 0x00000000 | 7        | 0x00000056 |
| 44 | 0x23   | 0         | 0x00000000 | 8         | 0x00000000 | 8        | 0xFFFFFFA9 |
| 48 | 0x00   | 0         | 0x00000000 | 0         | 0x00000000 | 6        | 0x00000000 |
| 52 | 0x00   | 0         | 0x00000000 | 0         | 0x00000000 | 31       | 0x0000000C |
| 56 | 0x00   | 0         | 0x00000000 | 0         | 0x00000000 | 8        | 0x00000000 |

# Section 2

The table for the pipelined data path is different from the single cycle datapath table due to stalls, hazards, and the pipelining itself. The pipelining adds 4 cycles to the execution of the init.asm program, and the value differences are due to the stalls and hazards. Two types of hazards that occur are data and control hazards. A control hazard happened at the branch instruction because the value of $a2 was not ready for the branch instruction. A data hazard happened at the add instruction because it attempts to use $v0 before it has returned from the lw instruction.

# Section 3

add $a1, $a0, $a0 <br/> <br/>
I chose this instruction because neither $a0 or $a1 are needed immediately after, so no hazards are introduced. $a1 also gets overwritten later in the addi instruction, so whatever is stored in $a0 has no impact on what the program outputs later. The inclusion of this "buffer" instruction does not eliminate the hazard because the add instruction is still dependent on $v0. However, this new instruction eliminates the stall caused by this hazard.
