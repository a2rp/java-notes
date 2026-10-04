# 06. Classes, objects, and constructors

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Arrays and strings](./05-arrays-and-strings.md) | [Notes index](../README.md) | [Next: Encapsulation, inheritance, and composition](./07-encapsulation-inheritance-and-composition.md) |

## Define a class and create objects

A class describes the fields and methods its objects have. An object is one instance of that class, created with new.

~~~java
class Book {
    private final String title;
    private final String author;

    Book(String title, String author) {
        this.title = title;
        this.author = author;
    }

    String getTitle() {
        return title;
    }

    String summary() {
        return title + " by " + author;
    }
}

public class Main {
    public static void main(String[] args) {
        Book first = new Book("Clean Code", "Robert C. Martin");
        Book second = new Book("Effective Java", "Joshua Bloch");

        System.out.println(first.summary());
        System.out.println(second.getTitle());
    }
}
~~~

Book is the class. first and second refer to two different Book objects. Each object has its own title and author fields.

## Initialize objects with a constructor

A constructor runs when an object is created. It initializes the new object's state. Its name matches the class name and it has no return type.

this.title refers to the field on the current object. The parameter named title is the value passed by the caller.

When no constructor is declared, Java supplies a no-argument constructor. Once a class declares a constructor, that automatic constructor is not supplied.

## Separate object state from shared class state

Instance fields belong to one object. A static field belongs to the class and is shared by its instances.

Use static for behavior or data that belongs to the class as a whole. Do not make ordinary object state static merely to avoid passing an object reference.

## Create focused classes

Keep a class responsible for a clear concept. A class that holds state can expose methods that use that state, while hiding implementation details behind a small interface.

The next chapter explains access control, invariants, inheritance, and composition in more detail.

## Practice questions

1. What does a class describe?
2. What is an object?
3. Which keyword creates an object instance?
4. What does a constructor do?
5. Why does a constructor have no return type?
6. What does this.title refer to in the example?
7. What happens to the default no-argument constructor after a class declares another constructor?
8. How does a static field differ from an instance field?

## Main references

- [Classes and objects](https://dev.java/learn/language/objects/)
- [Defining classes](https://dev.java/learn/language/objects/classes/)
- [Constructors](https://dev.java/learn/language/objects/classes/constructors/)
- [Java language specification: classes](https://docs.oracle.com/javase/specs/jls/se26/html/jls-8.html)