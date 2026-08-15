
### . What is the difference between a class and an object?

**Answer:**

- A **class** is a blueprint or template.
- An **object** is an instance of that class occupying memory.

Example:

```
class Student {}      // Class

Student s = new Student();   // Object
```

---

### 2. When is a constructor called?

**Answer:**  
A constructor is **automatically called when an object is created** using the `new` keyword.

```
Student s = new Student();
```

###  3. Can a constructor be private

Yes. A constructor **can be private**.

A private constructor means **objects of the class cannot be created from outside the class** using `new`.

### Example

```
class Demo {
    private Demo() {
        System.out.println("Constructor called");
    }
}

public class Main {
    public static void main(String[] args) {
        Demo d = new Demo();   // ❌ Compile-time error
    }
}
```

The compiler gives an error because the constructor is not accessible.

---

## Why use a private constructor?

### 1. Singleton Design Pattern (Most common interview answer)

A singleton ensures **only one object** of a class can exist.

```
class Singleton {
    private static Singleton obj = new Singleton();

    private Singleton() { }

    public static Singleton getInstance() {
        return obj;
    }
}

public class Main {
    public static void main(String[] args) {
        Singleton s1 = Singleton.getInstance();
        Singleton s2 = Singleton.getInstance();

        System.out.println(s1 == s2); // true
    }
}
```

Since the constructor is private, no one can do:

```
Singleton s = new Singleton(); // ❌ Error
```

They must use `getInstance()`.

### 4. Can a constructor return a value?

**Answer:**  
**No.**

A constructor has **no return type**, not even `void`.

Wrong:

```
public void Student() {}
```

Correct:

```
public Student() {}
```

### 5. Can a class have multiple constructors?

**Answer:**  
**Yes.**

This is called **constructor overloading**.

Example:

```
Student(){}

Student(String name){}

Student(String name,int age){}
```

### 7. What happens if you don't write any constructor?

**Answer:**  
The compiler automatically creates a **default constructor**.
### 8. What is the purpose of `this`?

**Answer:**

`this` refers to the **current object**.

It is mainly used to distinguish instance variables from method parameters.

### 9. Why do we make variables private?

**Answer:**

To achieve **encapsulation**.

Benefits:

- Protect data
- Prevent direct modification
- Control access using getters/setters

---

### 10. Can an object access private variables directly?

**Answer:**
**No.**

### 11) Note 
```
StringBuilder sb = new StringBuilder("Hello");

String s = sb.toString();
```
## Step 1

```
StringBuilder sb = new StringBuilder("Hello");
```

### Heap Memory

```
             Heap
+-----------------------------+
| StringBuilder Object        |
| value = "Hello"             |
+-----------------------------+
            ▲
            |
           sb
```

- A **StringBuilder object** is created.
- `sb` points to it.

---

## Step 2

```
String s = sb.toString();
```

The JVM calls the built-in `toString()` method.

Internally (simplified), it behaves like this:

```
public String toString() {
    return new String(value);
}
```

Notice the keyword:

```
new String(...)
```

This creates a **brand new String object**.

---

## After `toString()`

```
             Heap

+-----------------------------+
| StringBuilder Object        |
| value = "Hello"             |
+-----------------------------+
            ▲
            |
           sb


+-----------------------------+
| String Object               |
| "Hello"                     |
+-----------------------------+
            ▲
            |
            s
```

Now there are **two different objects**:

1. **StringBuilder**
2. **String**

---

## Are they the same object?

No.

```
sb
```

points here:

```
StringBuilder
```

while

```
s
```

points here:

```
String
```

Different classes.  
Different objects.

# Interview Questions

### Why are packages used?

- Organize classes.
- Avoid naming conflicts.
- Provide access control.
- Improve maintainability.

---

### What is the difference between a package and a folder?

A package is a **Java namespace**, while a folder is a **file system directory**. In practice, Java packages usually map to folders, but conceptually they represent namespaces for organizing code.

---

### Is `java.lang` imported automatically?

**Yes.**

That's why you can use:

```
String
System
Math
Object
```

without writing an `import` statement.

---

### Do we need to import classes from the same package?

**No.**

Classes in the same package can use each other directly.

---

## Quick Summary

- A **package** is a namespace used to organize related Java classes and interfaces.
- It helps prevent **name conflicts** and keeps large projects organized.
- Java provides **built-in packages** (like `java.util`) and you can create **user-defined packages**.
- Use the `package` keyword to declare a package and the `import` keyword to use classes from another package.
- `java.lang` is imported automatically, while most other packages require an explicit `import`


