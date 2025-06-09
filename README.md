# CIRD-Summer-industrial-training-2025

# Object-Oriented Programming (OOP) in C++ - A Summary

Object-Oriented Programming (OOP) is a programming paradigm that organizes software design around data, or objects, rather than functions and logic. In C++, OOP is a fundamental aspect that allows for the creation of modular, reusable, and scalable code.

## Core Concepts (The Pillars of OOP in C++)

C++ fully supports the four primary pillars of OOP:

### 1. Encapsulation
* **Definition:** The bundling of data (member variables) and the functions (member methods) that operate on that data into a single unit, known as a `class`. It also involves restricting direct access to some of an object's components to prevent unintended modification.
* **C++ Implementation:**
    * Achieved using **access specifiers**:
        * `public`: Members are accessible from anywhere.
        * `private`: Members are only accessible from within the same class. This is typically used for data hiding.
        * `protected`: Members are accessible within the same class and by derived classes.
    * Example:
      ```cpp
      class Car {
      private:
          std::string model; // Data is private
          int speed;
      public:
          void accelerate() { // Method to operate on data
              speed += 10;
          }
          std::string getModel() { // Public method to access private data
              return model;
          }
      };
      ```
* **Benefit:** Data security, improved code organization, and easier maintenance.

### 2. Abstraction
* **Definition:** Showing only essential features of an object to the outside world and hiding the complex implementation details. In C++, this is often achieved through interfaces and abstract classes.
* **C++ Implementation:**
    * **Abstract Classes:** Classes that contain at least one pure virtual function (a virtual function declared with `= 0`). You cannot create objects of an abstract class.
      ```cpp
      class Shape { // Abstract Class
      public:
          virtual void draw() = 0; // Pure virtual function
          void getDescription() {
              std::cout << "This is a generic shape." << std::endl;
          }
      };
      ```
    * **Header Files:** Often used to expose class interfaces (`.h` or `.hpp` files) while hiding implementation details in source files (`.cpp`).
* **Benefit:** Reduces complexity, improves readability, and makes systems easier to design and manage.

### 3. Inheritance
* **Definition:** A mechanism where a new class (derived class or child class) can acquire properties (member variables) and behaviors (member methods) from an existing class (base class or parent class). This promotes code reusability and establishes an "is-a" relationship.
* **C++ Implementation:**
    * Uses the colon (`:`) followed by an access specifier (`public`, `protected`, `private`) for the base class.
    * Example:
      ```cpp
      class Vehicle { // Base class
      public:
          void start() { std::cout << "Vehicle started." << std::endl; }
      };

      class Car : public Vehicle { // Derived class, public inheritance
      public:
          void drive() { std::cout << "Car is driving." << std::endl; }
      };
      ```
    * **Types of Inheritance:** Single, Multiple (using comma-separated base classes), Multilevel, Hierarchical, Hybrid.
* **Benefit:** Code reusability, reduced redundancy, and support for runtime polymorphism.

### 4. Polymorphism
* **Definition:** The ability of an object to take on many forms. In C++, it refers to the ability to define one interface and have multiple implementations.
* **C++ Implementation:**
    * **Compile-time Polymorphism (Static Polymorphism):**
        * **Function Overloading:** Multiple functions with the same name but different parameters (number, type, or order).
        * **Operator Overloading:** Defining how operators (like `+`, `-`, `*`) behave for user-defined types.
        * **Templates:** Allows writing generic code that works with different data types.
    * **Runtime Polymorphism (Dynamic Polymorphism):**
        * Achieved through **virtual functions** and **pointers/references to base class objects**.
        * When a virtual function is called through a base class pointer or reference, the actual function executed is determined at runtime based on the type of the object pointed to.
        * Example:
          ```cpp
          class Animal {
          public:
              virtual void makeSound() { // Virtual function
                  std::cout << "Animal makes a sound." << std::endl;
              }
          };

          class Dog : public Animal {
          public:
              void makeSound() override { // Overrides base class virtual function
                  std::cout << "Woof!" << std::endl;
              }
          };

          class Cat : public Animal {
          public:
              void makeSound() override {
                  std::cout << "Meow!" << std::endl;
              }
          };

          // In main:
          // Animal* animalPtr1 = new Dog();
          // Animal* animalPtr2 = new Cat();
          // animalPtr1->makeSound(); // Calls Dog::makeSound()
          // animalPtr2->makeSound(); // Calls Cat::makeSound()
          ```
* **Benefit:** Flexibility, extensibility, and cleaner, more readable code that can adapt to different object types.

## Additional C++ OOP Concepts

* **Classes and Objects:**
    * **Class:** A blueprint or a template for creating objects. It defines the structure (data members) and behavior (member functions) that objects of that class will have.
    * **Object:** An instance of a class. When a class is defined, no memory is allocated until an object of that class is created.
