# 15. Concurrency, executors, and virtual threads

[Back to notes index](../README.md)

| Previous | Notes index | Next |
| --- | --- | --- |
| [Previous: Files, I/O, and date-time APIs](./14-files-io-and-date-time-apis.md) | [Notes index](../README.md) | [Next: Packages, modules, testing, and JVM tools](./16-packages-modules-testing-and-jvm-tools.md) |

## Run a task on another thread

A thread is an independent path of execution. Concurrent code can make progress on more than one task, but shared mutable state must be coordinated.

An Executor separates task submission from the details of thread creation and scheduling.

## Submit work to an executor

ExecutorService can run tasks and return their results through Future.

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

The executor manages worker threads. get waits for the task result. Closing the executor waits for submitted work to finish and releases its resources.

## Protect shared state

Two threads that update the same mutable value can overwrite each other's work. This is a race condition.

~~~java
import java.util.concurrent.atomic.AtomicInteger;

AtomicInteger completedTasks = new AtomicInteger();

Runnable task = () -> completedTasks.incrementAndGet();
~~~

AtomicInteger provides atomic operations for a single integer value. For several related values, use a suitable lock or synchronization strategy so the state changes together.

## Use virtual threads for many blocking tasks

Virtual threads became a permanent feature in Java 21. They are lightweight threads managed by the Java runtime and are useful for many concurrent tasks that spend time waiting on I/O.

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

The executor starts a virtual thread for each submitted task. Virtual threads are intended for blocking tasks, not for making CPU-heavy calculations run faster. Limit scarce resources such as database connections separately from the number of virtual threads.

## Prefer managed task execution

For application work, use an executor or another managed task API rather than creating an unbounded number of platform threads manually. Keep task boundaries clear and handle interruption and failures deliberately.

Do not share mutable objects between threads unless access is protected. Immutable values are easier to use safely.

## Practice questions

1. What does a thread represent?
2. What does an Executor separate from the task code?
3. What does Future.get return?
4. What is a race condition?
5. What does AtomicInteger provide?
6. In which Java version did virtual threads become permanent?
7. What kind of workload suits virtual threads?
8. Why should scarce resources still be limited when using virtual threads?

## Main references

- [Concurrency utilities](https://docs.oracle.com/en/java/javase/26/docs/api/java.base/java/util/concurrent/package-summary.html)
- [Executors](https://docs.oracle.com/en/java/javase/26/docs/api/java.base/java/util/concurrent/Executors.html)
- [Virtual threads](https://dev.java/learn/new-features/virtual-threads/)
- [Thread API](https://docs.oracle.com/en/java/javase/26/docs/api/java.base/java/lang/Thread.html)
- [AtomicInteger](https://docs.oracle.com/en/java/javase/26/docs/api/java.base/java/util/concurrent/atomic/AtomicInteger.html)