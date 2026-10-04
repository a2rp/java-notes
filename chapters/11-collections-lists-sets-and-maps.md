# 11. Collections, lists, sets, and maps

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Generics and type safety](./10-generics-and-type-safety.md) | [Notes index](../README.md) | [Next: Lambdas and functional interfaces](./12-lambdas-and-functional-interfaces.md) |

## Choose a collection interface

The Collections Framework provides interfaces and implementations for groups of values. Declare variables with an interface and construct the implementation the program needs.

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

List preserves element order and allows duplicates. ArrayList is a common default implementation for a resizable list.

## Use a set for unique values

Set does not contain duplicate values. HashSet is a common implementation when encounter order is not important.

~~~java
import java.util.HashSet;
import java.util.Set;

Set<String> tags = new HashSet<>();
tags.add("java");
tags.add("collections");
tags.add("java");

System.out.println(tags.size());
~~~

The set size is 2 because adding an existing value does not add another copy. Do not rely on HashSet iteration order.

## Use a map for key and value pairs

Map associates each key with one value. A key can appear only once.

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

put replaces the value for an existing key. get returns null when a key is absent, so use containsKey when the distinction between an absent key and a stored null matters.

## Know whether a factory collection is mutable

List.of, Set.of, and Map.of create unmodifiable collections. Operations that change them throw UnsupportedOperationException.

~~~java
List<String> fixedNames = List.of("Maya", "Ravi");
List<String> editableNames = new ArrayList<>(fixedNames);
editableNames.add("Tara");
~~~

Copy values into a mutable implementation when later updates are needed. The fact that a variable is declared with List does not make its current object mutable.

## Select an implementation for its behavior

Use ArrayList for an ordered resizable sequence, HashSet for unique values without a useful iteration order, and HashMap for key and value lookup when order is not required.

Other implementations provide different behavior, such as insertion order or sorted order. Choose based on the operations and ordering guarantees the program needs.

## Practice questions

1. What does the Collections Framework provide?
2. Which behavior distinguishes a List?
3. What happens when a duplicate value is added to a Set?
4. Does HashSet promise encounter order?
5. What does a Map associate?
6. What does put do when its key already exists?
7. Are collections created with List.of mutable?
8. Which implementations are common defaults for a list, set, and map?

## Main references

- [Collections Framework](https://dev.java/learn/api/collections-framework/)
- [Collection interfaces](https://docs.oracle.com/en/java/javase/26/docs/api/java.base/java/util/package-summary.html)
- [List](https://docs.oracle.com/en/java/javase/26/docs/api/java.base/java/util/List.html)
- [Set](https://docs.oracle.com/en/java/javase/26/docs/api/java.base/java/util/Set.html)
- [Map](https://docs.oracle.com/en/java/javase/26/docs/api/java.base/java/util/Map.html)