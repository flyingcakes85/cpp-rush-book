# Introduction

C++ first appeared in 1985 and 35 years later, it still remains relevant. In most university level CS courses, C or C++ is a part of the syllabus. Depending on your plans about your future profession, you will need to master different technologies and languages. C++ is one language that you should know irrespective of the domain you choose to work in.

For me, C++ was my first language, that I started at the age of 14. Some things made sense. Some didn't. What I can say is that is was a thrilling experience - the realization that you can make a computer work the way you want it to. I was limited to writing basic programs using i/o, conditionals and loops. There wasn't much knowledge that I gained, however, the familiarity I gained with the language helped me later on. When I started learning data structures, I found it easy to implement them. For me, transferring an idea from my head to actual code was a smooth process.

In this chapter, I will quickly go over some basic concepts that you should know about. These are not exhaustive and I recommend you do web searches to learn more about topics that you are not clear about.

## Machine code

_Machine code_ is a low level programming language that can interact directly with the CPU. Each processor family has a set of instructions that can be used to interact with it.

Machine code is in _binary_ or _hexadecimal_ and is difficult to write and debug. So programmers generally don't code using machine code. Instead, they use a high level language, which is eventually converted to machine instructions when it is run.

## High Level Languages

A _high level language_ abstracts machine code and functioning of the computer. It presents an easier way to write code. High level languages use common words to compose a program.

C++ is a high level language, since it uses common terms to compose a program. Sometimes, it will be referred to as a _middle level language_ owing to its memory management style, pointers etc. Also, there have been many languages introduced after C++, which may provide a higher level of abstraction than C++. A common example is Python, which provides significantly higher abstractions as compared to C/C++.

## Compilation process

Compilation of a C++ program can be broken down into four steps:

- Preprocessing
- Compilation
- Assembling
- Linking

Note that this count is not a standard. Many professors or instructors will list three steps by taking compilation and assembling step into one. I am going to briefly tell what these steps are.

### Preprocessing

Your C++ program will use certain header files. These header files contain pre-defined functions, objects etc for common tasks, which you can utilize to write programs. During the preprocessing phase, all the code from these header files is merged with your code, so that all the required code to compile the program is in one file.

For a loose analogy, consider your code as a recipe which only tells that you need mangoes, milk, ice cream etc for preparing mango shake. The "preprocessing phase" will actually bring the mangoes, milk and other ingredients all at one place in your kitchen.

Apart from imports, there are more such directives, which will be discussed in a future chapter.

### Compilation

Now, all the required code is in one file. It is compiled to produce assembly code. Assembly is a low level language.

### Assembling

This process converts assembly code produced in the last step to its corresponding machine code. As I told you earlier, the CPU understands machine code. However, the output from assembling step cannot yet be executed. Assembled files are stored as object files.

### Linking

This is the final step, where your object files are converted into binaries that can be executed. This is the step where most errors are reported. Linker needs to check all references and replace them with correct addresses. If it does not find the address, it throws an error.

## Interpreters

I just described the process via which C++ code is converted into a binary. This resulting binary does not look like the original C++ code. The source code was _compiled_ into a binary.

There is another way to run programs. That is by executing statements line by line. Python is a popular example of this kind of language. When an interpreter runs the code, it does not check the complete source file. Instead it starts executing line by line and halts when it detects an error in the line it has to execute.

Both styles have their pros and cons, the discussion of which is out of the scope of this book.

It should be noted that a _language_ is neither compiled or interpreted. Language is only a set of rules. Depending on the tools you use, you can compile or interpret your source code. C++ programs are usually compiled into a binary and then distributed. But it possible to _interpret_ a C++ source code. Similarly, Python provides an interpreter, but it is possible to generate a binary from python source code.

## Compiling examples from this book

All code snippets presented in this book are tested on gcc version 11.1.0. The snippets should work on reasonably older versions of gcc and also on different compilers, like mingw. In this book however, any "defaults" I talk about will be said with respect to the behavior of gcc.

To compile a source file, you run the following shell command

```sh
g++ mycode.cpp -o mycode
```

This will compile and create a binary with name `mycode`.

To execute the binary, run

```sh
./mycode
```

The `-o mycode` part specifies name of this resulting binary. Change it to something else if you want to. If you omit the flag altogether, and simply use `g++ mycode.cpp`, then the output binary will be by default named `a.out`.

While compilation, if your code has any errors, they will be printed on screen and compilation will halt. The `g++` command running without any output means compilation was successful.

Even if your code does not have any syntactical errors, it may have still have warnings. These mean that your code _may_ not behave the way you are expecting it to. To enable warnings while compiling, use the `-Wall` flag.

```sh
g++ mycode.cpp -Wall -o mycode
```

Sometimes, `-Wall` may show errors from header files, that you can ignore. `-Wall` sounds like it issues all possible warnings, but in fact this is not the case. Quoting from the g++ manpage,

> Note that some warning flags are not implied by -Wall. Some of them warn about constructions that users generally do not consider questionable, but which occasionally you might wish to check for; others warn about constructions that are necessary or hard to avoid in some cases, and there is no simple way to modify the code to suppress the warning. Some of them are enabled by -Wextra but many of them must be enabled individually.

So, for strict warnings, we also need to use the `-Wextra` flag. However, even this flag does not enable all warnings, as per the last line. You need to manually enable some flags. One such flag is the `-Wshadow` flag, which I recommend enabling.

Summing up, use the following command to compile if you want to find most common sources of bugs.

```sh
g++ source.cpp -Wall -Wextra -Wshadow -o output
```

From now on, whenever I say _running the code_ or _executing the code_, I will mean that I first compile source code then execute it.

```sh
g++ source.cpp
./a.out
```

<!--
@todo Proof read chapter 02-introduction
@body This chapter hasn't been checked yet. Need to proof read.
 -->
