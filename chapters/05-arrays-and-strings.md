# 05. Arrays and strings

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Methods, parameters, and return values](./04-methods-parameters-and-return-values.md) | [Notes index](../README.md) | [Next: Classes, objects, and constructors](./06-classes-objects-and-constructors.md) |

## Store a fixed-size sequence in an array

An array holds a fixed number of values of one element type. Its indexes start at zero.

~~~java
int[] scores = {82, 95, 74};
scores[0] = 88;

System.out.println(scores[0]);
System.out.println(scores.length);
~~~

scores.length is a field, not a method. Valid indexes range from zero through length minus one. Reading or writing outside that range throws ArrayIndexOutOfBoundsException.

## Loop through array values

Use an indexed loop when the index matters. Use an enhanced for loop when each value is enough.

~~~java
int[] scores = {88, 95, 74};

for (int index = 0; index < scores.length; index++) {
    System.out.println(index + ": " + scores[index]);
}

for (int score : scores) {
    System.out.println(score);
}
~~~

Arrays.toString formats an array for quick inspection.

~~~java
import java.util.Arrays;

int[] scores = {88, 95, 74};
System.out.println(Arrays.toString(scores));
~~~

## Work with immutable strings

String values are immutable. Methods such as trim and replace return another String rather than changing the original.

~~~java
String course = " Java ";
String cleaned = course.trim();

System.out.println(cleaned);
System.out.println(course);
~~~

Use equals to compare String content. The == operator checks whether two reference variables refer to the same object.

~~~java
String selectedCourse = new String("Java");

if ("Java".equals(selectedCourse)) {
    System.out.println("Course selected");
}
~~~

Calling equals on a known non-null literal also avoids a NullPointerException if selectedCourse is null.

## Build changing text with StringBuilder

Repeated string concatenation in a loop can create many temporary String objects. StringBuilder is designed for assembling mutable text.

~~~java
StringBuilder report = new StringBuilder();

report.append("Completed ");
report.append(3);
report.append(" chapters");

String message = report.toString();
System.out.println(message);
~~~

Use String for ordinary text values and StringBuilder when many appends are required.

## Choose an array or a collection

An array has a fixed length after creation. When a sequence needs to grow or shrink, a collection such as ArrayList is usually a better fit. Collections are covered in a later chapter.

## Practice questions

1. What kind of sequence does an array hold?
2. Which index identifies the first array element?
3. Is length a field or a method on an array?
4. What exception can an invalid array index cause?
5. When is an enhanced for loop convenient?
6. Are String objects mutable?
7. What does == check for references?
8. When can StringBuilder be useful?

## Main references

- [Arrays](https://dev.java/learn/language/arrays/)
- [Strings](https://dev.java/learn/language/strings/)
- [The Arrays class](https://docs.oracle.com/en/java/javase/26/docs/api/java.base/java/util/Arrays.html)
- [The String class](https://docs.oracle.com/en/java/javase/26/docs/api/java.base/java/lang/String.html)
- [The StringBuilder class](https://docs.oracle.com/en/java/javase/26/docs/api/java.base/java/lang/StringBuilder.html)