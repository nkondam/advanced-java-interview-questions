# Java Basic Interview Questions

### Table Of Contents
| No | Questions |
|----|-----------|
| 1 | [What is Java?](#what-is-java) |
| 2 | [Explain main features of java](#explain-main-features-of-java) |
| 3 | [What is the difference between `==` and `.equals()` in Java?](#what-is-the-difference-between--and-equals-in-java) |
| 4 | [What is the Java Virtual Machine (JVM)?](#what-is-the-java-virtual-machine-jvm) |
| 5 | [What is the difference between `abstract class` and `interface`?](#what-is-the-difference-between-abstract-class-and-interface) |
| 6 | [Explain the concept of multithreading in Java](#explain-the-concept-of-multithreading-in-java) |
| 7 | [What is the Java Collections Framework?](#what-is-the-java-collections-framework) |
| 8 | [What is the difference between `String`, `StringBuilder`, and `StringBuffer`?](#what-is-the-difference-between-string-stringbuilder-and-stringbuffer) |
| 9 | [What is the purpose of the `finalize()` method?](#what-is-the-purpose-of-the-finalize-method) |
| 10 | [Explain the concept of exception handling in Java.](#explain-the-concept-of-exception-handling-in-java) |
| 11 | [What is the `super` keyword used for in Java?](#what-is-the-super-keyword-used-for-in-java) |
| 12 | [What is the difference between `method overloading` and `method overriding`?](#what-is-the-difference-between-method-overloading-and-method-overriding) |
| 13 | [Explain the `static` keyword in Java.](#explain-the-static-keyword-in-java) |
| 14 | [What is the purpose of the `transient` keyword in Java?](#what-is-the-purpose-of-the-transient-keyword-in-java) |
| 15 | [What is the `this` keyword in Java?](#what-is-the-this-keyword-in-java) |
| 16 | [Explain the concept of autoboxing and unboxing in Java.](#explain-the-concept-of-autoboxing-and-unboxing-in-java) |
| 17 | [What is the `try-with-resources` statement in Java?](#what-is-the-try-with-resources-statement-in-java) |
| 18 | [What is the difference between `public`, `private`, `protected`, and default access modifiers in Java?](#what-is-the-difference-between-public-private-protected-and-default-access-modifiers-in-java) |
| 19 | [How does Java support multiple inheritance?](#how-does-java-support-multiple-inheritance) |
| 20 | [Explain the `Comparator` interface in Java.](#explain-the-comparator-interface-in-java) |
| 21 | [What is the purpose of the `clone()` method in Java?](#what-is-the-purpose-of-the-clone-method-in-java) |
| 22 | [Explain the concept of inner classes in Java.](#explain-the-concept-of-inner-classes-in-java) |
| 23 | [What is the purpose of the `break` and `continue` statements in Java?](#what-is-the-purpose-of-the-break-and-continue-statements-in-java) |
| 24 | [How does Java support multithreading at the language level?](#how-does-java-support-multithreading-at-the-language-level) |
| 25 | [What is the purpose of the `clone()` method in Java?](#what-is-the-purpose-of-the-clone-method-in-java) |
| 26 | [Explain the concept of inner classes in Java.](#explain-the-concept-of-inner-classes-in-java) |
| 27 | [What is the purpose of the `break` and `continue` statements in Java?](#what-is-the-purpose-of-the-break-and-continue-statements-in-java) |
| 28 | [What are anonymous classes in Java?](#what-are-anonymous-classes-in-java) |
| 29 | [How does the `static` keyword impact memory management in Java?](#how-does-the-static-keyword-impact-memory-management-in-java) |
| 30 | [What is the purpose of the `assert` statement in Java?](#what-is-the-purpose-of-the-assert-statement-in-java) |
| 31 | [Explain the concept of the Java Reflection API.](#explain-the-concept-of-the-java-reflection-api) |
| 32 | [What is the purpose of the `throws` clause in a method signature?](#what-is-the-purpose-of-the-throws-clause-in-a-method-signature) |
| 33 | [Explain the difference between `List`, `Set`, and `Map` in the Java Collections Framework.](#explain-the-difference-between-list-set-and-map-in-the-java-collections-framework) |
| 34 | [How does Java handle method overloading with variable arguments (varargs)?](#how-does-java-handle-method-overloading-with-variable-arguments-varargs) |
| 35 | [Explain the concept of JavaBeans.](#explain-the-concept-of-javabeans) |
| 36 | [What is the difference between `ArrayList` and `LinkedList` in Java?](#what-is-the-difference-between-arraylist-and-linkedlist-in-java) |
| 37 | []() |
| 38 | []() |
| 39 | []() |
| 40 | []() |
| 41 | []() |
| 42 | []() |
| 43 | []() |
| 44 | []() |
| 45 | []() |



1. ### What is Java?
    Java is a high level, object-oriented programming language developed Sun Microsystems. It is designed to be platform independent and follows the "Write Once, Run Anywhere" (WORA) principle.

    **[⬆ Back to Top](#table-of-contents)**

2. ### Explain main features of java?
    Key features of java include:
    - Object-oriented programming
    - Platform-independent (via Java Virtual Machine)
    - Simply and Easy to learn
    - Distributed computing support (via RMI and EJB)
    - Multi-threading
    - Robust and secure (Garbage Collection, Exception Handling, etc..)
    - Dynamic and Extensible
  
    **[⬆ Back to Top](#table-of-contents)**

3. ### What is the difference between `==` and `.equals()` in Java?
    - `==` is used for comparing primitive data types or chrcking if two referrences point to the same object.
    - `.equals()` is a method used for comparing the content or values of a objects. It's usually overridden by custom classes for meaningful comparision.

    **[⬆ Back to Top](#table-of-contents)**

4. ### What is the Java Virtual Machine (JVM)?
    JVM is a virtual machine that enables java applications to run on any device or operating system. It provides abstraction layer between the java program and underlying hardware and operating system.

    **[⬆ Back to Top](#table-of-contents)**

5. ### What is the difference between `abstract class` and `interface`?
    - An abstract class can have both abstract and concrete methods, while interface can only have abstract methods.
    - A class can extend only one abstract class, but it can implement multiple interfaces.
    - Abstract classes can have constructors, while interface cannot.
  
    **[⬆ Back to Top](#table-of-contents)**

6. ### Explain the concept of multithreading in Java
    Multithreading is a java feature that allows concurrent execution of two or more threads. Each threads run independently, and java provides built in support for multithreading with the `Thread` class and `Runnable` interface.

    **[⬆ Back to Top](#table-of-contents)**

7. ### What is the Java Collections Framework?
    The Java Collections Framework provides a set of interfaces and classes for managing and manipulating group of objects. it includes like List, Set, and Map along with their implementing classes such as ArrayList, HashSet, and HashMap.

    **[⬆ Back to Top](#table-of-contents)**

8. ### What is the difference between `String`, `StringBuilder`, and `StringBuffer`?
    - `String` is a immutable, meaning its value cannot be changed once it's assigned.
    - `StringBuilder` and `StringBuffer` are mutable and can be modified `StringBuilder` is not thread safe, while `StringBuffer` is thread safe.

    **[⬆ Back to Top](#table-of-contents)**

9. ### What is the purpose of the `finalize()` method?
    The `finalize()` method is called by the garbage collector before an object is reclaimed. It allows the object to perform cleanup operations, such as releasing resources or closing connections.

    **[⬆ Back to Top](#table-of-contents)**

10. ### Explain the concept of exception handling in Java.
    Exception handling in Java is done through try, catch, and finally blocks. The `try` block contains the code that might thow an exception, the `catch` block catches and handles the exception, and `finally` block contains code that is executed regardless of whether an exception thrown or not.

    **[⬆ Back to Top](#table-of-contents)**

11. ### What is the `super` keyword used for in Java?
    The `super` keyword is used to refer to the superclass or parent class. It can be used to call methods, access fields, or invoke the constructor of parent class.

    **[⬆ Back to Top](#table-of-contents)**

12. ### What is the difference between `method overloading` and `method overriding`?
    - Method overloading occurs when two or more methods in the same class have the same name but different parameters.
    - Method overriding occurs when a subclass provides a specific implementation for a method that is already defined in it's superclass.
  
    **[⬆ Back to Top](#table-of-contents)**

13. ### Explain the `static` keyword in Java.
    The `static` keyword is used to declare members (fields, methods, blocks) that belong to the class rather than an instance of class. Static memebers are shared among the all the instances of class and can be accessed using same class name.

    **[⬆ Back to Top](#table-of-contents)**

14. ### What is the purpose of the `transient` keyword in Java?
    The `transient` keyword is used to indicate that the field should not be serialized when the object it containing it is serialized. This is often used for sensitive information that should not be persisted

    **[⬆ Back to Top](#table-of-contents)**

15. ### What is the `this` keyword in Java?
    The `this` keyword refers to the current instance of the class. It is often used to differentiate instance variables from local variables when they have same name, and to invoke current class methods.

    **[⬆ Back to Top](#table-of-contents)**

16. ### Explain the concept of autoboxing and unboxing in Java.
    Autoboxing is the automatic conversion of a primitive type to it's corresponding wrapper class (e.g., int to Integer). Unboxing is the reverse process, Where the wrapper class object is automatically converted to its primitive type.

    **[⬆ Back to Top](#table-of-contents)**

17. ### What is the `try-with-resources` statement in Java?
    The `try-with-resources` statement is used for automatic resource management. It ensures that each resource (e.g., stream, connections) declared in the paranthesis is closed at end of statement, whether an exception occurs or not.

    **[⬆ Back to Top](#table-of-contents)**

18. ### Explain the concept of garbage collection in Java
    Garbage Collection in java is the process of automatically reclaiming memory occupied by objects that are no longer reachable. The JVM's garabage collector identifies and removes unreferenced objects to free up memory.

    **[⬆ Back to Top](#table-of-contents)**

19. ### What is the difference between `public`, `private`, `protected`, and default access modifiers in Java?
    - `public`: Accessible from any class
    - `private`: Accessible only within the declared class
    - `protected`: Accessible with within the same package or a subclass
    - Default (no modifier): Accessible with in the same package
   
    **[⬆ Back to Top](#table-of-contents)**

20. ### Explain the concept of the Java Naming and Directory Interface (JNDI).
    JNDI is an API that provides naming and directory functionality to Java applications. It allows Java programs to look up and access services, objects, and resources in a network. JNDI is often used in conjunction with naming services like LDAP.

    **[⬆ Back to Top](#table-of-contents)**

21. ### How does Java support multiple inheritance?
    Java supoorts multiple inheritence through interfaces. A class can implement multiple interfaces, allowing it to inherit abstract methods from multiple sources.

    **[⬆ Back to Top](#table-of-contents)**

22. ### Explain the `Comparator` interface in Java.
    The `comparator` interface is used for custom sorting of objects. It provides a way to compare two objects and is often used in conjuction with sorting methods, such as `Collections.sort()`

    **[⬆ Back to Top](#table-of-contents)**

23. ### What is the `instanceof` operator used for?
    The `instanceOf` operator is used to test if an object is an instance of a particular class or interface. It returns `true` if the object is an instance; otherwise, it returns `false`.

    **[⬆ Back to Top](#table-of-contents)**

24. ### How does Java support multithreading at the language level?
    Java supports multithreading through the `Thread` class and the `Runnable` interface. Additionally, the `synchronized` keyword is used to control access to shared resources, and the `wait()` and `notify()` methods facilitate communication between threads.

    **[⬆ Back to Top](#table-of-contents)**

25. ### What is the purpose of the `clone()` method in Java?
    The `clone()` method is used to create a copy of an object. The class of the object must implement the `Cloneable` interface, and the `clone()` method can be overridden to provide a meaningful copying mechanism.

    **[⬆ Back to Top](#table-of-contents)**

26. ### Explain the concept of inner classes in Java.
    Inner classes are classes defined within other classes. They have access to the members of of the outer class and are used to logically group classes and interfaces in one place.
    **[⬆ Back to Top](#table-of-contents)**

27. ### What is the purpose of the `break` and `continue` statements in Java?
    - The `break` statement is used to exit a loop prematurely.
    - The `continue` statement is used to skip the rest of loop's code and start the next iteration
    **[⬆ Back to Top](#table-of-contents)**

28. ### What are anonymous classes in Java?
    Annonymous classes are classes without a name. They are often used for one-time use, especially when implementing interfaces or extending classes on the fly. Example: 
    ```java
        Runnable runnable = new Runnable() {
            public void run() {
                System.out.println("Anonymous class implementation");
            }
        }
    ```
    **[⬆ Back to Top](#table-of-contents)**

29. ### How does the `static` keyword impact memory management in Java?
    The `static` keyword means that a member (method, variable) belongs to the class rather than an instance of the class. Static members are loaded into memory once and shared among all instances of the class. They can be accessed using the class name.

    **[⬆ Back to Top](#table-of-contents)**

30. ### What is the purpose of the `assert` statement in Java?
    The `assert` statement is used for debugging purposes. It checks a boolean expression, and if it's false, an `AssertionError` is thrown. Assertions can be enabled or disabled using the `-ea` or `-da` JVM flags.


    **[⬆ Back to Top](#table-of-contents)**

31. ### Explain the concept of the Java Reflection API.
    Reflection allows a program to inspect or modify it own structure, behaviour, or state at runtime. The `java.lang.reflect` package provides classes for this purpose. Reflection is commonly used for bulding tools, frameworks and debuugers.

    **[⬆ Back to Top](#table-of-contents)**

32. ### What is the purpose of the `throws` clause in a method signature?
    The `throws` clause is used to declare that a method might throw one or more types of exceptions. It signals to the calling code that it should handle these exceptions or propagate them further.

    **[⬆ Back to Top](#table-of-contents)**

33. ### Explain the difference between `List`, `Set`, and `Map` in the Java Collections Framework.
    - `List`: An ordered collection that allows duplicate elements.
    - `Set`: An unordered collection that does not allow duplicate elements.
    - `Map`: A collection of key-value pairs, where each key must be unique.

    **[⬆ Back to Top](#table-of-contents)**

34. ### How does Java handle method overloading with variable arguments (varargs)?
    Java allows you to create methods that can take a variable number of arguments using varargs. The varargs parameter must be the last parameter in the method signature. Example:
     ```java
     void printNumbers(int... numbers) {
         for (int num : numbers) {
             System.out.println(num);
         }
     }
     ```

    **[⬆ Back to Top](#table-of-contents)**

35. ### Explain the concept of JavaBeans.
    JavaBeans are reusable software components for Java that follow specific conventions, such as having a public default constructor, providing getter and setter methods, and being serializable. They are commonly used in building graphical user interfaces (GUIs) and other software components.
    **[⬆ Back to Top](#table-of-contents)**

36. ### What is the difference between `ArrayList` and `LinkedList` in Java?
    - `ArrayList` is implemented a dynamic array, providing fast random access and better performance for scenarios involving frequent element access.
    - `LinkedList` is implemented as a doubly linked list, offering better performance for insertions and deletions in scenarios where elements are frequently added or removed.

    **[⬆ Back to Top](#table-of-contents)**

