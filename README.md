# ALCOROA Language – Overview and Examples
## This document describes the basic syntax, concepts, and examples of the **ALCOROA** language.  

Alcoroa is an interpreted, functional, curried programming language with a pragmatic approach, designed to run within a limited memory space and a lightweight garbage collection system.  
![alcoroa codes](https://github.com/KNOBIEK/ALCOROA/blob/main/imgs/alcoroa_print_code2.png)

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

