# Data types

Data type specifies the type of data that a variable can store. There are different types like integer, floating point value, character, boolean, which we will discuss in this chapter.

## Fundamental data types in C++

Fundamental data types are in built in C++. All these have their own implementations and don't rely on any other data type. There are seven fundamental data types in C++.

| Datatype  | Full name                       | Size in bytes |
| --------- | ------------------------------- | :-----------: |
| `int`     | Integer                         |       4       |
| `float`   | Floating Point                  |       4       |
| `double`  | Double Precision Floating Point |       8       |
| `char`    | Single Character                |       1       |
| `wchar_t` | Wide Character                  |       2       |
| `bool`    | Boolean                         |       1       |
| `void`    | Implies lack of data            |       -       |

These fundamental data types can be used to create **derived data types**.

Note some books will not consider `wchar_t` as fundamental data type and report only 6, while some newer guides will also mention types I have not included in this list. This is because C++ evolves over time and keeps getting new features.

## Integer

This represents an integer. In your mathematics class, you must have learnt that integers represent the set of whole numbers and negative numbers. In programming languages, integer types usually have some practical limits. In C++, integer takes 4 bytes, meaning it has 32 bits for binary representation. Using signed notation, we can represent a range of -2^31^ to 2^31^-1.

We have already been using this data type in past chapters, so you may be familiar with the syntax.

```cpp
int myInt = 6; // initialization
std::cout << "Value of myInt is " << myInt;
```

Recall that there are multiple ways of initializing a variable.

## Float and Double

These are used to store numbers that have a fractional part. Float can accurately represent up to 7 decimal places, while double can accurately represent up to 15 decimal places.

Values stored by these variables cannot be represented in exact value. This has to do with how decimal fractional numbers are represented in binary. The explanation is out of the scope of this programing book, but I do recommend reading up about this on the internet.

```cpp
float radius = 43.463454;
double area = 3.141 * radius * radius;
std::cout << "Area of my farm is " << area;
```

Output is

```
Area of my farm is 5933.57
```

There isn't a strict rule as to when you should use float and when you should use double. It depends on your requirements. Say, if you are storing precise measurements for a scientific application, then you may want to use double. But if you are calculating the approximate time taken by a process, then float will suffice. The added precision of double comes with the cost of using double memory as compared to float.

An interesting behavior is when you assign a fractional value to an integer variable. The fractional part is dropped, and only the whole part is copied.

```cpp
int a = 4.6;
float b = 5.138;
int c = b;

std::cout << a << "\n" << b << "\n" << c;
```

Output is

```
4
5.138
5
```

One catch is when you use brace initialization. It is considered an error if you provide a fractional number in brace initialization of in integer.

```cpp
int a = {4.2}; // gives error
```

This behavior should not be used as a part of your code logic. There are functions that can help you _floor_ a fractional number.

## Boolean

These store either true or false. It takes up one byte of memory.

Here is an example declaration of boolean variable.

```cpp
bool isWeatherGood = true,
```

The name of this type comes from the 19^th^ century mathematician George Boole. He authored _The Laws of Thought_ (1854) which contained _Boolean Algebra_. In most programming languages, this kind of data type that can store true or false, is called `bool` or `boolean`.

## Character

A `char` can represent a single ASCII character. This takes up 1 byte of space, meaning it has 8 bits for representation. This gives us a maximum of 2^8^ = 256 unique values. At the memory level, its the integer value that is stored. When accessing this variable, it is first mapped to its corresponding ASCII value and then used. This mapping happens automatically and you don't need to do anything extra. We will understand this behavior via code snippets when I discuss type casting.

```cpp
char myChar = 'a';
std::cout << "My char is " << a;
```

Output is

```
My char is a
```

Notice that characters are enclosed in single quotes, whereas in our hello world code, we enclosed the words in double quotes. This is because `Hello World` is a string, i.e. a combination of multiple characters.

### Escape Sequences

Remember when we printed newline in last chapter? We used `\n` to add newline. You need two key presses to type this, but C++ sees this as a single character only. So, the following code will be valid

```cpp
char newline = `\n`;
std::cout << "Hello" << newline << "World";
```

`\t` and `\n` denote tab and new line respectively. These two are important to know.

Try running the following code snippet

```cpp
std::cout << "\t" << "text\n";
std::cout << "tex\tt";
std::cout << "\n";
std::cout << "more content";
```

We receive the following output:

```
        text
tex     t
more content
```

Notice that the text after tabs are aligned. Also, `\t` and `\n` themselves aren't printed. To print them, you would use double slash.

```cpp
std::cout << "Printing \\t and \\n";
```

output :

```
Printing \t and \n
```

More escape sequences you should know about are :

