### **1. What is the difference between JDK, JRE, and JVM?**

- **JDK (Java Development Kit)**: The JDK is a software development kit that includes JRE, compilers, and other tools needed for developing Java applications.
- **JRE (Java Runtime Environment)**: The JRE provides libraries and the JVM (Java Virtual Machine) to run Java applications. It doesn’t include development tools like compilers.
- **JVM (Java Virtual Machine)**: The JVM is a virtual machine that runs Java bytecode. It provides platform independence by converting bytecode into machine code.

**Example:**

- **JDK** is used by developers for creating Java applications.
- **JRE** is used by end-users to run Java applications.
- **JVM** runs Java bytecode in a platform-independent manner.

---

### **2. What is the difference between `==` and `.equals()` in Java?**

- **`==`**: Compares memory addresses (references) of two objects.
- **`.equals()`**: Compares the contents (state) of two objects. It should be overridden in classes like `String` to compare the actual data.

**Example:**

```java
String str1 = new String("hello");
String str2 = new String("hello");
System.out.println(str1 == str2);      // false (different memory addresses)
System.out.println(str1.equals(str2)); // true (same content)
```

---

### **3. What is method overloading and method overriding?**

- **Method Overloading**: Same method name, but different parameters (different type or number of parameters).
- **Method Overriding**: Subclass provides its own implementation of a method defined in the superclass, keeping the same signature.

**Example of Overloading:**

```java
class Demo {
    public void display(int a) {
        System.out.println("Integer: " + a);
    }

    public void display(String a) {
        System.out.println("String: " + a);
    }
}

public class Main {
    public static void main(String[] args) {
        Demo demo = new Demo();
        demo.display(10);   // Integer: 10
        demo.display("Hello"); // String: Hello
    }
}
```

**Example of Overriding:**

```java
class Animal {
    public void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    public void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a = new Dog();
        a.sound(); // Dog barks
    }
}
```

---

### **4. What is the difference between an interface and an abstract class in Java?**

- **Interface**: Defines a contract with method signatures (no body). A class can implement multiple interfaces.
- **Abstract Class**: Can have both method signatures and concrete methods (with implementations). A class can extend only one abstract class.

**Example:**

```java
interface Animal {
    void sound();
}

abstract class AnimalAbstract {
    abstract void sound();

    public void sleep() {
        System.out.println("Animal is sleeping");
    }
}
```

---

### **5. What is a `constructor` in Java?**

A constructor is a special method used to initialize objects. It has the same name as the class and no return type.

- **Default Constructor**: Automatically provided by Java if no constructor is defined.
- **Parameterized Constructor**: Used to pass initial values to an object during creation.

**Example:**

```java
class Person {
    String name;
    int age;

    // Parameterized constructor
    Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}

public class Main {
    public static void main(String[] args) {
        Person p = new Person("John", 30);
        System.out.println(p.name + " is " + p.age + " years old.");
    }
}
```

---

### **6. What are `String`, `StringBuilder`, and `StringBuffer` in Java?**

- **String**: Immutable. Every time you modify it, a new object is created.
- **StringBuilder**: Mutable. It can be modified without creating a new object.
- **StringBuffer**: Similar to `StringBuilder`, but it is thread-safe.

**Example of StringBuilder:**

```java
StringBuilder sb = new StringBuilder("Hello");
sb.append(" World");
System.out.println(sb); // Output: Hello World
```

---

### **7. Explain the concept of `Encapsulation` in Java.**

**Encapsulation** is the process of hiding the internal state of an object and requiring all interaction to be performed through well-defined methods. This helps protect the object's state from unintended changes.

**Example:**

```java
class Person {
    private String name; // private field

    public String getName() { // getter
        return name;
    }

    public void setName(String name) { // setter
        this.name = name;
    }
}

public class Main {
    public static void main(String[] args) {
        Person p = new Person();
        p.setName("John");
        System.out.println(p.getName()); // John
    }
}
```

---

### **8. What is `Polymorphism` in Java?**

**Polymorphism** means "many shapes". It allows methods to take different forms depending on the object that calls them. There are two types:

- **Compile-time Polymorphism** (Method Overloading)
- **Runtime Polymorphism** (Method Overriding)

**Example of Runtime Polymorphism:**

```java
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a = new Dog();
        a.sound(); // Dog barks
    }
}
```

---

### **9. What is the difference between `ArrayList` and `LinkedList` in Java?**

