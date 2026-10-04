# 98. All code samples

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Packages, modules, testing, and JVM tools](./16-packages-modules-testing-and-jvm-tools.md) | [Notes index](../README.md) | [Next: Complete questions and answers](./99-complete-q-and-a.md) |

## Source chapter: [01. JDK setup and first Java program](./01-jdk-setup-and-first-java-program.md)

### Sample 1

~~~sh
java --version
javac --version
~~~

### Sample 2

~~~java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello, Java!");
    }
}
~~~

### Sample 3

~~~sh
javac Main.java
java Main
~~~

### Sample 4

~~~text
jshell> int count = 3;
jshell> count * 2
$2 ==> 6
~~~

## Source chapter: [02. Variables, primitive types, and references](./02-variables-primitive-types-and-references.md)

### Sample 1

~~~java
int age = 28;
double temperature = 21.5;
char initial = 'A';
boolean isReady = true;
String language = "Java";
~~~

### Sample 2

~~~java
int itemCount = 12;
long population = 8_000_000_000L;
double price = 19.95;
float scale = 0.75f;
char grade = 'B';
boolean available = false;
~~~

### Sample 3

~~~java
String firstName = "Ashish";
String greeting = "Hello, " + firstName;
Integer score = 95;
~~~

### Sample 4

~~~java
var message = "Study Java";
var attemptCount = 3;
~~~

### Sample 5

~~~java
int count = 5;
double exactCount = count;

double measurement = 7.8;
int wholePart = (int) measurement;
~~~

## Source chapter: [03. Operators, expressions, and control flow](./03-operators-expressions-and-control-flow.md)

### Sample 1

~~~java
int total = 17;
int people = 5;

int wholePerPerson = total / people;
int remainder = total % people;
double average = (double) total / people;
~~~

### Sample 2

~~~java
int score = 78;
boolean passed = score >= 60;
boolean eligible = passed && score < 100;
boolean needsReview = score < 60 || score > 100;
~~~

### Sample 3

~~~java
int score = 78;

if (score >= 60) {
    System.out.println("Passed");
} else {
    System.out.println("Try again");
}

String level = switch (score / 10) {
    case 10, 9 -> "excellent";
    case 8 -> "strong";
    case 7, 6 -> "passing";
    default -> "keep practicing";
};
~~~

### Sample 4

~~~java
for (int index = 0; index < 3; index++) {
    System.out.println("Attempt " + index);
}

int remaining = 3;
while (remaining > 0) {
    System.out.println("Remaining: " + remaining);
    remaining--;
}
~~~

## Source chapter: [04. Methods, parameters, and return values](./04-methods-parameters-and-return-values.md)

### Sample 1

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

### Sample 2

~~~java
static String displayName(String name) {
    if (name == null || name.isBlank()) {
        return "Guest";
    }

    return name.trim();
}
~~~

### Sample 3

~~~java
static int multiply(int first, int second) {
    return first * second;
}

static double multiply(double first, double second) {
    return first * second;
}
~~~

### Sample 4

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

### Sample 5

~~~java
static int sum(int... values) {
    int result = 0;
    for (int value : values) {
        result += value;
    }
    return result;
}
~~~

## Source chapter: [05. Arrays and strings](./05-arrays-and-strings.md)

### Sample 1

~~~java
int[] scores = {82, 95, 74};
scores[0] = 88;

System.out.println(scores[0]);
System.out.println(scores.length);
~~~

### Sample 2

~~~java
int[] scores = {88, 95, 74};

for (int index = 0; index < scores.length; index++) {
    System.out.println(index + ": " + scores[index]);
}

for (int score : scores) {
    System.out.println(score);
}
~~~

### Sample 3

~~~java
import java.util.Arrays;

int[] scores = {88, 95, 74};
System.out.println(Arrays.toString(scores));
~~~

### Sample 4

~~~java
String course = " Java ";
String cleaned = course.trim();

System.out.println(cleaned);
System.out.println(course);
~~~

### Sample 5

~~~java
String selectedCourse = new String("Java");

if ("Java".equals(selectedCourse)) {
    System.out.println("Course selected");
}
~~~

### Sample 6

~~~java
StringBuilder report = new StringBuilder();

report.append("Completed ");
report.append(3);
report.append(" chapters");

String message = report.toString();
System.out.println(message);
~~~

