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





