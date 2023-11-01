# GDB
* * *

## Debug
```
gdb -q fileName
```

## syntax
```
show disassembly-flavor
set disassembly-flavor intel
set disassembly-flavor att
```

## info
```
info file
info functions
info frame
```

## Assembly
```
disass
```

## Break points
```
break or b
b main -> if debugging symboles are active
b * <address>
info b
delete <number> -> deletes breakpoints number x
```

## Run a program
```
run or r
run argument
run < path/to/file
```

## Steps
```
# Forward Step
stepi or si	 -> on instruction at a time (step into subroutine)
step or s 		-> steps one line at a time
until or u		-> doesn't step into subroutines
continue or c -> until the next breakpoint

# Reverse steps
reverse-next or rn
reverse-neti or rni
reverse-continue or rc

# direction of execution
set exec-direction forward/reverse
```

## Registers
```
info reg
```

## Memory
```
x/16x 0xvffff304-40  		-> examine memory at expression
```

## Data Tyep
```
/i	$rax		-> asm instruction
/x	$rax		-> hex value
/d	$rax		-> decimal
/b	$rax		-> byte
/h	$rax		-> half word (2bytes)
/w	$rax		-> word (4 bytes)
```

## Stack
```
backtrace or bt 	-> print trace of the call stack
```

## ret2libc
```
find "/bin/sh" libc
p system
p exit
```

## Remote Target
```
gdb
target remote localhost:5555
```


## Run a binary as a network service
```
while true; do nc -lnvp 6666 -e ./binaryName; done

#check netstat
netstat -antp

sudo gdb -q
ps -aux
attach PID # PID of binaryName
```