## Source chapter: [06. Classes, objects, and constructors](./06-classes-objects-and-constructors.md)

### Sample 1

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

## Source chapter: [07. Encapsulation, inheritance, and composition](./07-encapsulation-inheritance-and-composition.md)

### Sample 1

~~~java
class BankAccount {
    private int balanceCents;

    public int getBalanceCents() {
        return balanceCents;
    }

    public void deposit(int amountCents) {
        if (amountCents <= 0) {
            throw new IllegalArgumentException("Deposit must be positive");
        }
        balanceCents += amountCents;
    }
}
~~~

### Sample 2

~~~java
class Employee {
    private final String name;

    Employee(String name) {
        this.name = name;
    }

    String getName() {
        return name;
    }
}

class Manager extends Employee {
    private final int teamSize;

    Manager(String name, int teamSize) {
        super(name);
        this.teamSize = teamSize;
    }

    int getTeamSize() {
        return teamSize;
    }
}
~~~

### Sample 3

~~~java
class Engine {
    void start() {
        System.out.println("Engine started");
    }
}

class Car {
    private final Engine engine;

    Car(Engine engine) {
        this.engine = engine;
    }

    void start() {
        engine.start();
    }
}
~~~

## Source chapter: [08. Interfaces, enums, and records](./08-interfaces-enums-and-records.md)

### Sample 1

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

### Sample 2

~~~java
enum Priority {
    LOW,
    NORMAL,
    HIGH
}

Priority taskPriority = Priority.HIGH;
~~~

### Sample 3

~~~java
record Point(double x, double y) {}

Point origin = new Point(0, 0);
System.out.println(origin.x());
System.out.println(origin.y());
~~~

### Sample 4

~~~java
record Temperature(double celsius) {
    Temperature {
        if (celsius < -273.15) {
            throw new IllegalArgumentException("Temperature is below absolute zero");
        }
    }
}
~~~

## Source chapter: [09. Exceptions and input validation](./09-exceptions-and-input-validation.md)

### Sample 1

~~~java
String input = "42";

try {
    int quantity = Integer.parseInt(input);
    System.out.println("Quantity: " + quantity);
} catch (NumberFormatException exception) {
    System.out.println("Enter a whole number.");
}
~~~

### Sample 2

~~~java
static int requirePositive(int value) {
    if (value <= 0) {
        throw new IllegalArgumentException("Value must be positive");
    }
    return value;
}
~~~

## Source chapter: [10. Generics and type safety](./10-generics-and-type-safety.md)

### Sample 1

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

### Sample 2

~~~java
static <T> T first(T left, T right) {
    return left;
}

String selected = first("Java", "HTML");
Integer count = first(3, 5);
~~~

### Sample 3

~~~java
static <T extends Number> double asDouble(T value) {
    return value.doubleValue();
}

double result = asDouble(12);
~~~

### Sample 4

~~~java
static double sum(java.util.List<? extends Number> values) {
    double total = 0;
    for (Number value : values) {
        total += value.doubleValue();
    }
    return total;
}
~~~

## Source chapter: [11. Collections, lists, sets, and maps](./11-collections-lists-sets-and-maps.md)

### Sample 1

~~~java
import java.util.ArrayList;
import java.util.List;

List<String> names = new ArrayList<>();
names.add("Maya");
names.add("Ravi");
names.add("Maya");

System.out.println(names.get(0));
System.out.println(names.size());
~~~

### Sample 2

~~~java
import java.util.HashSet;
import java.util.Set;

Set<String> tags = new HashSet<>();
tags.add("java");
tags.add("collections");
tags.add("java");

System.out.println(tags.size());
~~~

### Sample 3

~~~java
import java.util.HashMap;
import java.util.Map;

Map<String, Integer> scores = new HashMap<>();
scores.put("Maya", 92);
scores.put("Ravi", 85);

Integer mayaScore = scores.get("Maya");

for (Map.Entry<String, Integer> entry : scores.entrySet()) {
    System.out.println(entry.getKey() + ": " + entry.getValue());
}
~~~

### Sample 4

~~~java
List<String> fixedNames = List.of("Maya", "Ravi");
List<String> editableNames = new ArrayList<>(fixedNames);
editableNames.add("Tara");
~~~

