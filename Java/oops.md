 
# Java OOP

> "Object-Oriented Programming (OOP) is a programming paradigm that organizes software around **objects**, which combine data (attributes) and behavior (methods)."

## Why OOP?

Before OOP, programs were written as a collection of functions. As applications grew larger, this became difficult to manage.

OOP solves these problems by promoting:

- Modularity
- Reusability
- Scalability
- Maintainability
- Security through encapsulation

## Real-Life Example

Imagine a **Car**.

A car has:

Attributes

- Brand
- Color
- Speed
- Fuel Level

Behaviors

- Start()
- Stop()
- Accelerate()
- Brake()

In Java:

```
class Car {
    String brand;
    String color;
    int speed;

    void start() {}
    void stop() {}
}
```

The class is the blueprint.

An object is the actual car.

---

## OOP Workflow

```
Class
      ↓
Object
      ↓
Fields (State)
Methods (Behavior)
```

## Advantages of OOP

- Easy to organize code
- Easier debugging
- Code reuse
- Better teamwork
- Easier testing
- Easier maintenance
- Closer to real-world modeling

---

## Disadvantages

- Slightly higher memory usage
- Can be overkill for very small programs
- Requires good design

## Where is OOP Used?

- Spring Boot Applications
- Android Apps
- Desktop Applications
- Game Development
- Banking Systems
- E-commerce Platforms
- Enterprise Software

## Key Takeaways

- OOP organizes programs using **objects**.
- Objects combine **data**(Attributes) and **behavior**(Methods).
- A **class** is a blueprint; an **object** is an instance of that blueprint.
- The four pillars of OOP are **Encapsulation, Inheritance, Polymorphism, and Abstraction**.
- Java is an object-oriented language built around these principles.

basic code
```
class Calculator
{
public int add(int n1,int n2)
{
int r=n1+n2;
return r;
}
}

public class Demo
{
public static void main(String args[])
{
int num1=4;
int num2=5;
Calculator calc=new Calculator();
int result=calc.add(num1,num2);
System.out.println(result);
}
}

```

->example explanation
## Step 1: Creating a Class

```
class Calculator
```

A **class** is a blueprint for creating objects.

Think of it like the design of a calculator. It defines what a calculator can do, but it is **not** an actual calculator.

---

## Step 2: Defining a Method

```
public int add(int n1, int n2)
```

This defines a method named `add`.

Breaking it down:

|Part|Meaning|
|---|---|
|`public`|Accessible from anywhere|
|`int`|Method returns an integer|
|`add`|Method name|
|`(int n1, int n2)`|Two integer parameters|

---

# Step 3: Method Body

```
int r = n1 + n2;
return r;
```

The method:

1. Adds `n1` and `n2`.
2. Stores the result in `r`.
3. Returns `r`.

If `n1 = 4` and `n2 = 5`:

```
r = 4 + 5
r = 9
```

Then:

```
return r;
```

returns `9`.

---

# Step 4: The Main Method

```
public static void main(String args[])
```

This is the **entry point** of every Java application.

Execution starts here.

---

# Step 5: Declaring Variables

```
int num1 = 4;
int num2 = 5;
```

Two integer variables are created and initialized.

Memory:

```
num1 → 4
num2 → 5
```

---

# Step 6: Creating an Object

```
Calculator calc = new Calculator();
```

This is one of the most important lines in OOP.

It has three parts:

```
Calculator
```

The **class name** (type of the object).

```
calc
```

The **reference variable**.

```
new Calculator()
```

Creates a new `Calculator` object in memory.

Memory representation:

```
Stack                    Heap
-----                    ----------------
calc ------------------> Calculator Object
```

The variable `calc` does **not** store the object itself. It stores a **reference (address)** to the object.

---

# Step 7: Calling a Method

```
int result = calc.add(num1, num2);
```

Here's what happens:

1. `calc` refers to the `Calculator` object.
2. Java finds the `add()` method in that object.
3. Passes:
    - `num1 = 4`
    - `num2 = 5`
4. The method returns `9`.
5. `result` stores `9`.

Memory:

```
result → 9
```

---

# Step 8: Printing the Result

```
System.out.println(result);
```

Output:

```
9
```

example 2:-
```

class Student {

    // Attributes (Instance Variables)
    String name;
    int age;

    // Method (Behavior)
    void display() {
        System.out.println("Name : " + name);
        System.out.println("Age  : " + age);
    }
}

public class Demo {
    public static void main(String[] args) {

        // Creating Object 1
        Student s1 = new Student();
        s1.name = "Santosh";
        s1.age = 19;

        // Creating Object 2
        Student s2 = new Student();
        s2.name = "Rahul";
        s2.age = 20;

        // Calling Methods
        s1.display();
        System.out.println();

        s2.display();
    }
}
```
### Output
`Name : Santosh`
`Age  : 19`

`Name : Rahul`
`Age  : 20`

## What happens at the back
```
Class (Loaded Once)

Student
│
├── name
├── age
└── display()

--------------------------------------------

Stack                          Heap
-----                          -------------------------

s1 ------------------------->  Student Object #1
                               name = "Santosh"
                               age = 19

s2 ------------------------->  Student Object #2
                               name = "Rahul"
                               age = 20
```

### Key Points

- A **class** is a blueprint.
- `Student` is the class.
- `s1` and `s2` are **reference variables** stored in the stack.
- `new Student()` creates an object in the heap.
- Every object has its **own copy** of instance variables (`name`, `age`).
- Multiple objects can be created from the same class.
- Methods (`display()`) define the behavior of the object.
### What is Method Overloading?

**Method overloading** means **having multiple methods with the same name in the same class, but with different parameter lists.**

The compiler decides which method to call based on the arguments you pass. This is called **compile-time polymorphism** or **static polymorphism**.

The parameter list can differ by:

- Number of parameters
- Type of parameters
- Order of parameters
### Code
```  
class Calc
{
    void add(int n1, int n2)
    {
        System.out.println(n1 + n2);
    }

    void add(int n1, int n2, int n3)
    {
        System.out.println(n1 + n2 + n3);
    }

    double add(double n1, int n2)
    {
        return n1 + n2;
    }
}

public class d
{
    public static void main(String args[])
    {
        Calc c = new Calc();

        c.add(1, 2);

        c.add(1, 3, 4);

        double pus = c.add(9.01, 2);

        System.out.println(pus);
    }
}
```

## Instance Variables

An **instance variable** is declared **inside a class but outside any method, constructor, or block**.

- Belongs to an **object (instance)** of the class.
- Every object gets its own copy.
- Created when the object is created.
- Destroyed when the object is destroyed.
- Gets **default values** automatically.

### Example

```
class Student
{
    String name;    // Instance variable
    int age;        // Instance variable

    void display()
    {
        System.out.println(name + " " + age);
    }
}

public class Demo
{
    public static void main(String args[])
    {
        Student s1 = new Student();

        s1.name = "Santosh";
        s1.age = 19;

        s1.display();
    }
}
```
## . Local Variables

A **local variable** is declared **inside a method, constructor, or block**.

- Exists only inside that method/block.
- Created when the method starts.
- Destroyed when the method ends.
- **No default value**—you must initialize it before using it.

### Example

```
class Calculator
{
    void add()
    {
        int a = 10;      // Local variable
        int b = 20;      // Local variable

        int sum = a + b; // Local variable

        System.out.println(sum);
    }
}

public class Demo
{
    public static void main(String args[])
    {
        Calculator c = new Calculator();
        c.add();
    }
}
```

Here,

- `a`
- `b`
- `sum`

are all **local variables** because they exist only inside the `add()` method.

- `Instance variable = belongs to an object.`
- `Local variable = belongs to a method.`


A **method is not stored as a stack**. Instead:

- **The method's code** is stored once in the **Method Area** (part of the JVM memory).
- **When the method is called**, the JVM creates a **stack frame** for that method on the **Thread Stack**.
---

### Example

```
class Demo
{
    void add()
    {
        int a = 10;
        int b = 20;
        int sum = a + b;

        System.out.println(sum);
    }

    public static void main(String args[])
    {
        Demo d = new Demo();
        d.add();
    }
}
```

### Before execution

```
Method Area
--------------------
main()
add()
```

The code for `main()` and `add()` is stored here.

---

### When `main()` starts

```
Thread Stack
--------------------
|   main() Frame    |
--------------------
```

A **stack frame** is created for `main()`.

---

### When `main()` calls `add()`

```
Thread Stack
--------------------
|    add() Frame    |  <-- Top of stack
|-------------------|
|   main() Frame    |
--------------------
```

The `add()` frame contains:

- Local variables (`a`, `b`, `sum`)
- Parameters (if any)
- Return address (where to go after finishing)

---

### After `add()` finishes

The `add()` frame is popped off the stack.

```
Thread Stack
--------------------
|   main() Frame    |
--------------------
```

When `main()` finishes, its frame is also removed.

---

## Where everything is stored

|Memory Area|Stores|
|---|---|
|**Method Area**|Class information, method bytecode, static variables|
|**Heap**|Objects created using `new`|
|**Stack**|One stack frame per method call (local variables, parameters, return address)|

### Important interview point

- ❌ **Methods are not created as stacks.**
- ✅ **Methods are stored in the Method Area.**
- ✅ **Each time a method is called, the JVM creates a stack frame for it on the thread's stack.**

This distinction is fundamental to understanding Java memory management.
### Note1
If the stack frames are created for then where exactly is the stack

Let's use your code.

```
class Demo
{
    void add()
    {
        int a = 10;
        int b = 20;
        int sum = a + b;

        System.out.println(sum);
    }

    public static void main(String args[])
    {
        Demo d = new Demo();
        d.add();
    }
}
```

---

# JVM Memory

When this program runs, the JVM mainly uses these memory areas:

```
+--------------------------------------+
|          Method Area                 |
|--------------------------------------|
| Demo class                           |
| main() bytecode                      |
| add() bytecode                       |
+--------------------------------------+

+--------------------------------------+
|               Heap                   |
|--------------------------------------|
| Demo Object                          |
+--------------------------------------+

+--------------------------------------+
|         Thread Stack                 |
|--------------------------------------|
| Stack Frame of add()                 |
|--------------------------------------|
| Stack Frame of main()                |
+--------------------------------------+
```

Notice that **the stack is not inside the object or inside the class**. It is a **separate memory area** maintained by the JVM.

---

# Step 1 : Class is Loaded

When you run

```
java Demo
```

the JVM loads the class.

```
Method Area
-------------------------
Demo Class
main()
add()
```

No object exists yet.

No stack frame for `add()` exists.

---

# Step 2 : main() Starts

The JVM begins execution with

```
public static void main(...)
```

It creates a stack frame.

```
Thread Stack

------------------------
|       main()         |
------------------------
```

Inside this frame are

```
args
d (reference variable)
```

Currently

```
d = null
```

---

# Step 3 : Object Creation

Now

```
Demo d = new Demo();
```

creates an object.

```
Heap

------------------
Demo Object
------------------
```

The variable `d` is **not** inside the object.

It is inside the **main() stack frame**.

```
Stack

------------------------
main()
------------------------
d -----------+
             |
             |
Heap         |
------------------
Demo Object
------------------
```

---

# Step 4 : d.add()

Now

```
d.add();
```

The JVM creates **another stack frame**.

```
Thread Stack

------------------------
add()
a
b
sum
------------------------
main()
d
------------------------
```

Notice something important.

The stack now has **two frames**.

The top frame is always the currently executing method.

---

Inside the `add()` frame

```
a = 10
b = 20
sum = 30
```

So

```
Thread Stack

------------------------
add()

a = 10
b = 20
sum = 30
------------------------
main()

d --------+
------------------------
```

---

# Step 5 : add() Finishes

When execution reaches

```
}
```

the entire frame disappears.

```
Thread Stack

------------------------
main()

d --------+
------------------------
```

Variables

```
a
b
sum
```

are completely destroyed.

---

# Step 6 : main() Ends

After

```
}
```

the `main()` frame is also removed.

The stack becomes empty.

```
Thread Stack

(empty)
```

