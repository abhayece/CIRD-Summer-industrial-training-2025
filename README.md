# *CIRD INDUSTRIAL TRAINING*  
## *Version Control with Git*
<br>

### *Terminal & Git Basics*
 
- *git clone* – Copies a remote repository to your local system.  
- *git status* – Shows modified, staged, and untracked files.

- *git add* – Stages files for the next commit.  
- *git commit -m ""* – Records a snapshot of staged changes.  
- *git diff* – Displays changes between working directory and staging.

- *git log* – Lists commits in reverse chronological order.  
- *git show* – Shows details of a specific commit.  
- *git log --stat* – Displays modified files and line changes per commit.

<br>

### *Branching, Tagging & Merging*

- *Tagging:*  
  Use *git tag* to label specific commits (commonly for releases).

- *Branching:*  
  Create branches with *git branch, and switch using *git switch* or *checkout**.  
  Branches allow isolated feature development without affecting the main codebase.

- *Merging:*  
  Use *git merge* to bring changes from one branch into another.  
  Git auto-merges when possible, but may require resolving conflicts.

<br>

### *Undoing Changes*

- *git commit --amend* – Updates the last commit (before pushing).  
- *git revert* – Creates a new commit that reverses changes without altering history.  
- *git reset* – Rewrites commit history; use cautiously:
  - *--soft* – Keeps changes staged.  
  - *--mixed* – Unstages changes but retains them in files.  
  - *--hard* – Removes all changes post-reset.

<br>

## *Introduction to Linux and CLI*  
<br>

### *Navigating Linux & Managing Files*

- *File System Hierarchy:*
  - / — Root directory (like the main door)
  - /home — Personal user folders
  - /bin — Essential binaries (e.g., ls, cp)
  - /etc — Configuration files
  - /usr — Installed apps and data
  - /tmp, /var, /root, /dev, /mnt, /proc — Special use directories

- *File Types in Linux (via ls -l):*
  - - Regular files, d Directories, l Symbolic links, c Character devices, b Block devices

- *User Permissions:*
  - chmod – Change permissions (symbolic or numeric, e.g., chmod 755 file.sh)
  - chown – Change file ownership
  - Permission types: r (read), w (write), x (execute)

<br>

### *Power Tools: Searching & Shell Scripts*

- *Searching:*
  - find – Locate files by name/type/size/date
    - Examples:  
      find . -name "file.txt"  
      find / -size +100M  
      find . -name "*.log" -exec rm {} \;
  - grep – Search inside files
    - Examples:  
      grep -i "linux" notes.txt  
      grep -rn "error" /var/log

- *Shell Scripting Basics:*
  - A *script* is a list of commands saved in a file (.sh).
  - Start with #!/bin/bash (shebang)
  - Use variables, conditions, and logic:
    bash
    #!/bin/bash
    name="CDC"
    echo "Hello, $name"
    if [ "$name" == "CDC" ]; then
      echo "Welcome!"
    else
      echo "Not CDC"
    fi
    
  - *Create & run a script:*
    bash
    nano myscript.sh       # create file
    chmod +x myscript.sh   # make executable
    ./myscript.sh          # run it
    
<br>

##  Introduction to ROS (Robot Operating System)

ROS is a flexible framework for writing robot software. It provides tools, libraries, and conventions to simplify the task of creating complex and robust robotic behavior across a wide variety of robotic platforms.

---

### Why ROS?

- *High-end capabilities*: Built-in packages like SLAM, AMCL, and MoveIt.
- *Powerful tools*: Includes rqt_gui, RViz, Gazebo for debugging and simulation.
- *Sensor & actuator support*: Supports LIDAR, Kinect, DYNAMIXEL, and more.
- *Language flexibility*: Develop nodes in C++, Python, or Java.
- *Modular architecture*: Each node is isolated and independently recoverable.
- *Concurrent processing*: Multiple nodes can subscribe to the same topic.

---

### ROS Filesystem Structure

