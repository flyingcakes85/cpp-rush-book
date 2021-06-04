# Variables

Variables are named containers for storing data in memory while your program is running.

## Declaring variables

Variables are declared using the general syntax below

```
datatype variable_name;
```

For now, keep in mind that `int` is a data type in C++, used to store 32 bit integers. I will explain data types in detail in the section on data types.

To **declare** an integer variable and name it `radius`, you will write the following

```cpp
int radius;
```

You can also declare multiple variables in one statement if they belong to the same type.

```cpp
int radius, perimeter;
```

## Assigning Values

You can assign values to `radius` by using **assignment operator** which is the equal sign (`=`).

```cpp
int radius;
radius = 2;
```

Keep in mind, the variable needs to be declared before assigning any value.

## Initialization

You can also **initialize** the value of a variable right when you declare it. There are three ways to do this.

```cpp
int p = 10; // Copy initialization

int q(22); // Direct initialization

int r{34}; // List initialization
```

### Copy initialization

This works quite like C language. An initial value is provided after the equals sign. This will copy the initial value into the variable right at creation.

```cpp
int p = 10;
```

Copy initialization in efficient for simple data types, but can get inefficient when dealing with more complex types.

### Direct initialization

An initial value is provided inside parenthesis. The variable is created and then this provided value is stored it its memory location. In practice, copy initialization and direct initialization are the same for simple data types. However, when dealing with complex types, direct initialization is more efficient than copy initialization.

```cpp
int q(22);
```

### List initialization

The initial value is provided inside curly braces. This acts like a uniform way to initialize values, since the above two mentioned methods cannot initialize a list of objects.

```cpp
int r{34};
```

There are several ways of list initialization too.

```cpp
int a{5}; // direct initialization

int b = {4}; // copy list initialization

int c{}; // value initialazation
```

### Value initialization

The last method of initialization you saw was value initialization.

```cpp
int c{};
```

This lets the compiler initialize variable with an appropriate value depending on the data type. For most compilers, `int` should be initialized to `0` in debug builds.

### Initializing multiple variable in single statement

You can initialize multiple variables in one statement my separating them with comma.

```cpp
int p = 10, q = 22, r = 34;
int a(4), b(3);
int y{6}, z{8};
```

Also, you need not initialize every value in the statement.

```cpp
int a, b, c = 4;
```

Here, `c` is initialized to 4. `a` and `b` are uninitialized.

### Why should you initialize?

It is a good idea to initialize your variables. Using an uninitialized value in your logic can give different results on every run. Then you will spend time finding the error. All this can be easily avoided if you initialize your variables. Uninitialized variables can also lead to memory leaks.

While it is not a _rule_ that variables must be initialized, it is a good practice to do so.

## Keywords and Variable Naming

In C++, there are some reserved keywords, which you can not use to name your variables. You can see the list of reserved keywords on [cppreference](https://en.cppreference.com/w/cpp/keyword). For example, if you name a variable as `int`, it will be confusing for the compiler to understand that, since it knows `int` is a datatype.

The name of a function, type, object or any other item you create is called _identifier_ and must follow the following rules:

- Must begin with an alphabet or underscore (\_), but not numbers
- Can contain numbers, but not at the first position
- No special characters or symbols expect underscore are allowed
- Names must be between 1 to 255 characters long (both inclusive)
- They case sensitive
- Cannot contain spaces
- Must not collide with a C++ keyword

<!--
@todo Proof read chapter 04-variables
@body This chapter hasn't been checked yet. Need to proof read.
 -->
