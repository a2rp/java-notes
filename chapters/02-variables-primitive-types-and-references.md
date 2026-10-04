# 02. Variables, primitive types, and references

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: JDK setup and first Java program](./01-jdk-setup-and-first-java-program.md) | [Notes index](../README.md) | [Next: Operators, expressions, and control flow](./03-operators-expressions-and-control-flow.md) |

## Declare a variable with a type

A variable has a name and a type. The type determines which values it can hold and which operations are valid.

~~~java
int age = 28;
double temperature = 21.5;
char initial = 'A';
boolean isReady = true;
String language = "Java";
~~~

Java is statically typed. The compiler checks that assignments and operations are compatible with their declared types.

## Use the primitive types

Java has eight primitive types: boolean, byte, short, int, long, float, double, and char. They represent boolean, integer, floating-point, and single UTF-16 code unit values.

~~~java
int itemCount = 12;
long population = 8_000_000_000L;
double price = 19.95;
float scale = 0.75f;
char grade = 'B';
boolean available = false;
~~~

Integer literals that need the long type use the L suffix. Float literals use the f suffix. For most decimal arithmetic, double is the common choice.

## Store references to objects

String is a class, not a primitive type. A variable whose type is a class holds a reference to an object.

~~~java
String firstName = "Ashish";
String greeting = "Hello, " + firstName;
Integer score = 95;
~~~

A reference can be null, meaning it refers to no object. Calling a method through a null reference causes a NullPointerException, so check whether a value may be absent before using it.

## Let the compiler infer a local type with var

Since Java 10, var can be used for a local variable when its initializer makes the type clear.

~~~java
var message = "Study Java";
var attemptCount = 3;
~~~

var does not make Java dynamically typed. The compiler infers a fixed type from the initializer. It cannot be used for fields or method parameters, and it needs an initializer.

## Convert numeric values deliberately

Widening conversions such as int to double can happen automatically. Narrowing conversions need an explicit cast and can lose information.

~~~java
int count = 5;
double exactCount = count;

double measurement = 7.8;
int wholePart = (int) measurement;
~~~

wholePart becomes 7 because the cast discards the fractional part. Use a conversion method or rounding rule when truncation is not the intended result.

## Practice questions

1. What information does a variable type provide?
2. What does statically typed mean in Java?
3. Name the eight primitive types.
4. Is String a primitive type?
5. What does a reference variable hold?
6. What does null indicate?
7. Does var make a variable dynamically typed?
8. What can be lost in a narrowing numeric conversion?

## Main references

- [Variables and naming](https://dev.java/learn/language/constructs/basics/variables/)
- [Primitive types](https://dev.java/learn/language/constructs/basics/primitive-types/)
- [The var type identifier](https://dev.java/learn/language-basics/using-var/)
- [Java language specification: types](https://docs.oracle.com/javase/specs/jls/se26/html/jls-4.html)