- **ArrayList**: A resizable array implementation of the `List` interface. It provides fast access and retrieval but slower insertions/deletions.
- **LinkedList**: A doubly linked list implementation of the `List` interface. It provides faster insertions/deletions but slower access and retrieval.

**Example of ArrayList:**

```java
ArrayList<String> list = new ArrayList<>();
list.add("Java");
list.add("Python");
System.out.println(list.get(0)); // Output: Java
```

---

### **10. What is `Java Collections Framework`?**

The **Java Collections Framework** provides a set of classes and interfaces for storing and manipulating data. It includes the following components:

- **List**: An ordered collection (ArrayList, LinkedList).
- **Set**: A collection that doesn’t allow duplicate elements (HashSet, TreeSet).
- **Queue**: A collection used for holding elements before processing (LinkedList, PriorityQueue).
- **Map**: A collection that maps keys to values (HashMap, TreeMap).

**Example:**

```java
Map<String, Integer> map = new HashMap<>();
map.put("One", 1);
map.put("Two", 2);
System.out.println(map.get("One")); // Output: 1
```

---

### **11. What is `Garbage Collection` in Java?**

**Garbage Collection (GC)** is the process of automatically reclaiming memory by destroying objects that are no longer reachable by the program. Java has a built-in garbage collector that handles memory management.

**Example:**

```java
class MyClass {
    String data;

    @Override
    protected void finalize() throws Throwable {
        System.out.println("Object is garbage collected");
    }
}

public class Main {
    public static void main(String[] args) {
        MyClass obj = new MyClass();
        obj = null;  // Object becomes eligible for GC
    }
}
```

---

### **12. What are `final`, `finally`, and `finalize()` in Java?**

- **`final`**: A keyword used to define constants, prevent method overriding, and prevent class inheritance.
- **`finally`**: A block of code that is always executed after a `try-catch` block, whether an exception occurs or not.
- **`finalize()`**: A method used to clean up before an object is garbage collected (deprecated in newer Java versions).

**Example:**

```java
try {
    // Code that may throw an exception
} catch (Exception e) {
    // Handling exception
} finally {
    System.out.println("This will always execute.");
}
```

---

### **13. What is `thread` in Java and how can we create a thread?**

A **thread** is a lightweight process that allows for concurrent execution of tasks. In Java, you can create a thread in two ways:

1. **Extending the `Thread` class** and overriding the `run()` method.
2. **Implementing the `Runnable` interface** and passing it to a `Thread` object.

**Example of Thread (Extending Thread):**

```java
class MyThread extends Thread {
    @Override
    public void run() {
        System.out.println("Thread is running");
    }
}

public class Main {
    public static void main(String[] args) {


 MyThread t = new MyThread();
        t.start();
    }
}
```

---

### **14. Explain the concept of `Synchronization` in Java.**

**Synchronization** is used to control access to a shared resource by multiple threads to avoid concurrency issues. It can be done by using the `synchronized` keyword.

**Example:**

```java
class Counter {
    private int count = 0;

    public synchronized void increment() {
        count++;
    }

    public synchronized int getCount() {
        return count;
    }
}

public class Main {
    public static void main(String[] args) {
        Counter counter = new Counter();
        counter.increment();
        System.out.println(counter.getCount()); // Output: 1
    }
}
```

---

### **15. What are `Checked Exceptions` and `Unchecked Exceptions` in Java?**

- **Checked Exceptions**: Exceptions that must be either caught or declared in the method signature (`IOException`, `SQLException`).
- **Unchecked Exceptions**: Runtime exceptions that do not need to be explicitly handled (`NullPointerException`, `ArithmeticException`).

---

### **16. What is the difference between `HashMap` and `TreeMap`?**

- **HashMap**: Stores key-value pairs in an unordered way, using hash codes for fast lookups.
- **TreeMap**: Stores key-value pairs in a sorted order, based on the natural ordering of keys or a custom comparator.

Here are the remaining Java interview questions along with explanations and examples:

---

### **17. What is the difference between `HashSet` and `TreeSet` in Java?**

- **HashSet**: Implements a set based on a hash table. It does not guarantee any order of elements.
- **TreeSet**: Implements a set based on a Red-Black tree. It stores elements in sorted order.

**Example:**

