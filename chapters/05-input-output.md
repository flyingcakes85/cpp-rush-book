# Input / Output

As we saw in our hello world program, C++ has inbuilt object to help us print text to the console. In this chapter we will be going to learn more about them, and also know how we can obtain input from the user.

## Introduction to streams

When your program starts, it is given access to certain **io streams**

- Standard input, or `stdin` : This is the handle from where your program can get input from.
- Standard output or `stdout` : This is the handle where your program writes its output.
- Standard error or `stderr` : This is the handle where your program can output error or diagnostic messages.

It is up to the operating system or the process starting your application to decide where these stream actually direct to. You will notice that there are two streams related to output. This is done to separate normal output from error messages. I will explain more about their significance at the end of this chapter.

## std::cout

To print some text on to the screen, you use the `std::cout` object. Note that when we provide a string to print, we enclose it inside double quotes. That instructs the compiler to interpret the text as a string rather than programming keywords.

```cpp
std::cout << "This is some text";
```

Try compiling above program after removing the double quotes.

You can output multiple times in one statement too.

```cpp
std::cout << "Hello, " << "I am " << "a C++ book ";
```

Now it doesn't make much sense to break the sentence in such a manner. You could have written the above sentence as a single string. However consider the situation when you want to output a variable as a part of a string. In that case, you would want to use such a syntax.

```cpp
int book_count = 5;
std::cout << "I have " << book_count << "books";
```

The output is

```
I have 5 books
```

You can also give an arithmetic expression to `cout`. It will be evaluated before output.

```cpp
int square_side = 5;
std::cout << "My square's perimeter is " << 4*square_side << "sq. cm.";
```

The output is

```
My square's perimeter is 20 sq. cm.
```

## std::cin

`std::cin` works pretty much like `std::cout`, but instead of output, it takes input.

```cpp
int age{0};
std::cout << "Enter your age : ";
std::cin >> age;
std::cout << "Ten years later you will be " << age + 10;
```

This program prompts for entering the age. Then it receives input and stores it in variable `age`. Finally, some text is printed to `stdout` telling the age after 10 years.

Note that the final output of this program depends upon the input it receives. Here is a sample output.

```
Enter your age : 24
Ten years later you will be 34
```

To print a new line, you have two options.

```cpp
// using std::endl
std::cout << "Hello" << std::endl << "World";

// using \n
std::cout << "Hello\nWorld";
```

Both of the above statements produce same output. Trying to print `std::endl` causes a **buffer flush** and moves the printing cursor to beginning of next line. A buffer flush means that any text that had been outputted earlier, but is not actually displayed on the console will be diplayes. This sounds funny at first. If `std::cout` prints text, why will it strore text at some other location and not actually display it?. This has got to do with performance reasons. Flushing buffer takes time, very small amount of time you won't even notice. However, when you program is ran again and again, this tiny slowdown adds up quickly.

By using `\n`, we just output it as normal text. It does not force a buffer flush. When this is finally written on to the console, `\n` is substituted with an actual new line. For this reason, using `\n` is faster.

## std::cerr

This works _exactly_ like `std::cout`, with the small difference that text is directed to `stderr` instead of `stdout`.

Here is an example program that utilizes all the streams we have discussed.

```cpp
int age{0};
std::cout << "Enter your age : ";
std::cin >> age;

if (age < 0){
    std::err << "Negative age provided";
    return -1;
}

std::cout << "Ten years later you will be " << age + 10;
return 0;
```

You will see an `if` block in this program. These will be discussed in detail in a future chapter. For now, understand that it will execute the two statements inside its curly braces, if the condition in parenthesis is true, i.e. if user inputs value of `age` less than 0, then the program will print to `stderr` and quit. Otherwise, it will print to `stdout`.

## Stream redirection

This section does not directly concern itself with C++. Nevertheless, you should know about working with streams when you are testing you applications. This will apply to Unix based or Unix like operating systems (Linux based distributions, Mac)

Say I compiled my source code with the following command

```cpp
g++ source.cpp -o myapp
```

The binary is saved with file name `myapp`.

Then I can run it with the following command and will read write my console

```sh
./myapp
```

If I want to make it read write to a file instead of the console. For that I use the following symbols in the shell

- `>` to redirect `stdout`
- `<` to redirect `stdin`
- `2>` to redirect `stderr`

So, now if I run my program with the following command

```sh
./myapp < file1 > file2 2> file3
```

it will read input from `file1`, write output to `file2` and write errors to `file3`.

Often, people do not redirect `stderr`.

```sh
./myapp < file1 > file2
```

This will let the program do its input and output from the specified files, while errors will be printed to console. This helps programmers focus on only errors. If there was no text printed in console, it means there were no errors.
