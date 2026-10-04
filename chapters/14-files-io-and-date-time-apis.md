# 14. Files, I/O, and date-time APIs

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Streams and Optional](./13-streams-and-optional.md) | [Notes index](../README.md) | [Next: Concurrency, executors, and virtual threads](./15-concurrency-executors-and-virtual-threads.md) |

## Represent a filesystem path

Path represents a filesystem location. Use Path.of to build one from a string.

~~~java
import java.nio.file.Path;

Path notesFile = Path.of("notes", "today.txt");
System.out.println(notesFile);
~~~

A Path describes a location. It does not itself read or write the file.

## Read and write text with Files

Files provides methods for common file operations. readString and writeString are available in Java 11 and later.

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

File operations can fail because a path is missing, access is denied, or storage is unavailable. IOException is checked, so callers must handle it or declare it.

## Close resources with try-with-resources

Resources such as readers and streams should be closed when work is complete. A resource declared in try-with-resources is closed automatically.

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

Use try-with-resources for objects that implement AutoCloseable. This avoids forgetting to close the resource when an exception occurs.

## Use java.time for dates and times

The java.time API provides types for dates, clock times, time zones, and instants.

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

LocalDate has no time or time zone. ZonedDateTime includes a time zone. Instant represents a point on the UTC timeline. Choose the type that matches the data rather than storing dates as arbitrary strings.

## Practice questions

1. What does Path represent?
2. Which class has common file read and write methods?
3. Which Java release introduced Files.readString?
4. Why can file operations throw IOException?
5. What does try-with-resources close automatically?
6. What is LocalDate intended to represent?
7. How does ZonedDateTime differ from LocalDate?
8. What does Instant represent?

## Main references

- [File I/O](https://dev.java/learn/java-io/file-system/)
- [Files API](https://docs.oracle.com/en/java/javase/26/docs/api/java.base/java/nio/file/Files.html)
- [Path API](https://docs.oracle.com/en/java/javase/26/docs/api/java.base/java/nio/file/Path.html)
- [Date and Time](https://docs.oracle.com/en/java/javase/26/docs/api/java.base/java/time/package-summary.html)
- [Try-with-resources](https://dev.java/learn/exceptions/)