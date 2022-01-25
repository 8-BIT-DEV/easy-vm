### Fair warning this library is new and unfinished
# EasyVM
EasyVM is an easy to use and general purpose virtual machine to be used in compilers. Its instructions are inspired by MIPS and GNU Lightning.

## Current features and planned features
  - [X] Generate EVM32 code and convert to binary
  - [X] Execute some EVM32 instructions
  - [X] Export EVM Objects (No loading support yet)
  - [ ] Read and link EVM Objects and then convert to ELF
  - [ ] Memory protection
  - [ ] Siganls (Like interupts)
  - [ ] Assembling EVM32 down to x86, amd64, sparc and 6502

# Compiling
EVM is currently in very early development so things in the API are bound to change. The project uses A makefile to produce the .so file and the test executable. Once the project files are installed run the following commands.

...
  make build
  make test
...

# Instructions
EVM run the Instruction set referred to as EVM32 it is 32 bit and signed. There is some support for floating point operations and in the furture there may be support for 64 bit operations in the form of long operations. Instructions are formed by the nibbles the instruction and modifier. Modifiers change whether instructions operate on Immediates or Registers. so the modifier "REGISTER" would make the "add" instruction take "R,R,R" and the modfier "IMMEDIATE" would make the "add" instrution take "R,R,I".

### Registers
There are 32 registers in EVM there is one ZERO register, 1 return register, 9 argument registers, 16 general registers, 1 flag register, 1 frame pointer, 1 stack pointer and 1 program counter. r31 being the PC and r1 being the return register. Only A few instructions are listed here so most are currently are undocumented but as the library grows into A more complete state more documentation will be written.

#### Add
Add can be affected by many modifers but for now I only talk about the 2 basic ones "IMMEDIATE" and "REGISTER".
  - "REGISTER" (RD,RS1,RS2) {RD=Register Destination, RS1=Register Source 1, RS2=Register Source 2}
  - "IMMEDIATE" (RD,RS,IS) {RD=Register Destination, RS=Register Source, IS=Immediate Source}

The add instruction also doubles as A copy/mov instruction using r0 to always act as 0 like in MIPS.
