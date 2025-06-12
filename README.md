# CIRD SUMMER INDSUTRIAL TRAINING INTERNSHIP

# DAY 3

```markdown
## Robot Operating System (ROS)

This repository summarizes key concepts and practical applications learned during an industrial training internship, focusing on the Robot Operating System (ROS). It covers foundational knowledge, installation, core concepts, and beginner tutorials.

### Table of Contents

1.  [Robot Operating System (ROS)](#1-robot-operating-system-ros)
    1.1. [Introduction to ROS](#11-introduction-to-ros)
    1.2. [Advantages and Challenges of ROS](#12-advantages-and-challenges-of-ros)
    1.3. [Core Concepts of ROS](#13-core-concepts-of-ros)
    1.4. [Essential ROS Components](#14-essential-ros-components)
    1.5. [ROS Noetic Installation on Ubuntu 20.04](#15-ros-noetic-installation-on-ubuntu-2004)
    1.6. [ROS Workspace Setup](#16-ros-workspace-setup)
    1.7. [ROS Filesystem](#17-ros-filesystem)
    1.8. [Creating ROS Packages](#18-creating-ros-packages)
    1.9. [Building ROS Packages](#19-building-ros-packages)
    1.10. [ROS Nodes](#110-ros-nodes)
    1.11. [ROS Topics](#111-ros-topics)
    1.12. [ROS Services](#112-ros-services)
    1.13. [ROS Launch Files (roslaunch)](#113-ros-launch-files-roslaunch)
    1.14. [Custom ROS Messages](#114-custom-ros-messages)

---

### 1.1. Introduction to ROS

ROS (Robot Operating System) is defined as a flexible framework for writing robot software. It provides tools, libraries, and conventions to simplify the task of creating complex and robust robot behavior.

### 1.2. Advantages and Challenges of ROS

* **Advantages**: ROS offers a rich set of capabilities such as SLAM, AMCL, and MoveIt. It includes numerous tools for debugging and visualization, such as `rqt`, `RViz`, and `Gazebo`. ROS also provides broad support for various sensors and actuators, supports multiple programming languages, features a modular design, and benefits from an active and growing community.
* **Challenges**: Key challenges in using ROS include a steep learning curve, complex robot modeling using URDF, and simulation challenges with Gazebo. Additionally, there can be a lack of real-time capabilities in some use cases and concerns regarding production-level code quality.

### 1.3. Core Concepts of ROS

ROS is structured across three levels:
1.  **Filesystem Level**: This level organizes packages, messages (`.msg`), services (`.srv`), and configuration files.
2.  **Computation Graph Level**: This level consists of Nodes, Topics, Services, the Master, Parameter Server, and Bags.
3.  **Community Level**: This level includes distributions, repositories, the wiki, forums, bug tracking systems, and Q&A sites.

### 1.4. Essential ROS Components

The essential components of ROS are:
* **Nodes**: Independent executable components.
* **Topics**: Message buses used for asynchronous communication.
* **Services**: Used for synchronous request/response communication.
* **Master**: Coordinates the system by managing registration and lookup.
* **Parameter Server**: Stores and manages configuration parameters.
* **Bag Files**: Used to record and playback messages for offline analysis.

### 1.5. ROS Noetic Installation on Ubuntu 20.04

The installation process for ROS Noetic on Ubuntu 20.04 involves several key steps:
* **Prerequisites**: Requires Ubuntu 20.04 LTS, a minimum of 15GB disk space, and an active internet connection.
* **Repository Configuration**: This step involves adding the ROS repository to your system's sources and importing the GPG key.
* **Installation**: After updating package lists, the full desktop bundle (`ros-noetic-desktop-full`) is installed.
* **Dependency Setup**: `rosdep` is initialized and updated to resolve system dependencies.
* **Environment Configuration**: The ROS setup script is permanently sourced in `~/.bashrc` to make ROS commands available in new terminals.
* **Verification**: The installation is verified by running `roscore` and installing `rosinstall` and `rosinstall_generator`.

### 1.6. ROS Workspace Setup

Setting up a Catkin workspace is fundamental for ROS development.
* **Create Catkin Workspace**: This involves creating the workspace directory structure (`~/catkin_ws/src`).
* **Build Workspace**: The workspace is initialized and built using `catkin_make` from the workspace root.
* **Source Workspace**: The workspace's setup file (`devel/setup.bash`) must be sourced to make its packages available.
* **Verify Workspace Path**: The `ROS_PACKAGE_PATH` environment variable can be checked to confirm the workspace is correctly set up.

### 1.7. ROS Filesystem

Understanding the ROS filesystem involves knowing key directories and navigation commands:
* **Key Directories**: The core ROS installation resides in `/opt/ros/noetic`, while user-developed packages are typically in `~/catkin_ws/src`.
* **Navigation Commands**:
    * `rospack find <package_name>`: Locates a package directory.
    * `roscd <package_name>`: Changes the current directory to a specified package's directory.
    * `rosls <package_name>`: Lists the contents of a package directory.

### 1.8. Creating ROS Packages

ROS packages are the fundamental units for organizing ROS software.
* **Package Structure**: A typical package includes `CMakeLists.txt` for compilation, `package.xml` for metadata and dependencies, and directories for Python nodes (`scripts/`), C++ nodes (`src/`), and custom messages (`msg/`).
* **Create New Package**: New packages are created using the `catkin_create_pkg` command, specifying the package name and its initial dependencies (e.g., `roscpp`, `rospy`, `std_msgs`).

### 1.9. Building ROS Packages

Packages in a Catkin workspace are built using `catkin_make`.
* **Build Process**: Running `catkin_make` from the workspace root compiles all packages. Specific packages can be built using `catkin_make --pkg <package_name>`.
* **Dependency Resolution**: System dependencies declared in `package.xml` can be installed using `rosdep install --from-paths src --ignore-src --rosdistro noetic -y`.

### 1.10. ROS Nodes

Nodes are independent executable components within the ROS computation graph.
* **Node Management**: Commands like `rosrun <package> <node>` are used to execute a node. `rosnode list` shows all active nodes, and `rosnode info /node_name` provides details about a specific node.
* **Python Node Template**: A basic Python node typically includes a shebang (`#!/usr/bin/env python3`), imports `rospy`, initializes the node using `rospy.init_node()`, and uses `rospy.Rate()` for controlling execution frequency within a main loop.

