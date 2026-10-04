# 03. Operators, expressions, and control flow

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Variables, primitive types, and references](./02-variables-primitive-types-and-references.md) | [Notes index](../README.md) | [Next: Methods, parameters, and return values](./04-methods-parameters-and-return-values.md) |

## Calculate with operators

Arithmetic operators perform calculations. When both operands are integers, division produces an integer result and discards the remainder.

~~~java
int total = 17;
int people = 5;

int wholePerPerson = total / people;
int remainder = total % people;
double average = (double) total / people;
~~~

wholePerPerson is 3 and remainder is 2. Casting before division makes the calculation use floating-point arithmetic.

## Compare values and combine conditions

Comparison operators produce a boolean result. Logical operators combine boolean conditions.

~~~java
int score = 78;
boolean passed = score >= 60;
boolean eligible = passed && score < 100;
boolean needsReview = score < 60 || score > 100;
~~~

&& and || use short-circuit evaluation. If the left side already determines the result, Java does not evaluate the right side.

## Choose a path with if and switch

Use if and else when the decision is based on a condition. A switch expression can map a value to a result. Switch expressions require Java 14 or later.

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

Arrow cases do not fall through into the next case. A switch expression must produce a value for every possible input, usually with a default case.

## Repeat work with loops

Use for when the repetition has a clear counter or range. Use while when repetition continues while a condition remains true.

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

The condition is checked before each while iteration. Update the values used by the condition so the loop eventually ends.

## Use break and continue carefully

break exits the nearest loop or switch. continue skips the rest of the current loop iteration and checks the next one.

Use them when they make the control flow easier to read. A complex loop with many early exits can be harder to maintain than a small helper method.

## Practice questions

1. What does integer division do with a remainder?
2. How can a cast make division produce a decimal result?
3. What type of value do comparison operators produce?
4. What does short-circuit evaluation mean?
5. When is an if and else statement useful?
6. Which Java version introduced switch expressions as a permanent feature?
7. When is a for loop a useful choice?
8. What is the difference between break and continue?

## Main references

- [Operators](https://dev.java/learn/language/expressions-operators/)
- [Control flow statements](https://dev.java/learn/language-basics/controlling-flow/)
- [Switch expressions](https://dev.java/learn/language-basics/switch-expression/)
- [Java language specification: expressions](https://docs.oracle.com/javase/specs/jls/se26/html/jls-15.html)