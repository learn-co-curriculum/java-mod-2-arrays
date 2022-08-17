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

An **array** is a way to hold multiple variables of the same type. We can think
of arrays anytime we think of "multiples". A classroom, for example, might have
a single teacher, but it would have multiple students. A vehicle might have a
single engine, but it would have multiple wheels. In Java, arrays are
considered to be an object and therefore, considered a reference type similar
to a `String` or an instance of a class. Each variable within the array is
referred to as **elements** and these elements can either be primitive types or
reference types. This means that an array could hold the data types `int`,
`double`, `String`, or even instances of our `Student` class!

To declare an array, we can use the following syntax:

`variableType[] arrayName`

We first state the type of variable the array will hold and follow it with `[]`
to indicate that instead of the variable holding a single value, it will hold
multiple values. We then give the array a name, like we would with any other
variable.

`String[] names` declares an array of `String` types called `names`.

An array can be initialized as follows:

`String[] names = {"Leslie", "Ann", "Ron", "Ben"};`

Once the array is initialized, each value in the array can be referenced by its
position in the array (called its **index**). In programming languages, when we
count indices, we start with 0 instead of 1. This is because we consider the
question: "How many positions would we need to move in order to get to that
value?" If the value we want is the first within the list, we say we move 0
positions. So if we want to find out the first value in the array, `names`, we
can do so by writing `names[0]`. We specify the index within the square brackets
of the position in the array we want to access: `array[index]`. In this case,
`names[0]` would evaluate to the `String` value Leslie.

`System.out.println(names[0]);` will print the name Leslie to the console while
`System.out.println(names[1]);` will print the name Ann to the console.

We can see a familiar pattern where the index of the value we want to print
increases by one every time we want to move on to the next item on the list.
This is a perfect use case for a `for` loop. Let's put one together to go
through and print every name in our array:

```java
String[] names = {"Leslie", "Ann", "Ron", "Ben"};
for (int nameIndex = 0; nameIndex < 4; nameIndex++) {
    System.out.println("Current name = " + names[nameIndex]);
}
```

This will produce the following output:

```plainttext
Current name = Leslie
Current name = Ann
Current name = Ron
Current name = Ben
```

This does the job, but we can improve the loop by basing the condition on the
length of the array instead of hardcoding it to 4. We can find the length of the
array by calling its public `length` property using dot-notation! The `length`
property holds the number of elements in the array. By making use of this
property, the code will still work if the array has a different number of
elements in it:

```java
String[] names = {"Leslie", "Ann", "Ron"};
for (int nameIndex = 0; nameIndex < names.length; nameIndex++) {
    System.out.println("Current name = " + names[nameIndex]);
}
```

The condition is now based on `names.length`, which returns the number of
elements in the `names` array. The example code above also removed the last
element of the array ("Ben") to demonstrate that the new code now works even
though the array has one less element than it did before.

Here is the output from this code:

```plaintext
Current name = Leslie
Current name = Ann
Current name = Ron
```

Another way to go through each element in the array is to use a special version
of the `for` loop that knows how to iterate through a list:

```java
String[] names = {"Leslie", "Ann", "Ron"};
for (String name: names) {
    System.out.println("Current name = " + name);
}
```

This code produces the same output as the previous version. Java knows that
`names` is a list, and this syntax indicates that we want to go through each
item in the array and assign it temporarily to the `name` variable, which can then
be used in the loop for whatever logic we need. The code above is equivalent to
the following code:

```java
String[] names = {"Leslie", "Ann", "Ron"};
for (int nameIndex = 0; nameIndex < names.length; nameIndex++) {
    String name = names[nameIndex];
    System.out.println("Current name = " + name);
}
```

We have been initializing our sample array with actual values, but an array can
also be defined by specifying its size:

```java
String[] anotherList = new String[10];
anotherList[7] = "Tom";
```

Once the array is initialized, any of its elements can be referenced by their
index.

```java
anotherList[0] = "April"; // initializes the first item in the array
```

Arrays in Java have two majors constraints:

1. Their size is fixed - once an array has been defined to be a certain size,
   its size cannot be changed
2. All objects in an array have to be the same type
