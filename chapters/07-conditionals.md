# Conditionals & Decision making

Often times, you need to make a decision in your software. For example, lets say you write a file downloader. Before it starts downloading files, it first checks if there is enough space on the disk to store that file. If there is enough space, then it should download, otherwise, it should throw an error. Such decision making can be achieved using if-else statements and switch-case.

## Introduction to if statements

The basic syntax for if statements is as follows

```cpp
if (condition) {
    // do if true
}
```

Here, if the provided condition evaluates to true, then the statement below it will be executed.

Consider the following example

```cpp
int age;
std::cout << "Enter your age";
std::cin >> age;

if (age >= 18) {
    std::cout << "Adult";
}
```

This program prompts user for an integer input. if the provided input is equal to or greater than 18, then it outputs the text `Adult`.

## Else statements

In the above program, there is no output if the input number is less than 18. We also want our program to take some action if the provided condition is false.

```cpp
if (age >= 18) {
    std::cout << "Adult";
}
else {
    std::cout << "Minor";
}
```

This program will work just like the earlier one if a number equal to or greater than 18 is provided. However, if the number is less than 18, then it outputs the word `Minor`.

As you saw in the first example, `else` statement is totally optional.

## Chained if statements

Now suppose you also want to check if the person is a senior citizen. This time you need three blocks - first for condition if age is greater than or equal to 60. Next for condition if age is greater than or equal to 18. And finally a block if the person is a minor.

```cpp
if (age >= 60){
    std::cout << "Senior Citizen";
}
else if (age >= 18) {
    std::cout << "Adult";
}
else {
    std::cout << "Minor";
}
```

We use `else if` to chain if statements. Every `else if` needs a condition that it will check. Note that in the `else if` condition, I am checking if `age` is greater than or equal to 18, but I am not checking if it is less than 60. This is because if the first condition is false, then age is guaranteed to be less than 60. You can use as many `else if` statements as you want. The general syntax is

```cpp
if (condition){
    // statements
}
else if (condition){
    // statements
}
else if (condition){
    // statements
}
...
else {
    // statements
}
```

Remember, as I said before, the final `else` statement is optional.

Another thing to note is that if there is only one statement inside the if block, then you don't need to enclose it in curly braces. So, the above code can be rewritten as

```cpp
if (age >= 60)
    std::cout << "Senior Citizen";
else if (age >= 18)
    std::cout << "Adult";
else
    std::cout << "Minor";
```

Remember, if there are multiple statements inside the block, then you need to enclose them in curly braces.

## Conditional Expression

A conditional expression is one which evaluates to a boolean value, i.e. either true or false.

In the above example, we saw a conditional `age >= 18`. This will evaluate to true if `age` is greater than or equal to 18, and false otherwise. Since all conditionals should evaluate to true, you can also directly use boolean values in place of conditionals.

```cpp
bool a = true;

if (a) // a is true, so statement is executed
    std::cout << "A is true";
```

We wil understand more about this when we discuss functions.

You can also use non boolean values in place for conditionals. Non zero values are interpreted as true, and zero is interpreted as true.

```cpp
int a = 6, b = 0;

if (a)
    std::cout << "This will be printed";

if (b)
    std::cout << "This is not printed"
```

For comparision, there are some conditionals you should know about

| Operator | Meaning                                             |
| :------: | --------------------------------------------------- |
|    ==    | True for a==b if the value of a is equal to b       |
|    <     | True for a<b if a is strictly lesser than b         |
|    >     | True for a>b if a is strictly greater than b        |
|    <=    | True for a<=b if a is less than or equal to b       |
|    >=    | True for a>=b if a is greater than or equal to b    |
|    !=    | True for a!=b if a is not equal to b                |
|   \|\|   | True for a\|\|b if either of a or b equates to true |
|    &&    | True for a&&b if both of a and b equate to true     |

In all these examples, a and b can be a boolean value, or a logical statement that equated to true or false.

### Short Circuiting

Note the last two entries from the table above.

Consider the statement `a||b`. If `a` is true, then it is guaranteed that the expression evaluates to true irrespective of the value of `b`. In this case, it is not required to check the value of `b`. So, C++ skips checking the value of `b`. This behavior is called short-circuiting.

Same way, in the expression `a&&b`, if `a` false, then the expression will evaluate to false irrespective of the value of `b`. The program will skip checking the value of `b`. This is again an example of short-circuiting.

## Switch case statements

We use switch case statements to compare a variable against different values and take decision based on that. The general syntax is

```cpp
switch (variable or expression)
{
    case CASE1:
        // statements
    case CASE2:
        // statements
    ...
    default:
        // statements
}
```

Here, the provided variable or expression is compared against the cases from top to bottom. When a case matches, then the following statements are executed. If no case matches, then the statements corresponding to `default` are executed. As we saw with `else` statements, the `default` case is also optional.

Remember, with if-else statements, only the statements corresponding to the matched conditions were executed and any following else statements were left untouched. In switch case however, all the conditions following after the matched case are exectued. So if `CASE1` matches, then `CASE2` statements and `default case statement will also be executed. This can be illustrated with the following example

```cpp
int a = 2;
switch (a) {
    case 1: std::cout<<"Case 1\n";
    case 2: std::cout<<"Case 2\n";
    case 3: std::cout<<"Case 3\n";
    case 4: std::cout<<"Case 4\n";
    default: std::cout<<"Default\n";
```

The output we get is

```
Case 2
Case 3
Case 4
Default
```

The variable `a` is compared against the provided cases. `a` is not equal to 1, so first case is false. For second case, `a` is equal to 2, so its corresponding statement is executed, and all the following statements belonging to other cases are also executed. To avoid this, we add `break` statements after cases.

```cpp
int a = 2;
switch (a) {
    case 1:
        std::cout<<"Case 1\n";
        break;
    case 2:
        std::cout<<"Case 2\n";
        break;
    case 3:
        std::cout<<"Case 3\n";
        break;
    case 4:
        std::cout<<"Case 4\n";
        break;
    default: std::cout<<"Default\n";
```

Notice I have added `break` statements after each case. This will break out of the switch block after a case is matched and its corresponding statements have been executed. Also, I did not use break statement after `default`. This is because `default` is the last case, and execution will automatically break out of switch after `default`. Adding a `break` would have been redundant. This time, we will get the output we expect

```
Case 2
```

<!--
@todo Proof read chapter 07-conditionals
@body This chapter hasn't been checked yet. Need to proof read.
 -->
