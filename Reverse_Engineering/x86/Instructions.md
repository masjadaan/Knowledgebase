# x86 Instructions
* * *

## NOP (No Operation)
- `nop`
- it is used to pad/align bytes, or just to delay time

## PUSH
- `push immediate/register`
- it decrements the stack pointer, esp, by 4 (in a system of 4B address)
- then, it pushes an immediate or value in a register onto the stack

## POP
- `pop register`
- ESP points to a value, pop places this value into the register 
- then, it increments the stack pointer, esp, by 4 (in a system of 4B address)
- e.x: pop rbp
	- place the value that ESP points to in rbp, then increments esp by 4

## CALL
- `call function`
- it decrement exp by 4
- then, it pushes the next instruction of the crrent function on the stack
- finally, it places the first instruction of the called function in Instruction Pointer EIP
- if the function receives parameters, then the parameters are pushed from right to left

## RET
### Cdecl
- `ret`
- it places the value that ESP points to in EIP (this is the next instruciton)
- it increments esp by 4 bytes

### Stdcall
- `ret 0x8`
- it places the value that ESP points to in EIP
- it adds bytes to ESP

## MOV
- `mov destination <- source`
- it is applicable for:
	-  register to register
	-  memory to register
	-  register to memory
	-  immediate to register
	-  immediate to memory
-  but NEVER memory to memory
-  in Intel syntax, [ ] means dereference an address

## LEA Load Effective Address
- `lea destination <- source`
- square brackets [ ] with this instruction does **`NOT`** mean dereference
- it moves the address in source to destination
- example:
```
ebx = 0x2, edx = 0x1000
lea eax, [edx + ebx*2] => eax = 0x1000 + (0x2 * 2) = 0x1004
# eax has the address 0x1004 NOT its value
```

## Leave Function epilogue
- `leav`
- it set esp to ebp
- pop ebp
	- ESP points to a value, pop places this value into ebp 
	- then, it increments the stack pointer, esp, by 4
- not always exist, Depends on compiler.

## Jump
- `jmp destination`
- it changes eip to a spicified address
- jmp -2 == infinite loop for short relative jmp

- `jne / jnz` (Jump if not equal, jump if not zero)
- if operands are equal, then it sets ZF = 1, otherwise ZF = 0
- if ZF = 0 -> don't jump, otherwise jump

- `JLE/JNG` Jump if Less or Equal / Jump if Not Greater Destination
- jump if the destination operand is less than or equal the source operand (signed)

- `JGE/JNL` Jump if Greater or Equal / Jump if Not Less Destination
- jump if the destination operand is greater than or equal the source operand (signed)

## Compare
- `CMP Destination, Source`
- It performs **subtraction** (Destination – Source)
- then, It sets the zero flag if the difference is zero (operands are equal).
- It doesnʼt mess up any register.


## Test (Logical Compare)
- `TEST  Destination, Source`
- It performs a bit-wise **AND** (Destination & Source)
- If the AND operation is zero, then ZF = 1. otherwise, ZF = 0.
- if the the number of set bits is even. Then PF =1, otherwise PF = 0.
- if the sign bit is set then, SF = 1, otherwise SF = 0.
- it doesnʼt mess up any register.

## XOR bit-wise Logical Exclusive
- `xor Destination, Source`
- remember, similar means 0
- XOR is used to zero a register, by XORing it with itself, because itʼs faster than a MOV

## Negation
- `NOT Negation` / One's Complement ~Operand

## ADD
- `add destination <- source`
- it adds the value in source to the value in destination and stores the result in destination
- Either the destination or the source can be immediate or register but not both
- it sets flags depending on the result


## SHL Shift Logical Left
- `SHL Destination ← number of shifts`
- Can be explicitly used with the C “<<” operator.
- Shift is either cl, between 1 and 64 , (lowest byte of ecx), or a 1 byte immediate.
- Each shift to the left by n lead to multiply the number by 2 to power of n .
- Shift to left will fill the vacant spaces with zeros.

## SHR Shift Logical Right
- `SHR Destination → number of shifts`
- Can be explicitly used with the C “>>” operator.
- Shift is either cl, between 1 and 64 , (lowest byte of ecx), or a 1 byte immediate.
- Each shift to the right by n lead to divide the number by 2 to power on n.
- Shift to right will fill the vacant spaces with zeros.


## IMUL Signed Multiply
- Three forms
```
imul <source> → multiply source by itself
imul <dest>, <src/imm> → multiply src/imm by dest
imul <dest>, <src>, <imm> → multiply imm by src, result in dest
```
- The result is placed in edx:eax
- The final result is truncated to the size of the destination operand.


## IDIV Integer Division
- The integer division uses a combination of the A and D registers.
- The divisor can be a memory location or register, but not an immediate.
- Result will be placed in the A register (al/ax/eax/rax) and the remainder in either the ah, dx, edx, or rdx register.
- The A, and possibly the D register, must be used in combination for the dividend.
	- Byte Divide: ax for 16-bits
	- Word Divide: dx:ax for 32-bits
	- Double-word divide: edx:eax for 64-bits
	- Quadword Divide: rdx:rax for 128-bits.


#### Notes
- `ebp - some value` = local variables
- `ebp + some value` = passing arguments to a function
- In Intel syntax, square brackets [ ] means derefrencing an address
	- `mov eax, ebx`
		- move the address in ebx into eax
	- `mov eax, [ebx]` 
		- go to the address in ebx
		- dereferenc that address and get the value.
	- `mov eax, [ebx + exc * X]` (X = 1, 2, 4, 8)
		- first, do the math operation and get the address
		- go to that address and dereference it to get the value
	- `mov eax [ebx + ecx * X + Y]` (Y = one or four bytes)
		- first, do the math operation and get the address
		- go to that address and dereference it to get the value
- Array references are represented as 
	- `[base + index * scale + offset]`
