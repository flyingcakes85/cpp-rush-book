# Loops

Loops are used when you want to repeat an instruction several number of times. There are three types of loops supported in C++ - while, for and do..while loops.

## While loop

The basic syntax of a while loop is as follows.

```cpp
while ( condition ){
	// statements
}
```

Here, `condition` can be any conditional statement that evaluates to a boolean value or an integer value. As we saw in previous chapter, in case of integer values, zero is considered false, and non zero values are considered true.

The enclosed statement are executed as long as the provided condition is true. When the condition becomes false, loop exits and the execution control passes to the line immediately following the loop.

Lets see an example.

```cpp
int a = 1;

while ( a <= 5 ){
    std::cout << "Loop running " << a << "\n";
    a = a + 1;
}
```

This is a simple example, where we first declare an integer `a` and initialize it to 1. Then we start the loop. Provided condition is `a <= 5`. This means that loop will keep executing the enclosed statements as long as `a` is less than or equal to 5. In the code block, we are first outputting some text, with value of `a`. Then we are incrementing `a` by 1. Output of above program is

```
Loop running 1
Loop running 2
Loop running 3
Loop running 4
Loop running 5
```

Suppose our condition is false from right from the beginning. In that case, the loop will not run.

```cpp
int a = 6;

// a is greater than 5, so condition is false
while ( a <= 5 ){
    std::cout << "Loop running " << a << "\n";
    a = a + 1;
}

std::cout << "Loop over";
```

This will output `Loop over` only, since the loop body is never executed.

Also, if the condition never becomes false, then the loop will run forever. This is called an infinite loop.

```cpp
int a = 1;

while ( a <= 5 ){
    std::cout << "Loop running " << a << "\n";
}
```

In this code snippet, we are not incrementing the value of `a` inside loop. So `a` is always 1 and the condition is always true. If you run this program, you will get the same line being printed indefinitely.

```
Loop running 1
Loop running 1
Loop running 1
...
```

To stop this, you can press `Ctrl + C`.

You can also write `true` or any non zero number for the condition if you want an infinite loop. As we already know, non zero numbers evaluate are considered true when used as condition. A common way to run loop a specific number of times is shown below.

```cpp
int n = 0;
std::cout << "How many times do you want to run loop? ";
std::cin >> n;

while ( n-- ){
    std::cout << "Loop running\n";
    // more statements
}
```

This asks the user for a number and then run the loop that number of times. The expression `n--` first returns the value of `n`. Then it is decreased by `1`. This way, after n times, `n` becomes zero and loop stops.

## For Loop

The general syntax of a for loop is as follows.

```cpp
for (initialization; condition; increment/decrement){
    // statements
}
```

Here, first part inside the parenthesis is initialization. This will initialize the variable that keeps account of how many times your loop has run. Next is the condition. We already know about this from the section on while loops. Finally, you have the increment or decrement.

This is quite like the while loop - just that the required pieces are all provided at one place. Remember, that to make our while loop work, we first declared an integer `a`. Then we put a condition. Finally, we incremented `a` inside the loop body, otherwise the loop will run infinitely. There are three components scattered at three different places. For loop simply brings them at one place. Keep in mind - there is no _better loop_. It depends on what you want to do.

We can rewrite the first while loop using for loop

```cpp
for ( int a = 1 ; a <= 5 ; a++ ) {
    std::cout << "Loop running " << a << "\n";
}
```

`a++` is just a shorthand for `a = a + 1`. This loop gives the same output as the first while loop we ran.

```
Loop running 1
Loop running 2
Loop running 3
Loop running 4
Loop running 5
```

There are three parts inside the parenthesis of for loop, and you may have one or more of them empty. So, if you have the initialization outside of your loop, you can skip specifying that.

```cpp
int a = 0;
std::cout << "Which number to start loop from? ";
std::cin >> a;

for ( ; a <= 5 ; a++ ) {
    std::cout << "Loop running " << a << "\n";
}
```

Here, we ask user for the number from which our loop will start. We have kept the initialization block in for loop empty. Also, notice that if the user enters a number greater than 5, then the provided condition is false right from the beginning. So the loop does not run even once in that case.

If you skip the condition, then it becomes an infinite loop. We'll see later in this chapter how you can exit from an infinite loop. Usually, an infinite for loop is denoted by having all three blocks empty.

```cpp
// infinite for loop
for ( ; ; ) {
    // statements
}
```

## Do while loop

The basic syntax of do while is as follows.

```cpp
do {
    // statements
}
while ( condition );
```

This looks like an upside down while loop with one extra keyword. `do{//statements}` specify the statements that need to be run and `while(condition)` specifies the condition.

Here's a rewrite of the our earlier program.

```cpp
int a = 1;

do {
    std::cout << "Loop running " << a << "\n";
    a = a + 1;
}
while ( a <= 5 );
```

The output, as you would expect is

```
Loop running 1
Loop running 2
Loop running 3
Loop running 4
Loop running 5
```

The interesting thing about do..while loop is that here the statement block comes before the condition block. So, the statement is guaranteed to be executed at least once. Lets take the same code, but set `a` equal to 6.

```cpp
int a = 6;

do {
    std::cout << "Loop running " << a << "\n";
    a = a + 1;
}
while ( a <= 5 );
```

When we did a similar thing with while loop, it did not run even once. However, in this case, we get an output

```
Loop running 6
```

This is because the statement was executed first. Then the condition was checked. Condition was false, so the loop did not execute statement again.

## Loop control

There are keywords that let you control the flow of a loop. Precisely speaking, you can exit the loop or skip one iteration. I have taken examples using while loop in this section, but remember that you can use these keywords in all three types of loops.

### break

We used this keyword in last chapter too. This was used to _break_ out of a switch statement. You can use this keyword in loops too.

Suppose we want to count from `a` to `b`. Both numbers will be entered by user. But we want to exit the loop if while counting we encounter a multiple of 5.

```cpp
int a = 0, b = 0;
std::cout << "Enter value of a " ;
std::cin >> a;
std::cout << "Enter value of b ";
std::cin >> b;

while (a <= b) {
    if ( a % 5 == 0 )
        break;

    std::cout << a << "\n";
    a++;
}

std::cout << "We are out of loop now";
```

`a%5` will calculate the remainder when `a` is divided by 5. If it is zero, it means `a` is a multiple of 5, and we break out of the loop in that case. Suppose I enter 7 for `a` and 16 for `b`. Then the output will be

```
Enter value of a 7
Enter value of b 16
7
8
9
We are out of loop now
```

`a` was being printed then incremented. When `a` became 10, the loop exited. If the `break` statement was not there, then the program would have counted till 16.

### continue

Suppose we have the same task, but instead of breaking at multiples of 5, we simply don't want to print them. We want to count, but only print numbers that are not multiples of 5.

```cpp
int a = 0, b = 0;
std::cout << "Enter value of a " ;
std::cin >> a;
std::cout << "Enter value of b ";
std::cin >> b;

while (a <= b) {
    if ( a % 5 == 0 ) {
        a++;
        continue;
    }

    std::cout << a << "\n";
    a++;
}

std::cout << "We are out of loop now";
```

The output is

```
Enter value of a 7
Enter value of b 16
7
8
9
11
12
13
14
16
We are out of loop now
```

Notice that 10 and 15 are not printed. In those cases, the value of `a` was incremented, and the `continue` statement moved on to next iteration without executing the statements below it.

<!--
@todo Proof read chapter 08-loops
@body This chapter hasn't been checked yet. Need to proof read.
 -->
