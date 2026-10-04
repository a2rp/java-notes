# 99. Complete questions and answers

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: All code samples](./98-all-code-samples.md) | [Notes index](../README.md) | End of notes |

## Source chapter: [1. JDK setup and first Java program](./01-jdk-setup-and-first-java-program.md)

1. What does the JDK provide?
   **Answer:** The JDK includes tools for developing Java programs, including the compiler, runtime, and standard libraries.
2. What does the JVM do?
   **Answer:** The JVM loads and executes compiled Java bytecode, translating it for the current platform.
3. Which command compiles a Java source file?
   **Answer:** Run `javac Main.java` from the directory containing the source file.
4. Which command runs a compiled Java class?
   **Answer:** After compilation, run the class with `java Main`.
5. What file is produced by compiling Main.java?
   **Answer:** Compiling `Main.java` normally produces `Main.class`, which contains bytecode.
6. Why must the public class name match the source filename?
   **Answer:** The Java source file name must match its public top-level class name so the compiler can locate and compile that public class consistently.
7. What is the purpose of the main method in this example?
   **Answer:** `main` is the program entry point that the Java launcher calls. Its `String[] args` parameter receives command-line arguments.
8. When is jshell useful?
   **Answer:** `jshell` is useful for trying short expressions and statements interactively without creating a full source file.

## Source chapter: [2. Variables, primitive types, and references](./02-variables-primitive-types-and-references.md)

1. What information does a variable type provide?
   **Answer:** A variable's type determines which values it can hold and which operations are valid for it.
2. What does statically typed mean in Java?
   **Answer:** Java checks variable types at compile time. A value of an incompatible type is rejected before the program runs unless it is explicitly converted.
3. Name the eight primitive types.
   **Answer:** The eight primitive types are `byte`, `short`, `int`, `long`, `float`, `double`, `char`, and `boolean`.
4. Is String a primitive type?
   **Answer:** No. `String` is a reference type from the Java standard library, although it is used frequently like a basic value.
5. What does a reference variable hold?
   **Answer:** A reference variable holds a reference to an object, or `null`; it does not contain the object's fields directly.
6. What does null indicate?
   **Answer:** `null` means a reference currently points to no object.
7. Does var make a variable dynamically typed?
   **Answer:** No. `var` asks the compiler to infer a local variable's type from its initializer. The inferred type remains fixed.
8. What can be lost in a narrowing numeric conversion?
   **Answer:** A narrowing conversion can discard high-order bits or fractional precision, so the resulting value may differ from the original.

## Source chapter: [3. Operators, expressions, and control flow](./03-operators-expressions-and-control-flow.md)

1. What does integer division do with a remainder?
   **Answer:** Integer division discards the fractional part and keeps the quotient toward zero. For example, `7 / 2` evaluates to `3`.
2. How can a cast make division produce a decimal result?
   **Answer:** Convert one operand to a floating-point type, such as `(double) 7 / 2`, so the operation produces `3.5`.
3. What type of value do comparison operators produce?
   **Answer:** Comparison operators produce a `boolean` value: either `true` or `false`.
4. What does short-circuit evaluation mean?
   **Answer:** Short-circuit evaluation stops evaluating a logical expression once its result is known. With `&&`, a false left side skips the right side.
5. When is an if and else statement useful?
   **Answer:** Use `if` and `else` to choose between two paths based on a condition.
6. Which Java version introduced switch expressions as a permanent feature?
   **Answer:** Switch expressions became a permanent feature in Java 14.
7. When is a for loop a useful choice?
   **Answer:** A `for` loop is useful when repeating work a known number of times or iterating over a sequence with a clear step.
8. What is the difference between break and continue?
   **Answer:** `break` exits the nearest loop or switch. `continue` skips the rest of the current loop iteration and starts the next one.

## Source chapter: [4. Methods, parameters, and return values](./04-methods-parameters-and-return-values.md)

1. What is a method parameter?
   **Answer:** A parameter is a named variable in a method declaration that receives a value when the method is called.
2. What is an argument?
   **Answer:** An argument is the value or expression supplied for a parameter at a method call.
3. What does void mean?
   **Answer:** `void` means the method does not return a value to its caller.
4. What must each path through a non-void method do?
   **Answer:** Every possible path through a non-void method must return a value compatible with the declared return type, or end by throwing an exception.
5. How can methods be overloaded?
   **Answer:** Methods can be overloaded by declaring the same name with different parameter lists, such as different parameter types, counts, or order.
6. Can methods be overloaded using only different return types?
   **Answer:** No. A different return type alone does not make a distinct method signature, so it cannot be used for overloading.
7. How does Java pass an object argument?
   **Answer:** Java passes the value of the reference. The method can use that copied reference to change the object's state, but reassigning the parameter does not change the caller's variable.
