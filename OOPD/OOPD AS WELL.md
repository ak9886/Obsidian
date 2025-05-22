Certainly! Below is the **extended code** with explanations for **Units 2, 3, 4, and 5** of **OODP** (Object Oriented Design and Programming) focused on **college-level depth**, including:

* Static members
* Friend functions
* Inheritance (with multiple types)
* Virtual functions
* Templates
* Exception handling
* STL usage

---

# 🔹 UNIT 2: Constructor, Static, Friend Functions, Type Conversion

---

### ✅ Extended Constructor Example (Default, Parameterized, Copy)

```cpp
#include<iostream>
using namespace std;

class Student {
    int id;
    string name;
public:
    // Default constructor
    Student() {
        id = 0;
        name = "Not Assigned";
    }

    // Parameterized constructor
    Student(int i, string n) {
        id = i;
        name = n;
    }

    // Copy constructor
    Student(const Student &s) {
        id = s.id;
        name = s.name;
    }

    void display() {
        cout << "ID: " << id << ", Name: " << name << endl;
    }
};

int main() {
    Student s1;           // Default constructor
    Student s2(101, "Ram"); // Parameterized
    Student s3 = s2;      // Copy

    s1.display();
    s2.display();
    s3.display();
    return 0;
}
```

---

### ✅ Static Data and Function

```cpp
class Counter {
    static int count;
public:
    Counter() {
        count++;
    }
    static void showCount() {
        cout << "Count = " << count << endl;
    }
};

int Counter::count = 0;

int main() {
    Counter c1, c2, c3;
    Counter::showCount(); // Static function call
    return 0;
}
```

---

### ✅ Friend Function Example

```cpp
class Box {
    int length;
public:
    Box() { length = 10; }

    // Declare friend
    friend void printLength(Box b);
};

void printLength(Box b) {
    cout << "Length = " << b.length << endl;
}
```

---

# 🔹 UNIT 3: Inheritance & Polymorphism

---

### ✅ Multilevel Inheritance Example

```cpp
class Vehicle {
public:
    Vehicle() {
        cout << "Vehicle constructor\n";
    }
    void start() {
        cout << "Vehicle started\n";
    }
};

class Car : public Vehicle {
public:
    Car() {
        cout << "Car constructor\n";
    }
    void drive() {
        cout << "Car driving\n";
    }
};

class ElectricCar : public Car {
public:
    ElectricCar() {
        cout << "ElectricCar constructor\n";
    }
    void charge() {
        cout << "Charging battery\n";
    }
};

int main() {
    ElectricCar ec;
    ec.start();
    ec.drive();
    ec.charge();
    return 0;
}
```

---

### ✅ Virtual Function & Runtime Polymorphism

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

int main() {
    Shape* s;
    Circle c;
    s = &c;
    s->draw(); // Calls Circle's draw()
    return 0;
}
```

---

# 🔹 UNIT 4: Templates & Exception Handling

---

### ✅ Class Template – Stack Implementation

```cpp
#include<iostream>
using namespace std;

template<class T>
class Stack {
    T arr[5];
    int top;
public:
    Stack() { top = -1; }

    void push(T val) {
        if (top < 4)
            arr[++top] = val;
        else
            cout << "Stack Overflow\n";
    }

    T pop() {
        if (top >= 0)
            return arr[top--];
        else {
            cout << "Stack Underflow\n";
            return -1;
        }
    }
};

int main() {
    Stack<int> s;
    s.push(10);
    s.push(20);
    cout << "Popped: " << s.pop() << endl;
    return 0;
}
```

---

### ✅ Exception Handling – Bank Scenario

```cpp
class Bank {
    float balance;
public:
    Bank(float b) { balance = b; }

    void withdraw(float amount) {
        if (amount > balance)
            throw "Insufficient funds!";
        balance -= amount;
        cout << "Withdrawn. Balance: " << balance << endl;
    }
};

int main() {
    Bank b(5000);
    float amt;
    cout << "Enter amount to withdraw: ";
    cin >> amt;

    try {
        b.withdraw(amt);
    } catch (const char* msg) {
        cout << "Error: " << msg << endl;
    }
    return 0;
}
```

---

# 🔹 UNIT 5: STL – Containers, Iterators, Algorithms

---

### ✅ Vector Example (Insert, Erase, Traverse)

```cpp
#include<vector>
#include<iostream>
using namespace std;

int main() {
    vector<int> v = {10, 20, 30};

    v.push_back(40);
    v.insert(v.begin() + 1, 15); // Insert 15 at index 1

    v.erase(v.begin() + 2); // Erase element at index 2

    cout << "Vector contents: ";
    for (int i : v)
        cout << i << " ";
    return 0;
}
```

---

### ✅ Set Example (Sorted Unique Storage)

```cpp
#include<set>
#include<iostream>
using namespace std;

int main() {
    set<int> s = {40, 10, 30};
    s.insert(20);

    for (auto x : s)
        cout << x << " "; // Output: 10 20 30 40
    return 0;
}
```

---

### ✅ Map Example (Key-Value Storage)

```cpp
#include<map>
using namespace std;

int main() {
    map<string, int> marks;
    marks["Alice"] = 95;
    marks["Bob"] = 88;

    for (auto p : marks)
        cout << p.first << ": " << p.second << endl;
    return 0;
}
```

---

### ✅ Stack Example (STL Adapter)

```cpp
#include<stack>
#include<iostream>
using namespace std;

int main() {
    stack<int> st;
    st.push(100);
    st.push(200);
    cout << "Top: " << st.top() << endl;
    st.pop();
    cout << "After pop, Top: " << st.top() << endl;
    return 0;
}
```

---

✅ These extended code examples are now well-suited for **lab programs**, **assignments**, and **university exams** (10-mark coding questions).

Would you like me to now generate a **"one-glance revision table"** or **quick reference cheat-sheet** too?