| Sequence | Meaning         |
| -------- | --------------- |
| `\'`     | Single quote    |
| `\"`     | Double quote    |
| `\\`     | Backslash       |
| `\a`     | Audible bell    |
| `\b`     | Backspace       |
| `\r`     | Carriage Return |
| `\f`     | Formfeed        |

Carriage return will move cursor to beginning of current line. Any characters you print after that will replace an already printed character. For example, see the output of following code snippet

```cpp
cout << "Hello World/rGreat";
```

The output is

```
Great World
```

This first prints `Hello World`. Then the cursor moves to beginning of line and `Great` is printed which replaces `Hello`.

## Larger characters

We saw that `char` can only represent ASCII values. This set of characters can only represent some symbols and Roman characters. To represent non Roman characters, or accented characters, we need to use a larger set of characters, called Unicode. `wchar_t` is _usually_ 2 bytes in size and can represent UTF-16 character.

Notice that I say "usually". This is because the size of `wchar_t` varies from compiler to compiler. Due to this reason, it is not recommended to use `wchar_t` unless you are working with the Windows API.

To represent UTF-16 characters, you can use `char16_t` instead, which is guaranteed to be large enough to represent any UTF-16 code unit. There is an even larger character set - UTF-32. For this, you need to use `char32_t`.

Using `char16_t` or `char32_t` in your code can help you use Unicode characters, which let you work with Greek, Cyrillic, Middle-Eastern and East Asian languages. This benefit comes at the cost of requiring more memory.

For the sake of simplicity, I will be working with only `char` data type and ASCII characters for the rest of this book.

## Strings

So far, we have been able to represent single characters. What if you need to store a string, like "Hello World"? For that C++ provides a data type called `string`. Note that I did not mention this in the list of fundamental data types. This is because string implementation is based on characters.

To use strings, you will need to include the header file `string`.

```cpp
#include <iostream>
#include <string> // add this line
```

Now, inside the `main` function, you can use the snippets presented in this section.

### Declaring a string

This works like other data types.

```cpp
string message;          // declaration
message = "I like C++";  // assignment
```

You can also initialize strings.

```cpp
string message = "I like C++";
```

You must have noticed, this time we are using double quotes. With `char` we used single quotes.

I will talk more about strings in a dedicated chapter.

## Datatype modifiers

In C++, you can use dataype modifiers to change the way an existing datatype works. This feature is available for char, int and double data types. The available modifiers are

- signed
- unsigned
- long
- short

All four modifiers can be applied to int. For char, signed and unsigned can be applied. And for double, only long can be applied. `signed` and `unsigned` can also be used to prefix `long` and `short`.

By default, integers are signed, meaning they can accept both negative and positive values. Using the unsigned modifier lets integer store only positive values and increases its upper limit to 2^32^-1. You can define unsigned integer with the following syntax

```cpp
unsigned int a;
```

Prefixing `long` or `short` modifies the size of integer to 8 bytes and 2 bytes respectively.

```cpp
long int a; // signed 64 bit integer
usnigned long int b; // unsigned 64 bit integer
```

## Type casting

You can convert data from one data type to another, if the destination datatype is at least as large as the source data type. For example, you can assign `float` variable an integer value. This code will be valid

```cpp
float a;
int b = 4;
a = b;
```

`bool` values can also be converted into `int`. `false` corresponds to 0, while `true` corresponds to 1.

```cpp
bool a = true;
int b = a;
std::cout << b;
std::cout << "\n";

a = false;
b = a;
std::cout << b;
```

This will output

```
1
0
```

In fact, `bool` values are cast before they are printed. The following statement prints `1` instead of printing `true`

```cpp
std::cout << true;
```

`char` as I had said, are represented as integers in memory. So you can assign character to an integer and it will store the ASCII value. The opposite will also work.

```cpp
int a =  'a';
std::cout << a;
```

Above code outputs `97`, which is the ASCII code for `a`.

```cpp
char a = 100;
std::cout << a;
```

Above code outputs `d`, which is the corresponding character for ASCII code point 100.

I will end this chapter with one concept. Since characters in memory are actually integers, you can perform simple arithmetic on them. These operation will be carried out on the integer representation, but while printing them, we will get the corresponding ASCII character to the resulting number.

```cpp
char a =  'a';
std::cout << a <<  "\n";

a = a +  1;
std::cout << a <<  "\n";

a = a +  5;
std::cout << a;
```

Output is

```
a
b
g
```

In the snippet below, I have carried out multiplication on a character.

```cpp
char a =  49;   // initialize with 49
a = a *  2;     // now a has 98
std::cout << a; // 98 corresponds to character 'b'
```

This will output the character `b`.
