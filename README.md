ALCOROA is a language where lines starting with `#` are comments.

recursion(z) print z
@recursion 10

Type tags such as `int`, `float`, and `text` are ignored by the lexer. They exist only as markers and do not affect execution.

recursion(int z) print z
recursion 10

This is a recursion without Tail Call Optimization. It is limited and deep recursion should be avoided, preferably no more than 10 levels.

recursion(int z) SEQ 10 : @recursion z
recursion 10

SEQ executes two expressions and returns the last one. SEQ can be nested inside another SEQ, but it always requires exactly two expressions.

SEQ expr : expr

Tail Call Optimized recursion requires the use of the REC keyword. REC means recursion / record. REC requires a base condition, an expression to execute, and arguments that are decremented in order to reach the base case and terminate execution.

recursion(x) REC(< z 1) expr : callrecursion

Final version of a tail call optimized recursion:

recursion(GEN) REC(> GEN 1) print GEN : GEN = - GEN 1
@recursion 100

Variable assignment examples:

x = 10
int x = 10
float x = 10
text x = "fabio"

Fibonacci example using REC:

y1 = 0
y2 = 0

fib(n) REC(> n 1) SEQ y1 = - n 1 : SEQ y1 = n : y2 = + y1 y2 : n = - n 1
@fib 10
print y2

List examples:

x = [1 2 3 4 5 6 7 8 9 10 11 12]
print ITEM [3 2 1] 2
print ITEM x 0

Recursive list traversal:

showlist(index) print * ITEM x index
recursion(size) REC(> size 0) @showlist size : size = - size 1
@recursion 11

Clone example:

z = [1 2 3]
CLONE 99 : z
print ITEM z 3

Final working clone example:

x = [1 2 3 4 5]
z = CLONE ITEM x 2 : []
print ITEM z 0

cond is an evaluator that receives a condition, an expression if true, and an expression if false.

cond(> 2 1) print 33 : print "false"

GEN is a global register or variable. It is accessible from all scopes.

x = cond(> 2 1) print 33 : print "false"
GEN = x

Scopes example:

{
  print GEN
}

Operators and comparisons:

print + "hello, " "world"
print == "hi" "hi"

x = 32.2
y = -100

print >= x 2
print <= 2 y

SPLIT example:

text = "fabio 2 hello 2 welcome "
arg = " "
z = SPLIT text : arg
print z

Tokens, parser, and eval example:

index = 0
tokens = ["add" 2 5]

parse = ITEM tokens index

node = cond(== parse "add") + ITEM tokens 1 ITEM tokens 2 : 0
print node

Write file example:

FILE = "index.html"
CONTENT = "console.log('ALCOROA')\n"
CONTENT = + CONTENT "alert('calling ALCOROA')"
WRITE FILE : CONTENT

LIST_SIZE returns the size of a list as a number.

LIST_SIZE []

Iterating over a list using REC:

arr = [3 2 1]
GEN = 0
REC(< GEN LIST_SIZE arr) print ITEM arr GEN : GEN = + GEN 1

Python Fibonacci example for comparison:

def fib(n):
    if n <= 1:
        return n
    return fib(n-1) + fib(n-2)

print(fib(10))
