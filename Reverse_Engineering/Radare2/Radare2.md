# Radare2
* * *

## Run program
```
r2 binaryFile

ood # reload the program

r2 -w binaryFile # open in writing mode

```

## Debugger
```
r2 -d -A binaryFile # in debug mode then analyze 
aaa or aaaa
s main  # seek main
db main # debug bread at main
dc 			 # continue until break point
S				# Step over
s				# step into
u				# go back
```

## Memory
```
px 16 @ address
```

## Visual Modes
```
Vpp
V!
VV -> then V or Shift V
```

## Function
```
af  # analyze function

pdf @function # pring disasseble function

afvd # get the address and values of function args

: afvn oldname newname # to rename a variable

afl  # list functions
afl | grep main # find main
```

## Generals
```
ax?			# analyze XREF

/?			# search

ps?			# print strings

C?			# comments

:			# enter command line mode
```


