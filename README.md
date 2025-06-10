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

# **ROS Implementation Summary**

Today marks the practical implementation of ROS concepts, bringing theoretical knowledge to life through hands-on application. This document provides a formal and comprehensive summary of the core Robot Operating System (ROS) concepts discussed, encompassing its fundamental architecture, communication mechanisms, and practical Python implementations for inter-node communication, along with diagnostic tools.

### **1\. Practical Implementation: ROS Publisher Node (`musicUpload.py`)**

The `musicUpload.py` script exemplifies a ROS publisher node, responsible for broadcasting messages onto a designated topic.

* **Purpose:** To continuously publish a string message, simulating the announcement of a new music video.  
* **Key Code Snippet:**

  
\#\!/usr/bin/env python3  
import rospy  
from std\_msgs.msg import String
def musicUpload():  
	rospy.init\_node('musicUpload', anonymous=True)  
	pub \= rospy.Publisher('T-Series', String, queue\_size=20) \# 'pub' is defined here  
	rate \= rospy.Rate(10) \# 10Hz
	\# THIS 'while' loop and its contents MUST be indented under the 'musicUpload' function  
	while not rospy.is\_shutdown():  
   	 musicPublished \= "Published a New Music Video\!\!"  
   	 pub.publish(musicPublished) \# This line now correctly accesses 'pub'  
   	 rate.sleep()  
   	 rospy.loginfo(musicPublished)  
if \_\_name\_\_ \== '\_\_main\_\_':  
    musicUpload()  


**Functionality:** The node initializes, creates a publisher for the `/TSeries` topic using the   
`std_msgs/String` message type, and then enters a loop to publish the `musicPublished` string at 10 Hz until shutdown.

### **2\. Practical Implementation: ROS Subscriber Node (`user.py`)**

The `user.py` script demonstrates a ROS subscriber node, designed to receive and process messages from a specific topic.

* **Purpose:** To subscribe to the `/TSeries` topic and print the received messages to the console.  
* **Key Code Snippet**


\#\!/usr/bin/env python3  
import rospy  
from std\_msgs.msg import String
def getdata(musicVideo):  
	\# This function is called ONLY when a message is received on the subscribed topic  
    rospy.loginfo("I watched the :: " \+ musicVideo.data)
def user():  
    rospy.init\_node('user', anonymous=True)  
    rospy.Subscriber('T-Series', String, getdata) \# Topic name: 'TSeries' \- MUST MATCH PUBLISHER  
    rospy.spin() \# Keeps the node alive and processing callback
if \_\_name\_\_ \== '\_\_main\_\_':  
    user()

### **3\. Inter-Node Communication and Debugging**

The `musicUpload.py` and `user.py` nodes exemplify the Publisher-Subscriber pattern. The publisher sends messages to the `/TSeries` topic, and the subscriber receives them from the same topic.
* Topic Name Case Sensitivity: It is crucial that the topic names used by both the publisher (`rospy.Publisher('TSeries', ...)`) and the subscriber (`rospy.Subscriber('TSeries', ...)`) match exactly, including capitalization. A mismatch will prevent communication.  
* `rqt_graph`: A powerful visualization tool used to inspect the ROS computation graph. It graphically displays running nodes and the topics/services connecting them, providing an invaluable aid in understanding and debugging ROS systems. By running `rqt_graph` alongside active publisher and subscriber nodes, one can visually confirm the `/musicUpload` node publishing to `/TSeries` and the `/user` node subscribing to it.  
* `rostopic echo /<topic_name>`: A command-line tool used to display messages being published on a specific topic in real-time. This is essential for verifying that a publisher is actually sending messages to the ROS system.

### **4 . Contextual Example: Turtle Motion in a Single Frame (`turtlesim`)**

The `turtlesim` package provides a simple 2D simulation environment, often used for introductory ROS tutorials.
* Coordinate System: The turtle operates within a single 2D coordinate **frame.**  
* Motion Control: Turtle motion is typically controlled by publishing `geometry_msgs/Twist` messages to its command velocity topic (e.g., `/turtle1/cmd_vel`).  
* `linear` component: Defines movement along the X, Y, and Z axes (for a 2D turtle, typically X for forward/backward).  
* `angular` component: Defines rotational movement around the X, Y, and Z axes (for a 2D turtle, typically Z for turning). By continuously sending `Twist` messages with appropriate linear and angular velocities, one can direct the turtle's movement within its single frame.  
    



**5\. Implementation of Alphabet ‘A’ using Turtlesim code**