The object on the heap becomes unreachable because nothing references it anymore, so Java's **Garbage Collector** can reclaim that memory later.

---

# Final Memory Picture While `add()` Is Running

```
                    JVM MEMORY

+------------------------------------------+
|              Method Area                 |
|------------------------------------------|
| Demo Class                               |
| main()                                   |
| add()                                    |
+------------------------------------------+

+------------------------------------------+
|                 Heap                     |
|------------------------------------------|
| Demo Object                              |
+------------------------------------------+

+------------------------------------------+
|              Thread Stack                |
|------------------------------------------|
| add() Frame                              |
|   a = 10                                 |
|   b = 20                                 |
|   sum = 30                               |
|------------------------------------------|
| main() Frame                             |
|   d ------------------------------+      |
+-----------------------------------|------+
                                    |
                                    v
                             Demo Object
```

## The key idea

Many beginners imagine that **each method has its own permanent stack**. That's **not** how it works.

- The **code** for `add()` exists once in the **Method Area**.
- Every time `add()` is **called**, the JVM creates a **temporary stack frame** for that call on the **thread's stack**.
- When the method returns, that stack frame is removed.

So there is **one stack per thread**, and **each method call pushes a new frame onto that stack**. That's why it's called a **call stack**.



### Note2
a reference variable can be **either local, instance, or static**.

### 1. Local Reference Variable

Declared inside a method.

```
class Student
{
}

public class Demo
{
    public static void main(String args[])
    {
        Student s = new Student();   // Local reference variable
    }
}
```

- `s` is a **reference variable**.
- It is **local** because it is declared inside `main()`.
- `s` lives on the **stack**.
- The `Student` object lives on the **heap**.

```
Stack                  Heap
------                 ----------------
s -------------------> Student Object
```

---

### 2. Instance Reference Variable

Declared inside a class but outside methods.

```
class Student
{
}

class College
{
    Student s = new Student();   // Instance reference variable
}
```

Here:

- `s` is still a **reference variable**.
- It is an **instance variable** because it belongs to every `College` object.

```
Heap
--------------------------------
College Object
    |
    | s
    v
Student Object
```

---

### Another Example

```
class Car
{
    Engine e;    // Instance reference variable

    void start()
    {
        Engine x = new Engine();   // Local reference variable
    }
}
```

- `e` → **Instance reference variable**
- `x` → **Local reference variable**

---

## Simple Rule
A variable has **two properties**:

1. **What does it store?**
    - Primitive value (`int`, `double`, `char`, etc.)
    - Reference to an object (`Student`, `Car`, `String`, etc.)
2. **Where is it declared?**
    - Inside a method → **Local variable**
    - Inside a class, outside methods → **Instance variable**
    - With `static` → **Static variable**

So when you write:

```
Student s = new Student();
```

- `Student` → Reference type
- `s` → Reference variable
- If inside a method → **Local reference variable**
- If inside a class (outside methods) → **Instance reference variable**

This distinction is asked very often in Java interviews, so it's worth remembering.

### Note
local variable is part of the stack and instance variable is part of the heap

### Here's a simple example that declares both **instance variables** and **local variables**, then prints them from `main()`
```
class Student
{
    // Instance variables
    int age = 19;
    String name = "Santosh";

    public static void main(String args[])
    {
        // Local variables
        int x = 10;
        String city = "Hyderabad";

        // Creating an object
        Student s = new Student();

        // Printing instance variables
        System.out.println("Age: " + s.age);
        System.out.println("Name: " + s.name);

        // Printing local variables
        System.out.println("x: " + x);
        System.out.println("City: " + city);
    }
}
```

### Output

```
Age: 19
Name: Santosh
x: 10
City: Hyderabad
```

---

## Memory Layout

```
                 JVM MEMORY

Method Area
-------------------------
Student class
main()

Heap
-------------------------
Student Object
---------------
age = 19
name = "Santosh"

Thread Stack
-------------------------
main() Frame
-------------
x = 10
city = "Hyderabad"
s --------------------+
                      |
                      |
                      v
                Student Object
```

### Observe carefully:

- `age` and `name` are **instance variables**, so they are stored **inside the object on the heap**.
- `x`, `city`, and `s` are **local variables**, so they are stored **in the `main()` stack frame**.
- `s` does **not** contain the object—it only stores a **reference** to the object in the heap.

This example is one of the best ways to visualize the difference between **instance variables (heap)** and **local variables (stack)**.

#  Encapsulation 
Bundling variables and methods that operate on that data into a single unit(class),while restricting direct access to the data

Hide the data and give controlled access to it
## Without Encapsulation ❌

```
class Student {
    public String name;
    public int age;
}

public class Main {
    public static void main(String[] args) {
        Student s = new Student();

        s.name = "Santosh";
        s.age = 100;    // Invalid age!
    }
}
```

### Problem
Anyone can modify the variables directly, even with invalid values.

## Real-life analogy

Think of an **ATM**.

- Your bank balance is **private**.
- You **cannot** directly change it.
- You interact through methods:
    - Withdraw
    - Deposit
    - Check Balance

The ATM controls what operations are allowed.

That's encapsulation.
 
### Note
so thing with the encapsulation is that you should use methods to access and modify data

```
class Human
{
    private String name;
    private int age;

    public void setname(String x)
    {
        name = x;
    }

    public void setage(int y)
    {
        age = y;
    }

    public String getname()
    {
        return name;
    }

    public int getage()
    {
        return age;
    }
}

public class demo
{
    public static void main(String args[])
    {
        Human h = new Human();

        h.setname("santosh");
        h.setage(19);

        System.out.println(h.getname());
        System.out.println(h.getage());
    }
}
```

the below code is the same as above
```
class Human {
    private String name;
    private int age;

    public void setName(String name) {
        this.name = name;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }
}

public class Demo {
    public static void main(String[] args) {
        Human h = new Human();

        h.setName("Santosh");
        h.setAge(19);

        System.out.println(h.getName());
        System.out.println(h.getAge());
    }
}
```

# this keyword

## Why use this keyword

Because it's much cleaner and easier to read.
this keyword refers to the current object.it is primarily used to distinguish between the instance variables and the method parameters when they have the  same name

## To initialize  default values when you are creating an object
### method 1
```
class Human
{
    private String name = "Santosh";
    private int age = 19;

    public String getname()
    {
        return name;
    }

    public int getage()
    {
        return age;
    }
}

public class demo
{
    public static void main(String args[])
    {
        Human h = new Human();

        System.out.println(h.getname());
        System.out.println(h.getage());
    }
}
```

### method 2(A default constructor)
A constructor is automatically called when you create a object.
A constructor has the same name as a class name
```
class Human
{
    private String name;
    private int age;

    public Human()
    {
        name = "Santosh";
        age = 19;
    }

    public String getname()
    {
        return name;
    }

    public int getage()
    {
        return age;
    }
}

public class demo
{
    public static void main(String args[])
    {
        Human h = new Human();

        System.out.println(h.getname());
        System.out.println(h.getage());
    }
}
```

## Parametrized constructor
```
class Human
{
    private String name;
    private int age;

    public Human(String name,int age) //Parametrized constructor
    {
        this.name =name;
        this.age = age;
    }

    public String getname()
    {
        return name;
    }

    public int getage()
    {
        return age;
    }
}

public class demo
{
    public static void main(String args[])
    {
        Human h = new Human("Santosh",19);

        System.out.println(h.getname());
        System.out.println(h.getage());
    }
}
```

## Note
A constructor is automatically called when you create a object even if you don't mention it.
## Constructor chaining
```
class Stud {
    String name;
    int age;

    // No-argument constructor
    Stud() {
        this("Santosh");
        System.out.println("No-argument constructor called");
    }

    // One-argument constructor
    Stud(String name) {
        this(name, 18);
        System.out.println("One-argument constructor called");
    }

    // Two-argument constructor
    Stud(String name, int age) {
        this.name = name;
        this.age = age;
        System.out.println("Two-argument constructor called");
    }

    void display() {
        System.out.println("Name : " + name);
        System.out.println("Age  : " + age);
    }
}

public class Constructor {
    public static void main(String[] args) {
        Stud s = new Stud();
        s.display();
    }
}
```
now all the initialization  happens at a single place
Constructor chaining is used to avoid code duplication and centralize object initialization. It does not create multiple objects; it only invokes another constructor on the same object using `this()`.


# Static Keyword
Static means it  belongs to the class not to an individual object.
Avoid calling the static variables with objects ,the static variables should be accessed in a static way so access them with Class name.
Static variables are shared by different objects and the value is same for all.
## With `static`

Suppose every student belongs to the same college.

```
class Student {
    String name;
    static String college = "KLU";
}
```

Now:

```
Student s1 = new Student();
Student s2 = new Student();
```

Memory becomes:

```
Student Class
-------------
college = "KLU"   <-- only ONE copy

Object s1
---------
name

Object s2
---------
name
```
There is **only one `college` variable**, shared by every object.

If you do

```
Student.college = "IIT";
```

then

```
s1.college -> IIT
s2.college -> IIT
```

Both see the updated value because they're sharing the same variable.

## Static Variables

```
class Student {
    static int count = 0;

    Student() {
        count++;
    }
}
```

```
Student s1 = new Student();
Student s2 = new Student();
Student s3 = new Student();

System.out.println(Student.count);
```

Output:

```
3
```

Every constructor increments the **same** variable.

## Static Methods

A method can also belong to the class.

```
class MathUtil {

    static int square(int x) {
        return x * x;
    }

}
```

Call it like this:

```
MathUtil.square(5);
```

You don't create an object, No

### main () method
```
MathUtil m = new MathUtil();
m.square(5);
```

Instead main() method
```
MathUtil.square(5);
```

because the method belongs to the class itself.


### Note
You can use static variables inside static methods, but you cannot directly use non-static variables inside static methods. This is because non-static variables have different values for different objects. When a static method is called using the class name, an error occurs if you try to access a non-static variable because the static method is not associated with any object. Therefore, Java doesn't know which object's variable it should access.



## Static Methods and Non-Static Variables

### Rule

- A **static method** belongs to the **class**.
- A **non-static variable** belongs to an **object**.
- Therefore, a **static method cannot directly access a non-static variable** because it has no object (`this`) associated with it.
- However, a **static method can access a non-static variable indirectly by using an object reference**.

---

### Example 1: Direct Access (❌ Not Allowed)

```
class Student {

    // Static variable
    static String college = "KLU";

    // Non-static variables
    String name;
    int age;

    Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    static void display() {
        // ✅ Direct access to static variable
        System.out.println("College: " + college);

        // ❌ Compile-time Errors
        System.out.println(name);
        System.out.println(age);
    }

    public static void main(String[] args) {

        Student s1 = new Student("Santosh", 19);
        Student s2 = new Student("Rahul", 20);

        Student.display();
    }
}
```

---

### Example 2: Indirect Access Using an Object (✅ Allowed)

```
class Student {
    int age = 20;

    static void display() {
        Student s = new Student();
        System.out.println(s.age);   // ✅ Allowed
    }

    public static void main(String[] args) {
        display();
    }
}
```

**Output**

```
20
```

**Reason:**  
Here Java knows to access the `age` variable of object `s`.

---

### Example 3: Passing an Object (✅ Allowed)

```
class Student {
    int age = 20;

    static void display(Student s) {
        System.out.println(s.age);
    }

    public static void main(String[] args) {
        Student obj = new Student();
        display(obj);
    }
}
```

**Output**

```
20
```

---

### Example 4: Static Variable in Static Method (✅ Allowed)

```
class Student {
    static int count = 10;

    static void display() {
        System.out.println(count);   // ✅ Allowed
    }

    public static void main(String[] args) {
        display();
    }
}
```

**Output**

```
10
```

**Reason:**  
Both `count` and `display()` belong to the class.

---

## Why Java Doesn't Allow Direct Access

```
class Student {
    int age;

    static void display() {
        System.out.println(age); // ❌ Which object's age?
    }
}
```

Suppose:

```
Student s1 = new Student();
s1.age = 20;

Student s2 = new Student();
s2.age = 30;
```

