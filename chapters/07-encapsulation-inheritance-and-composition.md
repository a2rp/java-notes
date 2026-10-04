# 07. Encapsulation, inheritance, and composition

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Classes, objects, and constructors](./06-classes-objects-and-constructors.md) | [Notes index](../README.md) | [Next: Interfaces, enums, and records](./08-interfaces-enums-and-records.md) |

## Protect object state with encapsulation

Encapsulation keeps a class's internal state private and exposes operations that preserve valid values.

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

The class prevents callers from setting the balance to any arbitrary value. The deposit method owns the rule that each deposit must be positive. Such a rule is an invariant that should remain true for every valid account.

## Extend a class when the subtype relationship is real

Inheritance lets one class extend another class. A subclass inherits accessible behavior and can add or override behavior.

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

Manager is an Employee, so extending Employee can make sense. super(name) calls the parent constructor. Keep fields private and expose methods intentionally.

When a subclass replaces an inherited method, use @Override so the compiler checks that a matching method exists.

## Prefer composition for a has-a relationship

Composition places one object inside another and delegates work to it.

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

A Car has an Engine. Composition lets a class use another object's behavior without claiming that it is a subtype.

## Choose a relationship from the model

Use inheritance when the child truly is a specialized form of the parent and callers can use it in place of the parent. Use composition when one object owns or collaborates with another object.

A deep inheritance tree can make behavior harder to change. Keep relationships small and explicit.

## Practice questions

1. What does encapsulation protect?
2. What is an invariant?
3. Which keyword declares a subclass?
4. What does super(name) do?
5. What does @Override ask the compiler to check?
6. When does inheritance represent a useful relationship?
7. What does composition represent in the Car example?
8. Why can a deep inheritance tree be difficult to change?

## Main references

- [Object-oriented programming](https://dev.java/learn/language/objects/)
- [Inheritance](https://dev.java/learn/language/objects/inheritance/)
- [Java language specification: classes](https://docs.oracle.com/javase/specs/jls/se26/html/jls-8.html)
- [Access control](https://dev.java/learn/language/objects/classes/access-control/)