# 08. Interfaces, enums, and records

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Encapsulation, inheritance, and composition](./07-encapsulation-inheritance-and-composition.md) | [Notes index](../README.md) | [Next: Exceptions and input validation](./09-exceptions-and-input-validation.md) |

## Define a contract with an interface

An interface describes behavior that implementing classes promise to provide. A class can implement multiple interfaces.

~~~java
interface Printable {
    String format();
}

class Note implements Printable {
    private final String text;

    Note(String text) {
        this.text = text;
    }

    @Override
    public String format() {
        return "Note: " + text;
    }
}
~~~

Code can depend on the Printable contract instead of requiring one concrete Note class. This makes it easier to provide another implementation later.

## Model a fixed set with an enum

Use an enum for a value that must be one of a known set of choices.

~~~java
enum Priority {
    LOW,
    NORMAL,
    HIGH
}

Priority taskPriority = Priority.HIGH;
~~~

Enum constants are instances of the enum type. They are safer than using unexplained integer or string values for a fixed set.

## Use a record for data

A record provides a concise class form for data whose components are set at construction. Records became a permanent language feature in Java 16.

~~~java
record Point(double x, double y) {}

Point origin = new Point(0, 0);
System.out.println(origin.x());
System.out.println(origin.y());
~~~

The record components produce private final fields and public accessor methods named after the components. The record also provides equals, hashCode, and toString implementations based on those components.

## Validate record components

A compact constructor can validate component values. The record assigns its components after the constructor body completes.

~~~java
record Temperature(double celsius) {
    Temperature {
        if (celsius < -273.15) {
            throw new IllegalArgumentException("Temperature is below absolute zero");
        }
    }
}
~~~

Use records for data carriers. Use a regular class when the type needs mutable identity or more complex lifecycle behavior.

## Choose a type by its job

Use an interface to express behavior, an enum for a fixed set of named choices, and a record for a compact data value. These types can work together: a record can implement an interface, and a class can use enum values as fields.

## Practice questions

1. What does an interface describe?
2. Which keyword connects a class to an interface?
3. Can a class implement multiple interfaces?
4. When is an enum a suitable choice?
5. What do record components define?
6. Which Java version made records a permanent language feature?
7. What can a compact record constructor validate?
8. When might a regular class be a better fit than a record?

## Main references

- [Interfaces](https://dev.java/learn/language/objects/interfaces/)
- [Enums](https://dev.java/learn/language/enums/)
- [Records](https://dev.java/learn/language/records/)
- [Java language specification: interfaces](https://docs.oracle.com/javase/specs/jls/se26/html/jls-9.html)
- [Java language specification: records](https://docs.oracle.com/javase/specs/jls/se26/html/jls-8.html#jls-8.10)