<!-- ISA = Instruction Set Architecture -->
### Instruction Encoding for SAP-X
- **Bits [7:3]**: 5-bit operation code (32 possible instructions) 2^5 = 32
- **Bits [2:1]**: register select (00=A, 01=B, 10=C, 11=SP)
- **Bit [0]**: mode/direction bit 
- **2 byte instructions**: Byte 1 = opcode, Byte 2 = 8bit address or immediate value

## Instruction Table
| Opcode | Mnemonic | Bytes | Description |
| ------ | -------- | ----- | ----------- |
| 00000  | NOP      | 1 | No operation |
| 00001  | HLT      | 1 | Halt CPU     |
| 00010  | LD rr    | 2 | R <- mem[addr] |
| 00011  | ST rr    | 2 | mem[addr] <- R |
| 00100  | LDI rr   | 2 | R <- immediate |
| 00101  | ADD rr   | 1 | A <- A + R |
| 00110  | ADC rr   | 1 | A <- A + R + carry |
| 00111  | SUB rr   | 1 | A <- A - R |
| 01000  | AND rr   | 1 | A <- A & R |
| 01001  | OR rr    | 1 | A <- A | R |
| 01010  | XOR rr   | 1 | A <- A ^ R |
| 01011  | NOT      | 1 | A <- ~A |
| 01100  | SHL      | 1 | A <- A << 1 |
| 01101  | SHR      | 1 | A <- A >> 1 |
| 01110  | MOV rr   | 1 | if bit0=0: A <- R, if bit0=1: R <- A |
| 01111  | CMP rr   | 1 | set flags from A - R |
| 10000  | JMP      | 2 | PC <- addr |
| 10001  | JZ       | 2 | if Z=1: PC <- addr |
| 10010  | JNZ      | 2 | if Z=0: PC <- addr |
| 10011  | JC       | 2 | if C=1: PC <- addr |
| 10100  | JNC      | 2 | if C=0: PC <- addr |
| 10101  | JN       | 2 | if N=1: PC <- addr |
| 10110  | PUSH rr  | 1 | SP--; mem[SP] <- R |
| 10111  | POP rr   | 1 | R <- mem[SP]; SP++ |
| 11000  | CALL     | 2 | SP--; mem[SP] <- PC+2; PC <- addr |
| 11001  | RET      | 1 | PC <- mem[SP]; SP++ |
| 11010  | OUT      | 1 | Output A |
| 11011  | IN       | 1 | A <- DIP switch input |
| 11100  | NOP2     | 1 | reserved |
