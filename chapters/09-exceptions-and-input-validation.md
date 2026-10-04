# 09. Exceptions and input validation

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Interfaces, enums, and records](./08-interfaces-enums-and-records.md) | [Notes index](../README.md) | [Next: Generics and type safety](./10-generics-and-type-safety.md) |

## Read an exception as a failed operation

An exception reports that an operation could not continue normally. Exceptions are objects that carry information about the failure.

RuntimeException and its subclasses are unchecked. The compiler does not require a method to catch or declare them. Other exception classes are checked, so a method must catch them or declare them in its throws clause.

Errors usually indicate serious problems that an application is not expected to handle as ordinary input failures.

## Catch a specific exception

Use try and catch around an operation that can fail. Catch the expected exception type and handle it meaningfully.

~~~java
String input = "42";

try {
    int quantity = Integer.parseInt(input);
    System.out.println("Quantity: " + quantity);
} catch (NumberFormatException exception) {
    System.out.println("Enter a whole number.");
}
~~~

Avoid catching Exception when a narrower type is known. A broad catch can hide programming errors along with expected failures.

## Validate input and throw a clear exception

A method can reject invalid input with an unchecked exception such as IllegalArgumentException.

~~~java
static int requirePositive(int value) {
    if (value <= 0) {
        throw new IllegalArgumentException("Value must be positive");
    }
    return value;
}
~~~

throw creates or passes an exception object. throws in a method declaration says that the method may let a checked exception reach its caller.

## Preserve useful failure information

Use the exception type and message to explain what went wrong. Do not silently ignore errors or return an unrelated default value unless that behavior is part of the method contract.

A catch block can recover, ask for corrected input, or add context before rethrowing. Choose the behavior that lets the caller make a good decision.

## Practice questions

1. What does an exception signal?
2. What makes an exception unchecked?
3. What must code do with a checked exception?
4. What do Errors usually represent?
5. Why catch a specific exception type?
6. What does throw do?
7. What does throws declare?
8. Why should a catch block not silently discard a failure?

## Main references

- [Exceptions](https://dev.java/learn/exceptions/)
- [Exception handling](https://dev.java/learn/language/exceptions/)
- [IllegalArgumentException API](https://docs.oracle.com/en/java/javase/26/docs/api/java.base/java/lang/IllegalArgumentException.html)
- [Java language specification: exceptions](https://docs.oracle.com/javase/specs/jls/se26/html/jls-11.html)