```java
HashSet<String> hashSet = new HashSet<>();
hashSet.add("Apple");
hashSet.add("Banana");
System.out.println(hashSet); // Output: [Apple, Banana] (unordered)

TreeSet<String> treeSet = new TreeSet<>();
treeSet.add("Apple");
treeSet.add("Banana");
System.out.println(treeSet); // Output: [Apple, Banana] (sorted)
```

---

### **18. What is `assert` in Java?**

The `assert` keyword is used to test assumptions in the code. It takes a boolean expression and throws an `AssertionError` if the expression evaluates to `false`. It is mainly used for debugging.

**Example:**

```java
int age = 25;
assert age > 18 : "Age should be greater than 18"; // If age <= 18, it will throw AssertionError
```

---

### **19. What is a `Lambda expression` in Java?**

A **Lambda expression** is a feature introduced in Java 8 that allows you to write more concise and readable code. It represents a function or a block of code that can be passed around as an argument.

**Example:**

```java
List<String> list = Arrays.asList("Apple", "Banana", "Orange");
list.forEach(item -> System.out.println(item));
```

---

### **20. What is the difference between `Comparable` and `Comparator`?**

- **Comparable**: Defines the natural ordering of objects by implementing the `compareTo()` method.
- **Comparator**: Defines a custom ordering of objects by implementing the `compare()` method.

**Example of Comparable:**

```java
class Person implements Comparable<Person> {
    String name;
    int age;

    Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    @Override
    public int compareTo(Person other) {
        return Integer.compare(this.age, other.age);
    }
}

List<Person> people = new ArrayList<>();
people.add(new Person("Alice", 25));
people.add(new Person("Bob", 30));
Collections.sort(people);
```

**Example of Comparator:**

```java
class Person {
    String name;
    int age;

    Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}

class AgeComparator implements Comparator<Person> {
    @Override
    public int compare(Person p1, Person p2) {
        return Integer.compare(p1.age, p2.age);
    }
}

List<Person> people = new ArrayList<>();
people.add(new Person("Alice", 25));
people.add(new Person("Bob", 30));
Collections.sort(people, new AgeComparator());
```

---

### **21. What is `Stream` in Java?**

A **Stream** in Java is an abstraction that allows you to process sequences of elements (such as collections) in a functional way. Streams support operations like filtering, mapping, and reducing.

**Example:**

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
numbers.stream()
       .filter(n -> n % 2 == 0)
       .map(n -> n * n)
       .forEach(System.out::println); // Output: 4 16
```

---

### **22. Explain the concept of `Functional Interfaces` in Java.**

A **Functional Interface** is an interface that has exactly one abstract method. They can have multiple default or static methods. Functional interfaces can be used as the basis for lambda expressions.

**Example:**

```java
@FunctionalInterface
interface MyFunctionalInterface {
    void myMethod();
}

public class Main {
    public static void main(String[] args) {
        MyFunctionalInterface myFunc = () -> System.out.println("Lambda expression");
        myFunc.myMethod();
    }
}
```

---

### **23. What is `Optional` in Java?**

`Optional` is a container object which may or may not contain a value. It helps to prevent `NullPointerException` by explicitly handling null values.

**Example:**

```java
Optional<String> optional = Optional.of("Hello");
optional.ifPresent(System.out::println); // Output: Hello

Optional<String> emptyOptional = Optional.empty();
System.out.println(emptyOptional.orElse("Default value")); // Output: Default value
```

---

### **24. What is the use of the `super` keyword in Java?**

The **`super`** keyword is used to refer to the immediate parent class instance. It can be used to:

1. Access parent class constructors.
2. Access parent class methods or fields.

**Example:**

```java
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        super.sound(); // Calling parent class method
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.sound(); // Output: Animal makes a sound
                      //         Dog barks
    }
}
```

---

### **25. What is the difference between `throw` and `throws` in Java?**

- **`throw`**: Used to explicitly throw an exception from a method or block of code.
- **`throws`**: Declares that a method can throw exceptions, allowing the caller to handle it.

**Example:**

```java
// Throwing an exception
public void checkAge(int age) {
    if (age < 18) {
        throw new IllegalArgumentException("Age must be 18 or older");
    }
}

// Declaring exceptions with throws
public void readFile() throws IOException {
    // Code that might throw an IOException
}
```

---

### **26. What is a `deadlock` in Java?**

A **deadlock** occurs when two or more threads are blocked forever, waiting for each other to release resources. This can happen if two threads are holding resources and waiting for the other to release theirs.

**Example:**

```java
class A {
    synchronized void methodA(B b) {
        b.last();
    }