Now there are two different values:

```
s1.age = 20
s2.age = 30
```

If Java allowed:

```
System.out.println(age);
```

which value should it print?

- `20`?
- `30`?

Since `display()` has **no object (`this`)**, Java cannot decide. Therefore, it gives a compile-time error.

---

## Interview Note

> **A static method cannot directly access non-static variables because static methods belong to the class, whereas non-static variables belong to objects. Since a static method has no object (`this`), Java doesn't know which object's variable to access. However, it can access non-static variables indirectly through an object reference.**

⭐ **Memory Trick**

- **Static → Class → No object → No `this`**
- **Non-static → Object → Needs an object**
- **No object = No direct access**
- **Object available = Indirect access allowed**

## Why is `main()` static?

```
public static void main(String[] args)
```

The JVM starts your program before creating any objects.

Since there is no object yet, the JVM needs a method it can call directly.

That's why `main()` is `static`.

## Static Block

```
class Demo {

    static {
        System.out.println("Runs first");
    }

    public static void main(String[] args) {
        System.out.println("Main");
    }

}
```

Output:

```
Runs first
Main
```

Static blocks execute only **once** when the class is loaded.

### Note
the class is loaded when you are creating an object, and the static block is only called once because it only gets called when the class is loaded and when you create an object that particular class is loaded, there is something called as the class loader

#### Class Loader
The **Class Loader** is another very important Java concept. It is **not directly part of OOP**, but it's part of how the **JVM works**.

Think of it like this:

> **A Class Loader loads `.class` files into the JVM's memory.**

---

## What happens when you run a Java program?

Suppose you have:

```
class Student {

    static {
        System.out.println("4. Student class loaded (Static Block)");
    }

    Student() {
        System.out.println("5. Student object created (Constructor)");
    }
}

public class Main {

    static {
        System.out.println("2. Main class loaded (Static Block)");
    }

    public static void main(String[] args) {

        System.out.println("3. main() started");

        Student s = new Student();

        System.out.println("6. Program ends");
    }
}
```

When you run it:

```
1. You write Main.java and Student.java
            ↓
2. javac compiles them
            ↓
3. Main.class and Student.class are created
            ↓
4. You run: java Main
            ↓
5. JVM starts
            ↓
6. Class Loader loads Main.class
            ↓
7. JVM verifies and prepares Main.class
            ↓
8. Static variables and static blocks of Main execute
            ↓
9. JVM calls main()
            ↓
10. main() executes
         ↓
11. Student s = new Student();
        ↓
12. Class Loader loads Student.class (if not already loaded)
        ↓
13. JVM initializes Student class (static variables and static blocks)
        ↓
14. Memory is allocated for the object
        ↓
15. Instance variables get default values
        ↓
16. Instance variable initializers execute
        ↓
17. Constructor executes
        ↓
18. Reference to the fully initialized object is assigned to s
```

Notice something:

**The class must be loaded before you can create an object of it.**

---


## What exactly does the Class Loader do?

It:

- Finds the `.class` file.
- Reads the bytecode.
- Loads it into JVM memory.
- Makes it available for execution.

Without the Class Loader, the JVM doesn't even know your class exists.

---    

## Types of Class Loaders

There are **three main class loaders**.

### 1. Bootstrap Class Loader

Loads Java's core classes.

Examples:

```
String
Object
Math
System
ArrayList
```

These come from the JDK itself.

---

### 2. Platform (Extension) Class Loader

Loads platform libraries.

Examples:

```
java.sql
java.xml
javax.*
```

---

### 3. Application (System) Class Loader

Loads **your own classes**.

Example:

```
Student
Employee
Main
Bank
```

Anything you write is usually loaded by the Application Class Loader.

---

---

## Why does `static` come before `main()`?

Suppose you have:

```
class Demo {

    static {
        System.out.println("Static Block");
    }

    public static void main(String[] args) {
        System.out.println("Main");
    }
}
```

Output:

```
Static Block
Main
```

Why?

When the **Class Loader loads the class**, the JVM initializes it. During initialization, **static variables and static blocks are executed once**. Only after that does the JVM invoke the `main()` method.
 
---

## Interview question

**Q: Who loads `String.class`?**

**Answer:** Bootstrap Class Loader.

---

**Q: Who loads your `Student.class`?**

**Answer:** Application (System) Class Loader.

---

## One-line definition

> **A Class Loader is a JVM component responsible for loading `.class` files (bytecode) into memory before the JVM executes them.**
### So who does what?

**Class Loader's job:**

- Find the `.class` file.
- Read the bytecode.
- Load it into JVM memory.

It **does not execute your Java code.**

**JVM's job:**

- Verify the loaded class.
- Allocate memory.
- Run static initialization.
- Call `main()`.
- Execute every Java statement.
## Static Class (Nested Class)

Only **nested classes** can be static.

```
class Outer {

    static class Inner {

    }

}
```

A top-level class cannot be declared `static`.

---

## When should you use `static`?

Use it when something is **common to every object**.

Examples:

- `Math.PI`
- `Math.sqrt()`
- Student college name
- Object counter
- Utility methods
- `main()`

## Quick Summary

| Member            | Belongs To | Copies                      |
| ----------------- | ---------- | --------------------------- |
| Instance variable | Object     | One per object              |
| `static` variable | Class      | One shared copy             |
| Instance method   | Object     | Called using an object      |
| `static` method   | Class      | Called using the class name |

### Variables

|Context|Static Variable|Non-static Variable|
|---|---|---|
|**Static context**|✅|❌ (directly)|
|**Non-static context**|✅|✅|

### Methods

|Context|Static Method|Non-static Method|
|---|---|---|
|**Static context**|✅|❌ (directly)|
|**Non-static context**|✅|✅|
## 1. Static Context → Static Variable ✅

```
class Demo {
    static int age = 20;

    static void show() {
        System.out.println(age);
    }
}
```

**Output**

```
20
```

---

## 2. Static Context → Non-static Variable ❌ (Directly)

```
class Demo {
    int roll = 101;

    static void show() {
        System.out.println(roll); // ERROR
    }
}
```

**Error**

```
non-static variable roll cannot be referenced from a static context
```

---

## 3. Static Context → Non-static Variable ✅ (Using an object)

```
class Demo {
    int roll = 101;

    static void show() {
        Demo d = new Demo();
        System.out.println(d.roll);
    }
}
```

**Output**

```
101
```

---

## 4. Non-static Context → Static Variable ✅

```
class Demo {
    static int age = 20;

    void display() {
        System.out.println(age);
    }
}
```

**Output**

```
20
```

---

## 5. Non-static Context → Non-static Variable ✅

```
class Demo {
    int roll = 101;

    void display() {
        System.out.println(roll);
    }
}
```

**Output**

```
101
```

---

## 6. Static Context → Static Method ✅

```
class Demo {

    static void hello() {
        System.out.println("Hello");
    }

    static void show() {
        hello();
    }
}
```

**Output**

```
Hello
```

---

## 7. Static Context → Non-static Method ❌ (Directly)

```
class Demo {

    void hello() {
        System.out.println("Hello");
    }

    static void show() {
        hello(); // ERROR
    }
}
```

**Error**

```
non-static method hello() cannot be referenced from a static context
```

---

## 8. Static Context → Non-static Method ✅ (Using an object)

```
class Demo {

    void hello() {
        System.out.println("Hello");
    }

    static void show() {
        Demo d = new Demo();
        d.hello();
    }
}
```

**Output**

```
Hello
```

---

## 9. Non-static Context → Static Method ✅

```
class Demo {

    static void hello() {
        System.out.println("Hello");
    }

    void display() {
        hello();
    }
}
```

**Output**

```
Hello
```

---

## 10. Non-static Context → Non-static Method ✅

```
class Demo {

    void hello() {
        System.out.println("Hello");
    }

    void display() {
        hello();
    }
}
```

> **A non-static context can access everything. A static context can directly access only static members.**

That single rule covers both **variables** and **methods**.


# Naming conventions

**Naming conventions** are **standard rules for naming classes, variables, methods, packages, constants, etc.** They are not enforced by Java, but every Java developer follows them to make code readable.

## 1. Class Names → Pascal Case

- First letter of every word is capitalized.

✅ Good

```
class Student { }
class BankAccount { }
class EmployeeDetails { }
```

❌ Bad

```
class student { }
class bank_account { }
class employee_details { }
```

---

## 2. Method Names → camelCase

- First word starts with lowercase.
- Every next word starts with uppercase.

✅ Good

```
getName()
calculateSalary()
displayStudent()
```

❌ Bad

```
GetName()
calculate_salary()
DisplayStudent()
```

---

## 3. Variable Names → camelCase

✅ Good

```
int age;
String firstName;
double accountBalance;
```

❌ Bad

```
int Age;
String First_Name;
```

---

## 4. Constants (`static final`) → UPPER_CASE

```
static final double PI = 3.14159;
static final int MAX_SIZE = 100;
static final String COLLEGE_NAME = "KLU";
```

---

## 5. Package Names → all lowercase

```
com.amazon.payment
java.util
java.io
org.springframework.boot
```

❌ Don't write

```
Com.Amazon.Payment
Java.Util
```

---

## 6. Interface Names → PascalCase

```
interface Animal { }

interface Runnable { }

interface Printable { }
```

---

## 7. Enum Names → PascalCase

```
enum Day {
    MONDAY,
    TUESDAY,
    WEDNESDAY
}
```

The **enum name** is PascalCase, while the **enum constants** are uppercase.

---

## 8. Object Names → camelCase

```
Student student1 = new Student();
Student student2 = new Student();

Scanner sc = new Scanner(System.in);
```

---

## 9. File Name

The file name must match the **public class name**.

```
public class Student {
}
```

File:

```
Student.java
```

---

## Summary Table

|Element|Convention|Example|
|---|---|---|
|Class|PascalCase|`Student`, `BankAccount`|
|Interface|PascalCase|`Runnable`, `Printable`|
|Enum|PascalCase|`Day`, `Color`|
|Method|camelCase|`getName()`, `display()`|
|Variable|camelCase|`firstName`, `studentAge`|
|Object|camelCase|`student`, `scanner`|
|Package|lowercase|`java.util`, `com.company.app`|
|Constant (`static final`)|UPPER_CASE|`MAX_SIZE`, `PI`|
# Packages
## Packages in Java

A **package** is a way of **grouping related classes, interfaces, enums, and sub-packages together**.

Think of it as a **folder** on your computer.

Just as folders organize files, **packages organize Java classes**.

---

## Why are Packages Used?

Packages help to:

- Organize code.
- Avoid naming conflicts.
- Provide access protection.
- Make projects easier to maintain.
- Group related classes together.

---

## Real-Life Analogy

Imagine your computer:

```
Documents
│
├── Photos
├── Movies
├── Music
└── Projects
```

Similarly, in Java:

```
com
│
└── company
    │
    ├── employee
    │      Employee.java
    │      Manager.java
    │
    ├── student
    │      Student.java
    │      Marks.java
    │
    └── library
           Book.java
```

Each folder is a **package**.

---

## Without Packages

Suppose you have:

```
Student.java
Student.java
Student.java
```

Which one is which?

Java wouldn't know.

---

## With Packages

```
college.student.Student
school.student.Student
company.student.Student
```

Now every class has a unique name.

## Declaring a Package

The **first line** of the Java file declares the package.

```
package com.company.employee;

public class Employee {

}
```

This means the `Employee` class belongs to the package:

```
com.company.employee
```
## Importing a Package

Suppose:

```
com.company.employee.Employee
```

To use it in another class:

```
import com.company.employee.Employee;
```

Now you can write:

```
Employee e = new Employee();
```
## Without Import

You must write the complete name.

```
com.company.employee.Employee e =
new com.company.employee.Employee();
```

## Built-in Packages

Java already provides many packages.

Some common ones are:

|Package|Purpose|
|---|---|
|`java.lang`|Basic classes (`String`, `Math`, `System`, `Object`)|
|`java.util`|Collections, Scanner, Random|
|`java.io`|File handling|
|`java.sql`|Database connectivity|
|`java.net`|Networking|
|`java.time`|Date and Time API|

