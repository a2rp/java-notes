# 04. Methods, parameters, and return values

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Operators, expressions, and control flow](./03-operators-expressions-and-control-flow.md) | [Notes index](../README.md) | [Next: Arrays and strings](./05-arrays-and-strings.md) |

## Declare and call a method

A method gives a named block of behavior that can accept input and return a result.

~~~java
public class MethodExamples {
    static int add(int first, int second) {
        return first + second;
    }

    static void printGreeting(String name) {
        System.out.println("Hello, " + name);
    }

    public static void main(String[] args) {
        int total = add(4, 7);
        printGreeting("Maya");
        System.out.println(total);
    }
}
~~~

static int describes a class method that returns an int. The names first and second are parameters. The values 4 and 7 are arguments passed to the method call. void means the method does not return a value.

## Return a result early

A return statement ends the current method. Returning early can keep simple validation easy to follow.

~~~java
static String displayName(String name) {
    if (name == null || name.isBlank()) {
        return "Guest";
    }

    return name.trim();
}
~~~

Every path through a non-void method must return a value compatible with its declared return type.

## Overload a method

Methods can share a name when their parameter lists differ. The compiler chooses an overload based on the argument types and count.

~~~java
static int multiply(int first, int second) {
    return first * second;
}

static double multiply(double first, double second) {
    return first * second;
}
~~~

Changing only the return type does not create a valid overload. The method call must provide enough information to identify a matching parameter list.

## Understand pass-by-value

Java always passes argument values by value. For an object argument, the copied value is a reference to the same object. The method can mutate that object, but assigning a different reference to its parameter does not replace the caller variable.

~~~java
static void appendMark(StringBuilder text) {
    text.append("!");
}

static void replaceLocalReference(StringBuilder text) {
    text = new StringBuilder("New value");
}

StringBuilder message = new StringBuilder("Hello");
appendMark(message);
replaceLocalReference(message);
System.out.println(message); // Hello!
~~~

The method changed the shared StringBuilder object in the first call. The second call only changed its local parameter.

## Accept a variable number of arguments

A varargs parameter lets a method receive zero or more values of one type. Inside the method, it behaves like an array.

~~~java
static int sum(int... values) {
    int result = 0;
    for (int value : values) {
        result += value;
    }
    return result;
}
~~~

A method can declare only one varargs parameter, and it must be the final parameter.

## Practice questions

1. What is a method parameter?
2. What is an argument?
3. What does void mean?
4. What must each path through a non-void method do?
5. How can methods be overloaded?
6. Can methods be overloaded using only different return types?
7. How does Java pass an object argument?
8. What does a varargs parameter represent inside a method?

## Main references

- [Defining methods](https://dev.java/learn/language/objects/classes/methods/)
- [Methods](https://dev.java/learn/language/)
- [Variable arity methods](https://docs.oracle.com/javase/specs/jls/se26/html/jls-8.html#jls-8.4.1)
- [Java language specification: method invocation](https://docs.oracle.com/javase/specs/jls/se26/html/jls-15.html#jls-15.12)