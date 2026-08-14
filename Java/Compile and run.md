Let's go through **every stage** using your `Demo` program.

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
## 1. `javac Demo.java`

**Meaning:** Compile the source code.

You type:

```
javac Demo.java
```

### What happens?

1. The compiler (`javac`) reads `Demo.java`.
2. It checks for syntax errors.
3. It checks types, variables, methods, etc.
4. If everything is correct, it creates:

```
Demo.class
```

This `.class` file contains **bytecode**.

After this command:

```
Demo.java   ← Your source code
Demo.class  ← Compiled bytecode
```

Nothing is executed yet.

---

## 2. `java Demo`

**Meaning:** Run the compiled program.

You type:

```
java Demo
```

**Notice:** You **don't** write `.class`.

### What happens?

1. JVM starts.
2. JVM looks for `Demo.class`.
3. JVM loads the class into memory.
4. JVM finds:

```
public static void main(String args[])
```

5. JVM starts executing `main()`.
6. Your program runs and prints the output.

---

## Simple Analogy

Imagine you're writing a book.

### `javac Demo.java`

- Takes your handwritten manuscript.
- Checks for mistakes.
- Prints a clean book.

📖 Book = `Demo.class`

---

### `java Demo`

- Opens the printed book.
- Reads it aloud.

🎤 Reading the book = Running the program.

---

## One-Line Summary

```
javac Demo.java
        ↓
Compiles Java source (.java)
        ↓
Creates bytecode (.class)

java Demo
        ↓
Loads the .class file
        ↓
Executes main()
        ↓
Program runs
```

### Remember this interview answer:

- **`javac` = Compiler → `.java` → `.class`**
- **`java` = JVM → `.class` → Executes `main()`**





# Phase 1: Writing the Code

You create a file:

```
Demo.java
```

At this point, it is just plain text.

The computer doesn't understand Java.

---

# Phase 2: Compilation

You run

```
javac Demo.java
```

Now the **Java Compiler (`javac`)** starts working.

Its job is to convert Java source code into **bytecode**.

---

## Step 2.1 Lexical Analysis

The compiler reads every character.

It recognizes tokens.

For example

```
Demo d = new Demo();
```

becomes

```
Demo      -> Identifier
d         -> Identifier
=         -> Operator
new       -> Keyword
Demo      -> Identifier
( )       -> Parentheses
;         -> Terminator
```

This stage is called **tokenization**.

---

## Step 2.2 Syntax Checking

The compiler checks grammar.

For example

Correct

```
int a = 10;
```

Wrong

```
int = a 10;
```

The compiler says

```
Syntax Error
```

---

## Step 2.3 Semantic Checking

Now it checks meaning.

For example

```
Demo d = new Demo();
```

Questions asked:

- Does class Demo exist?
- Is `d` declared correctly?
- Is `new Demo()` valid?
- Does `add()` exist?
- Are parameter types correct?

If not

```
Compilation Error
```

---

## Step 2.4 Type Checking

Example

```
int x = "Hello";
```

Compiler says

```
Type mismatch
```

because

```
String → int
```

is impossible.

---

## Step 2.5 Method Overloading Resolution

Suppose

```
add(10,20)
```

Compiler searches

```
add(int,int)
```

If you wrote

```
add(10.5,20)
```

Compiler selects

```
add(double,int)
```

Notice

This happens **during compilation**, not runtime.

---

## Step 2.6 Bytecode Generation

Finally

```
Demo.java
```

becomes

```
Demo.class
```

The `.class` file contains **bytecode**, not machine code.

Example (simplified)

```
new Demo
invoke add
return
```

The JVM understands this bytecode.

---

# Phase 3: Running the Program

You type

```
java Demo
```

Now **JVM starts**.

Think of the JVM as a small operating system for Java programs.

---

# Step 3.1 Class Loader

The JVM first loads

```
Demo.class
```

into memory.

It creates metadata.

```
Method Area

-------------------
Demo Class
main()
add()
```

Notice

Only the class is loaded.

