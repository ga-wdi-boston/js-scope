# A Little Computer Science Background

A software program passes through a couple of phases as it's being developed and used.

## We Do

#### Program Creation/Development.
A developer writes code in a file using an editor. Perhaps in a source file named `hello_world.c`

```
$ touch hello_world.c
$ subl hello_world.c
```

Write some code in this file.

```c
/* Hello World program */
#include<stdio.h>
main(){
    printf("Hello World");
}
```

#### Program Compilation, this is compile time.
A developer *compiles* the code. This is the process of turning the text, i.e. source code, in the above file into a form, ones and zeros, that can executed by the computer. The resulting ones and zeros is often referred to as a *binary* or *executable*.

Perhaps the name of the *executable* is `hello_world`. **Notice the executable is missing the file extension .c**

Here we compile hello_world.c and produce an executable named hello_world: 

```
$ gcc -o hello_world hello_world.c
```

#### Program Execution, i.e. Runtime.
A User will install the *executable*, `hello_world`, on their computer and run it.

```
$ hello_world
Hello World!
$
```

**Notice the distinction between Compile time and Runtime.** *We'll come back to how these two are different*

## I Do

Draw diagram/s to represent the above process.

## Compiled Languages
This is the process used for programming languages that are explicitly compiled. Compiled languages such as C, C++, Go, Swift, etc follow this process.

The source code is translated from text, i.e. source code, to ones and zeros, i.e. executables, that are understood and run by the computer's CPU. 

The Central Proccessing Unit(CPU) is an actual piece of hardware, a chip, that knows what to do with all these 1's and 0's in the executable.

## You Do
* Look at the executable file, it's a bunch of 1's and 0's that are represented using Hexidecimal/Hex. What's Hex?

* Draw a diagram of the above process and show it to another student and the instructor.

* Create a C program that will output your name.

## We Do

Show and discuss some diagrams created by students.

## Virtual Machines (VM)

There is the concept of running programs, executables, not directly on the computer's CPU, but running executables on a software representation of a CPU. This software representation of a CPU is a Virtual Machine (VM).

The VM is actually a program that when run acts like the computer's CPU.

An example of running a VM is starting nodejs and pass nodejs a javascript file, `$ node foo.js`

## I Do 
Draw diagram/s to represent how a VM works.

## Interpreted Languages

When creating a program for an interpreted language we skip the explicit compilation phase. Another words, the developer doesn't run a command to compile the source code into an executable. Like we did above.

Instead the developer will:

#### Program Creation
A developer writes code in a file using an editor. Perhaps in a source file named `hello_world.js`

```
$ touch hello_world.js
$ subl hello_world.js
```

Write some code.

```javascript
// Hello World program 
console.log('Hello World!');
```

#### Program Execution, i.e. Runtime.
A User will run install the source code `hello_world.js`, on their computer and run it.

```
$ node hello_world.js
Hello World!
$
```

Running the program above will:
* Start up the node program
* Which will load the hello_world.js file in.
* Pass the source code on to node's Javascript VM. 
* The Javascript VM will automatically compile the source code to "byte code".
* The Javascript VM will run the program's byte code. 

Just like the CPU knows what to do with the 1's and 0's in the executable. The VM knows what to do with the "byte code".

## You Do
Create a Javascript program that will output your name. *Should be a piece of cake, aye*

Enumerate each step, in your own words, that happens when one runs `node foo.js` to another student.

Listen to another students explaination of these steps and write them out, on a whiteboard, piece of paper, ...


## We Do
Show and discuss a student's explaination.

## Compiled vs Interpreted Languages
Here we used Javascript as the interpreted language, but there are many more interpreted languages. Java, Ruby, Python, Smalltalk, Lisp are all interpreted languages. Lisp is the granddad of interpreted languages.

There are many reasons why one would choose a compiled or interpreted langauge. For example, compiled languages run much faster and the compilation phase can help a developer determine if they are using the correct data types.

Intepreted languages are typically easier to develop with and easily run on a number of different platforms, such as Windows and Linux. These languages are typically more expressive, they are better at representing concepts in code.

There are lots of flame wars about these and other pros and cons of compiled vs interpreted langauges. IMO, use the right tool for the job. 

## Your Turn (Optional) 
Research the differences, pros and cons, of compiled and interpreted languages.

