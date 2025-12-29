# ALCOROA Language – Overview and Examples
[DOWNLOAD ALCOROA](https://github.com/KNOBIEK/ALCOROA/releases)  
## This document describes the basic syntax, concepts, and examples of the **ALCOROA** language.  

# Comments  
`#this is a comment`  
Everything after # is ignored by the interpreter.

# Functions  
## Basic Function Definition  

```
recursao(z) print z
@recursao 10
```
Defines a function named recursao that receives one parameter and prints it.  
## Function with Type Tags  

Type tags like int, float,list, and text are **ignored by the lexer**.  
They exist only as markers for readability and organization.  

# Recursion  
## Simple Recursion (Without TCO)  
```
recursao(int z) SEQ 10 : @recursao z  
@recursao 10  
```
This is a recursion **without Tail Call Optimization (TCO)**.  
⚠️ Avoid recursion depth greater than 10.

# SEQ Expression
```
SEQ expr1 : expr2  
```

Executes two expressions sequentially  
Returns the value of the last expression  
SEQ can be nested, but always requires exactly two expressions  

# Tail Call Optimized Recursion (TCO)
To create an optimized recursion, use the ```REC``` keyword.  
```
recursao(x) REC(< z 1) expr : callrecursion  
```
Rules:
1 A base condition  
2 An expression to execute  
3 Updated arguments to move toward the base condition  

# Final Optimized Recursion Example  
```
recursao(GEN) REC(> GEN 1) print GEN : GEN = - GEN 1  
@recursao 100  

```
GEN is a global register  
Recursion stops when GEN <= 1  

# Variable Assignment  
```
x = 10
int x = 10
float x = 10
text x = "fabio"
```
Type annotations are optional and not enforced.  

# Fibonacci Example

```
y1 = 0
y2 = 0
fib(n) REC(> n 1) 
    SEQ y1 = - n 1 :
    SEQ y1 = n :
    y2 = + y1 y2 :
    n = - n 1

@fib 10
print y2
```
Calculates the Fibonacci sequence using optimized recursion.  

# Lists
## List Definition

```
x = [1 2 3 4 5 6 7 8 9 10 11 12]  
```

## Accessing Items
```
print ITEM [3 2 1] 2  
print ITEM x 0  
```

## Iterating Over a List with Recursion
```
showlist(index) print * ITEM x index 

recursao(size) REC(> size 0) 
    @showlist size :
    size = - size 1 

@recursao 11

```