- *config/* – Configuration files (params, settings)
- *include/* – Header files (for C++ packages)
- *script/* – Python scripts
- *src/* – C++ source code
- *launch/* – .launch files to start ROS nodes
- *msg/* – Custom message definitions
- *srv/* – Service definitions
- *action/* – Action definitions (goal-based operations)
- *package.xml* – Metadata and dependencies
- *CMakeLists.txt* – Build configuration

---

### Core Concepts

- *Packages*: Unit of software in ROS.
- *Metapackages*: Grouping of related packages.
- *Messages (.msg)*: Data format for node communication.
- *Services (.srv)*: Request-response communication.

---

### ROS Computation Graph

- *Nodes*: Independent processes performing tasks.
- *Master*: Registers nodes and manages naming.
- *Parameter Server*: Shared config storage.
- *Topics*: Publish/subscribe messaging system.
- *Services*: Synchronous communication (function-call style).
- *Bagfiles*: Record and playback of ROS data.

---

###  Starting ROS

Before running nodes:
bash
roscore


## OOPs Concepts

### Introduction to Object-Oriented Programming
OOPS (Object-Oriented Programming System) is a programming paradigm based on objects and classes, emphasizing encapsulation, inheritance, abstraction, and polymorphism.

### Core Concepts
1. *Class*: Blueprint for creating objects (defines attributes and methods)
2. *Object*: Instance of a class with state (attributes) and behavior (methods)
3. *Encapsulation*: Binding data and methods together while hiding internal details
4. *Abstraction*: Showing only essential features and hiding implementation
5. *Inheritance*: Child class acquiring properties of parent class (promotes code reuse)
6. *Polymorphism*: 
   - Compile-time (Method Overloading)
   - Runtime (Method Overriding)
7. *Constructors*:
   - Special methods for object initialization
   - Types: Shallow copy and Deep copy
8. *Destructor*: Method called when object is destroyed to free resources

### Access Specifiers
- public: Accessible everywhere
- private: Accessible only within class
- protected: Accessible in derived classes

## Communication Protocols

---

## Core Protocols

### I2C (Inter-Integrated Circuit)

- *Wiring: Uses 2 wires – **SDA (data)* and *SCL (clock)*
- *Topology: Supports **multi-master* and *multi-slave* setup
- *Speed: Up to **3.4 Mbps* (high-speed mode)
- *Communication Type: **Half-duplex*
- *Applications: Commonly used for **sensors, **RTC, **EEPROM*

---

### SPI (Serial Peripheral Interface)

- *Wiring: Uses 4 wires – **MOSI, **MISO, **SCLK, and **SS*
- *Topology: **Master-slave*
- *Speed: Up to **10+ Mbps*
- *Communication Type: **Full-duplex*
- *Applications: Ideal for **displays, **flash memory, **ADCs*

---

### UART (Universal Asynchronous Receiver/Transmitter)

- *Wiring: 2 wires – **TX (Transmit)* and *RX (Receive)*
- *Topology: **Point-to-point*
- *Clocking: **Asynchronous* (no clock line)
- *Speed: Typically ≤ **1 Mbps*
- *Communication Type: **Full-duplex*
- *Applications: Used in **debugging, **GPS modules, **serial console*

---

### RS485

- *Wiring: Uses differential pair – **A and B*
- *Topology: **Multi-point bus* (multiple devices on the same line)
- *Speed: Up to **10 Mbps* over short distances
- *Communication Type: **Half-duplex*
- *Applications: Industrial use – **PLCs, **automation, **SCADA*

---

##   Key Features Summary

| Protocol | Addressing | Duplex Type | Clock Line | Speed          | Common Uses                          |
|----------|------------|-------------|------------|----------------|--------------------------------------|
| I2C      | Yes (7/10-bit) | Half       | Yes        | ≤ 3.4 Mbps     | Sensors, RTC, EEPROM                 |
| SPI      | No (uses SS lines) | Full   | Yes        | ≥ 10 Mbps      | Displays, Flash, ADCs                |
| UART     | No         | Full         | No         | ≤ 1 Mbps       | Debugging, Serial Console, GPS       |
| RS485    | No         | Half         | No         | ≤ 10 Mbps      | Industrial Systems, Long-Distance    |

---
<br>

##   ROS Tutorials

### Creating a publisher/subscriber
* catkin\_create\_pkg \<pkg\_name\> roscpp std\_msgs: Create a ROS package with dependencies.  
* roscd \<pkg\_name\>/src: Navigate to the package source directory.  
* rosrun \<pkg\_name\> \<node\_name\>: Run the publisher/subscriber node.
### Examining the Simple Publisher and Subscriber
* rostopic list: List active topics.  
* rostopic echo /topic\_name: Display messages published on a topic.  
* rosnode info /node\_name: Get details about a running node.
### Writing a Simple Service and Client (C++)
* rossrv show \<srv\_type\>: Inspect a service message structure.  
* rosservice call /service\_name args: Manually call a service with arguments.
### Examining the Simple Service and Client
* rosservice list: List active services.  
* rosservice type /service\_name: Check the type of a service.
### Recording and Playing Back Data
* rosbag record \-O \<file\_name\> /topic1 /topic2: Record topics to a bag file.  
* rosbag play \<file\_name\>.bag: Play back recorded data.
### Getting Started with roswtf
* Roswtf: Run a general system check.  
* roswtf \-r: Check for runtime issues.
### Navigating the ROS Filesystem
* rospack find \<pkg\_name\>: Locate a package’s directory.  
* roscd \<pkg\_name\>: Navigate to a package.  
* rosls \<pkg\_name\>: List package contents.
### Understanding ROS nodes
* rosrun \<pkg\_name\> \<node\_name\>: Start a node.  
* rosnode list: List running nodes.  
* rosnode ping /node\_name: Test node connectivity.
---
<br>


## Embedded Systems & Hardware Platforms

### Platform Overview

- *Microcontroller*: Single chip with CPU, RAM, ROM, and I/O. Real-time support, low power. Example: Arduino, STM32.
- *Microprocessor*: CPU-only chip needing external RAM and I/O. High speed, high power. Used in desktops/laptops.
- *Raspberry Pi*: Small Linux-based computer with GPIO, USB, HDMI, etc. Good for IoT and prototyping.
- *Jetson Nano*: NVIDIA single-board computer with GPU and ML libraries. Suitable for AI, vision, edge computing.

### Comparison Table

| Feature             | Microcontroller       | Microprocessor        | Raspberry Pi           | Jetson Nano             |
|---------------------|------------------------|------------------------|-------------------------|--------------------------|
| Integration         | CPU + RAM + I/O        | CPU only               | CPU + RAM + I/O + OS    | CPU + GPU + RAM + OS     |
| Operating System    | No                     | Yes (external RAM)     | Yes (Raspberry Pi OS)   | Yes (Ubuntu JetPack)     |
| Power Consumption   | Very Low               | High                   | Medium                  | Medium-High              |
| Real-time Support   | Yes                    | Limited                | No                      | No                       |
| Best Use Case       | Control, sensors       | General-purpose tasks  | IoT, prototyping        | AI, ML, vision tasks      |

### Sensor Matching

- *Basic Sensors (Ultrasonic, PIR)*: Best with Microcontrollers, compatible with Raspberry Pi and Jetson Nano.
- *Camera for AI*: Use Jetson Nano; Raspberry Pi supports basic usage; not suitable for microcontrollers.
- *Advanced AI Sensors*: Only Jetson Nano handles them efficiently.

### Application Examples

- Weather Station → Raspberry Pi with DHT11/BMP180  
- Smart Security Camera → Jetson Nano with PIR + Camera + Mic

### Selection Guide

- Use *Microcontrollers* for real-time, low-power tasks.
- Use *Raspberry Pi* for multitasking and moderate sensor integration.
- Use *Jetson Nano* for AI, image processing, and GPU-intensive applications.
---
<br>


## ROS Intermediate Tutorials

### Creating a ROS Package Manually

- Use catkin_create_pkg or manually create CMakeLists.txt, package.xml, and source directories.
- Define dependencies clearly in package.xml and find_package() in CMakeLists.txt.

### Managing System Dependencies with rosdep

- Use rosdep install to automatically install system dependencies listed in package.xml.
- Ensures cross-platform compatibility and ease of deployment.

### roslaunch Tips for Large Projects

- Use <arg> and <param> to make launch files reusable.
- Group related nodes using <group>, and manage namespaces to avoid topic conflicts.
- Set required="true" to ensure critical nodes terminate the launch if they fail.

### Nodelets

- Lightweight nodes that share the same process and memory space.
- Reduce overhead from message passing and are suitable for high-frequency data (e.g., image processing).
- Use the nodelet package and load via nodelet manager.

### roswtf: Debugging Tool

- roswtf analyzes your ROS environment and provides warnings/errors.
- Useful for checking bad configurations, multiple node registrations, or network issues.

### Topic Tools

- Tools like throttle, relay, drop, and mux allow advanced topic-level control.
- Example: rosrun topic_tools throttle messages /input_topic 10.0 limits the topic rate to 10 Hz.

### Recording and Playing Back Data (rosbag)

- Record data: rosbag record -a (records all topics).
- Play data: rosbag play filename.bag.
- Useful for debugging and offline testing.

### Namespaces, tf Prefixes, and Node Remapping

- Namespaces prevent topic clashes in multi-robot setups.
- Use tf_prefix to isolate coordinate frames.
- Use rosrun package node _param:=value or remap topics with :=.

### rqt: GUI Toolset

- Modular GUI for visualization and debugging (e.g., rqt_graph, rqt_plot, rqt_console).
- Extendable via plugins.

### Intermediate-Level Summary Table

| Feature               | Description                                                               |
|------------------------|---------------------------------------------------------------------------|
| Package Management     | catkin_create_pkg, rosdep for dependencies                           |
| Launch Configuration   | Modular launch files with arguments and groups                           |
| Nodelets               | Efficient, memory-sharing components                                     |
| Debugging              | roswtf for environment checks                                           |
| Topic Tools            | Modify, throttle, relay, or multiplex topics                             |
| Data Logging           | rosbag to record and replay topics                                     |
| Namespaces             | Organize topics/frames in large systems                                  |
| Visualization          | rqt tools for live monitoring and debugging                            |


---

### *Industrial Visit – CIRD Lab*

As part of the Summer Industrial Training, we visited the *Center for Innovation, Research, and Development (CIRD)*. The visit provided valuable insight into cutting-edge research and industrial automation practices.  
- Observed *real-time applications* of *autonomous robotics, **embedded systems, and **IoT-enabled devices* in production environments  
- Demonstrations included *ROS-based robots, **sensor fusion, **cloud-integrated control systems, and **edge computing with Jetson Nano*  
- Gained exposure to *LiDAR-based navigation, **thermal imaging, **motor control mechanisms, and **live telemetry dashboards*  
- The visit bridged the gap between theoretical learning and practical implementation, helping us understand how software and hardware interact in real-world systems  

---

### *Project – Mobile Interface for Live Robot Control*

Led the development of a cross-platform mobile interface to *remotely control an inspection robot* and *stream live annotated video* with sensor feedback.  
- *Frontend (React Native + Expo)*: Real-time MJPEG video decoding, dynamic robot status panel (battery, GPS, time), manual joystick control, and Google Maps integration  
- *Backend (Express.js + MongoDB Atlas)*: Receives annotated video frames and sensor data from Jetson Nano, logs values in real time, and exposes API endpoints for app access  
- *Hardware Integration*: ROSBridge + custom CSV data transfer for camera, thermal sensor, GPS, and motor control via Jetson Nano  
- *Use Case: Enables **remote industrial monitoring*, especially in areas unsafe for human inspection, with visual + telemetry intelligence  
- Focused on seamless UX, cloud sync, and fault-tolerant communication between robot and app  

---

### *Intel Unnati AI Workshop*

Successfully completed the *Intel Unnati Workshop on AI & ML, hosted in collaboration with **EdGate Technologies* and *Intel Corporation*. The workshop was a deep dive into both theoretical and practical aspects of AI development.  
- *Core Concepts*:  
  - Math: Linear Algebra (dot product, eigenvalues), Statistics (mean, variance), Probability  
  - ML Models: Linear/Polynomial Regression, SVM, Decision Trees, Naive Bayes, K-Means  
  - DL Models: Neural Networks, Activation Functions, Optimizers, Backpropagation  
- *Hands-On Projects*:  
  - *House Price Prediction* – Trained regression models to predict real estate values  
  - *PIMA Diabetes Detection* – Built classifiers using logistic regression & SVM  
  - *Customer Segmentation* – Unsupervised clustering with K-Means & DBSCAN  
  - *Digit Recognition* – Built a CNN using TensorFlow/Keras on the MNIST dataset  
- *Tools Used*: Python 3.11, Scikit-learn, TensorFlow, Pandas, Seaborn, Google Colab  
- Emphasis was placed on *real-world data, **model evaluation, and **hyperparameter tuning*, with visualizations and insights shared during peer presentations
