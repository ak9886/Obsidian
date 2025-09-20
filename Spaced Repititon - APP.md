---
updated_at: 2025-09-20T16:22:00.534+05:30
edited_seconds: 30
---
  #flashcards/java/basics

What makes Java both compiled and interpreted? :: It compiles source code into bytecode, then the JVM interpreter executes it.

What is meant by "Write Once, Run Anywhere"? :: Java bytecode runs on any machine with a JVM, making it platform-independent.
<!--SR:!2025-09-24,4,270-->

Define an Object in Java. :: An object bundles state (variables) and behavior (methods).

Define a Class in Java. :: A class is a blueprint/template for creating objects.

What is the role of a constructor? :: To initialize objects when they are created.

How does the `this` keyword help? :: It refers to the current object, avoids variable shadowing, and allows constructor chaining.

What is Encapsulation? :: Wrapping data and methods in a class with restricted access using access modifiers.

List Java’s access modifiers. :: public, private, protected, default (package-private).

What are Java’s primitive types? :: byte, short, int, long, float, double, char, boolean.

Difference between `==` and `.equals()` for Strings? :: `==` compares references, `.equals()` compares content.

What is short-circuit evaluation? :: In `&&` and `||`, the second operand is evaluated only if needed.

How are operators prioritized in Java? :: Unary > Multiplicative (*,/,% ) > Additive (+,-) > Relational > Equality > Logical AND > Logical OR > Assignment.

---

#flashcards/java/advanced

What is concurrency in programming? :: Executing multiple tasks independently but possibly interacting.

Name two concurrency models. :: Shared Memory and Message Passing.

What are common issues in concurrency? :: Resource sharing, synchronization, race conditions.

Difference between process-based and thread-based multitasking? :: Process-based = multiple programs run; Thread-based = multiple tasks in one program run.

How do you create a thread in Java? :: Extend Thread class and override run(), or implement Runnable interface.

Key thread control methods? :: start(), run(), sleep(), join(), isAlive().

What are thread priorities? :: Values from 1 (MIN) to 10 (MAX), default = 5 (NORM).

What is JDBC? :: Java Database Connectivity – API to connect Java programs with relational databases.

List the JDBC steps. :: Import packages → Load driver → Establish connection → Create statement → Execute query → Process results → Close connection.

Difference between Statement, PreparedStatement, CallableStatement? :: Statement: simple SQL, no parameters · PreparedStatement: precompiled, parameterized, reusable · CallableStatement: stored procedures with IN/OUT parameters.

How does a ResultSet work? :: It stores query results, iterates with next(), and retrieves data with getInt(), getString(), etc.

Difference between CUI and GUI? :: CUI requires typed commands; GUI provides windows, buttons, menus.

Difference between AWT and Swing? :: AWT = heavyweight, platform-dependent; Swing = lightweight, platform-independent, richer components.

What is MVC in Java GUI? :: Model = data, View = UI, Controller = logic.

What is an Applet? :: A small Java program embedded in web pages, runs in JVM sandbox.

Applet lifecycle stages? :: init() → start() → stop() → destroy().

Advantages of applets? :: Portable, secure, embeddable in web pages.

Why are applets obsolete? :: Browser/JVM support dropped due to security issues.
