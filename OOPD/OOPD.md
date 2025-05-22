
---

### **1. Inheritance Concept**

**Definition**: Inheritance is a mechanism in C++ by which one class (derived class) acquires the properties and behaviors (data members and member functions) of another class (base class).

**Types of Inheritance**:

- **Single Inheritance**: One base class → one derived class.
    
- **Multiple Inheritance**: One derived class inherits from more than one base class.
    
- **Multilevel Inheritance**: Class A → Class B → Class C.
    
- **Hierarchical Inheritance**: One base class → multiple derived classes.
    
- **Hybrid Inheritance**: Combination of multiple types (e.g., multiple + multilevel).
    

**Syntax Example**:

```cpp
class Base {
public:
    void display() {
        cout << "Base class\n";
    }
};

class Derived : public Base {
public:
    void show() {
        cout << "Derived class\n";
    }
};
```

**Use**: Promotes code reuse, logical hierarchy, and modularity.

---

### **2. Polymorphism**

**Definition**: Polymorphism means “many forms”. It allows functions or methods to behave differently based on the object invoking them.

**Types**:

- **Compile-time Polymorphism (Static)**: Achieved via function overloading or operator overloading.
    
- **Run-time Polymorphism (Dynamic)**: Achieved using virtual functions.
    

**Example** (Runtime):

```cpp
class Animal {
public:
    virtual void speak() {
        cout << "Animal speaks\n";
    }
};

class Dog : public Animal {
public:
    void speak() override {
        cout << "Dog barks\n";
    }
};

Animal* a = new Dog();
a->speak();  // Output: Dog barks (dynamic binding)
```

---

### **3. Class and Object**

**Class**: A blueprint for creating objects. It defines data and functions that operate on the data.

**Object**: An instance of a class.

**Example**:

```cpp
class Car {
public:
    string brand;
    void drive() {
        cout << "Driving " << brand << endl;
    }
};

Car c1;
c1.brand = "Tesla";
c1.drive();  // Output: Driving Tesla
```

---

### **4. Virtual Function**

**Definition**: A member function that is declared using the `virtual` keyword and can be overridden in derived classes to enable **runtime polymorphism**.

**Key Concepts**:

- Enables **dynamic dispatch**.
    
- Use of **vtable** and **vptr** internally.
    

**Example**:

```cpp
class Shape {
public:
    virtual void draw() {
        cout << "Drawing Shape\n";
    }
};

class Circle : public Shape {
public:
    void draw() override {
        cout << "Drawing Circle\n";
    }
};

Shape* s = new Circle();
s->draw();  // Output: Drawing Circle
```

---

### **5. Friend Function**

**Definition**: A non-member function that has access to the private and protected members of a class.

**Syntax**: Declared using the `friend` keyword.

**Example**:

```cpp
class Box {
private:
    int width;
public:
    Box(int w) : width(w) {}
    friend void printWidth(Box b);
};

void printWidth(Box b) {
    cout << "Width: " << b.width << endl;
}
```

**Use**: To allow controlled external access to class internals.

---

### **6. Static Function**

**Definition**: A function that belongs to the class, not to any object of the class.

**Characteristics**:

- Can be called without creating an object.
    
- Can only access static data members.
    

**Example**:

```cpp
class Counter {
public:
    static int count;
    static void increment() {
        count++;
    }
};

int Counter::count = 0;
Counter::increment();
```

---

### **7. Constructor**

**Definition**: A special member function that is automatically invoked when an object is created. Used to initialize objects.

**Types**:

- **Default Constructor**
    
- **Parameterized Constructor**
    
- **Copy Constructor**
    
- **Destructor** (opposite of constructor)
    

**Example**:

```cpp
class Student {
    int id;
public:
    Student() {
        id = 0;
        cout << "Default Constructor\n";
    }
    Student(int x) {
        id = x;
        cout << "Parameterized Constructor\n";
    }
};
```

---

### **8. Templates**

**Definition**: Allow functions and classes to operate with generic types. Useful for **code reusability**.

**Types**:

- **Function Templates**
    
- **Class Templates**
    

**Function Template Example**:

```cpp
template <typename T>
T add(T a, T b) {
    return a + b;
}
```

**Class Template Example**:

```cpp
template <class T>
class Container {
    T element;
public:
    Container(T e) : element(e) {}
    T get() { return element; }
};
```

---

### **9. STL (Standard Template Library)**

**Definition**: A powerful set of C++ template classes to provide general-purpose classes and functions with templates.

**Components**:

- **Containers**: Store collections (e.g., `vector`, `list`, `map`, `set`)
    
- **Algorithms**: Common algorithms like `sort`, `find`, `reverse`
    
- **Iterators**: Bridge between containers and algorithms
    
- **Function Objects (Functors)**
    

**Example**:

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    vector<int> v = {5, 3, 9, 1};
    sort(v.begin(), v.end());
    for (int i : v)
        cout << i << " ";
}
```

**Output**:

```
1 3 5 9
```

---

### **Summary Table**

|Concept|Keyword / Type|Use / Purpose|
|---|---|---|
|Inheritance|`:` syntax|Code reuse, hierarchy|
|Polymorphism|`virtual`, overload|Dynamic or static behavior|
|Class & Object|`class`|Encapsulation and instantiation|
|Virtual Function|`virtual`|Runtime method overriding|
|Friend Function|`friend`|Access private members externally|
|Static Function|`static`|Belongs to class, not object|
|Constructor|Same name as class|Initializes objects|
|Templates|`template<typename T>`|Generic programming|
|STL|`vector`, `map`, etc.|Built-in data structures and algorithms|

---