8. What does a varargs parameter represent inside a method?
   **Answer:** Inside the method, a varargs parameter is available as an array of the declared element type.

## Source chapter: [5. Arrays and strings](./05-arrays-and-strings.md)

1. What kind of sequence does an array hold?
   **Answer:** An array holds a fixed-length sequence of values of one declared component type. The values may be primitives or object references.
2. Which index identifies the first array element?
   **Answer:** Index `0` identifies the first array element.
3. Is length a field or a method on an array?
   **Answer:** `length` is a field on an array, not a method.
4. What exception can an invalid array index cause?
   **Answer:** An invalid array index causes `ArrayIndexOutOfBoundsException`.
5. When is an enhanced for loop convenient?
   **Answer:** An enhanced `for` loop is convenient when visiting each element in order and the index is not needed.
6. Are String objects mutable?
   **Answer:** No. `String` objects are immutable. Operations that appear to change a string return a new string value.
7. What does == check for references?
   **Answer:** For reference values, `==` checks whether both references point to the same object, not whether their contents are equal.
8. When can StringBuilder be useful?
   **Answer:** `StringBuilder` is useful when building a string through many appends, because it avoids creating a new intermediate string for every concatenation.

## Source chapter: [6. Classes, objects, and constructors](./06-classes-objects-and-constructors.md)

1. What does a class describe?
   **Answer:** A class describes a type of object by declaring its state and behavior.
2. What is an object?
   **Answer:** An object is a runtime instance of a class with its own identity and state.
3. Which keyword creates an object instance?
   **Answer:** The `new` keyword creates an object instance and invokes a constructor.
4. What does a constructor do?
   **Answer:** A constructor initializes a new object, usually by setting its fields to valid starting values.
5. Why does a constructor have no return type?
   **Answer:** A constructor has no return type because it is a special initialization operation, not a regular method.
6. What does this.title refer to in the example?
   **Answer:** `this.title` refers to the `title` field of the current object. It distinguishes the field from a parameter also named `title`.
7. What happens to the default no-argument constructor after a class declares another constructor?
   **Answer:** Once a class declares any constructor, Java no longer supplies the implicit default no-argument constructor. Add one explicitly if callers need it.
8. How does a static field differ from an instance field?
   **Answer:** A static field belongs to the class and is shared by its instances. Each instance field belongs to an individual object.

## Source chapter: [7. Encapsulation, inheritance, and composition](./07-encapsulation-inheritance-and-composition.md)

1. What does encapsulation protect?
   **Answer:** Encapsulation protects an object's state by controlling how callers can read or change it, which helps keep its rules valid.
2. What is an invariant?
   **Answer:** An invariant is a condition that must remain true for an object or operation to be valid, such as a bank balance never going below zero.
3. Which keyword declares a subclass?
   **Answer:** The `extends` keyword declares a subclass of a class.
4. What does super(name) do?
   **Answer:** `super(name)` calls the superclass constructor and passes it the `name` value so the superclass can initialize its part of the object.
5. What does @Override ask the compiler to check?
   **Answer:** `@Override` asks the compiler to verify that the method correctly overrides an inherited method.
6. When does inheritance represent a useful relationship?
   **Answer:** Inheritance is useful when a subtype truly can be used wherever its parent type is expected and the shared behavior is stable.
7. What does composition represent in the Car example?
   **Answer:** Composition means an object contains or uses other objects to perform work. In the car example, a `Car` has an `Engine`.
8. Why can a deep inheritance tree be difficult to change?
   **Answer:** A deep inheritance tree spreads behavior across many classes, so a small change can have unexpected effects in distant subclasses.

## Source chapter: [8. Interfaces, enums, and records](./08-interfaces-enums-and-records.md)

1. What does an interface describe?
   **Answer:** An interface describes a set of operations that implementing classes promise to provide.
2. Which keyword connects a class to an interface?
   **Answer:** The `implements` keyword connects a class to an interface.
3. Can a class implement multiple interfaces?
   **Answer:** Yes. A Java class can implement more than one interface by listing them after `implements`.
4. When is an enum a suitable choice?
   **Answer:** Use an enum when a value must be one of a fixed set of named choices, such as a status or direction.
5. What do record components define?
   **Answer:** Record components define the record's state, constructor parameters, accessor methods, and generated equality-related behavior.
6. Which Java version made records a permanent language feature?
   **Answer:** Records became a permanent language feature in Java 16.
7. What can a compact record constructor validate?
   **Answer:** A compact record constructor can validate or normalize component values before they are assigned to the record's fields.
8. When might a regular class be a better fit than a record?
   **Answer:** A regular class is a better fit when the type needs mutable state, complex construction, identity-based behavior, or control over accessors and equality.

## Source chapter: [9. Exceptions and input validation](./09-exceptions-and-input-validation.md)

