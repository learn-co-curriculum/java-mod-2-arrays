# Arrays

## Learning Goals

- Understand what an array is
- Work with Java arrays

## Introduction

A variable is a container for a single value. As we have seen, that value can be
a simple type, such as an `Integer` or a `String`, or it can be a complex type
that itself contains a set of variables. These can be nested and have complex
structures that we will explain in the following sections.

There is a specific type of "variable combination" that is both very common and
very useful in programming called an "array".

## Working with Arrays

An "array" is a way to hold multiple variables, usually of the same type,
together in a list. You can think of arrays anytime you think of "multiples". A
classroom, for example, might have a single teacher, but it would have multiple
students. A vehicle might have a single engine, but it would have multiple
wheels.

The syntax to declare an array is to start with the type of objects the array
will contain and follow the type declaration with `[]` to indicate that instead
of the variable holding a single value, it will hold multiple values:

`String[] names` declares an array of `String` objects called `names`.

An array can be initialized as follows:

`String[] names = {"James", "Jamaal", "Jennifer", "Jules"};`

Once the array is initialized, each value in the array can be referenced by its
position in the array (called its `index`):

`System.out.println(names[0]);` will print the name `James` to the console while
`System.out.println(names[1]);` will print the name `Jamaal` to the console.

You can see a familiar pattern where the index of the value we want to print
increases by one every time we want to move on to the next item on the list.
This is a perfect use case for a `for` loop. Let's put one together to go
through and print every name in our array:

```java
String[] names = {"James", "Jamaal", "Jennifer", "Jules"};
for (int nameIndex = 0; nameIndex < 4; nameIndex++) {
    System.out.println("Current name = " + names[nameIndex]);
}
```

This will produce the following output:

```plainttext
Current name = James
Current name = Jamaal
Current name = Jennifer
Current name = Jules
```

This does the job, but we can improve the loop by basing the condition on the
length of the array instead of harcoding it to `4`, so that the code will still
work if the array has a different number of elements in it:

```java
String[] names = {"Jamaal", "Jennifer", "Jules"};
for (int nameIndex = 0; nameIndex < names.length; nameIndex++) {
    System.out.println("Current name = " + names[nameIndex]);
}
```

The condition is now based on `names.length`, which returns the number of
elements in the `names` array. The example code above also removed the first
element of the array ("James") to demonstrate that the new code now works even
though the array has one less element than it did before.

Here is the output from this code:

```plaintext
Current name = Jamaal
Current name = Jennifer
Current name = Jules
```

Another way to go through each element in the array is to use a special version
of the `for` loop that knows how to iterate through a list:

```java
String[] names = {"Jamaal", "Jennifer", "Jules"};
for (String name: names) {
    System.out.println("Current name = " + name);
}
```

This code produces the same output as the previous version. Java knows that
`names` is a list, and this syntax indicates that we want to go through each
item in the list, assign it temporarily, for the duration of one iteration
through the loop, to the `name` variable, which can then be used in the loop for
whatever logic you need.

The code above is equivalent to the following code:

```java
String[] names = {"Jamaal", "Jennifer", "Jules"};
for (int nameIndex = 0; nameIndex < names.length; nameIndex++) {
    String name = names[nameIndex];
    System.out.println("Current name = " + name);
}
```

We have been initializing our sample array with actual values, but an array can
also be defined by specifying its size:

```java
String[] anotherList = new String[10];
anotherList[7] = "Hemali";
```

Once the array is initialized, any of its elements can be referenced by their
index. Note that array indexes are 0-based, which means that the first element
of an array is referenced by the index value of `0`:

```java
anotherList[0] = "Anthony"; // initializes the first item in the array
```

Arrays in Java have two majors constraints:

1. Their size is fixed - once an array has been defined to be a certain size,
   its size cannot be changed
2. All objects in an array have to be the same type

Later in this section, we will go through data structures that address some of
these limitations.
