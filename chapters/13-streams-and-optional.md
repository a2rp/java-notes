# 13. Streams and Optional

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Lambdas and functional interfaces](./12-lambdas-and-functional-interfaces.md) | [Notes index](../README.md) | [Next: Files, I/O, and date-time APIs](./14-files-io-and-date-time-apis.md) |

## Process collection data with a stream

A stream describes a sequence of operations over data. A typical pipeline has a source, zero or more intermediate operations, and a terminal operation.

~~~java
import java.util.List;

List<String> names = List.of("Maya", "Ravi", "Marina", "Tara");

List<String> result = names.stream()
        .filter(name -> name.length() >= 5)
        .map(String::toUpperCase)
        .sorted()
        .toList();

System.out.println(result);
~~~

filter keeps matching elements. map transforms each remaining element. sorted orders the results. toList is a terminal operation that produces an unmodifiable list in Java 16 and later.

Intermediate operations are lazy. They run when a terminal operation consumes the stream. A stream should be used for one pipeline, not stored and reused after a terminal operation.

## Use common stream operations

filter selects values, map transforms them, distinct removes duplicates, and reduce combines values into one result. Choose operations that make each step easy to understand.

~~~java
import java.util.List;

int totalLength = List.of("HTML", "Java", "CSS")
        .stream()
        .mapToInt(String::length)
        .sum();

System.out.println(totalLength);
~~~

Avoid changing unrelated shared state inside a stream operation. Prefer a pipeline that returns a result rather than hiding work in side effects.

## Represent a possibly missing result with Optional

Optional represents a value that may be present or absent. Methods such as findFirst return an Optional.

~~~java
import java.util.List;
import java.util.Optional;

List<String> names = List.of("Maya", "Ravi", "Tara");

Optional<String> match = names.stream()
        .filter(name -> name.startsWith("R"))
        .findFirst();

String displayName = match
        .map(String::toUpperCase)
        .orElse("No match");

System.out.println(displayName);
~~~

map transforms a value only when present. orElse supplies a fallback when the Optional is empty. Use orElseGet when computing the fallback is expensive and should happen only when needed.

## Avoid unsafe Optional access

Avoid calling get without first checking whether a value exists. Prefer methods such as map, orElse, orElseGet that make the empty case visible.

Optional is useful as a return type for an optional result. It is usually not needed for every field or method parameter.

## Practice questions

1. What are the common parts of a stream pipeline?
2. What does filter do?
3. What does map do?
4. When do intermediate stream operations run?
5. Can a consumed stream be reused?
6. What does Optional represent?
7. What does orElse provide?
8. Why is calling Optional.get without checking risky?

## Main references

- [Streams](https://dev.java/learn/api/streams/)
- [Stream API](https://docs.oracle.com/en/java/javase/26/docs/api/java.base/java/util/stream/package-summary.html)
- [Optional API](https://docs.oracle.com/en/java/javase/26/docs/api/java.base/java/util/Optional.html)
- [Stream interface](https://docs.oracle.com/en/java/javase/26/docs/api/java.base/java/util/stream/Stream.html)