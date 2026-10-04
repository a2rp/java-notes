# 10. Generics and type safety

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Exceptions and input validation](./09-exceptions-and-input-validation.md) | [Notes index](../README.md) | [Next: Collections, lists, sets, and maps](./11-collections-lists-sets-and-maps.md) |

## Specify the type a container holds

Generics let a class or method work with a type chosen by its caller. A type parameter such as T is filled in when the generic type is used.

~~~java
class Box<T> {
    private final T value;

    Box(T value) {
        this.value = value;
    }

    T getValue() {
        return value;
    }
}

Box<String> title = new Box<>("Java notes");
String text = title.getValue();
~~~

The compiler checks that title stores and returns a String. A caller does not need to cast the result.

## Write a generic method

A method can declare its own type parameter.

~~~java
static <T> T first(T left, T right) {
    return left;
}

String selected = first("Java", "HTML");
Integer count = first(3, 5);
~~~

The compiler infers T from the arguments and the assignment context.

## Set an upper bound

A bound limits which types can be used for a type parameter. extends can name a class or an interface bound.

~~~java
static <T extends Number> double asDouble(T value) {
    return value.doubleValue();
}

double result = asDouble(12);
~~~

The method can call Number methods because T must be Number or one of its subclasses.

## Use wildcards for flexible parameters

A wildcard represents an unknown type. Use extends when a method needs to read values from a family of types.

~~~java
static double sum(java.util.List<? extends Number> values) {
    double total = 0;
    for (Number value : values) {
        total += value.doubleValue();
    }
    return total;
}
~~~

Use super when a method needs to accept values into a generic destination. The familiar guideline is to use extends for producers and super for consumers.

## Avoid raw types

A raw type omits its generic argument, such as List instead of List<String>. Raw types bypass much of the compiler's type checking and can cause ClassCastException later.

Use parameterized types such as List<String> or Box<Integer>. Generic type arguments must be reference types, so use wrapper types such as Integer rather than primitive int.

## Practice questions

1. What does a generic type parameter represent?
2. What does Box<String> tell the compiler?
3. Why does a generic return value often not need a cast?
4. What does a bound such as T extends Number allow?
5. What is a wildcard type?
6. When is ? extends useful?
7. When is ? super useful?
8. Why should raw types be avoided?

## Main references

- [Generics](https://dev.java/learn/generics/)
- [Generics in Java](https://dev.java/learn/language/generics/)
- [Java language specification: types and generics](https://docs.oracle.com/javase/specs/jls/se26/html/jls-4.html)
- [Type erasure](https://dev.java/learn/generics/)