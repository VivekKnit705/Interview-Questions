# Mojro Interview Questions

**1. How to make a class immutable** <br>
**Ans:** To make a class immutable we can have 
1. W can meke class as final
2. Declare field with private and final
3. Set Variable only via constructure.



**2. What do you mean by @Transactional Annotation**<br>
**Ans:** We can make Class as Transactional and a method as Transactional 
1. when we make a class as Transactional it make all the public method as Transactional
2. when we make a method as Transactional it overrides the class.


**@Transactional** ensures **atomicity**. If any runtime exception occurs, the entire method is rolled back and the database remains consistent.

**3. ConcurrentHashmap vs Synchronized HashMap**<br>
**Synchronized HashMap:** put log on whole map<br>
**ConcurrentHashMap:** is a thread safe HashMap multiple thread can perform read-write operation

HashTable is also a thread safe, but it provides less performance than the ConcurrentHashMap.

**4. Type of reference object**
1. Strong: Until the object is being used GC can not delete the object
2. Week: We can access it but once GC runs it will delete the Object
3. Soft: It is a type of Week Reference but, it says GC delete it when ever it is urgent

**5. Heap Memory**

Heap Memory divided into three part
1. Young Generation
   1. Eden 
   2. Survivor (s0)
   3. Survivor (s1) 
2. Old Generation
3. Non Heap(Meta Space)

How does Heap memory works
So as we know heap memory divided into three parts 
Young Generation, Old Generation, Meta Space.

So Whenever an object get created it store in Eden part of the Heap memory after running the GC, GC uses Mark and Sweep algorithm to find what are the object which are not being used delete them and move the remaining one to the service alternating and increase their age once the age reaches to the threshold to the limit then it will move the object to the old generation.  

**6. Garbage Collection type:**
1. **Serial GC**<br> Serial GC only one thread do the memory clean-up and as we know GC is very expesive task so Seral GC is not a feasible solution because application has to wait for longer Time 
2. **Parallel GC** <br> In Parallel GC we have multiple thread to perform the Clean-up but again out application will get stop for some time
3. **Concurrent Mark and Sweep** <br>  Concurrent Mark and Sweep ensure that I will not make you system pause for can not grantee about that 
4. **G1 GC** <br> G1 GC is the better version of Concurrent mark and sweep where it ensure that i will not let you system get down


**7. @Bean Annotation**
1. **Class Level**: If you place **@Bean** directly on class it will not work.
2. **Variable Level**: If we place **@Bean** at variable level it will fail to compile
3. **Method Level**:  This controls the Object creation as we know **@Component** creates the object and register it to IOC container we use **@Bean** when we want to control the object creation as we may require to create a complex bean.

**8. In a Java (or C#) method, if a return statement is executed inside the try block, will the finally block still execute?**

If you include a return statement in the finally block, you enter "danger zone" territory. In Java, the finally block's return will override any previous return statement from the try or catch blocks.
The only common exceptions where finally won't run are:
1. If the Virtual Machine crashes or the process is killed. 
2. If you call a hard exit command like System.exit(0). 
3. If the code enters an infinite loop inside the try block.

**9. Java Volatile vs. Non-Volatile Variables**

**Volatile Variable:**

By default, Java variables are non-volatile. To improve performance, each thread may keep a local copy of a variable in its CPU cache instead of reading it from main memory every single time.

**The Problem:** If Thread A updates a variable, Thread B might not see that update immediately because it’s still looking at its own "stale" cached version.<br>
**Performance:** High (due to caching).<br>
**Thread Safety:** Low (no guarantee of visibility).

**Non-Volatile Variable:**

When you mark a variable as volatile, you are telling the JVM: "Always read and write this variable directly to main memory."

**Key Features:**
**Visibility:** Any write to a volatile variable is immediately visible to all other threads. It "flushes" the change to main memory instantly.

**Happens-Before Relationship:** It prevents the compiler from reordering code around the volatile variable, ensuring that any instructions before the write are completed first.

**No Atomicity:** This is the big "gotcha." volatile does not make operations atomic.

**Example of the volatile trap:**
If you have public volatile int count = 0;, the operation count++ is not thread-safe. This is because count++ is actually three steps: read, increment, and write. Two threads could read the same value simultaneously, increment it, and write it back, losing one of the increments.

**When to Use Which?**

1. **Use Non-Volatile:** For local variables within methods, or when you are already using synchronized blocks or Locks to handle concurrency. 
2. **Use Volatile**: For simple "status flags" or "signals" between threads where only one thread modifies the value, but many threads need to see the most recent update instantly