## How to use 1. 
**Download the binary** 
Get the latest `.exe` file from the [Releases](https://github.com/KNOBIEK/ALCOROA/releases). 
2. **File extension** 
Alcoroa source files use the extension: .alcoroa


3. **Run a program**  
From the terminal, run:
```bash
alcoroa main.alcoroa

# =============== ALCOROA ==============
Alcoroa is an interpreted functional programming language with currying support.
This document shows the current features and syntax examples.
 --- ## Comments Use `#` for comments.
 ```alcoroa
# This is a comment

Functions
# Simple function
recursion(z) print z
@recursion 10

Type tags
Tags like int, float, text are ignored by the lexer.
They serve only as markers.

recursion(int z) print z
recursion 10

Recursion
Non-TCO recursion (avoid depth > 10):
recursion(int z) SEQ 10 : @recursion z
recursion 10

SEQ executes two expressions and returns the last:
SEQ expr : expr

TCO recursion requires REC:
recursion(x) REC(< z 1) expr : callrecursion

Final recursion example:
recursion(GEN) REC(> GEN 1) print GEN : GEN = - GEN 1
@recursion 100

Variables
x = 10
int x = 10
float x = 10
text x = "fabio"

Fibonacci Example
y1 = 0
y2 = 0
fib(n) REC(> n 1) SEQ y1 = - n 1 : SEQ y1 = n : y2 = + y1 y2 : n = - n 1
@fib 10
print y2

Lists
x = [1 2 3 4 5 6 7 8 9 10 11 12]
print ITEM [3 2 1] 2
print ITEM x 0

Recursive list printing:
showlist(index) print * ITEM x index
recursion(size) REC(> size 0) @showlist size : size = - size 1
@recursion 11

Clone example:
z = [1 2 3]
CLONE 99 : z
print ITEM z 3

Final working version:
x = [1 2 3 4 5]
z = CLONE ITEM x 2 : []
print ITEM z 0

Conditionals
cond evaluates a condition and returns one of two expressions:
cond(> 2 1) print 33 : print "false"

Global register GEN:
x = cond(> 2 1) print 33 : print "false"
GEN = x

{
  print GEN
}

Operators

print + "hello, " "world"
print == "hi" "hi"
x = 32.2
y = -100
print >= x 2
print <= 2 y


Text Split
text = "fabio 2 ola 2 bem vindo "
arg = " "
z = SPLIT text : arg
print z


Tokens, Parser, Eval Example
index = 0
tokens = ["add" 2 5]
parse = ITEM tokens index

node = cond(== parse "add") + ITEM tokens 1 ITEM tokens 2 : 0
print node

File Writing Example

FILE = "index.html"
CONTENT = "console.log('ALCOROA')\n"
CONTENT = + CONTENT "alert('calling ALCOROA')"
WRITE FILE : CONTENT


List Size Example
LIST_SIZE [] # returns a number

arr = [3 2 1]
GEN = 0
REC(< GEN LIST_SIZE arr) print ITEM arr GEN : GEN = + GEN 1













