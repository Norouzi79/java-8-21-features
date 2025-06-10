
# Java Features from Java 9 to Java 21

Here’s an extensive list of features that have remained in Java from **Java 9** to **Java 21**. These features have stayed in the language due to their usefulness, efficiency, and stability.

---

## 1. **Module System (Java 9)**
The **Module System** was introduced as Project Jigsaw to modularize the Java platform and Java applications.
- **Why it stayed**: It improves maintainability, security, and scalability of large systems.
- **Example**:
  ```java
  module com.example {
      exports com.example.package;
  }
  ```
- **Trick**: Modularize libraries or large applications for better dependency management.

---

## 2. **JShell (Java 9)**
JShell allows for interactive evaluation of Java code.
- **Why it stayed**: It makes Java more accessible for experimentation and learning.
- **Example**:
  ```bash
  jshell> System.out.println("Hello, World!")
  Hello, World!
  ```
- **Trick**: Use JShell for quick experimentation with Java expressions.

---

## 3. **Local Variable Type Inference (`var`) (Java 10)**
The `var` keyword allows you to declare variables without specifying their types.
- **Why it stayed**: It reduces boilerplate code and improves readability.
- **Example**:
  ```java
  var list = new ArrayList<String>();
  ```
- **Trick**: Use `var` for local variables when the type is obvious.

---

## 4. **String Methods (Java 11)**
Java 11 introduced useful methods for `String` manipulation like `isBlank()`, `lines()`, and `strip()`.
- **Why it stayed**: These methods are essential for handling strings more effectively.
- **Example**:
  ```java
  String text = "   Hello   ";
  System.out.println(text.strip()); // Output: "Hello"
  ```
- **Trick**: Use `strip()` instead of `trim()` for more accurate whitespace handling.

---

## 5. **Switch Expressions (Java 12)**
Switch expressions allow more flexible and expressive switch statements.
- **Why it stayed**: It simplifies complex `switch` statements and makes the code cleaner.
- **Example**:
  ```java
  var result = switch (day) {
      case MONDAY, FRIDAY -> "Workday";
      case SATURDAY, SUNDAY -> "Weekend";
      default -> throw new IllegalStateException("Unexpected value: " + day);
  };
  ```
- **Trick**: Use switch expressions for cleaner, more readable code.

---

## 6. **Records (Java 14 and Finalized in Java 16)**
Records provide a way to define immutable data carriers without boilerplate code.
- **Why it stayed**: It eliminates repetitive code like `equals()`, `hashCode()`, and `toString()`.
- **Example**:
  ```java
  public record Point(int x, int y) {}
  ```
- **Trick**: Use records when defining data carriers for better readability and reduced boilerplate.

---

## 7. **Pattern Matching (Java 16, Previewed in Java 14)**
Pattern matching simplifies type checking and casting.
- **Why it stayed**: It makes working with data types easier and reduces redundancy.
- **Example**:
  ```java
  if (obj instanceof String s) {
      System.out.println(s.toUpperCase());
  }
  ```
- **Trick**: Use pattern matching to simplify type checks and casting in your code.

---

## 8. **Sealed Classes (Java 15, Finalized in Java 17)**
Sealed classes restrict which classes or interfaces can extend them.
- **Why it stayed**: It allows for controlled class hierarchies.
- **Example**:
  ```java
  public sealed class Shape permits Circle, Square { }
  ```
- **Trick**: Use sealed classes to control inheritance in your application for better security and maintainability.

---

## 9. **Virtual Threads (Java 19, Previewed in Java 18, Finalized in Java 21)**
Virtual threads make handling massive concurrency more efficient.
- **Why it stayed**: It simplifies the management of high-concurrency applications.
- **Example**:
  ```java
  var thread = Thread.startVirtualThread(() -> {
      System.out.println("Hello from virtual thread");
  });
  ```
- **Trick**: Use virtual threads for applications requiring high concurrency, like servers.

---

## 10. **Foreign Function & Memory API (Java 16, Previewed in Java 14)**
This API allows Java to interact with native code and manage native memory.
- **Why it stayed**: It provides a more efficient and safer alternative to JNI.
- **Example**:
  ```java
  try (var session = MemorySession.openConfined()) {
      var segment = session.allocate(100);
  }
  ```
- **Trick**: Use the **Foreign Function & Memory API** for more efficient native code interaction.

---