---

## Example

```
import java.util.Scanner;
```

Here

- `java` → package
- `util` → sub-package
- `Scanner` → class

---

## Types of Packages

### 1. Built-in Packages

Provided by Java.

Examples:

- `java.util`
- `java.io`
- `java.net`
- `java.time`

---

### 2. User-defined Packages

Created by programmers.

Example:

```
package college.student;
```

---

## Package Naming Convention

Packages are usually written in **lowercase**.

Example:

```
com.google
com.amazon
com.microsoft
org.apache
```

---

## Relationship Between Packages and Classes

```
Package
│
├── Class A
├── Class B
├── Class C
└── Interface D
```

A package can contain:

- Classes
- Interfaces
- Enums
- Sub-packages

---

## Default Package

If you don't write a package statement:

```
public class Student {

}
```

the class belongs to the **default package**.

It has no package name.

---

## Common Imports

```
import java.util.*;
```

`java.util.*`-Imports all classes inside

the `*` is used when  you want to import all files from that particular package, it only imports files which are classes so when you wont mention the sub package which are stored as folders (util) and do something like this `import java.*;` the classes won't be imported.

Example:

- Scanner
- Array List
- LinkedList
- HashMap
- HashSet

---

## Fully Qualified Name (FQN)

Every Java class has a complete name.

Example:

```
java.util.Scanner
```

where:

- `java.util` → package
- `Scanner` → class

---


#  Access modifiers

Access modifiers  control who can access a class, variable ,method or a  constructor.

Imagine you have a house 
some rooms are open to everyone.
some are only for family
some are only for you

## Private
The most restrictive modifier
only same class can access it
```
class Student {

    private int age = 20;

    void display() {
        System.out.println(age);
    }

}
```
works  because display () is inside the main class
## Default(Package-private)
If you don't write anything  it will  be considered as default.
```
class Student {

    int age;

}
```
notice there is no keyword this is called as default access

```
college
│
├── Student.java
└── Test.java
```
so here a variable in the student class can be accessed by the class test.

## Public
Everyone can access it
any package and any class ,it is made public when it useful for everyone.

## Protected
### Definition

A `protected` member can be accessed:

- Within the **same class**
- By **all classes in the same package**
- By **subclasses**, even if they are in a different package
- **Not** by non-subclasses in a different package

---

## Access Rules

### 1. Same Class

✔ Accessible

### 2. Same Package

✔ Accessible, even without inheritance

### 3. Different Package + Subclass

✔ Accessible through inheritance

### 4. Different Package + No Inheritance

❌ Not accessible

The actual rule is:

> **The class accessing the `protected` member must itself be a subclass of the class that declares the `protected` member.**



|                                    | **Private** | **Protected** | **Public** | **Default** |
| ---------------------------------- | :---------: | :-----------: | :--------: | :---------: |
| **Same class**                     |      ✓      |       ✓       |     ✓      |      ✓      |
| **Same package subclass**          |      ✗      |       ✓       |     ✓      |      ✓      |
| **Same package non-subclass**      |      ✗      |       ✓       |     ✓      |      ✓      |
| **Different package subclass**     |      ✗      |       ✓       |     ✓      |      ✗      |
| **Different package non-subclass** |      ✗      |       ✗       |     ✓      |      ✗      |
## Note
### 1)In java a top level class can only be public or default(package-private)
- ✅ `public`
- ✅ _default_ (package-private, i.e., no modifier)

You **cannot** declare a top-level class as:

- ❌ `protected`
- ❌ `private`

Why?
protected is only meaningful only in the context of inheritance. A top level class is not a member of another class so protected doesn't apply.

However, nested(Inner) classes can be protected
```
public class Outer {

    protected class Inner {   // ✅ Valid
    }
}
```

### 2)In java a top level child class can only be  public or default(package-private).

```
class Parent {
}

protected class Child extends Parent { // ❌ Invalid
}

private class Child extends Parent {   // ❌ Invalid
}
```

However 
If the child is inside another class then it can be default, public protected and private.
```
public class Parent {

    protected class Child extends Parent {  // ✅ Valid
    }

    private class AnotherChild extends Parent { // ✅ Valid
    }
}
```

# Inheritance

Inheritance is the mechanism by which one class(child's) inherits the properties of  another class(parent's) so instead  of  writing the same code again the  child class reuses the existing properties of parent class it can add its own features as well.

**Syntax**

```
class Parent {
    // variables and methods
}

class Child extends Parent {
    // additional variables and methods
}
```

The keyword **`extends`** is used to inherit a class.

### Why is Inheritance Used?
reuse existing code
avoid code duplication
improve maintainability
build relationship between classes
support run time polymorphism

A **Parent Class** (also called a **Superclass** or **Base Class**) is the class whose properties and methods are inherited.

Example:

```
class Animal {

    void eat() {
        System.out.println("Animal is eating");
    }

}
```

Here, `Animal` is the parent class.

# Child Class (Subclass)

A **Child Class** (also called a **Subclass** or **Derived Class**) inherits the members of the parent class and can also have its own members.

Example:

```
class Dog extends Animal {

    void bark() {
        System.out.println("Dog is barking");
    }

}
```

Here:

- `Dog` is the child class.
- `Dog` automatically gets access to the `eat()` method.

# Code Reusability

Without inheritance:

```
Animal
-------
eat()

Dog
----
eat()
bark()

Cat
----
eat()
meow()
```

The `eat()` method would have to be written multiple times.

With inheritance:

```
          Animal
             |
      ----------------
      |              |
     Dog            Cat
```

- `Animal` contains `eat()`.
- `Dog` inherits `eat()` and adds `bark()`.
- `Cat` inherits `eat()` and adds `meow()`.

The common code is written only once.


# Real-World Examples

### Example 1

```
Vehicle
│
├── Car
├── Bike
└── Truck
```

Every vehicle can:

- Start
- Stop
- Accelerate

Each subclass can also have its own unique behavior.

---

### Example 2

```
Person
│
├── Student
├── Teacher
└── Employee
```

Common properties:

- Name
- Age
- Address

Specific properties:

Student

- Roll Number
- Branch

Teacher

- Subject
- Salary

Employee

- Employee ID
- Department

---

### Example 3

```
Animal
│
├── Dog
├── Cat
└── Lion
```

Common behavior:

- Eat
- Sleep
- Breathe

Unique behavior:

Dog

- Bark

Cat

- Meow

Lion

- Roar

