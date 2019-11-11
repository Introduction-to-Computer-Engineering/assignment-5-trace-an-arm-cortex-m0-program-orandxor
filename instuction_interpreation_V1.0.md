### Reference
All the instruction links and one of the footnotes come from this [ARM Cortex-M0 User Guide](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.dui0497a/BABIHJGA.html).

### trace assignment
| Label | Instruction | Intepretation |
| --- | --- | --- |
| value: |  | function named value |
| | .word 6 | initialize four byte value to 6 |
| negate: |  | function named negate |
|  | sub sp,sp, #8 | subtract the location of stack pointer 8 bytes |
|  | str r0, [sp,#4] | store register 0 to the first four bytes of the stack pointer |
|  | ldr r3, [sp,#4] | load register 3 from the first  four bytes of the stack pointer |
|  | rsbs r3, r3, #0 | negate the contents of register 3 and save to register 3 |
|  | movs r0 , r3 | move the contents of register 3 to register 0 |
|  | add sp, sp, #8 | Add 8 to the stack pointer |
| main: |  | function named main also the starting point of programs |
|  | push {r4, lr} | push on to register list |
|  | ldr r3, .L6 | load into register 3 the contents of function L6 which calls a 4 byte value frm the function value |
|  | ldr r3, [r3] | load into register 3 the memory of register 3 |
|  | cmp r3, #0 | compare the contents of register 3 to the value 0 |
|  | ble .L4 | branch if less than to function L4 |
|  | ldr r3, .L6 | load to register 3 the contents of function L6 which calls value which is 6 |
|  | ldr, [r3] | laod to register 3 the contents of register 3 |
|  | movs r0, r3 | move the contents of register 3 to register 0 |
|  | bl negate | branch to function negate |
|  | movs r2, r0 | move the contents of register 0  to register 2 |
|  | ldr r3, .L6 | load from function L6 which calls function value that is 6 |
|  | str r2, [r3] | store on to register 2 the address of register 3 |
| .L4 |  | function named L4 |
|  | movs r3, #0 | move onto register 3 the value 0 |
|  | movs r0, r3 | move the  contents of register 3 to register 0 |
|  | pop {r4, pc} |  pops register 4 to the pc |
| .L6 |  | function named L6 |
|  | .word value | load on to 4 bytes the value of function value which is 6 |

### Footnotes

**1** _[Addressing modes](http://www.davespace.co.uk/arm/introduction-to-arm/addressing.html)_ 

**2** _[Conditional execution](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.dui0497a/BABEHFEF.html)_ 