## 11. **Enhanced `switch` Statements (Java 12, Previewed in Java 14)**
Enhancements to the `switch` statement introduced new ways to write cleaner switch code.
- **Why it stayed**: It reduces nested conditionals and simplifies code.
- **Example**:
  ```java
  switch (day) {
      case MONDAY, FRIDAY -> System.out.println("Workday");
      case SATURDAY, SUNDAY -> System.out.println("Weekend");
  }
  ```
- **Trick**: Use enhanced `switch` for better readability and reducing nested conditional logic.

---

## 12. **Compact JDK (Java 9)**
Create smaller, optimized JDK runtimes by including only required modules.
- **Why it stayed**: Useful for systems with limited resources.
- **Example**:
  ```bash
  jlink --module-path $JAVA_HOME/jmods --add-modules java.base,java.logging --output my-image
  ```
- **Trick**: Use **`jlink`** to create a custom JDK runtime image with just the necessary modules.

---

## 13. **`java.util.concurrent` Improvements (Java 9)**
Java 9 improved **`CompletableFuture`** and added new concurrency utilities.
- **Why it stayed**: These features help developers easily work with asynchronous programming.
- **Example**:
  ```java
  CompletableFuture.supplyAsync(() -> "Hello")
      .thenApplyAsync(result -> result + " World")
      .thenAccept(System.out::println); // Outputs: Hello World
  ```
- **Trick**: Use **`CompletableFuture`** for async programming instead of manually handling threads.

---

## 14. **`@NonNull` and `@Nullable` Annotations (Java 9 and onwards)**
These annotations help in handling nullability in a more declarative way.
- **Why it stayed**: It improves code clarity and reduces the chances of `NullPointerException`.
- **Example**:
  ```java
  @NonNull
  public String concat(@NonNull String str1, @Nullable String str2) {
      return str1 + (str2 != null ? str2 : "");
  }
  ```
- **Trick**: Use **`@NonNull`** and **`@Nullable`** annotations for clearer contracts in your APIs and to enforce null safety.

---

## 15. **`try-with-resources` Enhancements (Java 9)**
Java 9 enhanced **`try-with-resources`** to handle multiple resources more efficiently.
- **Why it stayed**: It helps manage resources like files and streams automatically, reducing the risk of resource leaks.
- **Example**:
  ```java
  try (var reader = new BufferedReader(new FileReader("file.txt"));
       var writer = new BufferedWriter(new FileWriter("output.txt"))) {
      // Use reader and writer
  } catch (IOException e) {
      e.printStackTrace();
  }
  ```
- **Trick**: Always use **`try-with-resources`** for automatic resource management, especially for files, streams, and other closable resources.

---

## 16. **`System::nanoTime()` for High-Resolution Time Measurement (Java 9)**
Java 9 introduced **`System.nanoTime()`** for more accurate performance measurements.
- **Why it stayed**: It offers high-resolution time measurement, perfect for performance profiling.
- **Example**:
  ```java
  long start = System.nanoTime();
  // some operation
  long end = System.nanoTime();
  System.out.println("Duration: " + (end - start) + " nanoseconds");
  ```
- **Trick**: Use **`nanoTime()`** for precise performance testing, especially for measuring small durations.

---

## 17. **Enhanced `java.time` (Java 9 and onwards)**
Java's **`java.time`** API received new methods for date and time manipulation.
- **Why it stayed**: It's the recommended way to handle date and time in Java, offering better accuracy and usability than `Date` or `Calendar`.
- **Example**:
  ```java
  LocalDate date = LocalDate.now();
  System.out.println(date.plusDays(5));
  ```
- **Trick**: Use **`java.time`** for all date and time operations to avoid the pitfalls of older classes like `Date` and `Calendar`.

---

## 18. **Compact Strings (Java 9)**
Compact strings optimize memory usage by using one byte per character for Latin-1 characters.
- **Why it stayed**: It reduces memory footprint for applications handling lots of text.
- **Trick**: Most applications benefit from compact strings automatically without requiring any extra work.

---

## 19. **`FileSystems` API Enhancements (Java 9)** 
Java 9 enhanced the **`FileSystems`** API to provide better handling of file systems with non-regular files like symbolic links.
- **Why it stayed**: Makes file system operations more efficient and flexible.
- **Example**:
  ```java
  Path path = FileSystems.getDefault().getPath("some/path");
  ```
- **Trick**: Use the **`FileSystems`** API for platform-independent and efficient file system operations.

---