    synchronized void last() {}
}

class B {
    synchronized void methodB(A a) {
        a.last();
    }

    synchronized void last() {}
}

public class Main {
    public static void main(String[] args) {
        A a = new A();
        B b = new B();

        Thread t1 = new Thread(() -> a.methodA(b));
        Thread t2 = new Thread(() -> b.methodB(a));

        t1.start();
        t2.start();
    }
}
```

---

### **27. What is the purpose of `volatile` keyword in Java?**

The **`volatile`** keyword ensures that the value of a variable is always read from the main memory, and not from the thread's local cache. This is useful in multi-threaded programming to ensure the latest value is visible to all threads.

**Example:**

```java
class MyThread extends Thread {
    private volatile boolean running = true;

    public void run() {
        while (running) {
            System.out.println("Thread running...");
        }
    }

    public void stopRunning() {
        running = false;
    }
}
```

---

### **28. What is `synchronized` keyword in Java?**

The **`synchronized`** keyword is used to ensure that only one thread can access a method or block of code at a time, preventing race conditions.

**Example:**

```java
class Counter {
    private int count = 0;

    public synchronized void increment() {
        count++;
    }

    public int getCount() {
        return count;
    }
}

public class Main {
    public static void main(String[] args) {
        Counter counter = new Counter();
        Thread t1 = new Thread(() -> counter.increment());
        Thread t2 = new Thread(() -> counter.increment());
        t1.start();
        t2.start();
    }
}
```

---

### **29. What is the purpose of `default` methods in Java interfaces?**

**`default` methods** were introduced in Java 8 to allow method implementations in interfaces. This helps to add new methods to interfaces without breaking the existing implementations.

**Example:**

```java
interface MyInterface {
    default void defaultMethod() {
        System.out.println("Default method in interface");
    }
}

public class Main implements MyInterface {
    public static void main(String[] args) {
        Main obj = new Main();
        obj.defaultMethod();  // Output: Default method in interface
    }
}
```

Continuing with more Java interview questions, explanations, and examples:

---

### **30. What is the purpose of `this` keyword in Java?**

The **`this`** keyword refers to the current instance of a class. It is often used to refer to instance variables when they are shadowed by method parameters.

**Example:**

```java
class Person {
    private String name;

    public Person(String name) {
        this.name = name; // Refers to the current instance variable
    }

    public void printName() {
        System.out.println(this.name); // Refers to the current instance
    }
}

public class Main {
    public static void main(String[] args) {
        Person person = new Person("John");
        person.printName(); // Output: John
    }
}
```

---

### **31. What is method overloading in Java?**

**Method overloading** occurs when a class has multiple methods with the same name but different parameters (either in number or type). It allows a method to perform different tasks based on the arguments.

**Example:**

```java
class Calculator {
    public int add(int a, int b) {
        return a + b;
    }

    public double add(double a, double b) {
        return a + b;
    }
}

public class Main {
    public static void main(String[] args) {
        Calculator calc = new Calculator();
        System.out.println(calc.add(5, 10));      // Output: 15
        System.out.println(calc.add(5.5, 10.5));  // Output: 16.0
    }
}
```

---

### **32. What is method overriding in Java?**

**Method overriding** occurs when a subclass provides its own implementation for a method that is already defined in its superclass. The overridden method should have the same signature.

**Example:**

```java
class Animal {
    public void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    public void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal animal = new Dog();
        animal.sound(); // Output: Dog barks
    }
}
```

---

### **33. What is the purpose of the `super` keyword in Java?**

The **`super`** keyword is used to refer to the immediate parent class instance. It can be used to:

1. Call a parent class constructor.
2. Call a parent class method that has been overridden in the subclass.

**Example:**

```java
class Animal {
    public Animal() {
        System.out.println("Animal constructor");
    }

    public void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    public Dog() {
        super(); // Calls Animal's constructor
        System.out.println("Dog constructor");
    }

    @Override
    public void sound() {
        super.sound(); // Calls Animal's sound method
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.sound();
    }
}
```

Output:

```
Animal constructor
Dog constructor
Animal sound
Dog barks
```

---

### **34. What are `static` methods and variables in Java?**

- **Static methods**: Belong to the class rather than an instance. They can be called without creating an object of the class.
- **Static variables**: Also belong to the class and are shared among all instances of the class.

**Example:**

```java
class Counter {
    static int count = 0;

    public static void increment() {
        count++;
    }
}