### 1.11. ROS Topics

Topics serve as message buses for asynchronous communication between ROS nodes. Data is published by one node to a topic and subscribed to by other nodes.
* **Diagnostic Tools**:
    * `rostopic list`: Displays all currently active topics.
    * `rostopic echo /topic_name`: Prints the messages being published on a specified topic to the console.
    * `rostopic hz /topic_name`: Shows the publishing rate (frequency) of a topic.

### 1.12. ROS Services

Services facilitate synchronous request/response communication between ROS nodes.
* **Service vs. Topic**: Unlike topics which are asynchronous and support one-to-many communication, services provide a one-to-one, on-demand interaction where a client sends a request and waits for a response from a service server.
* **Service Commands**: `rosservice list` displays all available services. `rosservice call /service_name [arguments]` is used to invoke a service with specified arguments.

### 1.13. ROS Launch Files (roslaunch)

`roslaunch` is a powerful tool used to start multiple ROS nodes, configure parameters, and manage environment variables from a single XML file.
* **Launch File Structure**: Launch files are written in XML, where `<node>` tags define the executable to run, specifying its package (`pkg`), type (executable name), and assigned `name`.
* **Launch Execution**: A launch file is executed using the command `roslaunch <package_name> <launch_file.launch>`.

### 1.14. Custom ROS Messages

Custom messages allow developers to define unique data structures tailored to their application's specific communication needs.
* **Create Custom Message**: Custom messages are defined in `.msg` files, typically placed within a `msg/` directory inside a ROS package (e.g., `float32 position float32 velocity` in `msg/MyMessage.msg`).
* **Build Configuration**: To enable the generation of source code for custom messages, modifications are required in `package.xml` (adding `message_generation` and `message_runtime` dependencies) and `CMakeLists.txt` (including `find_package(catkin COMPONENTS ... message_generation REQUIRED)` and `add_message_files()`/`generate_messages()` calls).
```

# Day4

```markdown
# C++ OOPs Concepts and Project Implementation