## Source chapter: [12. Lambdas and functional interfaces](./12-lambdas-and-functional-interfaces.md)

### Sample 1

~~~java
@FunctionalInterface
interface TextCheck {
    boolean accepts(String text);
}

TextCheck hasContent = text -> !text.isBlank();

System.out.println(hasContent.accepts("Java"));
~~~

### Sample 2

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

### Sample 3

~~~java
import java.util.List;

List<String> names = List.of("Maya", "Ravi", "Tara");
names.forEach(System.out::println);
~~~

### Sample 4

~~~java
import java.util.ArrayList;
import java.util.List;

List<String> names = new ArrayList<>(List.of("Maya", "", "Ravi"));
names.removeIf(name -> name.isBlank());

System.out.println(names);
~~~

## Source chapter: [13. Streams and Optional](./13-streams-and-optional.md)

### Sample 1

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

### Sample 2

~~~java
import java.util.List;

int totalLength = List.of("HTML", "Java", "CSS")
        .stream()
        .mapToInt(String::length)
        .sum();

System.out.println(totalLength);
~~~

### Sample 3

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

## Source chapter: [14. Files, I/O, and date-time APIs](./14-files-io-and-date-time-apis.md)

### Sample 1

~~~java
import java.nio.file.Path;

Path notesFile = Path.of("notes", "today.txt");
System.out.println(notesFile);
~~~

### Sample 2

~~~java
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;

Path file = Path.of("today.txt");

try {
    Files.writeString(file, "Review collections today.");
    String content = Files.readString(file);
    System.out.println(content);
} catch (IOException exception) {
    System.out.println("Could not read or write the file.");
}
~~~

### Sample 3

~~~java
import java.io.BufferedReader;
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;

try (BufferedReader reader = Files.newBufferedReader(Path.of("today.txt"))) {
    String line;
    while ((line = reader.readLine()) != null) {
        System.out.println(line);
    }
} catch (IOException exception) {
    System.out.println("Could not read the file.");
}
~~~

### Sample 4

~~~java
import java.time.LocalDate;
import java.time.ZoneId;
import java.time.ZonedDateTime;
import java.time.format.DateTimeFormatter;

LocalDate dueDate = LocalDate.of(2026, 10, 20);
ZonedDateTime meeting = ZonedDateTime.now(ZoneId.of("Asia/Kolkata"));
DateTimeFormatter format = DateTimeFormatter.ofPattern("dd MMM uuuu");

System.out.println(dueDate.format(format));
System.out.println(meeting);
~~~

## Source chapter: [15. Concurrency, executors, and virtual threads](./15-concurrency-executors-and-virtual-threads.md)

### Sample 1

~~~java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

public class Main {
    public static void main(String[] args) throws Exception {
        try (ExecutorService executor = Executors.newFixedThreadPool(2)) {
            Future<String> result = executor.submit(() -> "Task finished");
            System.out.println(result.get());
        }
    }
}
~~~

### Sample 2

~~~java
import java.util.concurrent.atomic.AtomicInteger;

AtomicInteger completedTasks = new AtomicInteger();

Runnable task = () -> completedTasks.incrementAndGet();
~~~

### Sample 3

~~~java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

public class VirtualThreadExample {
    public static void main(String[] args) throws Exception {
        try (ExecutorService executor =
                     Executors.newVirtualThreadPerTaskExecutor()) {
            Future<String> response = executor.submit(() -> "Response ready");
            System.out.println(response.get());
        }
    }
}
~~~

## Source chapter: [16. Packages, modules, testing, and JVM tools](./16-packages-modules-testing-and-jvm-tools.md)

### Sample 1

~~~java
package com.example.notes;

public class Main {
    public static void main(String[] args) {
        System.out.println("Package ready");
    }
}
~~~

### Sample 2

~~~sh
javac -d out src/com/example/notes/Main.java
java -cp out com.example.notes.Main
~~~

### Sample 3

~~~java
module com.example.notes {
    exports com.example.notes.api;
}
~~~

### Sample 4

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

### Sample 5

~~~sh
jar --create --file app.jar --main-class com.example.notes.Main -C out .
java -jar app.jar
~~~

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Packages, modules, testing, and JVM tools](./16-packages-modules-testing-and-jvm-tools.md) | [Notes index](../README.md) | [Next: Complete questions and answers](./99-complete-q-and-a.md) |