The implementation of drawing the letter 'A' in Turtlesim utilizes a ROS Python script that precisely controls the turtle's movements. It leverages `geometry_msgs/Twist` messages for linear and angular velocity commands to draw lines. Crucially, the code employs `turtlesim.srv.TeleportAbsolute` to move the turtle to specific coordinates without drawing, ensuring clean, distinct lines for each segment of the 'A'. Additionally, `turtlesim.srv.SetPen` is used to control when the turtle draws, allowing for accurate repositioning between drawing the two legs and the crossbar of the letter.

**Code:-** 

\#\!/usr/bin/env python3
import rospy  
from geometry\_msgs.msg import Twist \# For publishing velocity commands  
from turtlesim.srv import TeleportAbsolute \# For precise positioning  
from turtlesim.srv import SetPen \# To control pen visibility (optional but useful)  
from std\_srvs.srv import Empty \# For services with no arguments, like /clear  
import math  
import time
\# Global publisher for velocity commands  
cmd\_vel\_publisher \= None
\# Global service proxies for teleportation and pen control  
teleport\_client \= None  
set\_pen\_client \= None
def init\_turtle\_services():  
	"""Initializes ROS service proxies for turtlesim."""  
	global teleport\_client, set\_pen\_client
	rospy.loginfo("Waiting for /turtle1/teleport\_absolute service...")  
	rospy.wait\_for\_service('/turtle1/teleport\_absolute')  
	teleport\_client \= rospy.ServiceProxy('/turtle1/teleport\_absolute', TeleportAbsolute)  
	rospy.loginfo("Teleport service ready.")
	rospy.loginfo("Waiting for /turtle1/set\_pen service...")  
	rospy.wait\_for\_service('/turtle1/set\_pen')  
	set\_pen\_client \= rospy.ServiceProxy('/turtle1/set\_pen', SetPen)  
	rospy.loginfo("SetPen service ready.")
def set\_pen(on=True):  
	"""Controls the turtle's pen visibility. Set to True for pen down (draw), False for pen up (don't draw)."""  
	if set\_pen\_client:  
    	\# r, g, b, width, off  
    	\# If 'on' is True, off=0 (pen is down). If 'on' is False, off=1 (pen is up).  
    	set\_pen\_client(0, 0, 0, 2, 0 if on else 1\) \# Black color, width 2  
    	time.sleep(0.1) \# Small delay for service call to process  
	else:  
    	rospy.logwarn("SetPen service not initialized.")
def rotate(pub, angle\_degree, speed=60): \# Increased default speed for faster turns  
	"""  
	Rotates the turtle by a given angle in degrees.  
	:param pub: The rospy.Publisher for /turtle1/cmd\_vel.  
	:param angle\_degree: Angle to rotate in degrees (positive for CCW, negative for CW).  
	:param speed: Angular speed in degrees/sec.  
	"""  
   v \= Twist()  
	angular\_speed\_rad\_s \= math.radians(abs(speed))  
	angle\_rad \= math.radians(abs(angle\_degree))

	v.angular.z \= angular\_speed\_rad\_s if angle\_degree \> 0 else \-angular\_speed\_rad\_s  
	t0 \= time.time()  
	duration \= angle\_rad / angular\_speed\_rad\_s

	while (time.time() \- t0) \< duration:  
    	pub.publish(v)  
    	rospy.sleep(0.01) \# Small sleep to ensure continuous publishing
	v.angular.z \= 0 \# Stop rotation  
	pub.publish(v)  
	rospy.sleep(0.2) \# Short pause after stopping
def move\_forward(pub, distance, speed=1.5):  
	"""  
	Moves the turtle forward by a given distance.  
	:param pub: The rospy.Publisher for /turtle1/cmd\_vel.  
	:param distance: Distance to move in units (positive for forward, negative for backward).  
	:param speed: Linear speed in units/sec.  
	"""  
	v \= Twist()  
	v.linear.x \= speed if distance \> 0 else \-speed  
	t0 \= time.time()  
	duration \= abs(distance / speed)
	while (time.time() \- t0) \< duration:  
    	pub.publish(v)  
    	rospy.sleep(0.01) \# Small sleep to ensure continuous publishing
	v.linear.x \= 0 \# Stop linear movement  
	pub.publish(v)  
	rospy.sleep(0.2) \# Short pause after stopping