* **Constructors:** Special member functions that are automatically called when an object of a class is created. They are used to initialize the object's data members.
    * Default Constructor, Parameterized Constructor, Copy Constructor.
* **Destructors:** Special member functions that are automatically called when an object is destroyed (goes out of scope or is explicitly deleted). They are used to perform cleanup tasks, such as releasing dynamically allocated memory.
* **`this` Pointer:** A pointer that refers to the current object. It is implicitly passed to all non-static member functions.
* **`static` Members:**
    * **Static Data Members:** Shared by all objects of the class; only one copy exists for the entire class.
    * **Static Member Functions:** Can only access static data members and static member functions. They can be called without creating an object of the class.
* **Friend Functions and Friend Classes:**
    * **Friend Function:** A non-member function that has special permission to access `private` and `protected` members of a class.
    * **Friend Class:** A class whose member functions are allowed to access the `private` and `protected` members of another class. Use sparingly as they violate encapsulation.
* **Operator Overloading:** Allows you to redefine the meaning of operators (e.g., `+`, `-`, `<<`, `>>`) for user-defined types. This makes code more intuitive and readable when working with objects.
* **Virtual Destructors:** Essential when dealing with polymorphism and inheritance. If you `delete` a base class pointer that points to a derived class object, and the base class destructor is not virtual, the derived class's destructor will not be called, leading to memory leaks.

## Advantages of OOP in C++

* **Modularity:** Code is organized into self-contained objects, making it easier to manage.
* **Reusability:** Inheritance promotes code reuse, reducing development time and effort.
* **Maintainability:** Encapsulation and abstraction make code easier to understand, debug, and modify.
* **Scalability:** Well-designed OOP systems can be easily extended and scaled for larger projects.
* **Flexibility:** Polymorphism allows for more flexible and adaptable code.
* **Improved Software Design:** Encourages a more structured and logical approach to problem-solving by modeling real-world entities.

## Disadvantages of OOP in C++ (General OOP considerations)

* **Steeper Learning Curve:** Can be more complex to grasp for beginners due to its multiple concepts.
* **Increased Overhead:** May introduce slight performance overhead in some cases (e.g., virtual function calls) compared to pure procedural programming.
* **Larger Program Size:** Can sometimes result in larger executable files due to added abstraction.

---

Understanding these OOP concepts in C++ is crucial for writing robust, efficient, and maintainable software.




# Introduction to ROS - Chapter 1 Summary

[cite_start]This document summarizes Chapter 1 from the book *Mastering ROS for Robotics Programming, Second Edition*. [cite_start]The chapter introduces the Robot Operating System (ROS), its advantages, basic architecture, and key concepts.

## Why Learn ROS?

[cite_start]ROS (Robot Operating System) is a flexible framework for writing robot software. [cite_start]It provides tools, libraries, and conventions to simplify the task of creating complex and robust robot behavior.

### Advantages of ROS 
* **Rich set of capabilities:** Includes functionalities like SLAM (Simultaneous Localization and Mapping), AMCL (Adaptive Monte Carlo Localization), and MoveIt (for motion planning).
* **Numerous tools:** Provides powerful tools for debugging and visualization such as `rqt`, `RViz`, and `Gazebo`.
* **Broad support:** Offers extensive support for various sensors and actuators.
* **Multi-language support:** Designed with modularity and supports multiple programming languages.
* **Active and growing community:** Benefits from a large and supportive community.

### Challenges in Using ROS 
* **Steep learning curve:** Can be challenging for new users to master.
* **Complex robot modeling:** URDF (Unified Robot Description Format) for robot modeling can be intricate.
* **Simulation challenges:** Working with Gazebo for simulation can sometimes present difficulties.
* **Lack of real-time capabilities:** Not inherently real-time in some use cases, which can be a concern for applications requiring strict timing.
* **Concerns with production-level code quality:** Some aspects may require careful consideration for robust production deployments.

## Core Concepts of ROS

ROS is structured across three distinct levels:

1.  [cite_start]**Filesystem Level:** Organizes packages, messages (`.msg`), services (`.srv`), and configuration files.
2.  [cite_start]**Computation Graph Level:** Comprises Nodes, Topics, Services, the Master, Parameter Server, and Bags.
3.  [cite_start]**Community Level:** Encompasses distributions, repositories, the wiki, forums, bug tracking systems, and Q&A sites.

### Essential ROS Components 
* **Nodes:** Independent executable components that perform computation.
* **Topics:** Message buses used for asynchronous, many-to-many communication between nodes.
* **Services:** Provide synchronous, request/response communication between nodes.
* **Master (ROS Master):** Coordinates the entire ROS system by managing the registration and lookup of nodes, topics, and services.
* **Parameter Server:** Stores and manages configuration parameters accessible by all nodes.
* **Bag Files:** Used to record and playback message data for offline analysis and debugging.


**Topic 1: Installing ROS Noetic on Ubuntu 20.04**

