# Basic concepts

To start off with, we will write and discuss a hello world program.

## Hello world

```cpp
#include <iostream>

int main()
{
    std::cout << "Hello World";

    return 0;
}
```

Upon running this, you will see the following output

```
Hello World
```

Let us understand this code line by line.

First line, `#include <iostream>` is a preprocessor directive. `iostream` is a header file that contains various functions and objects relating to **i**nput and **o**utput. Hence the name i-o-stream. If you remember the section on [preprocessing](#preprocessing) from last chapter, you will recall that header files are expanded and injected into the source code before compilation. In other words, this is a _prerequisite_ for successful compilation of the code and hence, these are called **preprocessor directives**.

Now, you may think that how can you identify a preprocessor directive? There is a simple rule for that. All preprocessor directives must start with a pound sign (`#`).
Also, unlike normal statements, preprocessor directives are not suffixed with semicolon.

<!-- TODO link to "future chapter" -->

I will come back to preprocessor directives in a future chapter.

Next line is empty. Compiler ignores empty lines. Programmers often put empty lines to make their code more presentable and to group related statements.

Next, we have `int main()`. This marks beginning of the function called `main`. Every C++ program **must** have a `main` function. This is the entry point of your program.

Line 4 is an opening curly brace. This marks the beginning of statements that are part of `main` function. Take a look at the last line, where you have a matching closing curly brace - that marks the end of `main` function.

Line 5 is `std::cout << "Hello World";`. This is the line that actually prints the text we see in console. `std::cout` is an **object**, that lets you print data to the **standard output**. `<<` is simply an **operator** that helps `std::cout` identify the data that needs to be printed. And finally `"Hello World"` is the data we want to print. Note that `Hello World` is a string so we enclose it inside double quotes. The statement is terminated with a semi-colon. It is necessary to end every statement with a semi-colon, since C++ isn't very strict with empty lines or white spaces.

Then you have an empty line, and the statement `return 0;`. After the program runs, it needs to tell the operating system if it was successful or not. `0` means success. By returning `0`, we are telling our operating system that everything went fine.

The final closing brace marks the end of `main` function, as I told earlier.

Don't worry if you are not 100% clear with these at the moment. I will come back to these topics in separate sections in this book.

## Comments

The hello world code we saw just now was quite small. In reality however, you will find yourself writing code that spans hundreds of lines. Your code will make sense to you when you are writing it. But when you come to it few days later, you would have forgotten some details. Also, if you are collaborating on a project, then your team mates need to know what your code does, or what logic did you use to arrive at the code you wrote.

To help us in these situations, we can add **comments** to our code. Comments are text that is not read by the compiler. So, we can use comments to describe what our code does.

Single line comments start with a double forward slash (`//`), while multi line comments start with `/*` and end with `*/`. They can appear anywhere in your code.

```cpp
// this is a single line comment

/*
this is multi
line
comment
*/

```

So if we were to rewrite our hello world program with comments, we could do something like this.

```cpp
#include <iostream>
// preprocessor directive as it starts with #
// iostream has input output related stuff

int main()
// main function is necessary for every program
// It is the entry point of our app
{
    // print text to console
    std::cout << "Hello World";

    // everything went fine
    return 0;
}

```

## About code snippets

Throughout this book, you will often see code snippets without the include statements or the main function. They will give an error if you try to compile them. They are meant to be enclosed inside the following template and then compiled.

```cpp
#include <iostream>

int main
{
    // code snippet here

    return 0;
}
```

To avoid unnecessary repetition, I will omit these lines in the snippets I present.
