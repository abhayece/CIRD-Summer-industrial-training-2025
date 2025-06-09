# CIRD-Summer-industrial-training-2025
# Object-Oriented Programming in C++ (OOP Module)

This module offers a comprehensive guide to Object-Oriented Programming in C++. It explains key concepts using code samples, flowcharts, comparison tables, and visualizations to enhance understanding.


## Module Type: Educational | Programming Fundamentals


## Flow of the Module

mermaid
flowchart TD
    A[Start: OOP Basics] --> B[Class and Object]
    B --> C[Encapsulation and Abstraction]
    C --> D[Inheritance and its Types]
    D --> E[Polymorphism]
    E --> F[Constructors & Destructors]
    F --> G[Pointers in OOP]
    G --> H[Friend Function & this Pointer]
    H --> I[Parameter Passing Techniques]
    I --> J[End]



## 1. Objective of OOP in C++

- Build reusable code with real-world mapping
- Enhance modularity and data security
- Promote abstraction and encapsulation
- Enable inheritance for reuse and hierarchy
- Support polymorphism for flexibility


## 2. Class and Object

cpp
class Car {
public:
    void start() {
        cout << "Car started";
    }
};

int main() {
    Car myCar;
    myCar.start();
}



## 3. Types of Inheritance in C++

mermaid
graph TD;
    A[Base Class]
    B[Single Inheritance --> Derived]
    C[Multilevel --> Derived2]
    D[Multiple --> Derived]
    E[Hierarchical --> Derived1 & Derived2]
    F[Hybrid --> Combination]
    A --> B
    B --> C
    A --> E
    A --> D



## 4. Four Pillars of OOP

| Pillar        | Description |
|---------------|-------------|
| Encapsulation | Bundling data and functions |
| Abstraction   | Hiding internal complexity |
| Inheritance   | Reusing code via hierarchy |
| Polymorphism  | One interface, many forms |


## 5. Parameter Passing in C++

| Type              | Description                        | Syntax Example        |
|-------------------|------------------------------------|-----------------------|
| Pass by Value     | Passes a copy                      | void fun(int a)     |
| Pass by Reference | Uses alias, reflects changes       | void fun(int &a)    |
| Pass by Pointer   | Uses memory address                | void fun(int *a)    |



## 6. Constructor and Destructor

cpp
class MyClass {
public:
    MyClass() { } // Default constructor
    MyClass(int x) { } // Parameterized constructor
    MyClass(const MyClass &obj) { } // Copy constructor
    ~MyClass() { } // Destructor
};




## 7. Polymorphism: Types and Differences

mermaid
flowchart LR
    A[Polymorphism] --> B[Compile-Time]
    A --> C[Run-Time]
    B --> D[Function Overloading]
    C --> E[Function Overriding]


### Comparison Table

| Feature             | Function Overloading         | Function Overriding             |
|---------------------|------------------------------|---------------------------------|
| Binding             | Compile-time                 | Run-time                        |
| Signature           | Different                    | Same                            |
| Inheritance Required| No                           | Yes                             |
| Scope               | Same class                   | Base-Derived relationship       |



## 8. Access Specifiers

| Specifier  | Scope                                      |
|------------|--------------------------------------------|
| Private    | Within the class only                      |
| Public     | Accessible from outside the class          |
| Protected  | Within class and its derived classes       |



## 9. Friend Function and this Pointer

cpp
class A {
    int data;
    friend void show(A);
};

void show(A obj) {
    cout << obj.data;
}

class B {
    int val;
public:
    void set(int val) {
        this->val = val;
    }
};



## 10. Diamond Problem in Multiple Inheritance

mermaid
graph TD;
    A[Class A]
    B[Class B inherits A]
    C[Class C inherits A]
    D[Class D inherits B and C]
    A --> B
    A --> C
    B --> D
    C --> D


**Solution**: Use virtual inheritance

cpp
class A {};
class B : virtual public A {};
class C : virtual public A {};
class D : public B, public C {};



## 11. Pie Chart: Distribution of OOP Concepts in Real-world Projects

[Placeholder: Render this with Python/Matplotlib or Google Charts]

Concept         | Percentage
----------------|------------
Encapsulation   | 30%
Inheritance     | 20%
Polymorphism    | 25%
Abstraction     | 25%



## 12. Graph: Complexity vs Reusability

mermaid
graph LR
    A[Low Abstraction] -->|Low Reuse| B[High Complexity]
    C[High Abstraction] -->|High Reuse| D[Low Complexity]