This repository summarizes my learning journey and practical application of Object-Oriented Programming (OOP) principles in C++. It covers foundational OOP concepts and demonstrates their use through two real-world projects.

## Table of Contents

- [1. OOPs Concepts Studied](#1-oops-concepts-studied)
  - [1.1. Introduction to OOP](#11-introduction-to-oop)
  - [1.2. Basic OOP Concepts](#12-basic-oops-concepts)
  - [1.3. Special Topics](#13-special-topics)
- [2. Projects Completed](#2-projects-completed)
  - [2.1. Project 1: Bank Account Management System](#21-project-1-bank-account-management-system)
  - [2.2. Project 2: Shape Area Calculator Using Abstraction and Polymorphism](#22-project-2-shape-area-calculator-using-abstraction-and-polymorphism)

## 1. OOPs Concepts Studied

During the first half of my session, I focused on understanding the foundational concepts of Object-Oriented Programming (OOP) in C++.

### 1.1. Introduction to OOP

* **Difference between procedural and object-oriented programming**: Explored the fundamental distinctions between these two programming paradigms.
* **Benefits of OOP**: Understood the advantages such as Modularity, Reusability, and Scalability.

### 1.2. Basic OOP Concepts

A structured summary of the core OOP concepts covered includes:

* **Class and Object**: Learned about classes as blueprints and objects as instances of real-world entities.
* **Encapsulation**: Understood the concept of wrapping data and functions into a single unit.
* **Abstraction**: Studied how to hide internal details and show only the necessary information.
* **Inheritance**: Explored the mechanism of acquiring properties and behaviors from another class.
* **Polymorphism**: Learned about the ability to use the same function in different forms.

### 1.3. Special Topics

Beyond the basics, the following special OOP topics were also covered:

* Constructor and Destructor
* Function Overloading
* Operator Overloading (introductory)
* Virtual Functions & Pure Virtual Functions
* Static Members

## 2. Projects Completed

In the second half of my session, I applied the learned OOP principles by developing two projects based on real-world scenarios.

### 2.1. Project 1: Bank Account Management System

**Objective**: To create a simple banking system that allows creating accounts, depositing and withdrawing money, and displaying account details.

**Concepts Used**:
* Classes & Objects
* Constructor Overloading
* Function Overloading (specifically `deposit()` with `int` and `float` arguments)
* Static Data Members
* Destructor

**Key Features**:
* Creation of multiple bank accounts
* Deposit & withdraw functionality
* Use of default constructor
* Static counter to track the number of accounts

### 2.2. Project 2: Shape Area Calculator Using Abstraction and Polymorphism

**Objective**: To implement an abstract base class for different geometric shapes and calculate their areas using runtime polymorphism.

**Concepts Used**:
* Abstract Class (Shape)
* Virtual Functions (`draw()`, `calculateArea()`)
* Inheritance (Circle, Rectangle derived from Shape)
* Dynamic Memory Allocation (`new`, `delete`)
* Function Overriding

**Key Features**:
* Abstract class with pure virtual functions
* Derived classes with specific implementations
* Drawing shapes and calculating their areas polymorphically
```
# DAY 5

```markdown
# Communication Protocols and Raspberry Pi I2C Implementation

This repository provides a comprehensive understanding of various digital communication protocols and demonstrates practical inter-device communication using the I2C protocol with Raspberry Pi units.

## Table of Contents

1.  [Theoretical Overview of Communication Protocols](#1-theoretical-overview-of-communication-protocols)
    1.1. [I2C (Inter-Integrated Circuit)](#11-i2c-inter-integrated-circuit)
    1.2. [UART (Universal Asynchronous Receiver/Transmitter)](#12-uart-universal-asynchronous-receivertransmitter)
    1.3. [SPI (Serial Peripheral Interface)](#13-spi-serial-peripheral-interface)
    1.4. [RS-232 (Recommended Standard 232)](#14-rs-232-recommended-standard-232)
    1.5. [RS-422 (Recommended Standard 422)](#15-rs-422-recommended-standard-422)
    1.6. [RS-485 (Recommended Standard 485)](#16-rs-485-recommended-standard-485)
2.  [Practical Implementation of I2C Communication Between Two Raspberry Pis](#2-practical-implementation-of-i2c-communication-between-two-raspberry-pis)

---

## 1. Theoretical Overview of Communication Protocols

The initial segment of the session was dedicated to an in-depth study of several fundamental digital communication protocols. Each protocol was analyzed concerning its operational principles, architecture, data transfer capabilities, and typical application domains. The following protocols were covered:

### 1.1. I2C (Inter-Integrated Circuit)

* **Nature**: Synchronous, half-duplex, multi-master/multi-slave serial bus.
* **Key Features**: Uses two wires (SDA for data, SCL for clock), supports unique device addressing, ideal for short-distance communication between integrated circuits on a PCB.
* **Applications**: Sensors (temperature, accelerometers), EEPROMs, real-time clocks.

### 1.2. UART (Universal Asynchronous Receiver/Transmitter)

* **Nature**: Asynchronous, full-duplex serial communication.
* **Key Features**: Employs two data lines (Tx for transmit, Rx for receive), relies on pre-agreed baud rates for synchronization, simple to implement for point-to-point communication.
* **Applications**: GPS modules, Bluetooth modules, serial consoles, microcontrollers communicating with PCs.

### 1.3. SPI (Serial Peripheral Interface)

* **Nature**: Synchronous, full-duplex, master-slave serial bus.
* **Key Features**: Utilizes four wires (MOSI, MISO, SCLK, SS/CS), offers high data transfer rates, highly flexible for various peripheral devices.
* **Applications**: SD cards, flash memory, LCD controllers, ADCs/DACs.

### 1.4. RS-232 (Recommended Standard 232)

* **Nature**: Asynchronous, full-duplex, point-to-point serial communication.
* **Key Features**: Older standard, uses varying voltage levels for signaling, limited speed and distance compared to newer standards.
* **Applications**: Legacy modems, printers, industrial control systems (older equipment).

### 1.5. RS-422 (Recommended Standard 422)

* **Nature**: Differential, full-duplex, multi-drop (one driver, multiple receivers) serial communication.
* **Key Features**: Employs differential signaling for enhanced noise immunity, supports longer distances and higher speeds than RS-232.
* **Applications**: Industrial automation, long-distance data acquisition, telecommunications.

### 1.6. RS-485 (Recommended Standard 485)

* **Nature**: Differential, half-duplex, multi-point serial communication.
* **Key Features**: Builds upon RS-422 with multi-point capabilities (multiple drivers and receivers), excellent noise immunity, robust for industrial environments and very long distances.
* **Applications**: Industrial control networks (PLCs, SCADA), building automation, DMX512 lighting control.

## 2. Practical Implementation of I2C Communication Between Two Raspberry Pis

The second half of the session transitioned into a practical demonstration and hands-on exercise, focusing on establishing I2C communication between two Raspberry Pi single-board computers.

* **Setup**: Two Raspberry Pi units were configured, with one designated as the I2C Master and the other as the I2C Slave. Necessary electrical connections were made between their respective I2C pins (SDA, SCL, GND).
* **Software Configuration**: The I2C interfaces on both Raspberry Pis were enabled through the `raspi-config` tool, and the required Python libraries (e.g., `smbus` or `smbus2`) were installed.
* **Code Development**: Python scripts were developed for both the Master and Slave Raspberry Pis. The Master script was programmed to send data (e.g., a simple command or a numerical value) to the Slave and subsequently read data back. The Slave script was designed to listen for incoming I2C data from the Master, process it (if required), and respond with its own data.
* **Demonstration**: Successful communication was demonstrated, showing data packets being reliably exchanged between the two Raspberry Pi units via the I2C bus. This practical exercise solidified the theoretical understanding of I2C addressing, read/write operations, and clock synchronization in a real-world embedded system context.
* This practical session effectively illustrated the capabilities and implementation nuances of I2C, reinforcing its utility for inter-device communication in embedded projects.
```
