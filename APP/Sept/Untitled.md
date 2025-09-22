---
updated_at: 2025-09-22T21:53:15.613+05:30
edited_seconds: 40
---

# Java Comprehensive Study Guide

---

## 1. Object, Class, and Constructors

### Concepts
- **Class:** Blueprint of an object; defines properties and behaviors.  
- **Object:** Instance of a class with its own state.  
- **Constructor:** Special method to initialize objects. Name matches the class and has no return type.  

### Code Example
```java
class Student {
    String name;
    int age;

    // Constructor
    Student(String n, int a) {
        name = n;
        age = a;
    }

    void display() {
        System.out.println("Name: " + name + ", Age: " + age);
    }

    public static void main(String[] args) {
        Student s1 = new Student("Rahul", 20);
        Student s2 = new Student("Ananya", 22);
        s1.display();
        s2.display();
    }
}
````

---

## 2. Procedural vs Function Programming

### Procedural Programming

```java
class Procedural {
    public static void main(String[] args) {
        int a = 10, b = 20;
        int sum = a + b;
        System.out.println("Sum = " + sum);
    }
}
```

### Function-Based Programming

```java
class Functional {
    static int add(int x, int y) {
        return x + y;
    }

    public static void main(String[] args) {
        int result = add(10, 20);
        System.out.println("Sum = " + result);
    }
}
```

---

## 3. Calling Functions with Arguments

```java
class CallFunc {
    static void greet(String name) {
        System.out.println("Hello, " + name);
    }

    public static void main(String[] args) {
        greet("Sharan");
        greet("Rahul");
    }
}
```

---

## 4. OOP Concepts

### Core Pillars

1. **Abstraction** – Focus on **what** an object does, not **how**.
    
2. **Encapsulation** – Hide internal data using **private variables**; provide getters/setters.
    
3. **Inheritance** – Reuse code from **parent classes**.
    
4. **Polymorphism** – Same method behaves differently (**overloading/overriding**).
    

---

## 5. Abstraction

```java
abstract class Shape {
    abstract void draw();
}

class Circle extends Shape {
    void draw() {
        System.out.println("Drawing Circle");
    }
}

class Square extends Shape {
    void draw() {
        System.out.println("Drawing Square");
    }
}

public class AbstractionDemo {
    public static void main(String[] args) {
        Shape s1 = new Circle();
        Shape s2 = new Square();
        s1.draw();
        s2.draw();
    }
}
```

---

## 6. Encapsulation

```java
class BankAccount {
    private double balance;

    public void deposit(double amount) {
        if(amount > 0) balance += amount;
    }

    public double getBalance() {
        return balance;
    }

    public static void main(String[] args) {
        BankAccount acc = new BankAccount();
        acc.deposit(500);
        System.out.println("Balance: " + acc.getBalance());
    }
}
```

---

## 7. Inheritance (3 Types)

### Single Inheritance

```java
class Animal {
    void eat() { System.out.println("Eating..."); }
}
class Dog extends Animal {
    void bark() { System.out.println("Barking..."); }
}
```

### Multilevel Inheritance

```java
class Puppy extends Dog {
    void weep() { System.out.println("Weeping..."); }
}
```

### Hierarchical Inheritance

```java
class Cat extends Animal {
    void meow() { System.out.println("Meowing..."); }
}
```

---

## 8. Polymorphism

### Method Overloading

```java
class MathOp {
    int add(int a, int b) { return a + b; }
    double add(double a, double b) { return a + b; }
}
```

### Method Overriding

```java
class Parent {
    void show() { System.out.println("Parent class"); }
}
class Child extends Parent {
    @Override
    void show() { System.out.println("Child class"); }
}

public class PolyDemo {
    public static void main(String[] args) {
        Parent p = new Child();
        p.show(); // calls Child's show
    }
}
```

---

## 9. Interface

```java
interface Vehicle {
    void drive();
}

class Car implements Vehicle {
    public void drive() {
        System.out.println("Car is driving");
    }
}

public class InterfaceDemo {
    public static void main(String[] args) {
        Vehicle v = new Car();
        v.drive();
    }
}
```

---

## 10. Threads and Multithreading

```java
class MyThread extends Thread {
    public void run() {
        for (int i = 1; i <= 5; i++) {
            System.out.println(Thread.currentThread().getName() + " - " + i);
        }
    }
}

public class ThreadDemo {
    public static void main(String[] args) {
        MyThread t1 = new MyThread();
        MyThread t2 = new MyThread();
        t1.start();
        t2.start();
    }
}
```

---

## 11. JDBC

```java
import java.sql.*;

public class JdbcDemo {
    public static void main(String[] args) {
        try {
            Connection con = DriverManager.getConnection(
                "jdbc:mysql://localhost:3306/testdb", "root", "password");
            Statement stmt = con.createStatement();
            ResultSet rs = stmt.executeQuery("SELECT * FROM student");
            while (rs.next()) {
                System.out.println(rs.getInt(1) + " " + rs.getString(2));
            }
            con.close();
        } catch (Exception e) {
            System.out.println(e);
        }
    }
}
```

---

## 12. JFrame (Swing GUI)

```java
import javax.swing.*;

public class MyFrame {
    public static void main(String[] args) {
        JFrame f = new JFrame("My First Frame");
        JButton b = new JButton("Click Me");
        b.setBounds(100, 100, 120, 40);

        f.add(b);
        f.setSize(300, 300);
        f.setLayout(null);
        f.setVisible(true);
    }
}
```

---