# Questions
1. What is inheritance?
2. Why is inheritance used?
3. What is a parent class (superclass)?
4. What is a child class (subclass)?
5. What is an IS-A relationship?
6. Why is inheritance considered code reusability?
7. Give five real-world examples of inheritance.
8. Why can't a parent class access child-specific members directly?
9. Why can a child class access parent members?
10. Why is inheritance called an IS-A relationship instead of HAS-A?
11. When should you use inheritance and when should you not?
12. Why doesn't Java support multiple inheritance using classes?
13. What problems would multiple inheritance create?
14. What is the purpose of the extends keyword?
15. Why doesn't Java automatically inherit every class?
16. What members are inherited?
17. What members are not inherited?
18. Why are constructors not inherited?
19. What would happen if constructors were inherited?
20. Can constructors be overridden? Why?
21. Can constructors be inherited? Why?
22. Can a child class exist without extending another class?
23. What is the default superclass of every Java class?
24. Does every class indirectly inherit Object?
25. What happens internally when a child object is created?
26. How many objects are created when a child object is created?
27. Does a child object contain the parent's variables?
28. Does the parent object exist separately?
29. Who creates the parent portion of a child object?
30. At what exact stage is the parent constructor executed?
31. Why does Java automatically insert super()?
32. Why must super() be the first statement?
33. What would happen if super() wasn't the first statement?
34. Can this() and super() appear together in one constructor?
35. Can super() be used inside a method?
36. Can super be used inside a static method?
37. What does super actually refer to?
38. Can this and super refer to the same object?
39. Can super access static members?
40. Can super access constructors?
41. Why is this unavailable inside static methods?
42. Why is super unavailable inside static methods?
43. What is package?
44. Why are packages used?
45. What problems do packages solve?
46. What would happen if Java had no packages?
47. Difference between package and folder.
48. What is a built-in package?
49. What is a user-defined package?
50. Why are package names usually lowercase?
51. What is a sub-package?
52. Can one Java file belong to multiple packages?
53. Why must the package statement be the first statement?
54. Why do we import packages?
55. What does the * wildcard import?
56. Why doesn't import java.* import Scanner?
57. Why doesn't import java.util.* import java.util.concurrent.*?
58. Does * import sub-packages?
59. Why was Java designed this way?
60. Why is java.lang imported automatically?
61. Why isn't java.util imported automatically?
62. Can two packages contain classes with the same name?
63. How does Java differentiate between classes with the same name?
64. What is a Fully Qualified Name (FQN)?
65. Can classes in the same package use each other without importing?
66. Can a class import itself?
67. What happens if two imported packages contain classes with the same name?
68. Difference between class loading and object creation.
69. Difference between object creation and constructor execution.
70. Who loads a class?
71. When is a class loaded?
72. When is an object created?
73. Who allocates memory for an object?
74. Does a constructor create the object?
75. What is the job of the constructor?
76. At what exact point is memory allocated?
77. At what exact point is the constructor called?
78. At what exact point is the reference assigned?
79. What is the difference between static initialization and object initialization?
80. Why is there only one copy of a static variable?
81. Why can't static methods directly access instance variables?
82. Why can instance methods access static members?
83. Why is this available only in instance methods?
84. Why does Java allow static methods to be called using an object reference?
85. Should static methods be called using an object? Why?
86. Can static methods be overridden?
87. Can static methods be inherited?
88. Why can't constructors be static?
89. Can a class contain only static members?
90. Should objects be created for utility classes? Why?
91. Why is String immutable?
92. Why are StringBuilder and StringBuffer mutable?
93. Does modifying a StringBuilder affect the String Pool?
94. Does StringBuilder.toString() create a new object?
95. Does toString() return a pooled String?
96. What does intern() do?
97. Difference between String Pool objects and heap String objects.
98. Why are String literals stored in the String Pool?
99. Why doesn't Java automatically pool runtime-created Strings?
100. Explain the complete execution flow from writing Main.java to object creation by the JVM.



# Interview Questions

### Q1. Are constructors inherited?

---

### Q2. Why are constructors not inherited?

---

### Q3. Are private members inherited?

---

### Q4. Can a child access protected members from another package?

---

### Q5. Are static methods inherited?

---

### Q6. Are static blocks inherited?

---

### Q7. Which members are inherited only within the same package?

---

### Q8. Why are static blocks not inherited?

---

# Memory Tip

```
                    Parent Members
                          │
        ┌─────────────────┼─────────────────┐
        │                 │                 │
   Public           Protected        Package-private
     ✅                 ✅              ✅ (Same Package)
                                            ❌ (Different Package)

        │
        ▼

     Child Receives

--------------------------------------------

Private Members      ❌ Not Inherited
Constructors         ❌ Not Inherited
Static Blocks        ❌ Not Inherited

--------------------------------------------

Static Variables     ✅ Inherited
Static Methods       ✅ Inherited
```

> **Golden Rule:** A child class inherits **all accessible members** of the parent class. Constructors, private members, and static blocks are **never inherited**, while package-private members are inherited **only within the same package**.