No object exists.

---

# Step 3.2 Bytecode Verification

JVM checks

- Is bytecode corrupted?
- Is it valid?
- Any illegal instructions?

If invalid

Program stops.

---

# Step 3.3 JIT Compilation

The JVM starts interpreting bytecode.

Frequently used methods are converted into native machine code by the **Just-In-Time (JIT) compiler** to improve performance.

So execution is usually:

```
Java Source
      ↓
Bytecode
      ↓
Interpreter
      ↓
Frequently executed code
      ↓
JIT Compiler
      ↓
Machine Code
```

---

# Step 3.4 main() Starts

JVM always starts here

```
public static void main(...)
```

It creates the first stack frame.

```
Thread Stack

---------------------
main()
---------------------
```

Inside

```
args
```

exist.

---

# Step 3.5 Execute

Now JVM executes

```
Demo d = new Demo();
```

Breaking it down

---

## Allocate Memory

Heap

```
Heap

----------------
Demo Object
----------------
```

---

## Initialize Variables

If there were instance variables

```
int x;
String name;
```

they become

```
x = 0
name = null
```

---

## Constructor Runs

Even if you don't write

```
Demo()
{
}
```

Java creates a default constructor.

It executes.

---

## Store Reference

The reference goes into

```
main() Stack Frame
```

```
main()

d ----------------------+
                         |
                         |
Heap                     |
-------------------------|
Demo Object <------------+
```

Notice

The object is on the heap.

The reference is on the stack.

---

# Step 3.6 Method Call

Now

```
d.add();
```

JVM

1. Looks at `d`.
2. Finds the object.
3. Finds `add()` inside Demo class metadata.
4. Pushes a new stack frame.

```
Stack

--------------------
add()
--------------------
main()
--------------------
```

---

Inside

```
a=10
b=20
sum=30
```

---

Then

```
System.out.println(sum);
```

calls another method.

Even **println()** gets its own stack frame.

```
Stack

-----------------------
println()
-----------------------
add()
-----------------------
main()
-----------------------
```

After printing

```
println()
```

returns.

Its frame disappears.

---

Then

```
add()
```

finishes.

Its frame disappears.

```
Stack

-----------------------
main()
-----------------------
```

---

# Step 3.7 main Ends

When

```
main()
```

returns

its stack frame disappears.

```
Stack

(empty)
```

---

# Step 3.8 Garbage Collection

Now

```
Demo Object
```

has no references.

```
Heap

Demo Object
 ^
 |
No references
```

It becomes **eligible** for garbage collection.

Later

Garbage Collector removes it.

---

# Entire Timeline

```
Write Code
      ↓
Demo.java
      ↓
javac Demo.java
      ↓
Compiler
      ↓
Lexical Analysis
      ↓
Syntax Checking
      ↓
Semantic Checking
      ↓
Type Checking
      ↓
Method Resolution
      ↓
Bytecode Generation
      ↓
Demo.class
      ↓
java Demo
      ↓
JVM Starts
      ↓
Class Loader
      ↓
Verification
      ↓
Method Area Created
      ↓
main() Frame Created
      ↓
Object Allocated in Heap
      ↓
Reference Stored in Stack
      ↓
add() Frame Created
      ↓
println() Frame Created
      ↓
println() Removed
      ↓
add() Removed
      ↓
main() Removed
      ↓
Garbage Collection
      ↓
Program Ends
```

---

### One small correction to a common misconception

People often say "the stack is created when the program runs." More precisely:

- Each **thread** has its own **JVM stack** that exists for the lifetime of that thread.
- As methods are called, **stack frames** are pushed onto that stack.
- As methods return, those frames are popped off.

So there isn't a new stack for every method—there is **one stack per thread**, and **many stack frames** are created and destroyed on it during execution.

Once you understand this flow, you're ready to dive into **what the `.class` bytecode actually looks like** and how JVM bytecode instructions like `new`, `invokevirtual`, `aload`, and `astore` manipulate the stack. That's the next level of understanding Java internals.