def draw\_A(pub):  
	"""  
	Draws the letter 'A' with precise movements and teleportation.  
	Adjust these coordinates as needed for your desired size/position on the 11x11 turtlesim window.  
	"""  
	rospy.loginfo("Starting to draw letter 'A'...")
	\# Define key points for 'A' geometry  
	\# Example: Base width 2 units, height 3 units  
	base\_y \= 3.0   	\# Y-coordinate of the base of the 'A'  
	peak\_y \= base\_y \+ 3.0 \# Y-coordinate of the peak of the 'A'  
	center\_x \= 5.5 	\# X-coordinate for the center of the 'A'  
	half\_base\_width \= 1.0 \# Half the width of the base (so total width is 2 \* 1.0 \= 2.0 units)
	\# Calculate X-coordinates for the base points  
	bottom\_left\_x \= center\_x \- half\_base\_width  
	bottom\_right\_x \= center\_x \+ half\_base\_width
	\# Crossbar height (e.g., 1.5 units from base)  
	crossbar\_y \= base\_y \+ 1.5  
	\# Calculate X-coordinates for crossbar ends based on the slope of the legs  
	\# Slope of the left leg (from bottom-left to peak)  
	\# m\_leg \= (peak\_y \- base\_y) / (center\_x \- bottom\_left\_x) \= 3.0 / 1.0 \= 3.0  
	\# X-coordinate on the left leg at crossbar\_y  
	crossbar\_start\_x \= bottom\_left\_x \+ (crossbar\_y \- base\_y) / 3.0  
	\# X-coordinate on the right leg at crossbar\_y (symmetric)  
	crossbar\_end\_x \= center\_x \+ (center\_x \- crossbar\_start\_x)
	\# Calculate leg length using Pythagorean theorem  
	leg\_length \= math.sqrt((half\_base\_width)\*\*2 \+ (peak\_y \- base\_y)\*\*2)
	\# 1\. Draw Left Leg  
	rospy.loginfo("Drawing left leg...")  
	\# Teleport to bottom-left of 'A', facing towards the peak  
	\# atan2(dy, dx) gives angle from x-axis. Here, dy \= peak\_y \- base\_y, dx \= center\_x \- bottom\_left\_x  
	target\_angle\_left\_leg \= math.atan2(peak\_y \- base\_y, center\_x \- bottom\_left\_x)  
	teleport\_client(bottom\_left\_x, base\_y, target\_angle\_left\_leg)  
	set\_pen(True) \# Pen down to draw  
	move\_forward(pub, leg\_length)  
	set\_pen(False) \# Pen up after drawing
	\# 2\. Draw Right Leg  
	rospy.loginfo("Drawing right leg...")  
	\# Teleport to bottom-right of 'A', facing towards the peak  
	target\_angle\_right\_leg \= math.atan2(peak\_y \- base\_y, center\_x \- bottom\_right\_x)  
	teleport\_client(bottom\_right\_x, base\_y, target\_angle\_right\_leg)  
	set\_pen(True) \# Pen down to draw  
	move\_forward(pub, leg\_length)  
	set\_pen(False) \# Pen up
	\# 3\. Draw Crossbar  
	rospy.loginfo("Drawing crossbar...")  
	\# Teleport to the starting point of the crossbar (on the left leg)  
	teleport\_client(crossbar\_start\_x, crossbar\_y, 0.0) \# Face right (0.0 radians)  
	set\_pen(True) \# Pen down to draw  
	move\_forward(pub, crossbar\_end\_x \- crossbar\_start\_x) \# Move horizontally for crossbar length  
	set\_pen(False) \# Pen up
	rospy.loginfo("Finished drawing letter 'A'.")
	\# Keep the node alive until manually shut down  
	rospy.spin()
def main():  
	"""Main function to initialize ROS and start drawing."""  
	global cmd\_vel\_publisher  
	rospy.init\_node('turtle\_draw\_A', anonymous=True)  
	cmd\_vel\_publisher \= rospy.Publisher('/turtle1/cmd\_vel', Twist, queue\_size=10)
	\# Initialize service proxies  
	init\_turtle\_services()
	\# Clear turtlesim background for a fresh drawing  
	rospy.loginfo("Clearing turtlesim background...")  
	clear\_client \= rospy.ServiceProxy('/clear', Empty) \# Corrected service proxy for /clear  
	try:  
    	clear\_client()  
    	rospy.loginfo("Background cleared.")  
	except rospy.ServiceException as e:  
    	rospy.logerr(f"Service call to /clear failed: {e}. Ensure turtlesim\_node is running.")
	\# Ensure pen is up before initial teleport to the first drawing point  
	set\_pen(False)  
	rospy.sleep(0.5) \# Give services a moment to process
	draw\_A(cmd\_vel\_publisher)
if \_\_name\_\_ \== '\_\_main\_\_':  
	try:  
    	main()  
	except rospy.ROSInterruptException:  
    	rospy.loginfo("Drawing process interrupted.")


   




