# MCS51 cycle rule

It seems that a complete table is available but exact category not done.

## (4 cycle) Multiply and divide 

`MUL AB` and `DIV AB` are only instructions that take 4 cycles. All following take 2 cycles and unlisted ones take 1.

## (Potential) jumps

* `SJMP`, `AJMP`, `LJMP`, `JMP @A+DPTR`
* `ACALL`, `LCALL`, `RET`, `RETI`
* `JB`, `JNB`, `JBC`, `JC`, `JNC`
* `JZ`, `JNZ`, `CJNE`, `DJNZ`

## Move between memory(including R0-R7)

* `PUSH`, `POP`
* `MOV addr, addr`, `MOV reg, addr`, `MOV addr, reg`
* `MOV @reg, addr`, `mov addr, @reg`

## 2-op bit operation(except `mov c, bit`)

* `anl c, bit`, `anl c, /bit`
* `orl c, bit`, `orl c, /bit`
* `mov bit, c`

## 3-byte instructions

(Not including mentioned above)

* `anl addr, #imm`, `orl addr, #imm`, `xrl addr, #imm`
* `mov addr, #imm`
* `mov dptr, #imm`

## Misc

* `movc`, `movx`
* `inc dptr`
