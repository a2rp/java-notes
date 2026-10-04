# 16. Packages, modules, testing, and JVM tools

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Concurrency, executors, and virtual threads](./15-concurrency-executors-and-virtual-threads.md) | [Notes index](../README.md) | [Next: All code samples](./98-all-code-samples.md) |

## Organize classes with packages

A package groups related Java types and helps avoid class name conflicts. A package declaration appears before imports and the class declaration.

~~~java
package com.example.notes;

public class Main {
    public static void main(String[] args) {
        System.out.println("Package ready");
    }
}
~~~

The source file belongs at a path that matches its package, such as src/com/example/notes/Main.java. Use lowercase package names by convention.

## Compile and run packaged source

javac can write compiled classes into a chosen output directory. java then uses that directory as the class path and the fully qualified class name.

~~~sh
javac -d out src/com/example/notes/Main.java
java -cp out com.example.notes.Main
~~~

Classpath tells the runtime where to find classes and libraries. Keep source and compiled output in separate directories.

## Add a module descriptor when needed

A module groups packages and declares dependencies and which packages it exposes. The descriptor is named module-info.java.

~~~java
module com.example.notes {
    exports com.example.notes.api;
}
~~~

Modules add explicit boundaries to a larger application. A small learning program does not need a module descriptor unless the project is practicing the module system.

## Test behavior with a small check

A test should verify observable behavior, not only that code compiles.

~~~java
static int add(int first, int second) {
    return first + second;
}

static void testAdd() {
    if (add(2, 3) != 5) {
        throw new AssertionError("Expected 5");
    }
}
~~~

In a real project, use a test framework to organize test cases and report failures. Keep tests repeatable and focused on one behavior.

## Build an executable JAR

The jar tool can package compiled classes into an archive and name the main class.

~~~sh
jar --create --file app.jar --main-class com.example.notes.Main -C out .
java -jar app.jar
~~~

A JAR is a ZIP-based archive containing classes and resources. Its manifest can identify the application's entry point.

## Use JDK tools to inspect a program

Useful tools include java to run a program, javac to compile, jshell for small experiments, jar to package, javadoc to generate API documentation, and javap to inspect compiled class files.

Run --help or consult the tool reference when an option is unfamiliar. Keep compiler warnings enabled and fix warnings that point to unsafe or unclear code.

## Practice questions

1. What does a package group?
2. Where should a package declaration appear?
3. How does the source path relate to a package name?
4. What does the -d option do for javac?
5. What does the classpath tell the Java runtime?
6. What does a module descriptor declare?
7. What should a behavior test verify?
8. Which JDK tool packages compiled classes into a JAR?

## Main references

- [Packages](https://dev.java/learn/classes-objects/packages/)
- [Java Platform Module System](https://dev.java/learn/modules/)
- [The javac command](https://docs.oracle.com/en/java/javase/26/docs/specs/man/javac.html)
- [The jar command](https://docs.oracle.com/en/java/javase/26/docs/specs/man/jar.html)
- [JDK tools](https://docs.oracle.com/en/java/javase/26/docs/specs/man/index.html)