### NOTE
- Inheritance allows one class to inherit the members of another class.
- The `extends` keyword is used for inheritance.
- Parent class = Superclass = Base class.
- Child class = Subclass = Derived class.
- Inheritance represents an **IS-A** relationship.
- Java supports **single inheritance** for classes (one parent class per child class).
- Inherited members include accessible fields and methods, but **constructors are not inherited** (though a child constructor can call a parent constructor using `super()`

   ### What gets inherited
   Knowing exactly what a child receives
   
  #### Inherited
  Public variables and public methods
  Protected variables and methods
  Package-private Variables and methods
  Static variables and  methods are inherited

#### Not inherited
Private variables and private methods
Static blocks and constructors

 Constructors are not inherited because they are used only to initialize the class when they are declared.

# 4. Types of Inheritance

Inheritance can be classified into different types based on how classes are related.

Java supports **Single**, **Multilevel**, and **Hierarchical** inheritance using classes.

Java **does not support Multiple and Hybrid inheritance using classes**.  
# 1. Single Inheritance

A child class inherits from only one parent class.

```
A
│
B
```

- `A` → Parent Class
- `B` → Child Class

### Example

```
class Animal {

    void eat() {
        System.out.println("Eating");
    }

}

class Dog extends Animal {

    void bark() {
        System.out.println("Barking");
    }

}
```

Here,

- Dog inherits from Animal.
- Dog can access the inherited `eat()` method and its own `bark()` method.
# 2. Multilevel Inheritance

A class inherits from another child class.

```
A
│
B
│
C
```

- `A` → Grandparent
- `B` → Parent
- `C` → Child

### Example

```
class Animal {

    void eat() {
        System.out.println("Eating");
    }

}

class Dog extends Animal {

    void bark() {
        System.out.println("Barking");
    }

}

class Puppy extends Dog {

    void play() {
        System.out.println("Playing");
    }

}
```

The `Puppy` class inherits:

- `play()` from itself
- `bark()` from `Dog`
- `eat()` from `Animal`

# 3. Hierarchical Inheritance

Multiple child classes inherit from the same parent.

```
      A
    / | \
   B  C  D
```

### Example

```
class Animal {

    void eat() {
        System.out.println("Eating");
    }

}

class Dog extends Animal {

}

class Cat extends Animal {

}

class Lion extends Animal {

}
```

Every child inherits:

- `eat()`

Each child may also have its own properties

# Multiple Inheritance (Not Supported Using Classes)
```
A      B
 \    /
   C
```

```
class A {

}

class B {

}

class C extends A, B {   // ❌ Compile-time Error

}

```

## Why doesn't  java support multiple inheritance?

The primary reason is the diamond pattern
```
      B   C
       \ /
        D
```

```
class B {
    void display() {
        System.out.println("B");
    }
}

class C {
    void display() {
        System.out.println("C");
    }
}

class D extends B, C {   // Assume Java allowed this
}
```

### What would happen if Java allowed this?

If you wrote:

```
D obj = new D();
obj.display();
```

The compiler would ask:

> **Which `display()` should I call?**

- `B.display()`?
- `C.display()`?

There is **ambiguity** because both parent classes define the same method with the same signature.

```
      B   C
       \ /
        D
Both B and C have display()
```

The compiler has no rule to decide automatically.

# 5. Hybrid Inheritance

Hybrid inheritance is a combination of two or more inheritance types.

Example:

```
          A
        /   \
       B     C
       │
       D
```

This combines:

- Hierarchical inheritance
- Multilevel inheritance

---

# Is Hybrid Inheritance Supported?

Using **classes**,

❌ No.

Because hybrid inheritance includes **multiple inheritance**, which Java does not allow.

---

# Can Hybrid Inheritance Be Achieved?

Yes.
Java achieves multiple inheritance through **interfaces**. so then hybrid can be acheived




# 5. Constructors in Inheritance

Constructors play a special role in inheritance. Although **constructors are not inherited**, whenever a child object is created, the **parent constructor always executes first**, followed by the child constructor.

This process is known as **constructor chaining**.


---

# Constructor Chaining

**Constructor chaining** is the process where constructors are executed from the **topmost parent class down to the child class** during object creation.

Every constructor calls another constructor until the topmost parent constructor is reached.

Java achieves this using the **`super()`** keyword.

# Why Constructor Chaining?

A child object contains both:

- Parent members
- Child members

Before the child can initialize its own part, the parent part must be initialized first.

Therefore,

**Parent Constructor**  
↓  
**Child Constructor**


# Parent Constructor

The constructor of the parent class is always executed before the child's constructor.

Example:

```
class Parent {

    Parent() {
        System.out.println("Parent Constructor");
    }

}

class Child extends Parent {

    Child() {
        System.out.println("Child Constructor");
    }

}
```

Output

```
Parent Constructor
Child Constructor
```

# Child Constructor

The child constructor executes **only after** the parent constructor has finished.

During object creation:

```
Child obj = new Child();
```

Execution order:

```
Memory Allocation
        ↓
Parent Constructor
        ↓
Child Constructor
        ↓
Reference Assigned
```


# Parameterized Constructor

Suppose the parent has only a parameterized constructor.

```
class Parent {

    Parent(int x) {
        System.out.println(x);
    }

}
```

This will not compile:

```
class Child extends Parent {

    Child() {

    }

}
```

Reason:

Java automatically inserts:

```
super();
```

But the parent **does not have** a no-argument constructor.

Compile-time Error.

Correct way:

```
class Child extends Parent {

    Child() {

        super(10);

    }
    
}
```

# Constructor Execution Order

Suppose Multiple level inheritance 

```
A
│
B
│
C
```
Constructors:

```
A()

B()

C()
```

Object Creation:
Object Creation:

```
C obj = new C();
```

Execution order:

```
Memory Allocation
        ↓
A()
        ↓
B()
        ↓
C()
        ↓
Reference Assigned
```

# Constructor Chaining with this()

Example:

```
class Child extends Parent {

    Child() {

        this(10);

    }

    Child(int x) {

        super();

    }

}
```

Execution:

```
Child()
      ↓
this(10)
      ↓
Child(int)
      ↓
super()
      ↓
Parent()
```

Eventually,

every constructor chain reaches a parent constructor.
# Rules of Constructor Chaining

### Rule 1

Every constructor calls another constructor.

---

### Rule 2

If you don't write `super()`, Java inserts it automatically.

---

### Rule 3

If you write `this()`, Java does **not** insert `super()` into that constructor.

Instead,

the constructor called through `this()` must eventually call `super()`.
### Rule 4

`this()` and `super()` cannot appear together in the same constructor.

❌ Invalid

```
Child() {

    this(10);

    super();

}
```

# Why Parent Constructor Executes First

A child object consists of:

```
+----------------------+
| Parent Members       |
+----------------------+
| Child Members        |
+----------------------+
```

The parent portion must be initialized before the child portion.

Hence,

```
Parent Constructor
        ↓
Child Constructor
```

---

# Constructors are NOT Inherited

```
class Parent {

    Parent() {

    }

}

class Child extends Parent {

}
```

The child does **not** inherit `Parent()`.

Instead,

the child constructor **calls** it using:

```
super();
```

---

# Complete Execution Flow

```
Child obj = new Child();
```

JVM Flow

```
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

---

# Summary Table

| Situation                                           | Result                                        |
| --------------------------------------------------- | --------------------------------------------- |
| Parent constructor executes first                   | ✅ Yes                                         |
| Child constructor executes first                    | ❌ No                                          |
| Constructors are inherited                          | ❌ No                                          |
| Child constructor can call parent constructor       | ✅ Yes (`super()`)                             |
| Java inserts `super()` automatically                | ✅ If not written                              |
| `super()` first statement                           | ✅ Mandatory                                   |
| `this()` and `super()` together in same constructor | ❌ Not Allowed                                 |
| Parent has only parameterized constructor           | Child must explicitly call `super(arguments)` |
# 6. `super` Keyword

The **`super`** keyword is a reference variable used inside a child class to refer to the **immediate parent class**.

It is mainly used for:

- Calling the parent constructor.
- Accessing parent variables.
- Calling parent methods.

---

# What is `super`?

`super` refers to the **immediate parent class** of the current object.

Example:

```
        Parent
           ↑
        Child
```

Inside `Child`:

- `this` → Current (Child) object
- `super` → Parent part of the current object

> **Important:** `super` does **not** refer to a separate parent object. It refers to the **parent portion of the current child object**.

# Uses of `super`

1. Calling the parent constructor.
2. Calling a parameterized parent constructor.
3. Accessing parent variables.
4. Calling parent methods.

# 1. Calling Parent Constructor

Syntax

```
super();
```

Used to call the parent's no-argument constructor.

Example

```
class Parent {

    Parent() {
        System.out.println("Parent Constructor");
    }

}

class Child extends Parent {

    Child() {

        super();

        System.out.println("Child Constructor");

    }

}
```

Output

```
Parent Constructor
Child Constructor
```

---

## Important Rules

- `super()` must always be the **first statement**.
- If you don't write it, Java inserts it automatically.
- It can only be used inside a constructor.

# 2. Calling Parameterized Parent Constructor

Syntax

```
super(10);
```

Example

```
class Parent {

    Parent(int x) {
        System.out.println(x);
    }

}

class Child extends Parent {

    Child() {

        super(10);

        System.out.println("Child");

    }

}
```

Output

```
10
Child
```
###  Note:
if there is no default parent constructor
If the child constructor is

```
Child() {

}
```

Java inserts

```
super();
```

Compile-time Error.

# 3. Accessing Parent Variables

Suppose both parent and child contain the same variable.

```
class Parent {

    int x = 10;

}

class Child extends Parent {

    int x = 20;

}
```

Inside the child

```
System.out.println(x);
```

prints

```
20
```

To access the parent's variable

```
System.out.println(super.x);
```

Output

```
10
```

# Can `super` Access Static Members?

Yes.

```
class Parent {

    static int x = 10;

}
```

```
System.out.println(super.x);
```

Works.

However, the recommended way is

```
Parent.x
```

because static members belong to the class.

---

# Can `super` Be Used in Static Methods?

❌ No.

Example

```
static void display() {

    super.show();

}
```

Compile-time Error.

Reason:

Static methods have no current object (`this`), therefore there is no parent reference (`super`).

---

# Can `super()` Be Used in Methods?

❌ No.

```
void display() {

    super();

}
```

Compile-time Error.

`super()` is a constructor call, so it is valid only inside constructors.

---

# Can `super()` and `this()` Be Together?

❌ No.

```
Child() {

    this(10);

    super();

}
```

Compile-time Error.

Reason:

Both must be the **first statement**.

---

# Constructor Chaining Using `super`

Suppose

```
A
│
B
│
C
```

Constructors

```
A()

B()

C()
```

Object creation

```
new C();
```

Execution

```
Memory Allocation
        ↓
A()
        ↓
B()
        ↓
C()
```

Every constructor reaches its parent through `super()`.

# `this` vs `super`

| `this`                                               | `super`                                                      |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| Refers to the current object                         | Refers to the immediate parent portion of the current object |
| Calls another constructor in the same class          | Calls a constructor of the parent class                      |
| Accesses current class variables                     | Accesses parent variables                                    |
| Calls current class methods                          | Calls parent methods                                         |
| Used when referring to the current class             | Used when referring to the parent class                      |
| Cannot be used in static methods                     | Cannot be used in static methods                             |
| `this()` calls another constructor in the same class | `super()` calls a parent constructor                         |

---

# `this()` vs `super()`

|`this()`|`super()`|
|---|---|
|Calls another constructor in the same class|Calls a parent constructor|
|Constructor chaining within the same class|Constructor chaining across inheritance|
|Must be the first statement|Must be the first statement|
|Cannot appear with `super()`|Cannot appear with `this()`|

---

# Summary Table

| Use                              | Syntax                                                        |
| -------------------------------- | ------------------------------------------------------------- |
| Parent constructor               | `super();`                                                    |
| Parameterized parent constructor | `super(value);`                                               |
| Parent variable                  | `super.variable;`                                             |
| Parent method                    | `super.method();`                                             |
| Parent static variable           | `super.variable` _(works but `Parent.variable` is preferred)_ |
| Parent static method             | `super.method()` _(works but `Parent.method()` is preferred)_ |





# Note(Variable hiding)
How that internals work if two classes have same variable names and they use inheritance ,how the usage of this and super works
# Example 1
```
package test;

class Vehicle {
    String name;

    Vehicle(String name) {
        this.name = name;
    }

    Vehicle() {
    }

    void display() {
        System.out.println(this.name);
    }
}

class Car extends Vehicle {
    String name;

    Car(String name) {
        this.name = name;
    }

    void display() {
        System.out.println(this.name);
        System.out.println(super.name);
        super.display();
    }
}

public class ex2 {
    public static void main(String args[]) {
        Vehicle v = new Vehicle("Porchse");
        Car c = new Car("911");

        c.display();
        v.display();
    }
}
```
## Step 1

```
Vehicle v = new Vehicle("Porchse");
```

Calls:

```
Vehicle(String name)
```

Execution:

```
this.name = name;
```

So:

```
Vehicle object

Vehicle.name = "Porchse"
```

---

## Step 2

```
Car c = new Car("911");
```

Your constructor is:

```
Car(String name)
{
    this.name = name;
}
```

Notice something important.

Since you **didn't write `super(...)`**, Java automatically inserts

```
super();
```

So internally it becomes:

```
Car(String name)
{
    super();      // inserted by Java
    this.name = name;
}
```

---

### First

```
super();
```

calls

```
Vehicle()
```

Your default constructor does nothing.

So

```
Vehicle.name = null  (Car's object)
```

---

### Then

```
this.name = name;
```

Which `name`?

Since you're inside **Car**,

```
this.name
```

means

```
Car.name
```

So now the object is

```
Car Object

---------------------
Vehicle.name = null
---------------------
Car.name = "911"
---------------------
```

---

## Step 3

```
c.display();
```

Runs

```
Car.display()
```

### First

```
System.out.println(this.name);
```

Inside Car,

```
this.name
```

means

```
Car.name
```

Output

```
911
```

---

### Next

```
System.out.println(super.name);
```

`super`

means

```
Vehicle.name (car's object)
```

which is

```
null
```

Output

```
null
```

---

### Next

```
super.display();
```

This executes

```
Vehicle.display()
```

Inside it

```
System.out.println(this.name);
```

Now here's the interesting part.

`this` is still the **Car object**.

But `Vehicle.display()` was compiled inside Vehicle.

So

```
this.name
```

is resolved to

```
Vehicle.name (Car's object)
```

NOT

```
Car.name
```

Vehicle.name is

```
null
```

Output

```
null
```

---

## Finally

```
v.display();
```

Vehicle.name

contains

```
Porchse
```

Output

```
Porchse
```

---

# Final Output

```
911
null
null
Porchse
```

## Example 2
```
package test;

class Vehicle {
    String name;

    Vehicle(String name) {
        this.name = name;
    }

    Vehicle() {
    }

    void display() {
        System.out.println(this.name);
    }
}

class Car extends Vehicle {
    String name;

    Car(String name) {
        super(name);
    }

    void display() {
        System.out.println(this.name);
        System.out.println(super.name);
        super.display();
    }
}

public class ex2 {
    public static void main(String args[]) {
        Vehicle v = new Vehicle("Porchse");
        Car c = new Car("911");

        c.display();
        v.display();
    }
}
```

### Output
```
null
911
911
porchse
```

### here this refers to the class whose object was created even though if you access super and in that parent constructor if you initialize the values using this keyword it initializes the variable in the child's object which were inherited for the parent class.

### better phrasing -`this` always refers to the **current object**, which is the object that was created (even if it's a child object). When a child object is created, the parent constructor runs first. Inside the parent constructor, `this` still refers to the **same child object**, not a separate parent object. Therefore, if the parent constructor initializes an inherited field using `this`, it initializes the parent part of that child object.



### final conclusion
`this` always refers to the current object, which is the object that was created (even if it's a child object). When a child object is created, the parent constructor runs first. Inside the parent constructor, `this` still refers to the same child object, not a separate parent object. Therefore, if the parent constructor initializes a field using `this`, it initializes the parent field that exists inside that child object. When multiple classes in the inheritance hierarchy have fields with the same name, the executing class determines which field `this.field` refers to.

# Method overriding

Method overriding happens when a class provides its own implementation of a method which already exists in the parent class.
The key idea:

> **Same method → Parent has it → Child gives its own version.**

### Basic example

```
class Animal {
    void sound() {
        System.out.println("Animal makes sound");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("Dog barks");
    }
}
```

Here, `Dog` **overrides** `sound()`.

Now:

```
Dog d = new Dog();
d.sound();
```

Output:

```
Dog barks
```

The child version is executed.
## Why do we need overriding?

Imagine:

```
class Animal {
    void sound() {
        System.out.println("Animal makes sound");
    }
}
```

Every animal has a different sound.

Instead of creating completely different method names:

```
dogSound()
catSound()
lionSound()
```

we keep the **same method name**:

```
sound()
```

and let each child provide its own implementation.

```
             Animal
              sound()
                ↑
       ┌────────┼────────┐
       ↓        ↓        ↓
      Dog      Cat      Lion
     sound()  sound()  sound()
     bark     meow     roar
```
## What if you want the parent's version?

That's where your previous `super` knowledge comes in.

```
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {

    void sound() {
        System.out.println("Dog bark");
        super.sound();
    }
}
```

Now:

```
Dog d = new Dog();
d.sound();
```

Output:

```
Dog bark
Animal sound
```

So:

```
sound();
```

inside `Dog` → calls the overridden child version.

```
super.sound();
```

→ explicitly calls the parent version.


#  Polymorphism

## 1.Definition

The word literally means poly=many, morph=forms, so it means one thing can take many forms .
Polymorphism essentially means that the same method can behave differently according to the object that's involved

For example:
```
Animal a;

a=new Dog();
a.sound();     //Dog's sound

a=new cat();
a.sound();     //Cat's sound
```

The method call is same but the behavior changes according to the object that's created. Where a is referring to a dog or cat.
That's polymorphism.

## 2. Why Do We Need Polymorphism?

Imagine you have:

```
Dog
Cat
Lion
```

and each has:

```
sound()
```

Without polymorphism, you might need:

```
Dog d = new Dog();
Cat c = new Cat();
Lion l = new Lion();

d.sound();
c.sound();
l.sound();
```

That's fine for three animals.

But imagine you have **10,000 different animals**.

Polymorphism allows you to work with them through their common parent:

```
Animal a;
```

Then:

```
a = new Dog();
a.sound();

a = new Cat();
a.sound();

a = new Lion();
a.sound();
```

The code can treat them all as `Animal`, while Java chooses the appropriate implementation.
## 3. The Two Types of Polymorphism in Java

There are two major forms:

```
                    Polymorphism
                         |
              ┌──────────┴──────────┐
              ↓                     ↓
       Compile-time             Runtime
       Polymorphism             Polymorphism
              |                     |
         Overloading             Overriding
```


Compile-time polymorphism

Usually achieved through:

> **Method overloading**

 Runtime polymorphism

Achieved through:

> **Method overriding + inheritance**


## 4. Compile-Time Polymorphism

Consider:

```
class Calculator {

    int add(int a, int b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }
}
```

Now:

```
Calculator c = new Calculator();

c.add(10, 20);
c.add(10, 20, 30);
```

Same method name:

```
add()
```

but different parameter lists.

Java determines which method to call **during compilation**.

Therefore:

> **Compile-time polymorphism**

This is also called:

> **Static polymorphism / early binding**

## 5. Runtime Polymorphism

Now the important one.

```
class Animal {

    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {

    void sound() {
        System.out.println("Dog barks");
    }
}

class Cat extends Animal {

    void sound() {
        System.out.println("Cat meows");
    }
}

public class h {

    public static void main(String args[]) {

        Animal a;

        a = new Dog();
        a.sound();

        a = new Cat();
        a.sound();
    }
}
```

Output:

```
Dog barks
Cat meows
```

Notice something strange.

The variable is:

```
Animal a;
```

But the actual object is:

```
new Dog()
```

and later:

```
new Cat()
```

Java chooses the method based on the **actual object at runtime**.

That's runtime polymorphism.
### 5.1 But Which Overridden Method Executes?

Now:

```
class Animal {
    void sound() {
        System.out.println("Animal");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog");
    }
}
```

Then:

```
Animal a = new Dog();

a.sound();
```

The compiler sees:

```
Animal has sound()
```

So compilation succeeds.

But at runtime, JVM sees:

```
Actual object = Dog
```

So it executes:

```
Dog.sound()
```

Output:

```
Dog
```

This is the core mechanism of **runtime polymorphism**.


### 5.2 What Can the Reference Access?

Suppose:

```
class Animal {

    void eat() {
        System.out.println("Eating");
    }
}

class Dog extends Animal {

    void bark() {
        System.out.println("Barking");
    }
}
```

Now:

```
Animal a = new Dog();
```

Can you do:

```
a.eat();
```

✅ Yes.

Because `eat()` belongs to `Animal`.

But:

```
a.bark();
```

❌ Compile-time error.

Why?

Because the **reference type** is `Animal`.

The compiler looks at:

```
Animal a
```

and says:

> "I only know that `a` is an Animal. I cannot assume that every Animal can bark."

This is extremely important.

#### Why Can't We Access `bark()`?

```
Animal a = new Dog();

a.bark();
```

Even though the object is actually a Dog, the compiler rejects it.

Why?

Because **method availability is checked using the reference type**.

The compiler doesn't execute the program to determine the actual object.

It only knows:

```
Animal a
```

So:

```
a.bark();
```

is invalid because `Animal` doesn't declare `bark()`.

### 5.3 The Most Important Concept: Reference Type vs Object Type

This is where you need to be extremely clear.

Look at:

```
Animal a = new Dog();
```

There are two types involved.

#### Reference type

```
Animal
```

This is the **type of the reference variable**.

#### Object type

```
Dog
```

This is the **actual object created**.

Think:

```
Animal a = new Dog();
       ↑          ↑
   reference    object
     type        type
```

This distinction is **fundamental** to polymorphism.

#### Note
Method overriding is the mechanism that provides run time polymorphism

#### Very basic example

```
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
        a.sound();
    }
}
```

#### Output

```
Dog barks
```

#### Why is this runtime polymorphism?

Look at this:

```
Animal a = new Dog();
```

The **reference type** is `Animal`, but the **actual object** is `Dog`.

Then:

```
a.sound();
```

Java decides **at runtime** which `sound()` method to execute.

Since the actual object is `Dog`, it executes:

```
Dog's sound()
```

So:

> **One reference → different behavior depending on the actual object.**

That's **runtime polymorphism**.

#### Think of it like this

```
Animal a = new Dog();
         ↓
     reference
         ↓
       Dog object
         ↓
      a.sound()
         ↓
   Dog.sound() runs
```

And if we change:

```
Animal a = new Cat();
a.sound();
```

then `Cat.sound()` runs.

**Important:** Runtime polymorphism requires **inheritance + method overriding + parent reference pointing to child object**.

```
Method Overriding + Parent reference + Child object
       ↓
Method call
       ↓
Decision made at RUNTIME
       ↓
Runtime Polymorphism
```

#### Here a=new Animal();
```
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a = new Animal();
        a.sound();
    }
}
```

Then **this is NOT runtime polymorphism**.

Why? Because both the **reference type** and the **actual object** are `Animal`.

```
Animal a = new Animal();
   ↑          ↑
reference   actual object
```

So when:

```
a.sound();
```

Java calls:

```
Animal.sound()
```

#### Compare the two

**1. Runtime polymorphism:**

```
Animal a = new Dog();
a.sound();
```

➡️ `Dog.sound()` runs ✅

**2. Normal method call:**

```
Animal a = new Animal();
a.sound();
```

➡️ `Animal.sound()` runs ❌ not runtime polymorphism

#### The key thing 🔥

The **overriding itself** is what makes runtime polymorphism possible, but you actually **demonstrate runtime polymorphism when a parent reference points to a child object**:

```
Animal a = new Dog();
```

That's the part you should remember.

#### How method overriding enables run time poly
##### 1. First, method overriding

Suppose:

```
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}
```

Here, `Dog` **overrides** `Animal`'s `sound()`.

So now there are **two versions** of `sound()`:

```
Animal → sound() → "Animal sound"
Dog    → sound() → "Dog barks"
```

##### 2. Now overriding enables runtime polymorphism

We create:

```
Animal a = new Dog();
```

This is the important part.

The reference says:

```
Animal
```

but the actual object is:

```
Dog
```

Now:

```
a.sound();
```

Which `sound()` should run?

Because `Dog` **overrode** `sound()`, Java can choose the `Dog` implementation based on the **actual object at runtime**.

```
Animal a = new Dog();
          ↓
     actual object
          ↓
         Dog
          ↓
      a.sound()
          ↓
   Dog.sound() runs
