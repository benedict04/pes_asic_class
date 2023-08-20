![image](https://github.com/benedict04/pes_asic_class/assets/109859485/2d45d0e2-8c4c-4596-86fa-f146a0c2cb05)         ![image](https://github.com/benedict04/pes_asic_class/assets/109859485/bcf6ff7b-42f4-4883-a367-3d74c1cfcff9)


# pes_asic_class
The objective of VLSI (Very Large Scale Integration) physical design for ASICs (Application-Specific Integrated Circuits) is to transform a digital circuit's logical representation into a physical layout that meets various performance, power, area, and manufacturability requirements.

## SKILL OUTCOMES

-  Architectural Design
-  RTL Design / Behavioral Modeling
-  Floorplanning
-  placement
-  clock Tree Synthesis
-  Routing


TABLE OF CONTENTS

 DAY 1

## Introduction to RISCV ISA and GNU Compiler Toolchain
- Introduction to Basic Keywords

  Introduction

  - ISA defines the interface between a computer's hardware and its software, specifically how the processor and its components interact with the software instructions that drive the execution of tasks.
  - It encompasses a set of instructions, addressing modes, data types, registers, memory organization, and the mechanisms for executing and managing instructions.

  RISC-V (Reduced Instruction Set Computing - Five)

  - It is an open-source Instruction Set Architecture (ISA) that has gained significant attention and adoption in the world of computer architecture and semiconductor design.
  - RISC architectures simplify the instruction set by focusing on a smaller set of instructions, each of which can be executed in a single clock cycle. This approach usually leads to faster execution of individual instructions.
![image](https://github.com/benedict04/pes_asic_class/assets/109859485/9b741651-11c9-474f-ab28-dcb517cdb588)



   ## From Apps to Hardware

  1. Apps: Application software, often referred to simply as "applications" or "apps," is a type of computer software that is designed to perform specific tasks or functions for end-users.

 2. System software: System software refers to a category of computer software that acts as an intermediary between the hardware components of a computer system and the user-facing application software. It provides essential services, manages hardware resources, and enables the execution of application programs. System software plays a critical role in maintaining the overall functionality, security, and performance of a computer system.'

3. Operating System: The operating system is a fundamental piece of software that manages hardware resources and provides various services for both users and application programs. It controls tasks such as memory management, process scheduling, file system management, and user interface interaction. Examples of operating systems include Microsoft Windows, macOS, Linux, and Android.

4. Compiler: A compiler is a type of software tool that translates high-level programming code written by developers into assembly-level language.

5. Assembler: An assembler is a software tool that translates assembly language code into machine code or binary code that can be directly executed by a computer's processor.

6. RTL: RTL serves as an abstraction level in the design process that represents the behavior of a digital circuit in terms of registers and the operations that transfer data between them.

7. Hardware: Hardware refers to the physical components of a computer system or any electronic device. It encompasses all the tangible parts that make up a computing or electronic device and enable it to perform various tasks.

## Detail Description of Course Content

+ Pseudo Instructions: Pseudo-instructions are used to simplify programming, improve code readability, and reduce the number of explicit instructions a programmer needs to write. They are especially useful for common programming patterns that involve multiple instructions.

+ Base Integer Instructions: The term "base integer instructions" refers to the fundamental set of instructions that form the foundation for performing basic arithmetic, logical, and data movement operations. 

+ Multiply Extension Intructions: The RISC-V architecture includes a set of multiply and multiply-accumulate (MAC) extension instructions that enhance the instruction set to perform efficient multiplication and multiplication-accumulate operations. 

+ Single and Double Precision Floating Point Extension: The RISC-V architecture includes floating-point extensions that provide support for both single-precision (32-bit) and double-precision (64-bit) floating-point arithmetic operations. These extensions are often referred to as the "F" and "D" extensions, respectively. Floating-point arithmetic is essential for handling real numbers with fractional parts and for performing accurate calculations involving decimal values.

+ Application Binary Interface: ABI stands for "Application Binary Interface." It is a set of rules and conventions that govern how software components interact with each other at the binary level. The ABI defines various aspects of program execution, including how function calls are made, how parameters are passed and returned, how memory is allocated and managed, and more.

+ Memory Allocation and Stack Pointer
- Memory allocation refers to the process of assigning and managing memory segments for various data structures, variables, and objects used by a program. It involves allocating memory space from the system's memory pool and releasing it when it is no longer needed to prevent memory leaks.
- The stack pointer is a register used by a program to keep track of the current position of the program's execution on the call stack.


## Labwork for RISCV Toolchain
We wrote a C program for calculating the sum from 1 to n using a text editor

``` c
#include<stdio.h>

int main(){
	int i, sum=0, n=26;
	for (i=1;i<=n; ++i) {
	sum +=i;
	}
	printf("Sum of numbers from 1 to %d is %d \n",n,sum);
	return 0;
}
```

Using the gcc compiler, we compiled the program to get the output.

![image](https://github.com/benedict04/pes_asic_class/assets/109859485/351a0ab8-e5ac-4177-b66c-341305b20e7f)

## RISCV GCC Compiler and Dissemble
Using the riscv gcc compiler we compiled the C program.
![image](https://github.com/benedict04/pes_asic_class/assets/109859485/a0cd1936-ad55-492c-8ca6-bc1c383d3b94)
To get the assembly code for the C program we use riscv64-unknown-elf-objdump -d sum1ton.o | less 
Here, since we used -O1 optimisation, the number of instructions are 15.
![image](https://github.com/benedict04/pes_asic_class/assets/109859485/c563c01b-7548-4a3a-87de-4ecefbe21001)

When we use -Ofast optimization , we can see that the number of instructions have been 12
![image](https://github.com/benedict04/pes_asic_class/assets/109859485/028ae227-578a-4a6c-83e6-904cd5b21b20)

## Spike Simulation and Debug
spike -d pk sum1ton.o is used debugging
![image](https://github.com/benedict04/pes_asic_class/assets/109859485/b0c62458-f3d1-4e52-8f97-5213e63e4ba1)

## Integer Number Representation
### Unsigned Numbers

- Unsigned numbers, also known as non-negative numbers, are numerical values that represent magnitudes without indicating direction or sign.
- Range: 0 to 2^(N) - 1.
### Signed Numbers
- Signed numbers are numerical values that can represent both positive and negative magnitudes, along with zero.
- Range : -(2^(N-1)) to 2^(N-1) - 1.

## Labwork
``` c
#include <stdio.h>
#include <math.h>

int main(){
	unsigned long long int max = (unsigned long long int) (pow(2,64) -1);
	unsigned long long int min = (unsigned long long int) (pow(2,64) *(-1));
	printf("lowest number represented by unsigned 64-bit integer is %llu\n",min);
	printf("highest number represented by unsigned 64-bit integer is %llu\n",max);
	return 0;
}
```
![Screenshot from 2023-08-19 08-45-25](https://github.com/benedict04/pes_asic_class/assets/109859485/8a99bfd2-da46-42c2-81dc-c454f303d66b)

### Signed 64-bit Number
``` c
#include <stdio.h>
#include <math.h>

int main(){
	long long int max = (long long int) (pow(2,63) -1);
	long long int min = (long long int) (pow(2,63) *(-1));
	printf("lowest number represented by signed 64-bit integer is %lld\n",min);
	printf("highest number represented by signed 64-bit integer is %lld\n",max);
	return 0;
}
```
![Screenshot from 2023-08-19 10-57-43](https://github.com/benedict04/pes_asic_class/assets/109859485/c3d8415c-291a-4d55-a9ae-de46829b42c4)


# Application Binary Interface
## Introduction to ABI
- An Application Binary Interface (ABI) is a set of rules and conventions that dictate how binary code interacts with and communicates with other binary code, typically at the level of machine code or compiled code. In simpler terms, it defines the interface between two software components or systems that are written in different programming languages, compiled by different compilers, or running on different hardware architectures.
- The ABI is crucial for enabling interoperability between different software components, such as different libraries, object files, or even entire programs. It allows components compiled independently and potentially on different platforms to work seamlessly together by adhering to a common set of rules for communication and data representation.

## Memmory Allocation for Double Words
64-bit number (or any multi-byte value) can be loaded into memory in little-endian or big-endian. It involves understanding the byte order and arranging the bytes accordingly

- Little-Endian: In little-endian representation, you store the least significant byte (LSB) at the lowest memory address and the most significant byte (MSB) at the highest memory address.
- Big-Endian: In big-endian representation, you store the most significant byte (MSB) at the lowest memory address and the least significant byte (LSB) at the highest memory address.

## Load, Add and Store Instructions
- Load Instructions: Load instructions are used to transfer data from memory to registers. They allow you to fetch data from a specified memory address and place it into a register for further processing.
  Example `ld x6, 8(x5)`
- Store Instructions: Store instructions are used to write data from registers into memory.They store values from registers into memory addresses
  Example `sd x8, 8(x9)`
- Add Instructions: Add instructions are used to perform addition operations on registers. They add the values of two source registers and store the result in a destination register.
  Example `add x9, x10, x11`

## Registers and their ABI Names
ABI names for registers serve as a standardized way to designate the purpose and usage of specific registers within a software ecosystem. These names play a critical role in maintaining compatibility, optimizing code generation, and facilitating communication between different software components.

![image](https://github.com/benedict04/pes_asic_class/assets/109859485/bea86dd0-1ee3-45bd-a814-dcc29eec5591)

# Labwork using ABI Function Calls

## Algorithm for C Program using ASM
- Incorporating assembly language code into a C program can be done using inline assembly or by linking separate assembly files with your C code.
- When you call an assembly function from your C code, the C calling convention is followed, including pushing arguments onto the stack or passing them in registers as required.
- The program executes the assembly function, following the assembly instructions you've provided.

![image](https://github.com/benedict04/pes_asic_class/assets/109859485/6dd201db-8994-41cd-9957-8e914a7f3c2c)

## Review ASM Function Calls
- You write your C code in one file and your assembly code in a separate file.
- In the assembly file, you declare assembly functions with appropriate signatures that match the calling conventions of your platform.

  ### c program
  ``` c
  #include <stdio.h>
  
  extern int load(int x, int y);
  
  int main()
  {
    int result = 0;
    int count = 9;
    result = load(0x0, count+1);
    printf("Sum of numbers from 1 to 9 is %d\n", result);
  }
```

### Asseembly File
**Asseembly File**
`load.s`
``` s
.section .text
.global load
.type load, @function

load:

add a4, a0, zero
add a2, a0, a1
add a3, a0, zero

loop:

add a4, a3, a4
addi a3, a3, 1
blt a3, a2, loop
add a0, a4, zero
ret
```
## Simulate C Program using Function Call
**Compilation:** To compile C code and Asseembly file use the command `riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o custom1to9.o custom1to9.c load.s` this would generate object file `custom1to9.o`.

**Execution:** To execute the object file run the command `spike pk custom1to9.o`


 







  



