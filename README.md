
# **intelliRed**
16 bit MIPS style Micro

![alt text](https://i.imgur.com/wZNK6Iy.png)
*(art by @0x526f6e696e)*

###### PROGRAMMING MODEL

The idea is to be able to use a mips32 gcc compiler and then convert the 32 bit mips to this custom 16 bit mips style CPU/ISA.
for instance: *https://godbolt.org/z/TWz4jh*

#### The CPU has the following specifications

* 16 bit data
* 32 integer registers
* 128 words of RAM
* 32 input ports with registers
* 32 output ports
* 6 stage pipeline
* 22 tick clock

# **ASSEMBLY LANGUAGE**



 REGISTER OP ASM MNEMONIC    | RTL                              | RTL                      | IMMEDIATE OP ASM MNEMONIC 
---------------------------- | -------------------------------- | ------------------------ | --------------------------
add $rd, $rs1, $rs2          | R[$rd] ← R[$rs1]  +  R[$rs2]     | R[$rd]← R[$rs1] + imm	   |	unused                  
addv $rd, $rs1, $rs2	       | R[$rd] ← R[$rs1]  +  R[$rs2]     | unused                   |  unused
no carry from bit 7 to 8     | no carry from bit 7 to 8         | unused                   |  unused
sub $rd, $rs1, $rs2	         | R[$rd] ← R[$rs1]  -  R[$rs2]     | R[$rd]← R[$rs1] - imm    | 	sub $rd, $rs1, imm
and $rd, $rs1, $rs2	         | R[$rd] ← R[$rs1] and R[$rs2]     | R[$rd]← R[$rs1] and imm  |  and $rd, $rs1, imm
abs $rd, $rs1, $rs2	         | R[$rd] ← abs R[$rs1]             | unused                   |  unused
xor $rd, $rs1, $rs2	         | R[$rd] ← R[$rs1] xor R[$rs2]     | R[$rd]← R[$rs1] xor imm  |  xor $rd, $rs1, imm
sll $rd, $rs1, $rs2	         | R[$rd] ← R[$rs1] <<  R[$rs2]     | R[$rd]← R[$rs1] << SHAMT |  sll $rd, $rs1, shamt
srl $rd, $rs1, $rs2	         | R[$rd] ← R[$rs1] >>  R[$rs2]     | R[$rd]← R[$rs1] >> SHAMT |  srl $rd, $rs1, shamt
sra $rd, $rs1, $rs2	         | R[$rd] ← R[$rs1] >>  R[$rs2]     | R[$rd]← R[$rs1] >> SHAMT |  sra $rd, $rs1, shamt	
unused                       | unused                           | pc ← address             |	j address 