```

That's **runtime polymorphism**.

##### What if there was NO overriding?

Suppose:

```
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    // no sound() here
}
```

Then:

```
Animal a = new Dog();
a.sound();
```

There isn't a different `Dog.sound()` implementation to choose.

So it simply uses the inherited `Animal.sound()`.

#### So remember this relationship 🧠

**Method overriding creates different implementations.**

**Parent reference + child object allows Java to choose between those implementations at runtime.**

Therefore:

> **Method overriding is the foundation/mechanism that makes runtime polymorphism possible.**

And the classic runtime-polymorphism pattern is:

```
Parent ref = new Child();
ref.overriddenMethod();
```

For example:

```
Animal a = new Dog();
a.sound();       // Dog's version
```

```
Animal a = new Cat();
a.sound();       // Cat's version
```

**Same `a.sound()` call → different behavior depending on the object.**

That's literally **poly (many) + morph (forms)**. 💯


### 5.4 Dynamic method dispatch
#### a) Definition

**Dynamic Method Dispatch** is the mechanism by which Java decides **at runtime which overridden method to execute**.

It is the basis of **runtime polymorphism**.

#### b) Basic Example

```
class Animal {
    void sound() {
        System.out.println("Animal sound");
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
        a.sound();
    }
}
```

**Output:**

```
Dog barks
```

#### c) Why?

Look at:

```
Animal a = new Dog();
```

There are **two types** involved:

- **Reference type:** `Animal`
- **Object type:** `Dog`

At compile time:

```
a.sound();
```

Java checks whether `Animal` has a `sound()` method.

At runtime, Java looks at the **actual object**:

```
a → Dog object
```

Since `Dog` has overridden `sound()`, Java executes:

```
Dog.sound()
```

This runtime decision is **Dynamic Method Dispatch**.

#### NOTE: if Animal does not have sound()
Suppose:

```
class Animal {
}

class Dog extends Animal {
    void sound() {
        System.out.println("Dog barks");
    }
}

Animal a = new Dog();
a.sound();
```

Here Java first looks at the **reference type**:

```
a.sound();
```

It asks:

> **Does `Animal` have a `sound()` method?**

❌ **No.**

Therefore, this code **will not compile**.

#### Why?

Even though the actual object is a `Dog`, the reference is an `Animal` reference.

```
Animal a = new Dog();

Animal reference
      ↓
   Dog object
```

The reference can only access methods that are available through `Animal`.

So:

```
a.sound();   // ❌ Compile-time error
```

#### But this works:

```
Animal a = new Dog();
```

because creating the object is perfectly valid.

You just can't do:

```
a.sound();
```

through an `Animal` reference if `Animal` doesn't declare/inherit `sound()`.

#### Compare:

```
class Animal {
    void sound() {
        System.out.println("Animal");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog");
    }
}
```

```
Animal a = new Dog();
a.sound();
```

Java:

```
1. Compile time:
   Does Animal have sound()? → YES ✓

2. Runtime:
   What is the actual object? → Dog

3. Dog has overridden sound()
   → Execute Dog.sound()
```

**So the parent/reference type must have the method for the call to be legal. Then runtime dispatch decides which overridden version runs.** 🔥

#### d) The key rule 🔥

> **Reference type decides what methods are accessible.**  
> **Object type decides which overridden method actually runs.**

For:

```
Animal a = new Dog();
a.sound();
```


---

#### e) Dynamic Method Dispatch requires

Usually, you need:

1. **Inheritance**
2. **Method overriding**
3. **Parent-class reference**
4. **Child-class object**

#### f)For Dynamic Method Dispatch, the method must be **available in the reference type**, and the child may either **override it or inherit it**.

##### Case 1: Available in both → overriding

```
class Animal {
    void sound() {
        System.out.println("Animal");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("Dog");
    }
}

Animal a = new Dog();
a.sound();  // Dog
```

Here `sound()` exists in both → **Dog's overridden method executes.**

##### Case 2: Only available in parent → inherited

```
class Animal {
    void sound() {
        System.out.println("Animal");
    }
}

class Dog extends Animal {
}

Animal a = new Dog();
a.sound();  // Animal
```

`Dog` doesn't have its own `sound()`, but it **inherits** `Animal.sound()` → it still executes.

##### Case 3: Only available in child → ❌

```
class Animal {
}

class Dog extends Animal {
    void bark() {
        System.out.println("Bark");
    }
}

Animal a = new Dog();
a.bark();   // ❌ Compile-time error
```

Because `bark()` isn't available through the `Animal` reference.

The rule to remember 🔥

> **The method must be available in the reference type. If the child overrides it, the child's version runs at runtime. If it doesn't override it, the inherited parent version runs.**

### 5.5 The Deep Rule

Remember this:

> **Reference type determines what you are allowed to call.**
> 
> **Object type determines which overridden implementation actually runs.**

### 5.6 Upcasting

#### a) Definition

**Upcasting** means converting a **child class reference into a parent class reference**.
```
Dog d = new Dog();

