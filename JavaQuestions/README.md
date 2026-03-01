# Java Questions

### 1. Why do we still need abstract classes when interfaces have default methods?
Abstract classes and interfaces serve different purposes in Java. While interfaces can have default methods, they cannot hold state (instance variables) or provide a common implementation for multiple methods. Abstract classes, on the other hand, can have instance variables and can provide a common implementation for multiple methods. This allows abstract classes to be used when there is a need for shared code or state among related classes, while interfaces are more suitable for defining a contract that multiple classes can implement without sharing code.

### 2. How do threads communicate in Java?
Threads in Java can communicate with each other using several mechanisms:
1. **Shared Variables:** Threads can share variables and objects to communicate. However, this requires proper synchronization to avoid race conditions.
2. **Wait and Notify:** Threads can use the `wait()`, `notify()`, and `notifyAll()` methods to coordinate their actions. A thread can call `wait()` to release the lock and wait until another thread calls `notify()` or `notifyAll()` to wake it up.
3. **Thread Interruption:** One thread can interrupt another thread using the `interrupt()` method, which can be used to signal that a thread should stop what it is doing and do something else.

### 3. How does HashSet internally identify and store duplicates?
HashSet in Java uses a HashMap internally to store its elements. When an element is added to a HashSet, it calculates the hash code of the element and uses it to determine the bucket where the element should be stored. If there is already an element in that bucket, it checks for equality using the `equals()` method. If the new element is equal to an existing element, it is considered a duplicate and will not be added to the HashSet. This way, HashSet ensures that all elements are unique.

### 4. If you create a custom user-defined class, what should you consider before storing it in a Set?
Before storing a custom user-defined class in a Set, you should consider the following:
1. **Override `hashCode()` and `equals()`:** You should override the `hashCode()` and `equals()` methods to ensure that the Set can correctly identify duplicates. The `hashCode()` method should return a consistent hash code for the same object, and the `equals()` method should compare the relevant fields of the objects to determine equality.
2. **Immutability:** If possible, make your class immutable (i.e., its state cannot change after it is created). This can help prevent issues with mutable objects being modified after they are added to the Set, which can lead to unexpected behavior when trying to retrieve or remove elements from the Set.
3. **Implement `Comparable` (optional):** If you want to store your objects in a sorted Set (like TreeSet), you should implement the `Comparable` interface and provide a `compareTo()` method to define the natural ordering of your objects. Alternatively, you can provide a custom `Comparator` when creating the Set.


### 5. Explain the complete Software Development Lifecycle (SDLC)
The Software Development Lifecycle (SDLC) is a systematic process for planning, creating, testing, and deploying software applications. It consists of several phases that guide the development team through the entire software development process. The main phases of SDLC are:
1. Requirement Gathering and Analysis
2. Feasibility Study & Planning 
3. System Design 
4. Implementation (Coding)
5. Testing 
6. Deployment 
7. Maintenance

### 6. Difference between Oracle DB and SQL
SQL is the language, and Oracle Database is the software that understands it.

### 7. application.yml vs application.properties
Both `application.yml` and `application.properties` are configuration files used in Spring Boot applications to define application settings. The main difference between them is the format they use:
- `application.properties` uses a simple key-value pair format, where each line contains a property and its value, separated by an equals sign (`=`). For example:
```server.port=8080
spring.datasource.url=jdbc:mysql://localhost:3306/mydb
```
- `application.yml` uses a hierarchical format based on YAML (YAML Ain't Markup Language), which allows for more complex configurations and better readability. For example:
```server:
  port: 8080
spring:
  datasource:
    url: jdbc:mysql://localhost:3306/mydb
```
Both formats are supported by Spring Boot, and you can choose the one that best suits your preferences and the complexity of your configuration.

### 8. What is the difference between a process and a thread?
A process is an independent program that runs in its own memory space, while a thread is a smaller unit of execution that runs within a process and shares the same memory space. A process can have multiple threads, and each thread can execute concurrently, allowing for multitasking within a single process. Threads are more lightweight than processes and can communicate with each other more easily since they share the same memory space. However, this also means that threads can interfere with each other if not properly synchronized, while processes are isolated and do not affect each other directly.