1. What does an exception signal?
   **Answer:** An exception signals that an operation could not complete normally and provides information about the failure.
2. What makes an exception unchecked?
   **Answer:** An unchecked exception is a `RuntimeException` or one of its subclasses. The compiler does not require callers to catch or declare it.
3. What must code do with a checked exception?
   **Answer:** Code must catch a checked exception or declare it with `throws`, allowing a caller to handle it.
4. What do Errors usually represent?
   **Answer:** Errors usually represent serious problems from which an application is not expected to recover, such as a JVM resource failure.
5. Why catch a specific exception type?
   **Answer:** Catching a specific exception lets the program handle a known failure accurately and avoids hiding unrelated programming errors.
6. What does throw do?
   **Answer:** `throw` creates or provides an exception and transfers control to exception handling.
7. What does throws declare?
   **Answer:** `throws` declares in a method signature that the method may pass the listed checked exceptions to its caller.
8. Why should a catch block not silently discard a failure?
   **Answer:** A silent catch hides the failure and leaves callers unable to tell that the operation did not succeed. Handle it, report it, or propagate it.

## Source chapter: [10. Generics and type safety](./10-generics-and-type-safety.md)

1. What does a generic type parameter represent?
   **Answer:** A generic type parameter is a placeholder for a type that will be supplied when using or declaring a generic class, interface, or method.
2. What does Box<String> tell the compiler?
   **Answer:** `Box<String>` tells the compiler that this box stores `String` values, so incompatible values are rejected at compile time.
3. Why does a generic return value often not need a cast?
   **Answer:** Because the compiler knows the declared generic type, it can check values and provide the correct return type at compile time.
4. What does a bound such as T extends Number allow?
   **Answer:** `T extends Number` restricts `T` to `Number` or one of its subclasses, so code can use operations available on `Number`.
5. What is a wildcard type?
   **Answer:** A wildcard `?` represents an unknown type argument, optionally restricted with an upper or lower bound.
6. When is ? extends useful?
   **Answer:** Use `? extends T` when a method reads values from a producer whose type is `T` or a subtype of `T`.
7. When is ? super useful?
   **Answer:** Use `? super T` when a method writes `T` values to a consumer typed as `T` or one of its supertypes.
8. Why should raw types be avoided?
   **Answer:** Raw types skip generic type checks, can allow invalid values into collections, and often move errors from compile time to runtime.

## Source chapter: [11. Collections, lists, sets, and maps](./11-collections-lists-sets-and-maps.md)

1. What does the Collections Framework provide?
   **Answer:** The Collections Framework provides common interfaces and implementations for storing, retrieving, and processing groups of objects.
2. Which behavior distinguishes a List?
   **Answer:** A `List` keeps elements in a sequence, supports positions by index, and can contain duplicates.
3. What happens when a duplicate value is added to a Set?
   **Answer:** A `Set` stores distinct values according to its equality rules. Adding a duplicate does not create a second set element.
4. Does HashSet promise encounter order?
   **Answer:** No. `HashSet` does not guarantee iteration or encounter order.
5. What does a Map associate?
   **Answer:** A `Map` associates each key with a value, with each key appearing at most once.
6. What does put do when its key already exists?
   **Answer:** `put` adds a new key-value association or replaces the value associated with an existing key.
7. Are collections created with List.of mutable?
   **Answer:** No. Collections created with `List.of` are unmodifiable; attempts to change them throw `UnsupportedOperationException`.
8. Which implementations are common defaults for a list, set, and map?
   **Answer:** Common defaults are `ArrayList` for a list, `HashSet` for a set, and `HashMap` for a map.

## Source chapter: [12. Lambdas and functional interfaces](./12-lambdas-and-functional-interfaces.md)

1. How many abstract methods does a functional interface have?
   **Answer:** A functional interface has one abstract method, although it may also declare default or static methods.
2. What does a lambda provide?
   **Answer:** A lambda provides an implementation of a functional interface's single abstract method, often directly at the point where it is needed.
3. What does Predicate represent?
   **Answer:** `Predicate<T>` represents a test that accepts a `T` and returns `boolean`.
4. What does Function represent?
   **Answer:** `Function<T, R>` represents a transformation that accepts a `T` and returns an `R`.
5. What does Consumer represent?
   **Answer:** `Consumer<T>` represents an operation that accepts a `T` and returns no result.
6. What does Supplier represent?
   **Answer:** `Supplier<T>` represents a computation that provides a `T` value without taking an input.
7. When can a method reference replace a lambda?
   **Answer:** A method reference can replace a lambda when the lambda simply calls an existing compatible method, such as `String::trim`.
8. When should a long lambda be moved into a named method?
   **Answer:** Move a long lambda into a named method when naming and testing the behavior separately makes the code easier to understand.

## Source chapter: [13. Streams and Optional](./13-streams-and-optional.md)