Animal a = d;
```

Here:

- `Dog` → child class
- `Animal` → parent class
- `a` → parent reference
- Actual object → `Dog`
#### b) Why is it called Upcasting?

Because we move **up the inheritance hierarchy**:
This is **upcasting**.

```
        Animal
          ↑
         Dog
```

  ```
  Dog d = new Dog();
  Animal a = d;   // Upcasting
  ```

#### c) Upcasting can be implicit

Java automatically performs upcasting.

`Dog d = new Dog();`
`Animal a = d;`

You don't need to do it explicitly:

`Animal a = (Animal) d;`

Although this is technically possible, the cast is unnecessary.

#### d) What can we access?

This is the **most important point**.

When you have:

Animal a = new Dog();

The **reference type** is `Animal`.

Therefore, you can directly access only members available through `Animal`.

```
class Animal {

    void eat() {
        System.out.println("Eating");
    }
}

class Dog extends Animal {

    void bark() {
        System.out.println("Barking");
    }
}
```

```
Animal a = new Dog();
a.eat();   // ✅
a.bark();  // ❌
```

Even though the actual object is a `Dog`, the reference is `Animal`.

---

#### e) But overridden methods behave differently

This is where **runtime polymorphism** comes in.

```
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog sound");
    }
}
```

```
Animal a = new Dog();
a.sound();
```

Output:
Dog sound

Why?
Because:

Reference type → Animal
Actual object  → Dog

For an **overridden instance method**, Java chooses the implementation based on the **actual object at runtime**.

---

#### f) Upcasting + Runtime Polymorphism

This is the classic pattern:

```
Animal a = new Dog();
a.sound();
```

Think:
```
        Animal reference

              ↓

        ┌───────────┐

        │ Dog object│

        └───────────┘
```

The reference determines **what members you can access**.

The actual object determines **which overridden method executes**.

---

#### g) Why use Upcasting?

It allows us to treat different child objects uniformly.

```
Animal a1 = new Dog();
Animal a2 = new Cat();
Animal a3 = new Cow();
```

Now all three can be handled as `Animal`.

```
a1.sound();
a2.sound();
a3.sound();
```

Each object can provide its own implementation of `sound()`.

This is one of the foundations of **polymorphism**.

---

#### h) Important limitation

Suppose:

```Animal a = new Dog();```

You cannot directly do:

```a.bark();   // ❌```

because `bark()` belongs to `Dog`, not `Animal`.

To access it, you need **downcasting**:

```
Dog d = (Dog) a;
d.bark();
```

So the relationship is:
```
Dog d = new Dog();

Animal a = d;       // Upcasting

                     ↓

              Animal reference

  

Dog d2 = (Dog) a;   // Downcasting

                     ↓

                Dog reference
```
#### ⭐ Core rule to remember

> **Upcasting: Child object → Parent reference.**

Animal a = new Dog();

And:

> **Reference type decides what you can access; actual object decides which overridden method runs.**

That second rule is **extremely important for understanding runtime polymorphism**.

### 5.7 Downcasting

#### a. Definition

**Downcasting** means converting a **parent class reference into a child class reference**.

```
Animal a = new Dog();
Dog d = (Dog) a;
```

Here:

- `Animal` → parent class
- `Dog` → child class
- `a` → parent reference
- `d` → child reference
- Actual object → `Dog`

This is **downcasting**.

---

#### b. Why is it called Downcasting?

Because we move **down the inheritance hierarchy**:

```
        Animal

          ↑

         Dog
```

```
Animal a = new Dog();
Dog d = (Dog) a;   // Downcasting
```
`Animal` → `Dog` = moving downward.

---

#### c. Explicit casting is required

Unlike upcasting, downcasting is **not automatic**.

❌ This is not allowed:

```
Animal a = new Dog();
Dog d = a;
```
You must explicitly cast:

```
Dog d = (Dog) a;
```
---

#### d. Why do we need downcasting?

After upcasting:

`Animal a = new Dog();`

The reference type is `Animal`.

So you cannot access methods that exist only in `Dog`.

`a.bark();   // ❌
`
After downcasting:

```
Dog d = (Dog) a;
d.bark();   // ✅
```

So downcasting allows you to access **child-specific members**.

---

#### e. Downcasting works only when the actual object is the child

This is extremely important.
```
Animal a = new Dog();
Dog d = (Dog) a;   // ✅
```

Why?

Reference type → Animal
Actual object  → Dog

The object really is a `Dog`, so the cast is valid.

---

#### f. Invalid downcasting

```
Animal a = new Cat();
Dog d = (Dog) a;   // ❌
```

The reference is `Animal`, but the actual object is `Cat`.

```
Animal
 ├── Dog
 └── Cat
```

a → Cat object

You cannot turn a `Cat` object into a `Dog`.

This causes:
ClassCastException at runtime.


---

#### g. Using `instanceof` to prevent the error

You can check the actual object before downcasting:

```
Animal a = new Cat();

if (a instanceof Dog) {
    Dog d = (Dog) a;
    d.bark();
}
```
Since `a` actually refers to a `Cat`, the condition is false.

---

#### h. Upcasting → Downcasting

These two are opposites.

```
Dog d1 = new Dog();
Animal a = d1;       // Upcasting
Dog d2 = (Dog) a;    // Downcasting
```

Think:
```
Dog object

    ↓

Animal reference

    ↓

Dog reference
```
---

#### i. Down casting and polymorphism

Consider:
```
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}
```
  

```
class Dog extends Animal {
    void sound() {
        System.out.println("Dog sound");

    }

    void bark() {
        System.out.println("Barking");
    }
}
```

```
Animal a = new Dog();
a.sound();   // Dog sound
```
Even before down casting, the overridden method works because of **runtime polymorphism**.

Then:

```
Dog d = (Dog) a;
d.bark();    // Barking
```

Down casting is needed here because `bark()` is **specific to `Dog`**.

---

#### j. Key distinction

```
Upcasting->
Child reference → Parent reference
Usually implicit
Safer
Used heavily for polymorphism
```

  
```
Down casting->
Parent reference → Child reference
Explicit cast required
Can cause ClassCastException
Used to access child-specific members
```
#### ⭐ Core rule to remember

> **Downcasting = converting a parent reference back into a child reference.**
```
Animal a = new Dog();
Dog d = (Dog) a;
```

And the golden rule:

> **Downcasting is valid only if the actual object is an instance of the target child class.**


### 5.8 The Real Power: Methods Taking Parent Types
```
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

class Cat extends Animal {

    @Override
    void sound() {
        System.out.println("Cat meows");
    }
}

class Lion extends Animal {

    @Override
    void sound() {
        System.out.println("Lion roars");
    }
}

public class Main {

    static void makeSound(Animal a) {
        a.sound();
    }

    public static void main(String[] args) {

        makeSound(new Dog());
        makeSound(new Cat());
        makeSound(new Lion());
    }
}
```

#### But why is this actually powerful?

Without polymorphism, you might write:

```
static void makeDogSound(Dog d) {

    d.sound();
}
```
  

```
static void makeCatSound(Cat c) {

    c.sound();

}
```


```
static void makeLionSound(Lion l) {

    l.sound();
    
}
```



That's ugly.

```
And imagine you have:

Dog

Cat

Lion

Tiger

Elephant

Horse

Cow

Monkey

```

You'd need a separate method for every animal.

Instead, you write **one method**:

```
static void makeSound(Animal a) {
    a.sound();
}
```

And every future subclass automatically works:

```
makeSound(new Dog());

makeSound(new Cat());

makeSound(new Lion());

makeSound(new Tiger());

makeSound(new Horse());
```
You don't have to modify `makeSound()`.


### 5.9 A REAL LIFE EXAMPLE

```
class Payment {

    void pay() {
        System.out.println("Making a payment");
    }
}

class CreditCard extends Payment {

    @Override
    void pay() {
        System.out.println("Payment made using Credit Card");
    }
}

class UPI extends Payment {

    @Override
    void pay() {
        System.out.println("Payment made using UPI");
    }
}

public class Main {

    static void processPayment(Payment p) {
        p.pay();
    }

    public static void main(String[] args) {

        processPayment(new CreditCard());
        processPayment(new UPI());
    }
}
```

 #### Output
```
Payment made using Credit Card
Payment made using UPI**
```

### 5.10 Accessing variables

This is an important trap.

Methods and variables behave differently.

```
class Animal {
    String name = "Animal";
}
class Dog extends Animal {
    String name = "Dog";
}
```

Now:

```
Animal a = new Dog()
System.out.println(a.name);
```
What happens?

Output:

```
Animal
```

Not:
```
Dog
```

Why?

Because **instance variables are not dynamically dispatched**.

Variables are resolved based on the **reference type**.

```
a.name

 ↓

reference type = Animal

 ↓

Animal.name
```

But methods:

```
a.sound()
```

are dynamically dispatched when overridden:

```
actual object = Dog

 ↓

Dog.sound()
```

#### Remember:

> **Methods → runtime dispatch**
> 
> **Fields → reference-type resolution**

This is a classic interview trap.

### 5.11  What About Static Methods?

Another important trap.

Static methods are **not overridden** in the runtime-polymorphism sense.

They are **hidden**.

Example:

```
class Animal {

    static void show() {

        System.out.println("Animal");

    }

}

class Dog extends Animal {

    static void show() {

        System.out.println("Dog");

    }

}
```

Now:

```
Animal a = new Dog();
a.show();
```

Output:

Animal

Why?

Because static methods belong to the **class**, not the object.

The reference type determines which static method is called.

So:

```
Overridden instance method

→ runtime polymorphism


Static method

→ no runtime polymorphism
```

Static methods are hidden, not overridden. They belong to the class, not the object, so the reference type (Animal) determines which static method is called — there's no runtime polymorphism for static methods.

### 5.12  Private and Final Methods in Polymorphism

#### a. Private Methods

A `private` method **cannot be overridden**.

##### Why?

Because a `private` method is **not inherited** by the child class.

> A method that is not inherited cannot be overridden.

Example
```
class Animal {

    private void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {

    void sound() {
        System.out.println("Dog sound");
    }
}
```
Here, `Dog.sound()` is **not overriding** `Animal.sound()`.

They are two completely separate methods.
```
Animal
  |
  | private sound()
  |
  X  ← Not inherited
  |
Dog
  |
  | sound()
  ↓
Separate method
```

Therefore:

- `private` methods are **not inherited**
- `private` methods **cannot be overridden**
- They do **not participate in runtime polymorphism**

##### Important Example
```
class Animal {

    private void sound() {
        System.out.println("Animal sound");
    }

    void makeSound() {
        sound();
    }
}

class Dog extends Animal {

    void sound() {
        System.out.println("Dog sound");
    }
}
```

```
Animal a = new Dog();
a.makeSound();
```

Output:

```
Animal sound
```

Why?

`makeSound()` belongs to `Animal`, and its call:

```
sound();
```

refers to the `private` method inside `Animal`.

`Dog.sound()` is a separate method and does not override it.

##### Note
A `private` method is **not inherited** and cannot be accessed through the parent reference `a`.

So:
```
class Animal {

    private void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {

    void sound() {
        System.out.println("Dog sound");
    }
}

```

```
Animal a = new Dog();
a.sound();   // ❌ Compile-time error
```
The important point is:

> `a.sound()` looks for an accessible `sound()` method based on the **reference type `Animal`**. But `Animal.sound()` is private, so it cannot be accessed.

And the `Dog.sound()` method **does not override** `Animal.sound()` — it is a completely separate method.

#### b. Final methods

A `final` method **cannot be overridden**.

##### Why?

Because Java explicitly prevents a child class from providing a new implementation of a `final` method.
```
class Animal {

    final void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {

    void sound() {
        System.out.println("Dog sound");
    }
}

public class Main {

    public static void main(String[] args) {

        Animal a = new Dog();
        a.sound();
    }
}
```