public class Main {
    public static void main(String[] args) {
        Counter.increment();
        System.out.println(Counter.count); // Output: 1
    }
}
```

---

### **35. What is the purpose of `interface` in Java?**

An **interface** in Java defines a contract that classes can implement. It specifies abstract methods that the implementing class must provide. Interfaces allow for multiple inheritance and can be used for polymorphism.

**Example:**

```java
interface Animal {
    void sound();
}

class Dog implements Animal {
    public void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal animal = new Dog();
        animal.sound(); // Output: Dog barks
    }
}
```

---

### **36. What is the difference between `ArrayList` and `Vector` in Java?**

- **ArrayList**: Not synchronized, generally faster, and does not have built-in thread safety.
- **Vector**: Synchronized, meaning it is thread-safe but slower due to locking.

**Example:**

```java
ArrayList<Integer> arrayList = new ArrayList<>();
arrayList.add(1);
arrayList.add(2);

Vector<Integer> vector = new Vector<>();
vector.add(1);
vector.add(2);
```

---

### **37. What is the `transient` keyword in Java?**

The **`transient`** keyword is used to mark variables that should not be serialized. When an object is serialized, transient variables are skipped.

**Example:**

```java
class Person implements Serializable {
    String name;
    transient int age;  // This will not be serialized

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

---

### **38. What is a `Singleton` design pattern in Java?**

The **Singleton pattern** ensures that a class has only one instance and provides a global point of access to it.

**Example:**

```java
class Singleton {
    private static Singleton instance;

    private Singleton() {} // Private constructor

    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}

public class Main {
    public static void main(String

[] args) {
        Singleton singleton = Singleton.getInstance();
    }
}
```

### **39. What is the clone() method in Java?**

The clone() method in Java creates and returns a copy of the current object. The class must implement the Cloneable interface for the clone() method to work.

Example:

```java
class Person implements Cloneable {
    private String name;

    public Person(String name) {
        this.name = name;
    }

    @Override
    public Person clone() throws CloneNotSupportedException {
        return (Person) super.clone();
    }

    public String getName() {
        return name;
    }
}

public class Main {
    public static void main(String[] args) throws CloneNotSupportedException {
        Person person1 = new Person("John");
        Person person2 = person1.clone();

        System.out.println(person1.getName());  // Output: John
        System.out.println(person2.getName());  // Output: John
    }
}

```

52. What is the difference between HashMap and TreeMap in Java?
    HashMap: Stores key-value pairs in an unordered fashion. It allows one null key and multiple null values.
    TreeMap: Stores key-value pairs in a sorted order (according to the natural ordering of keys or a custom comparator). It does not allow null keys but allows null values.
    Example:

java
Copy code
HashMap<String, Integer> hashMap = new HashMap<>();
hashMap.put("apple", 1);
hashMap.put("banana", 2);

TreeMap<String, Integer> treeMap = new TreeMap<>();
treeMap.put("apple", 1);
treeMap.put("banana", 2);

System.out.println(hashMap); // Output: {apple=1, banana=2} (order may vary)
System.out.println(treeMap); // Output: {apple=1, banana=2} (sorted) 53. What is a Lambda expression in Java?
A Lambda expression is a short block of code that takes in parameters and returns a value. It is a function that can be passed around as an argument to methods or stored in variables. It is commonly used to implement functional interfaces.

Example:

java
Copy code
interface Greet {
void sayHello(String name);
}

public class Main {
public static void main(String[] args) {
Greet greet = (name) -> System.out.println("Hello, " + name);
greet.sayHello("John"); // Output: Hello, John
}
}

### **40. What is the difference between finalize() and gc() in Java?**

finalize(): A method in the Object class that is called by the garbage collector before an object is garbage collected. It can be overridden to perform cleanup operations.
gc(): A method in the System class that suggests the JVM to run the garbage collector, though it does not guarantee that the garbage collection will occur immediately.
Example:

```java

class MyObject {
    @Override
    protected void finalize() throws Throwable {
        System.out.println("Object is being garbage collected");
    }
}

public class Main {
    public static void main(String[] args) {
        MyObject obj = new MyObject();
        obj = null; // Object is eligible for GC
        System.gc(); // Suggests garbage collection
    }
}

```

### 41. **What is the difference between Thread.sleep() and Object.wait() in Java?**

Thread.sleep(): Makes the current thread sleep for the specified time (in milliseconds). It does not release the lock.
Object.wait(): Causes the current thread to release the lock and wait until it is notified.
Example:

```java

class SleepExample extends Thread {
    public void run() {
        try {
            System.out.println("Thread is sleeping...");
            Thread.sleep(1000);
            System.out.println("Thread woke up!");
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }
}

public class Main {
    public static void main(String[] args) {
        SleepExample thread = new SleepExample();
        thread.start();
    }
}

```

### **42. Can a constructor call another constructor in the same class?**

Yes, a constructor can call another constructor in the same class using the this() keyword. This is called constructor chaining and helps to avoid code duplication.

Example:

```java

class Rectangle {
    int length;
    int width;

    // Constructor with no parameters
    public Rectangle() {
        this(5, 10);  // Calls the parameterized constructor
    }

    // Parameterized constructor
    public Rectangle(int length, int width) {
        this.length = length;
        this.width = width;
    }

    public void display() {
        System.out.println("Length: " + length + ", Width: " + width);
    }

    public static void main(String[] args) {
        Rectangle rect = new Rectangle(); // Calls the default constructor, which calls the parameterized constructor
        rect.display(); // Output: Length: 5, Width: 10
    }
}

```

### 43. **What is the output of this code?**

```java
public class Main {
    public static void main(String[] args) {
        String str1 = "Java";
        String str2 = "Java";
        String str3 = new String("Java");
        System.out.println(str1 == str2);
        System.out.println(str1 == str3);
        System.out.println(str1.equals(str3));
    }
}
```

**Answer:**

```
true
false
true
```

Explanation: `str1` and `str2` point to the same string object in the string pool. `str3` is a new string object created in heap, so `==` checks reference equality (false), but `equals()` checks content equality (true).

---

### 44. **What is the output of the following code?**

```java
public class Main {
    public static void main(String[] args) {
        int i = 1;
        do {
            System.out.print(i + " ");
        } while (i < 0);
    }
}
```

**Answer:**

```
1
```

Explanation: The `do-while` loop executes at least once, even though the condition `i < 0` is false.

---

### 45. **What is the output of this code?**

```java
public class Main {
    public static void main(String[] args) {
        String str = "hello";
        StringBuilder sb = new StringBuilder(str);
        sb.reverse();
        System.out.println(sb);
    }
}
```

**Answer:**

```
olleh
```

Explanation: The `StringBuilder`'s `reverse()` method reverses the string, resulting in "olleh".

---

### 46. **What is the output of the following code?**

```java
public class Main {
    public static void main(String[] args) {
        StringBuilder sb = new StringBuilder("hello");
        sb.append(" world");
        sb.replace(0, 5, "Hi");
        System.out.println(sb);
    }
}
```

**Answer:**

```
Hi world
```

Explanation: `append(" world")` adds " world" to the string, and `replace(0, 5, "Hi")` replaces "hello" with "Hi", giving "Hi world".

---

### 47. **What is the output of the following code?**

```java
public class Main {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3};
        for (int i = 0; i < 4; i++) {
            System.out.println(arr[i]);
        }
    }
}
```

**Answer:**

```
1
2
3
ArrayIndexOutOfBoundsException
```

Explanation: The loop runs for `i` from 0 to 3, but `arr` has only 3 elements, causing an `ArrayIndexOutOfBoundsException` when `i` equals 3.

---

### 48. **What is the output of the following code?**

```java
public class Main {
    public static void main(String[] args) {
        Integer a = 127;
        Integer b = 127;
        System.out.println(a == b);
    }
}
```

**Answer:**

```
true
```

Explanation: Integer values between -128 and 127 are cached in Java, so `a` and `b` point to the same object in the Integer cache.

---

### 49. **What is the output of the following code?**

```java
public class Main {
    public static void main(String[] args) {
        String s1 = "Java";
        String s2 = "Java";
        String s3 = new String("Java");
        System.out.println(s1 == s2);
        System.out.println(s1 == s3);
        System.out.println(s1.equals(s3));
    }
}
```

**Answer:**

```
true
false
true
```

Explanation: `s1` and `s2` are literals and point to the same string in the string pool. `s3` is a new object, so `==` returns false, but `equals()` checks content, so it returns true.

---

### 50. **What is the output of the following code?**

```java
public class Main {
    public static void main(String[] args) {
        int x = 10;
        int y = 5;
        System.out.println(x++ - --y);
    }
}
```

**Answer:**

```
5
```

Explanation: `x++` returns 10 (post-increment), and `--y` returns 4 (pre-decrement). So, `10 - 4 = 6`.

---

### 51. **What is the output of this code?**

```java
public class Main {
    public static void main(String[] args) {
        int[] arr = new int[3];
        System.out.println(arr[0]);
    }
}
```

**Answer:**

```
0
```

Explanation: The default value for an uninitialized `int` array element is 0.

---

### 52. **What is the output of the following code?**

```java
public class Main {
    public static void main(String[] args) {
        Integer a = 200;
        Integer b = 200;
        System.out.println(a == b);
    }
}
```

**Answer:**

```
false
```

Explanation: Integer values greater than 127 are not cached, so `a` and `b` refer to different objects, hence `==` returns false.

---

### 53. **What is the output of this code?**

```java
public class Main {
    public static void main(String[] args) {
        String str = "Java";
        StringBuilder sb = new StringBuilder(str);
        sb.append(" is fun");
        System.out.println(sb);
    }
}
```

**Answer:**

```
Java is fun
```

Explanation: The `StringBuilder` appends " is fun" to the original string "Java", resulting in "Java is fun".

---

### 54. **What is the output of the following code?**

```java
public class Main {
    public static void main(String[] args) {
        String str = "hello";
        StringBuilder sb = new StringBuilder(str);
        sb.append(" world").insert(0, "Java ");
        System.out.println(sb);
    }
}
```

**Answer:**

```
Java hello world
```

Explanation: `insert(0, "Java ")` inserts "Java " at the beginning of the `StringBuilder`, followed by appending " world", resulting in "Java hello world".

---

### 55. **What is the output of this code?**

```java
public class Main {
    public static void main(String[] args) {
        int a = 5;
        int b = 10;
        if (a == 5 && b == 10) {
            System.out.println("True");
        } else {
            System.out.println("False");
        }
    }
}
```

**Answer:**

```
True
```

Explanation: Both conditions `a == 5` and `b == 10` are true, so "True" is printed.

---

### 56. **What is the output of this code?**

```java
public class Main {
    public static void main(String[] args) {
        int x = 5;
        int y = 5;
        System.out.println(x == y);
    }
}
```

**Answer:**

```
true
```

Explanation: Both `x` and `y` have the same value, so `==` returns true.

---

### 57. **What is the output of the following code?**

```java
public class Main {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4};
        for (int i : arr) {
            if (i == 3) {
                continue;
            }
            System.out.print(i + " ");
        }
    }
}
```

**Answer:**

```
1 2 4
```

Explanation: When `i == 3`, the `continue` statement skips the current iteration, so 3 is not printed.

---

### 58. **What is the output of this code?**

```java
public class Main {
    public static void main(String[] args) {
        StringBuilder sb = new StringBuilder("Java");
        sb.append(" Programming");
        sb.insert(4, " is fun");
        System.out.println(sb);
    }
}
```

**Answer:**

```
Java is fun Programming
```

Explanation: The `insert(4, " is fun")` inserts " is fun" at index 4, which results in "Java is fun Programming".

---

### 59. **What is the output of this code?**

```java
public class Main {
    public static void main(String[] args) {
        int x = 10;
        int y = 5;
        System.out.println(x / y + x % y);
    }
}
```

**Answer:**

```
7
```

Explanation: `x / y` is 2, and `x % y` is 0, so the result is `2 + 5 = 7`.

---

### 60. **What is the output of the following code?**

```java
public class Main {
    public static void main(String[] args) {
        double d =

 10.5;
        int i = (int) d;
        System.out.println(i);
    }
}
```

**Answer:**

```
10
```

Explanation: The casting from `double` to `int` truncates the decimal part, resulting in 10.

---

### 61. **What is the output of the following code?**

```java
public class Main {
    public static void main(String[] args) {
        String s1 = "abc";
        String s2 = "xyz";
        System.out.println(s1 + s2);
    }
}
```

**Answer:**

```
abcxyz
```

Explanation: The `+` operator concatenates the two strings, resulting in "abcxyz".

---

### 62. **What is the output of the following code?**

```java
public class Main {
    public static void main(String[] args) {
        String str = "Java";
        String str2 = new String("Java");
        System.out.println(str == str2);
    }
}
```

**Answer:**

```
false
```

Explanation: `==` checks reference equality, and `str` and `str2` refer to different objects, so it returns `false`.

---