1. What are the common parts of a stream pipeline?
   **Answer:** A common stream pipeline has a source, zero or more intermediate operations, and a terminal operation.
2. What does filter do?
   **Answer:** `filter` keeps only the elements that satisfy its predicate.
3. What does map do?
   **Answer:** `map` transforms each element into a value produced by a function.
4. When do intermediate stream operations run?
   **Answer:** Intermediate operations usually run lazily when a terminal operation starts consuming the stream.
5. Can a consumed stream be reused?
   **Answer:** No. A stream is intended for one use. After a terminal operation, create another stream from the source if more processing is needed.
6. What does Optional represent?
   **Answer:** `Optional` represents a value that may be present or absent, encouraging the caller to handle the missing case explicitly.
7. What does orElse provide?
   **Answer:** `orElse` supplies a fallback value when an Optional is empty.
8. Why is calling Optional.get without checking risky?
   **Answer:** Calling `get` without checking can throw `NoSuchElementException` when the Optional is empty. Prefer operations such as `orElse`, `orElseThrow`, or `ifPresent`.

## Source chapter: [14. Files, I/O, and date-time APIs](./14-files-io-and-date-time-apis.md)

1. What does Path represent?
   **Answer:** `Path` represents a filesystem path in a platform-independent way.
2. Which class has common file read and write methods?
   **Answer:** `Files` contains common static methods for reading, writing, copying, and inspecting files.
3. Which Java release introduced Files.readString?
   **Answer:** `Files.readString` was introduced in Java 11.
4. Why can file operations throw IOException?
   **Answer:** File operations can fail because of missing files, permissions, invalid paths, or other filesystem problems, and report these failures with `IOException` or a subclass.
5. What does try-with-resources close automatically?
   **Answer:** Try-with-resources closes each declared resource automatically when control leaves the block, including when an exception occurs.
6. What is LocalDate intended to represent?
   **Answer:** `LocalDate` represents a calendar date without a time or time zone.
7. How does ZonedDateTime differ from LocalDate?
   **Answer:** `ZonedDateTime` includes a date, time, and time zone, while `LocalDate` contains only a date.
8. What does Instant represent?
   **Answer:** `Instant` represents a point on the global timeline, typically as seconds and fractional seconds from the Unix epoch.

## Source chapter: [15. Concurrency, executors, and virtual threads](./15-concurrency-executors-and-virtual-threads.md)

1. What does a thread represent?
   **Answer:** A thread is an independent path of execution within a process. Multiple threads can make progress concurrently while sharing process memory.
2. What does an Executor separate from the task code?
   **Answer:** An `Executor` separates submitting work from the details of how and when that work runs.
3. What does Future.get return?
   **Answer:** `Future.get` waits for the computation to finish and returns its result, or throws if the computation failed or was cancelled.
4. What is a race condition?
   **Answer:** A race condition occurs when a program's result depends on the timing or interleaving of unsynchronized concurrent operations.
5. What does AtomicInteger provide?
   **Answer:** `AtomicInteger` provides integer operations such as increment and compare-and-set that are safe to use across threads without a separate lock for each operation.
6. In which Java version did virtual threads become permanent?
   **Answer:** Virtual threads became a permanent feature in Java 21.
7. What kind of workload suits virtual threads?
   **Answer:** Virtual threads suit workloads with many concurrent tasks that spend much of their time waiting, such as blocking network or database calls.
8. Why should scarce resources still be limited when using virtual threads?
   **Answer:** Virtual threads make waiting tasks cheaper but do not create more database connections, file handles, or remote-service capacity. Bound access to those scarce resources.

## Source chapter: [16. Packages, modules, testing, and JVM tools](./16-packages-modules-testing-and-jvm-tools.md)

1. What does a package group?
   **Answer:** A package groups related Java types under a namespace and helps avoid class-name conflicts.
2. Where should a package declaration appear?
   **Answer:** The package declaration appears at the beginning of the source file, before imports and type declarations.
3. How does the source path relate to a package name?
   **Answer:** A type in package `com.example.notes` is conventionally stored below a `com/example/notes` directory under a source root.
4. What does the -d option do for javac?
   **Answer:** The `-d` option tells `javac` where to place generated class files, arranged in directories that match their package names.
5. What does the classpath tell the Java runtime?
   **Answer:** The classpath tells the Java compiler or runtime where to find compiled classes and libraries.
6. What does a module descriptor declare?
   **Answer:** A module descriptor declares a module's name, required modules, and packages it exports or services it provides or uses.
7. What should a behavior test verify?
   **Answer:** A behavior test should verify observable results for a meaningful input, including important boundary cases, without depending on private implementation details.
8. Which JDK tool packages compiled classes into a JAR?
   **Answer:** The JDK `jar` tool packages compiled classes and related resources into a JAR file.