This causes a **compile-time error**.

The parent is essentially saying:

> "This method's implementation cannot be changed by subclasses."

 Important Difference

Unlike `private`, a `final` method **is inherited**.
```
Animal
  |
  | final sound()
  ↓
Dog inherits sound()
  |
  X  ← Cannot override
```
Therefore:

- `final` methods **are inherited**
- `final` methods **cannot be overridden**
- They do **not participate in runtime polymorphism**

#### c) The Four Most Important Cases

Memorize the behavior, not the code.

|Member|Overridden?|Runtime polymorphism?|
|---|---|---|
|Instance method|✅ Yes|✅ Yes|
|Static method|❌ No|❌ No|
|Instance variable|❌ No|❌ No|
|Constructor|❌ No|❌ No|

So if you see:

Parent p = new Child();

ask:

> **What am I accessing?**

##### Method?

Potentially **Child's overridden version**.

##### Variable?

**Parent's version** based on reference type.

##### Static method?

**Parent's version** based on reference/class context.

##### Constructor?

Constructors aren't polymorphic.

### 5.13 Constructor + Polymorphism Trap

```
class Animal {
    Animal() {
        sound();
    }

    void sound() {
        System.out.println("Animal");
    }
}

class Dog extends Animal {
    Dog() {
        System.out.println("Dog constructor");
    }
    
    void sound() {
        System.out.println("Dog");
    }
}
```

```
Dog d = new Dog();
```

What happens?

The parent constructor runs first.

Inside the parent constructor:
```
sound();
```

Which method is called?

**Dog's `sound()`**.

Why?

Because `sound()` is an overridable instance method, and the actual object being constructed is a `Dog`.

This is a **dangerous design pattern**, because the child part of the object hasn't finished initialization yet.

So generally:

> **Avoid calling overridable methods from constructors.**

This is an important deeper Java concept.

The output is same even if you create
```
Animal a = new Dog();
```

### 5.14 Conclusion
Whenever you see:
```
Parent p = new Child();
```
split it mentally:
```
              Parent p = new Child()
                    │
          ┌─────────┴─────────┐
          ↓                   ↓
   Reference Type         Object Type
      Parent                Child
          │                   │
          ↓                   ↓
What can I call?       Which overridden
                       method executes?
```

Then ask:

#### Step 1 — Compiler

> Is the method/member available through `Parent`?

If **no** → compile-time error.

If **yes** → continue.

#### Step 2 — Runtime

> Is this an overridden instance method?

If **yes** → JVM uses the actual object's implementation.

If **no** → normal compile-time/reference-based resolution applies.

#### ⭐ Core rule to remember
In Java runtime polymorphism, the reference type determines what members can be accessed, while the actual object determines which overridden instance method executes.

# Final Keyword

The basic idea is:

> **`final` means "this cannot be changed further."**

But _what_ cannot be changed depends on where you use it.

There are 3 major uses:
```
final
 ├── final variable
 ├── final method
 └── final class
```

## `final` Variable

A `final` variable **cannot be reassigned after it gets a value**.

```
final int x = 10;

x = 20;   // ❌ ERROR
```

Once `x` becomes `10`, you cannot make it `20`.

### Why use it?

When you want a value to remain constant.
```
final double PI = 3.14159;
```

## `final` Reference Variable

```
final Student s = new Student();
```
Can you do:
```
s = new Student();  // ❌
```
No.

But can you modify the object?
```
s.name = "Santosh";  // ✅
```

Yes!

Why?

Because `final` prevents the **reference from changing**, not necessarily the object.

Think:
```
s
│
│ final reference
▼
┌───────────────┐
│ Student       │
│ name = null   │
└───────────────┘
```
You cannot make `s` point somewhere else:
```
s ─────X────> another Student
```
But you can modify the existing object's fields.

Therefore:

> **`final` reference ≠ immutable object**

This is a VERY important interview concept.

### Without `final`

```
Student d = new Student();
d = new Student();  // ✅ Allowed
```

`d` is a **reference variable**, and you can make it refer to another `Student` object.
## `final` Method

Now we're getting into **inheritance**.

A `final` method **cannot be overridden by a child class**.
```
class Animal {

    final void sound() {
        System.out.println("Animal sound");
    }
}
```
Now:
```
class Dog extends Animal {

    void sound() {       // ❌ ERROR
        System.out.println("Dog sound");
    }
}
```

Why?

Because the parent said:
```
final void sound()
```
Meaning:

> "Child classes are not allowed to change my implementation."

### Why would we use a final method?

Suppose a parent class has some critical behavior that must remain unchanged.

```
class Bank {

    final void calculateInterest() {
        // important logic
    }
}
```
You don't want subclasses to override that logic.

## `final` Class

This is the third major use.

A `final` class **cannot be inherited**.
```
final class Animal {
}
```

```
class Dog extends Animal {   // ❌ ERROR
}
```
Because `Animal` is final.

It's basically saying:

> "This class is the end of the inheritance chain.

## Now Connect All Three

This is the easiest way to remember:

### `final` variable

final int x = 10;

➡️ **Cannot change the variable's value/reference.**

### `final` method

final void sound () {}

➡️ **Cannot override the method.**

### `final` class

final class Animal {}

➡️ **Cannot extend the class.**

`final` + Inheritance
```
                    final
                      │
          ┌───────────┼───────────┐
          ↓           ↓           ↓
       variable      method      class
          │           │           │
      cannot       cannot       cannot
      reassign     override     inherit
```


## One Important Trap: Constructors

Can a constructor be `final`?
```
final Animal() {
}
```

❌ **No.**

Constructors cannot be `final`.

Why?

Because constructors are **not inherited or overridden** in the first place.

`final` on a constructor would therefore make no sense.

## One More Important Trap: `final` + `static`

You will frequently see:

```
static final int MAX = 100;
```

This means:

- `static` → one copy belongs to the class
- `final` → cannot be reassigned

So:

class Config {

```
    static final int MAX_USERS = 100;
```
}

Access it as:

```
Config.MAX_USERS
```

These are commonly called **constants**.

By convention:

```
static final int MAX_USERS = 100;
```

uses uppercase letters with underscores.

## `final` vs `finally` vs `finalize`

Don't confuse these.

|Keyword|Meaning|
|---|---|
|`final`|Prevents change/inheritance/overriding|
|`finally`|Block used with exception handling|
|`finalize()`|Old GC-related method; deprecated and should not be used|

They're completely different concepts.

## General Note

->A method name can be the same as its class name

->method overloading works wit the final keyword
```
package build;

class Animal {

    final int aa(int num) {
        return num;
    }

    final int aa(int y, int x) {
        return x + y;
    }
}

public class finalll {

    public static void main(String args[]) {

        Animal a = new Animal();

        System.out.println(a.aa(10));
        System.out.println(a.aa(10, 11));
    }
}
```

# Wrapper Class

## Why do wrapper classes exist

Java has 8 primitive types
```
byte
short
int
long
float
double
char
boolean
```
these are not objects they are primitive types.

For example 
```
int x = 10;
```
`x `directly holds a primitive `int` value.

But java also has many APIs that work with objects ,not primitives.

The biggest example is the Collections Framework:

```
ArrayList<Integer> list=new ArrayList<>();
```
But you cannot do
```
ArrayList<int> list=new ArrayList<>();
```
why?
Because the <> in generics expects a reference type, not a primitive type.
so java provides wrapper classes

## What are wrapper classes

A wrapper class is a class that represents a primitive value as an object.
The mapping is

|Primitive|Wrapper|
|---|---|
|`byte`|`Byte`|
|`short`|`Short`|
|`int`|`Integer`|
|`long`|`Long`|
|`float`|`Float`|
|`double`|`Double`|
|`char`|`Character`|
|`boolean`|`Boolean`|
## Primitive vs Wrapper

```
int x=10;
```
here x is a variable whose type is primitive 

```
Integer x=10;
```
here x is a reference variable whose type is Integer.

## Box
### Boxing
Boxing means converting a primitive value into its corresponding wrapper object.

```
int x= 10;
Integer y=new Integer(x);
```

### Auto boxing
Java can perform boxing automatically

Instead of:
```
int x = 10;
Integer y = Integer.valueOf(x);
```
you can simply write
```
int x=10;
Integer y=x;
```

### Why is it called boxing
Imagine putting a value inside a box.
```
 Primitive:
  10

 ↓ boxing

┌──────────────┐
│ Integer      │
│     10       │
└──────────────┘
```
The wrapper object is essentially the "box" around the primitive value.

## Unbox
### Manual/Explicit Unboxing
Unboxing means converting a wrapper object into a primitive.

```
Integer x = 10;

int y = x.intValue();
```
### Automatic Unboxing
```
Integer x = 10;
int y = x;
```

##  Autoboxing in Collections
This is where you'll see it constantly.
```
ArrayList<Integer> list = new ArrayList<>();

list.add(10);
list.add(20);
list.add(30);
```

`add()` expects:
```
Integer
```

But you're giving:
```
int
```

Java automatically boxes them:

```
10
 ↓
Integer.valueOf(10)
```

So this:

```
list.add(10);
```

is conceptually similar to:

```
list.add(Integer.valueOf(10));
```
## Unboxing from Collections
```
ArrayList<Integer> list = new ArrayList<>();

list.add(10);

int x = list.get(0);
```

`list.get(0)` returns:
```
Integer
```
But `x` requires:
```
int
```
So Java automatically unboxes:
```
Integer
 ↓
int
```
Conceptually:
```
int x = list.get(0).intValue();
```

## Wrapper Classes are Immutable

This is important.

Suppose:

```
Integer x = 10;
```

You can't modify the existing `Integer` object from 10 to 20.

When you do:

```
x = 20;
```

you're effectively making `x` refer to another `Integer` value/object.

This is similar to `String` being immutable.

##  Very Important: `==` with Wrappers

This is where wrapper classes become tricky.

Consider:

```
Integer a = 100;
Integer b = 100;
System.out.println(a == b);
```

You might expect:
```
false
```
because they're objects.

But the result is typically:

```
true
```
Why?

```
Java caches certain `Integer` values, commonly **-128 through 127**.
```

So:
```
Integer a = 100;

Integer b = 100;
```

can refer to the same cached object.

Conceptually:

```
       ┌─────────────┐
a ────►│ Integer 100 │◄──── b
       └─────────────┘
```

Therefore:

```
a == b
```

can be `true`.

---
 But Look at This
```
Integer a = 200
Integer b = 200;
System.out.println(a == b);
```

This can produce:

```
false
```

because those values aren't guaranteed to come from the same cached object.

Therefore:

> **Never use `==` to compare wrapper values when you mean value equality.**

Use:

```
a.equals(b)
```

instead.

## Java  wrapped classes guaranteed cached range
range where both refer to same object
```
Byte       → -128 to 127
Short      → -128 to 127
Integer    → -128 to 127
Long       → -128 to 127

Character  → 0 to 127
Boolean    → true / false

Float      → no standard cache
Double     → no standard cache
```

## Wrapper class and null

You can do:
```
Integer x = null;
```
But you cannot do:
```
int x = null;   // ❌
```
Now:
```
Integer x = null;
int y = x;
```
What happens?

Java tries to unbox `x`.

But `x` is `null`.

So you get:

```
NullPointerException
```
Conceptually:
```
int y = x.intValue();
```

But you can't call a method on `null`.

So:

> **Auto unboxing a null wrapper causes `NullPointerException`.**

This is a very common interview question.
### Note

```
int x = 0;
```

A primitive has a value.

But:

```
Integer x = null;
```

A wrapper reference can represent **absence of a value**.

This is one reason wrapper types are useful when working with databases and frameworks.

## `parseInt()` vs `valueOf()`

`Very important distinction.

```
Integer.parseInt("123");
```

returns:

```
int
```

while:

```
Integer.valueOf("123");
```

returns:
```
Integer
```

`So:

```
int a = Integer.parseInt("123");
Integer b = Integer.valueOf("123");
```

## Why Do Generics Need Wrappers?
Because generics work with **reference types**, not primitive types.

# Abstract Keyword
