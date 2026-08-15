# Why are Strings Immutable in Java?

In Java, a `String` object cannot be modified after it is created. Whenever we perform an operation that appears to modify a string, Java actually creates a **new `String` object** instead of changing the existing one.

Example:

```
String s = "Hello";
s = s + " World";

System.out.println(s);
```

**Output:**

```
Hello World
```

The original string `"Hello"` is not modified. Instead, a new object `"Hello World"` is created, and `s` now refers to the new object.

---

# Reasons Why Strings are Immutable

## 1. Security

Strings are used to store many sensitive values in Java, such as:

- Usernames
- Passwords
- Database URLs
- Network addresses
- File paths

Example:

```
String url = "jdbc:mysql://localhost:3306/student";
```

Many parts of the JVM use this URL.

If strings were mutable:

```
url = "jdbc:mysql://hacker.com";
```

or if the object itself could be modified,

every class using that string would suddenly start connecting to the wrong database.

Because `String` is immutable, once created, its value cannot change, making Java much more secure.

---

## 2. String Constant Pool (Memory Efficiency)

Java stores string literals in a special memory area called the **String Constant Pool (SCP)**.

Example:

```
String s1 = "Java";
String s2 = "Java";
```

Instead of creating two separate objects, Java creates only one object.

```
        +------------+
s1 ---->|   "Java"   |
s2 ---->|            |
        +------------+
```

This saves memory.

Suppose strings were mutable.

```
s1 = s1.replace('J', 'K');
```

If the original object could change,

```
s1 -> "Kava"
s2 -> "Kava"
```

But we never intended to change `s2`.

Therefore, immutability allows safe sharing of objects inside the String Pool.

---

## 3. HashCode Caching

Strings are frequently used as keys in collections like `HashMap`.

Example:

```
HashMap<String, Integer> map = new HashMap<>();

map.put("Apple", 100);
```

When `"Apple"` is inserted, Java calculates its `hashCode()`.

If strings were mutable:

```
Apple
```

became

```
Mpple
```

the hash code would also change.

Now HashMap would search using the old hash code and fail to find the key.

Because strings are immutable, the hash code never changes.

Java even **caches** the hash code inside the String object, making repeated lookups faster.

---

## 4. Thread Safety

Suppose two threads use the same string.

```
String message = "Hello";
```

Thread A prints it.

Thread B also prints it.

If Thread A modified the string,

```
Hello
```

to

```
Yello
```

Thread B would suddenly see different data.

This creates synchronization problems.

Since strings are immutable, multiple threads can safely use the same String object without synchronization.

---

## 5. Class Loading

During class loading, Java stores class names as strings.

Example:

```
Class.forName("Student");
```

If `"Student"` could be modified,

```
Student
```

might become

```
Teacher
```

The JVM could load the wrong class, leading to serious errors.

Immutability prevents such issues.

---

## 6. Easier Caching

Because strings never change, Java can cache and reuse them.

Example:

```
String s1 = "Hello";
String s2 = "Hello";
```

Both variables point to the same object.

Java does not need to create duplicate objects repeatedly.

This improves memory usage and performance.

---

## 7. Predictable Behavior

Consider:

```
void display(String name)
{
    System.out.println(name);
}
```

Call:

```
String s = "Santosh";
display(s);
```

Inside `display()`, the string cannot be modified.

The method can safely assume the value remains `"Santosh"` throughout its execution.

This makes programs easier to understand and debug.

---

# What Happens When We Modify a String?

```
String s = "Hello";
```

Memory:

```
s
 |
 v
+---------+
| Hello   |
+---------+
```

Now:

```
s = s.concat(" World");
```

Java creates a **new object**.

```
Old Object

+---------+
| Hello   |
+---------+

New Object

+---------------+
| Hello World   |
+---------------+

s
 |
 v
+---------------+
| Hello World   |
+---------------+
```

The original `"Hello"` object remains unchanged.

---

# If Strings Are Immutable, How Do We Modify Text Efficiently?

Java provides **mutable** classes:

- `StringBuilder` (fast, not thread-safe)
- `StringBuffer` (thread-safe)

Example:

```
StringBuilder sb = new StringBuilder("Hello");
sb.append(" World");

System.out.println(sb);
```

**Output:**

```
Hello World
```

Here, the same object is modified without creating new objects.

---

## Interview/Exam Answer

**Strings are immutable in Java to provide security, enable the String Constant Pool for memory optimization, allow hash code caching for efficient `HashMap` operations, ensure thread safety, support secure class loading, and improve overall performance. Whenever a string is modified, Java creates a new `String` object instead of changing the existing one.**

# Interview Questions

### Q1. What is constructor chaining?

---

### Q2. Why does the parent constructor execute before the child constructor?

---

### Q3. What happens if you don't write `super()`?

---

### Q4. What happens if the parent has only a parameterized constructor?

---

### Q5. Can `this()` and `super()` be used in the same constructor?

---

### Q6. Why are constructors not inherited?

---

### Q7. What is the exact execution order when a child object is created?

---

### Q8. Does `super()` create the parent object?

---

### Q9. Who inserts the default `super()` call?

---

### Q10. What is the difference between `this()` and `super()` in constructor chaining?

---

# Memory Trick

```
Child Object Creation

Class Loading
      ↓
Static Initialization
      ↓
Memory Allocation
      ↓
Default Values
      ↓
Instance Variable Initialization
      ↓
Parent Constructor
      ↓
Child Constructor
      ↓
Reference Assigned
```

> **Golden Rule:** Constructors are **never inherited**, but they are **always chained**. Every child constructor ultimately calls a parent constructor using `super()`, ensuring that the parent part of the object is initialized before the child part.



---

# Interview Questions

### Q1. What is the `super` keyword?

---

### Q2. What are the uses of `super`?

---

### Q3. Why must `super()` be the first statement?

---

### Q4. Can `super()` be called inside a method?

---

### Q5. Can `super` be used inside a static method?

---

### Q6. Does `super()` create the parent object?

---

### Q7. What is the difference between `super` and `this`?

---

### Q8. What is the difference between `super()` and `this()`?

---

### Q9. When is `super.variable` required?

---

### Q10. When is `super.method()` required?



















> **Golden Rule:** Constructors are **never inherited**, but they are **always chained**. Every child constructor ultimately calls a parent constructor using `super()`, ensuring that the parent part of the object is initialized before the child part.
