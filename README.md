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

Type tags like int, float,list, and text are *ignored by the lexer*.  
They exist only as markers for readability and organization.  
