# 01. JDK setup and first Java program

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Notes index](../README.md) | [Notes index](../README.md) | [Next: Variables, primitive types, and references](./02-variables-primitive-types-and-references.md) |

## Install a JDK

The Java Development Kit (JDK) provides the compiler, runtime, standard libraries, and developer tools used to build Java programs. The Java Virtual Machine (JVM) loads and executes Java bytecode.

Check that the JDK commands are available:

~~~sh
java --version
javac --version
~~~

java runs a program. javac compiles Java source code. The exact version depends on the JDK installed on the computer.

## Write a small Java program

Save this source file as Main.java. A public top-level class named Main must be in a file named Main.java.

~~~java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello, Java!");
    }
}
~~~

main is the program entry point for this traditional Java application form. System.out.println writes a line of text to the terminal.

## Compile and run the program

From the folder containing Main.java, compile the source and run the resulting class:

~~~sh
javac Main.java
java Main
~~~

javac creates a Main.class file containing bytecode. java asks the JVM to load the class and call its main method. The command uses the class name Main, not the source filename.

## Try a short expression in jshell

jshell is an interactive tool included with the JDK. It can evaluate expressions without creating a source file.

~~~text
jshell> int count = 3;
jshell> count * 2
$2 ==> 6
~~~

Use it for small experiments. Keep complete programs in source files so they can be compiled, tested, and maintained.

## Follow the compile and run cycle

Change the printed message, save the file, compile again, and run it. If a compiler error appears, read the first reported line and compare its location with the source.

Common first checks include matching braces, spelling class and method names consistently, and saving the public class in the matching filename.

## Practice questions

1. What does the JDK provide?
2. What does the JVM do?
3. Which command compiles a Java source file?
4. Which command runs a compiled Java class?
5. What file is produced by compiling Main.java?
6. Why must the public class name match the source filename?
7. What is the purpose of the main method in this example?
8. When is jshell useful?

## Main references

- [Learn Java](https://dev.java/learn/)
- [Your first Java code](https://dev.java/learn/getting-started/)
- [JDK tools](https://docs.oracle.com/en/java/javase/26/docs/specs/man/index.html)
- [The java command](https://docs.oracle.com/en/java/javase/26/docs/specs/man/java.html)
- [The javac command](https://docs.oracle.com/en/java/javase/26/docs/specs/man/javac.html)
- [The jshell command](https://docs.oracle.com/en/java/javase/26/docs/specs/man/jshell.html)