## 20. **`@Target` and `@Retention` Annotations (Java 9)**
Java 9 introduced enhancements to **`@Target`** and **`@Retention`** annotations to provide more control over annotation usage.
- **Why it stayed**: It gives developers more control over how annotations are used and retained.
- **Example**:
  ```java
  @Retention(RetentionPolicy.RUNTIME)
  @Target(ElementType.METHOD)
  public @interface MyMethodAnnotation {}
  ```
- **Trick**: Use **`@Retention`** and **`@Target`** annotations when building custom frameworks to control annotation behavior.

---

## 21. `java.lang.invoke` API (Java 9)
The `java.lang.invoke` API was further enhanced for efficient method invocation, enabling features like dynamic proxies and lambda function support.
- **Why it stayed**: Provides efficient access to methods, making frameworks like Spring more powerful.
- **Example**:
```java
MethodHandles.lookup().findStatic(MyClass.class, "myMethod", MethodType.methodType(void.class)).invoke();
```

## 22. Weak and Soft References (Java 9 and onwards)
Java continues to enhance weak and soft references, allowing better management of memory for cache and other memory-sensitive tasks.
- **Why it stayed**: Provides better memory management by allowing objects to be collected under specific conditions.
- **Example**:
```java
WeakReference<MyObject> weakRef = new WeakReference<>(new MyObject());
```

## 23. Java Flight Recorder (Java 11)
Java Flight Recorder (JFR) is a low-overhead, continuous profiling tool that records JVM events. It's used for diagnosing issues in production environments.
- **Why it stayed**: JFR allows developers and operators to record detailed information about JVM runtime behavior with minimal performance impact.
- **Example**:
```bash
java -XX:StartFlightRecording=duration=60s -jar app.jar
```

## 24. Pattern Matching for switch (Java 17)
Pattern Matching for `switch` enhances the ability to match complex data structures.
- **Why it stayed**: It simplifies working with complex conditional logic, making it more intuitive and readable.
- **Example**:
```java
switch (obj) {
    case Integer i -> System.out.println("Integer: " + i);
    case String s -> System.out.println("String: " + s);
    default -> System.out.println("Unknown type");
}
```

## 25. New macOS Rendering Pipeline (Java 17)
Introduced a new macOS rendering pipeline based on Apple's Metal framework, replacing the previous OpenGL-based pipeline.
- **Why it stayed**: Improves performance and visual quality on macOS devices.
- **Trick**: If you're developing for macOS, use the Metal-based pipeline for enhanced graphics performance.


## 26. Foreign Linker API (Java 17)
The **Foreign Linker API** allows Java applications to more easily interface with native libraries without using JNI.
- **Why it stayed**: Offers a more efficient way to invoke native code compared to the traditional JNI interface.
- **Example**:
  ```java
  var linker = Linker.getInstance();
  var function = linker.lookup("printf", FunctionType.ofVoid(), String.class);
  function.invoke("Hello, %s!", "World");
  ```


## 27. Virtual Threads and Structured Concurrency (Java 20)
Introduced structured concurrency and virtual threads to make working with concurrency easier and more efficient.
- **Why it stayed**: Helps developers handle concurrency in a cleaner, more predictable way.
- **Example**:
  ```java
  try (var scope = new StructuredScope()) {
      scope.fork(() -> { /* Task 1 */ });
      scope.fork(() -> { /* Task 2 */ });
  }
  ```

## 28. ZGC Improvements (Java 20)
The Z Garbage Collector (ZGC) saw significant improvements in Java 20, making it even more efficient for low-latency applications.
- **Why it stayed**: ZGC helps reduce pause times, making it ideal for real-time applications.
- **Trick**: Use **ZGC** when low-latency is critical in your Java applications.


## 29. Shenandoah Garbage Collector (Java 12)
The Shenandoah Garbage Collector (GC) was introduced to reduce pause times, aiming to optimize the garbage collection process.
- **Why it stayed**: Its ability to minimize pause times makes it suitable for latency-sensitive applications.
- **Example**:
  ```bash
  java -XX:+UseShenandoahGC -jar app.jar
  ```


## 30. Record Patterns (Java 19, Finalized in Java 21)
Record patterns allow deconstruction of records in `instanceof` expressions, making it easier to work with data.
- **Why it stayed**: It simplifies the process of destructuring records, improving code clarity.
- **Example**:
  ```java
  if (obj instanceof Point(var x, var y)) {
      System.out.println("x: " + x + ", y: " + y);
  }
  ```

