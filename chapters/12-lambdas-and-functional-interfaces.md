# 12. Lambdas and functional interfaces

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Collections, lists, sets, and maps](./11-collections-lists-sets-and-maps.md) | [Notes index](../README.md) | [Next: Streams and Optional](./13-streams-and-optional.md) |

## Represent behavior with a functional interface

A functional interface has one abstract method. It can be implemented with a lambda expression.

~~~java
@FunctionalInterface
interface TextCheck {
    boolean accepts(String text);
}

TextCheck hasContent = text -> !text.isBlank();

System.out.println(hasContent.accepts("Java"));
~~~

The lambda provides the behavior for accepts. The compiler checks the expression against the functional interface method signature.

## Use standard functional interfaces

The java.util.function package provides common interfaces.

~~~java
import java.util.function.Consumer;
import java.util.function.Function;
import java.util.function.Predicate;
import java.util.function.Supplier;

Predicate<String> isLong = text -> text.length() > 8;
Function<String, Integer> length = text -> text.length();
Consumer<String> print = text -> System.out.println(text);
Supplier<String> message = () -> "Ready";

System.out.println(isLong.test("Study Java"));
System.out.println(length.apply("Java"));
print.accept(message.get());
~~~

Predicate tests a value, Function transforms a value, Consumer accepts a value without returning a result, and Supplier provides a value without taking an argument.

## Simplify a lambda with a method reference

A method reference can name an existing method when its signature matches the functional interface.

~~~java
import java.util.List;

List<String> names = List.of("Maya", "Ravi", "Tara");
names.forEach(System.out::println);
~~~

System.out::println is a shorter form of passing a value to that method from a lambda such as name -> System.out.println(name).

## Use lambdas with collection operations

A lambda can describe a condition or action passed to a collection method.

~~~java
import java.util.ArrayList;
import java.util.List;

List<String> names = new ArrayList<>(List.of("Maya", "", "Ravi"));
names.removeIf(name -> name.isBlank());

System.out.println(names);
~~~

Use a method reference or lambda when it makes the behavior easier to read. A longer lambda can be moved into a named method.

## Practice questions

1. How many abstract methods does a functional interface have?
2. What does a lambda provide?
3. What does Predicate represent?
4. What does Function represent?
5. What does Consumer represent?
6. What does Supplier represent?
7. When can a method reference replace a lambda?
8. When should a long lambda be moved into a named method?

## Main references

- [Lambda expressions](https://dev.java/learn/lambdas/)
- [Functional interfaces](https://dev.java/learn/language/lambdas/)
- [java.util.function API](https://docs.oracle.com/en/java/javase/26/docs/api/java.base/java/util/function/package-summary.html)
- [The FunctionalInterface annotation](https://docs.oracle.com/en/java/javase/26/docs/api/java.base/java/lang/FunctionalInterface.html)