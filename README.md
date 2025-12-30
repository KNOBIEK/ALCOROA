# ALCOROA Language – Overview and Examples
## This document describes the basic syntax, concepts, and examples of the **ALCOROA** language.  

Alcoroa is an interpreted, functional, curried programming language with a pragmatic approach.  

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
fib(n) REC(> n 1) SEQ y1 = - n 1 : SEQ y1 = n : y2 = + y1 y2 : n = - n 1
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
recursao(size) REC(> size 0) @showlist size : size = - size 1 
@recursao 11
```

## Clone and List Manipulation
```
z = [1 2 3]
CLONE 99 : z
print ITEM z 3
```
## Final Working Example
```
x = [1 2 3 4 5]
z = CLONE ITEM x 2 : []
print ITEM z 0
```
# Conditional Expression (cond)
```
cond(condition) expr_if_true : expr_if_false
```

Example:  
```
cond(> 2 1) print 33 : print "false"
```
# Global Register (GEN)
GEN ,GENX and GENY is a global variable accessible from all scopes.
```
x = cond(> 2 1) print 33 : print "false"
GEN = x
```

# Scope Example
```
{
    print GEN
}
```
# Operators Examples
```
print + "hello, " "world"
print == "hi" "hi"

x = 32.2
y = -100

print >= x 2
print <= 2 y
```

# SPLIT Text
```
text = "fabio 2 hello 2 welcome "
arg = " "
z = SPLIT text : arg
print z
```
Splits a text into a list based on a delimiter.  

# Tokens, Parser, and Evaluator Example
```
index = 0
tokens = ["add" 2 5]
parse = ITEM tokens index
node = cond(== parse "add") + ITEM tokens 1 ITEM tokens 2 : 0
print node
```
# File Writing Example
```
FILE = "index.html"
CONTENT = "console.log('ALCOROA')\n"
CONTENT = + CONTENT "alert('calling ALCOROA')"
WRITE FILE : CONTENT
```
# List Size Example
```
arr = [3 2 1]
GEN = 0
REC(< GEN LIST_SIZE arr) print ITEM arr GEN : GEN = + GEN 1
```



## How to Use
### Running ALCOROA

1. Download the **ALCOROA binary**.  
2. Run the binary in your terminal, followed by the name of the source file.  

#### Example
```sh
alcoroa main.alcoroa
```

# Adding Libraries
You can load additional source files (libraries) by passing them as extra arguments when running ALCOROA.  
## Example
```sh
alcoroa main.alcoroa mylib.alcoroa
```
In this example:  
main.alcoroa is the main entry file  
mylib.alcoroa is an additional library loaded at runtime  
Multiple libraries can be added in the same way.  

[DOWNLOAD ALCOROA](https://github.com/KNOBIEK/ALCOROA/releases)  
**Note:** The current binary is for Windows 64-bit only.  





