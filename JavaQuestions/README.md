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


### 8. Garbage Collection types (Minor vs Major GC)
In Java, there are two main types of garbage collection: Minor GC and Major GC (also known as Full GC).
1. **Minor GC:** This type of garbage collection occurs in the Young Generation of the heap, which is where new objects are allocated. Minor GC is triggered when the Young Generation becomes full. During a Minor GC, the garbage collector identifies and removes objects that are no longer in use, and promotes surviving objects to the Old Generation if they have been alive for a certain number of GC cycles.
2. **Major GC (Full GC):** This type of garbage collection occurs in the Old Generation of the heap, which is where long-lived objects are stored. Major GC is triggered when the Old Generation becomes full or when certain conditions are met (e.g., a System.gc() call). During a Major GC, the garbage collector performs a more comprehensive cleanup, which can include compacting the heap to reduce fragmentation. Major GC is typically more time-consuming than Minor GC, and it can cause noticeable pauses in the application, so it should be used judiciously.

### 9. How do you make a class thread-safe? Provide a practical example.
To make a class thread-safe, you can use synchronization to control access to shared resources and ensure that only one thread can access a critical section of code at a time. This can be achieved using the `synchronized` keyword or by using locks from the `java.util.concurrent.locks` package.

### 10.  How would you implement global exception handling in Spring Boot?
In Spring Boot, you can implement global exception handling by using the `@ControllerAdvice` annotation along with `@ExceptionHandler` methods. This allows you to handle exceptions across the whole application in a centralized manner.


### 11. How do you manage concurrent updates to the same database record?
To manage concurrent updates to the same database record, you can use optimistic locking or pessimistic locking.
1. **Optimistic Locking:** This approach assumes that multiple transactions can complete without affecting each other. It uses a version number or timestamp to detect if a record has been modified by another transaction. If a conflict is detected, the transaction can be retried or an error can be returned to the user.
2. **Pessimistic Locking:** This approach locks the record for the duration of the transaction, preventing other transactions from modifying it until the lock is released. This can be achieved using database-level locks (e.g., `SELECT FOR UPDATE`) or application-level locks (e.g., using `synchronized` blocks in Java). Pessimistic locking can lead to reduced concurrency and potential deadlocks, so it should be used carefully.

### 12. Explain the step-by-step flow of JWT authentication.
1. **User Login:** The user sends a login request with their credentials (e.g., username and password) to the authentication server.
2. **Authentication:** The authentication server verifies the user's credentials. If they are valid, the server generates a JWT (JSON Web Token) that contains the user's information and any relevant claims (e.g., roles, permissions).
3. **Token Generation:** The JWT is signed using a secret key or a public/private key pair to ensure its integrity and authenticity.
4. **Token Response:** The authentication server sends the generated JWT back to the client in the response.
5. **Token Storage:** The client stores the JWT (e.g., in local storage or a cookie) for future use.
6. **Authenticated Requests:** For subsequent requests to protected resources, the client includes the JWT in the Authorization header (e.g., `Authorization: Bearer <token>`).
7. **Token Validation:** The server receives the request and validates the JWT by checking its signature, expiration time, and any relevant claims. If the token is valid, the server processes the request and returns the appropriate response. If the token is invalid or expired, the server returns an error response (e.g., 401 Unauthorized).
8. **Token Refresh (optional):** If the JWT has a short expiration time, the client can request a new token using a refresh token before the original token expires. This allows the user to stay authenticated without having to log in again.

