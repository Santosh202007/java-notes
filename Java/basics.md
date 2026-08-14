here you are solving real world problems with the virtual world of information and reasoning.

Java is platform independent it means that i can run on any hardware  and software but it should have jvm.
```
You
 │
 ▼
Java Source Code (.java)
 │
 │  javac (Java Compiler)
 ▼
Bytecode (.class)
 │
 │  JVM (Java Virtual Machine)
 ▼
Operating System (Windows/Linux/macOS)
 │
 ▼
Hardware (CPU, RAM, etc.)
```
### Step 1: You write Java code

Example:

```
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello");
    }
}
```

This is saved as:

```
Main.java
```

At this point it's just **human-readable text**. Your computer cannot execute it.

---

### Step 2: `javac` compiles the code

When you run

```
javac Main.java
```

the **Java Compiler (`javac`)** checks for errors.

If everything is correct, it creates

```
Main.class
```

This is called **Bytecode**.

Bytecode is **not machine code**.

It is an intermediate language that any JVM can understand.

---

### Step 3: JVM runs the Bytecode

Now you execute

```
java Main
```

Notice you don't write `.class`.

The JVM loads `Main.class`.

The JVM then translates the bytecode into the machine instructions your processor understands.

Internally it does something like:

```
Bytecode
      ↓
Machine Code
      ↓
CPU executes it
```

---

### Step 4: Operating System

The JVM communicates with Windows (or Linux/macOS).

For example, when you write

```
System.out.println("Hello");
```

the JVM asks Windows

> "Please display this text on the console."

Windows then uses the hardware.

---

### Step 5: Hardware

Finally the CPU executes the instructions.

So the real execution chain is

```
Java Code
    ↓
javac
    ↓
Bytecode (.class)
    ↓
JVM
    ↓
Machine Code
    ↓
Windows
    ↓
CPU
```

---

# Why not compile directly to machine code?

Imagine Java compiled directly into Windows machine code.

```
Java
   ↓
Windows Machine Code
```

That program would **only work on Windows**.

For Linux you'd need another compiler.

For macOS another compiler.

Instead Java does this:

```
Java
   ↓
Bytecode
```

Then

```
Windows JVM
Linux JVM
macOS JVM
```

Each JVM converts the same bytecode into the correct machine code for that operating system.

That's why:

> **Write Once, Run Anywhere (WORA)**

The same `.class` file can run on Windows, Linux, and macOS—as long as each system has a compatible JVM.

---

# A quick note about JDK, JRE, and JVM

These names are easy to confuse:

- **JDK (Java Development Kit)** → Used to **develop** Java programs. It includes `javac`, the JVM, and other tools.
- **JRE (Java Runtime Environment)** → Used to **run** Java programs. It includes the JVM and required libraries.
- **JVM (Java Virtual Machine)** → The engine that executes bytecode.
	```
	JDK
     ├── javac
     ├── JRE
     │     └── JVM
	```



java is object orientated and to create an object we need class
```
 class Hello {
    public static void main(String[] args) {
        System.out.println("Hello");
    }
}
```


before compiling
![[Pasted image 20260714201540.png]]
after compiling we got a hello. class file this is file which gets created automatically it is the extension for byte code
![[Screenshot 2026-07-14 201522.png]]
here compilation is done now to run we have to enter the command java and the class name
![[Pasted image 20260714202144.png|342]]
to run something you need JRE
JVM with libraries is a part of JRE

```
Your Java Code (.java)
          │
      javac (Compiler)
          │
     Bytecode (.class)
          │
        JRE
     ┌───────────────┐
     │     JVM       │
     │ + Libraries   │
     └───────────────┘
          │
Operating System
          │
      Hardware
```

## Java Data Types

## What are Data Types?

A data type specifies:

- What kind of value a variable can store.
- How much memory is allocated.
- What operations can be performed on that value.

**Example:**

```
int age = 20;
```

Here, `int` is the data type.

---

# Categories of Data Types

Java has **two categories** of data types:

1. Primitive Data Types
2. Non-Primitive (Reference) Data Types

```
Data Types
│
├── Primitive
└── Non-Primitive (Reference)
```

---

# 1. Primitive Data Types

Primitive data types are predefined by Java.

They store actual values directly in memory.

There are **8 primitive data types**.

## Integer Types

Used to store whole numbers.

| Data Type | Size    | Range             |
| --------- | ------- | ----------------- |
| byte      | 1 byte  | -128 to 127       |
| short     | 2 bytes | -32,768 to 32,767 |
| int       | 4 bytes | -2³¹ to 2³¹ - 1   |
| long      | 8 bytes | -2⁶³ to 2⁶³ - 1   |

**Example**

```
byte age = 25;
short year = 2026;
int salary = 50000;
long population = 8000000000L;
```

---

## Floating Point Types

Used to store decimal numbers.

|Data Type|Size|
|---|---|
|float|4 bytes|
|double|8 bytes|

**Example**

```
float pi = 3.14f;
double value = 12345.6789;
```

> **Note:** Float values require the suffix `f`.

---

## Character Type

Stores a single character.

**Data Type**

```
char
```

**Size**

```
2 bytes (16 bits)
```

**Example**

```
char grade = 'A';
char letter = 'b';
char symbol = '@';
```

Characters are enclosed in **single quotes (' ')**.

---

## Boolean Type

Stores logical values.

Possible values:

```
true
false
```

**Example**

```
boolean isJavaFun = true;
boolean isLoggedIn = false;
```

---

# Summary of Primitive Data Types

|Category|Data Types|
|---|---|
|Integer|byte, short, int, long|
|Decimal|float, double|
|Character|char|
|Boolean|boolean|

**Total Primitive Data Types = 8**

---
# Difference Between `float` and `double`

Both `float` and `double` are **primitive data types** used to store **decimal (floating-point) numbers**

|Feature|`float`|`double`|
|---|---|---|
|Size|4 bytes (32 bits)|8 bytes (64 bits)|
|Precision|~6–7 decimal digits|~15–16 decimal digits|
|Memory Usage|Less|More|
|Speed|Slightly faster (rarely noticeable on modern CPUs)|Slightly slower|
|Suffix Required|Yes (`f` or `F`)|No|
|Default in Java|❌ No|✅ Yes|
## Example

### float

```
float pi = 3.14f;
float marks = 95.5F;
```

⚠️ Without the `f`, Java gives an error.

```
float pi = 3.14;   // ❌ Error
```

Reason: `3.14` is treated as a `double` by default.

Correct:

```
float pi = 3.14f;
```

# Precision Example

```
float f = 3.14159265358979f;
double d = 3.14159265358979;

System.out.println(f);
System.out.println(d);
```

**Output**

```
3.1415927
3.14159265358979
```

Notice how `double` stores many more decimal places than `float`.

# 2. Non-Primitive (Reference) Data Types

Reference data types store the **memory address (reference)** of an object.

Examples:

- String
- Arrays
- Classes
- Objects
- Interfaces

**Example**

```
String name = "Santosh";
```

---

# Primitive vs Reference Data Types

|Primitive|Reference|
|---|---|
|Stores actual value|Stores memory address|
|Fixed size|Size varies|
|Built into Java|Created using classes|
|Faster|Slightly slower|
|Cannot be `null`|Can be `null`|

---

# Quick Revision

```
Primitive Data Types

Integer
├── byte
├── short
├── int
└── long

Decimal
├── float
└── double

Character
└── char

Boolean
└── boolean
```

### Remember

- Whole Numbers → `byte`, `short`, `int`, `long`
- Decimal Numbers → `float`, `double`
- Character → `char`
- True/False → `boolean`


# Java Number Systems (Binary, Octal, Decimal, Hexadecimal)

## 1. Decimal (Base 10)

- Digits: `0 - 9`
    
- Prefix: **None**
    

```java
int a = 25;
```

---

## 2. Binary (Base 2)

- Digits: `0, 1`
    
- Prefix: `0b`
    

```java
int a = 0b11001;   // 25
```

### Binary Place Values

|Bit|128|64|32|16|8|4|2|1|
|---|--:|--:|--:|--:|--:|--:|--:|--:|

Example:

```
1010

= 1×8 + 0×4 + 1×2 + 0×1
= 10
```

---

## 3. Octal (Base 8)

- Digits: `0 - 7`
    
- Prefix: `0`
    

```java
int a = 031;    // 25
```

### Octal Place Values

```
8⁰ = 1
8¹ = 8
8² = 64
8³ = 512
```

Example:

```
031

= 3×8 + 1
= 24 + 1
= 25
```

---

## 4. Hexadecimal (Base 16)

- Digits: `0 - 9`
    
- Letters: `A - F`
    
- Prefix: `0x`
    

```java
int a = 0x19;    // 25
```

### Hexadecimal Values

|Hex|Decimal|
|---|--:|
|A|10|
|B|11|
|C|12|
|D|13|
|E|14|
|F|15|

### Hexadecimal Place Values

```
16⁰ = 1
16¹ = 16
16² = 256
16³ = 4096
```

Example:

```
0x7E

= 7×16 + E
= 7×16 + 14
= 126
```

Example:

```
0xFF

= F×16 + F
= 15×16 + 15
= 255
```

---

# Number System Prefixes in Java

|Number System|Prefix|Example|
|---|---|---|
|Decimal|None|`25`|
|Binary|`0b`|`0b11001`|
|Octal|`0`|`031`|
|Hexadecimal|`0x`|`0x19`|

---

# Binary ↔ Decimal

```
1010₂

= 1×2³ + 0×2² + 1×2¹ + 0×2⁰
= 8 + 2
= 10
```

---

# Octal ↔ Decimal

```
031₈

= 3×8¹ + 1×8⁰
= 24 + 1
= 25
```

---

# Hexadecimal ↔ Decimal

```
0x7E

= 7×16¹ + 14×16⁰
= 112 + 14
= 126
```

---

# Binary ↔ Hexadecimal Conversion

**1 Hex digit = 4 Binary bits**

|Binary|Hex|
|---|---|
|0000|0|
|0001|1|
|0010|2|
|0011|3|
|0100|4|
|0101|5|
|0110|6|
|0111|7|
|1000|8|
|1001|9|
|1010|A|
|1011|B|
|1100|C|
|1101|D|
|1110|E|
|1111|F|

Example:

```
11111111

1111 1111
  F    F

= 0xFF
```

Example:

```
01111110

0111 1110
  7    E

= 0x7E
```

---

# Hexadecimal Letters

```
A = 10
B = 11
C = 12
D = 13
E = 14
F = 15
```

---

# Quick Memory Trick

```
Base 2  → Binary      → 0,1
Base 8  → Octal       → 0-7
Base 10 → Decimal     → 0-9
Base 16 → Hexadecimal → 0-9, A-F
```

Java Prefixes:

```
25       → Decimal
0b11001  → Binary
031      → Octal
0x19     → Hexadecimal
```

note
`double num1 = 12e10;`
`System.out.println(num1);`

`output=1.2E11`
### What does `e` mean?

`e` means **"× 10 to the power of"**.

```
12e10
```

means

```
12 × 10¹⁰
```

which is

```
12 × 10,000,000,000
= 120,000,000,000
```

Output:

```
1.2E11
```

or

```
120000000000.0
```

### Quick Cheat Sheet

|Literal|Meaning|Value|
|---|---|---|
|`2e3`|2 × 10³|2000|
|`5e2`|5 × 10²|500|
|`3.5e2`|3.5 × 10²|350|
|`1.2e4`|1.2 × 10⁴|12000|
|`5e-2`|5 × 10⁻²|0.05|
|`12e10`|12 × 10¹⁰|120000000000|

### Type conversion and casting
# ype Conversion vs Type Casting in Java

## What is Type Conversion?

**Type Conversion (Implicit/Widening Conversion)** is when Java **automatically converts** a smaller data type into a larger one.

No data is lost.

Example:

```
int num = 10;
double d = num;

System.out.println(d);
```

Output:

```
10.0
```

Java automatically converts `int` → `double`.

---

## Widening Conversion Order

Java performs these conversions automatically:

```
byte
  ↓
short
  ↓
int
  ↓
long
  ↓
float
  ↓
double
```

Also,

```
char
  ↓
int
  ↓
long
  ↓
float
  ↓
double
```

Example:

```
byte b = 20;
int i = b;
double d = i;
```

Everything happens automatically.

---

## Why is it Safe?

Because the larger type can store every value of the smaller type.

Example:

```
int x = 100;
double y = x;
```

```
100
↓
100.0
```

Nothing is lost.

---

# Type Casting

**Type Casting (Explicit/Narrowing Conversion)** is when **you manually convert** a larger data type into a smaller one.

Syntax:

```
datatype variable = (datatype) value;
```

Example:

```
double d = 10.75;
int x = (int) d;

System.out.println(x);
```

Output:

```
10
```

The decimal part is removed.

---

## Narrowing Conversion Order

```
double
   ↓
float
   ↓
long
   ↓
int
   ↓
short
   ↓
byte
```

You must use casting.

Example:

```
long l = 5000;
int i = (int) l;
```

---

# Examples

### Example 1 (Automatic)

```
int a = 25;
double b = a;

System.out.println(b);
```

Output

```
25.0
```

---

### Example 2 (Manual)

```
double x = 19.99;
int y = (int) x;

System.out.println(y);
```

Output

```
19
```

---

### Example 3

```
char ch = 'A';
int ascii = ch;

System.out.println(ascii);
```

Output

```
65
```

Because `'A'` has ASCII/Unicode value **65**.

---

### Example 4

```
int num = 66;
char ch = (char) num;

System.out.println(ch);
```

Output

```
B
```

---

### Example 5

```
int i = 130;
byte b = (byte) i;

System.out.println(b);
```

Output

```
-126
```

Why?

A `byte` stores values only from **-128 to 127**. Since `130` is outside this range, it **overflows** and wraps around.

---

# Conversion vs Casting

| Feature     | Type Conversion | Type Casting |
| ----------- | --------------- | ------------ |
| Also Called | Widening        | Narrowing    |
| Done By     | Java            | Programmer   |
| Syntax      | No cast needed  | `(datatype)` |
| Data Loss   | No              | Possible     |
| Safe        | Yes             | May not be   |
### ✅ Implicit conversion _can_ be written explicitly.

Example:

```
char c = 'A';
int x = c;          // Implicit
```

You can also write:

```
char c = 'A';
int x = (int) c;    // Explicit, but unnecessary
```

Both produce the same result.

---

### ❌ Explicit conversion cannot become implicit.

Example:

```
double d = 10.5;
int x = d;          // ❌ Compilation Error
```

You **must** write:

```
int x = (int) d;    // ✅ Explicit cast required
```

Java won't do it automatically because information could be lost.


`Implicit conversion`
      `↓`
`Can be written explicitly (optional)`

`Explicit conversion`
      `↓`
`Cannot be written implicitly (mandatory cast)`

# Java Operators

Java has **9 types of operators**:

1. Arithmetic Operators
2. Unary Operators
3. Assignment Operators
4. Relational (Comparison) Operators
5. Logical Operators
6. Bitwise Operators
7. Shift Operators
8. Ternary Operator
9. instanceof Operator

---

# 1. Arithmetic Operators

| Operator | Example |
|----------|---------|
| + | a + b |
| - | a - b |
| * | a * b |
| / | a / b |
| % | a % b |

---

# 2. Unary Operators

| Operator | Example |
|----------|---------|
| + | +a |
| - | -a |
| ++ | ++a, a++ |
| -- | --a, a-- |
| ! | !flag |
| ~ | ~a |

---

# 3. Assignment Operators

| Operator | Equivalent |
|----------|------------|
| = | a = b |
| += | a = a + b |
| -= | a = a - b |
| *= | a = a * b |
| /= | a = a / b |
| %= | a = a % b |
| &= | a = a & b |
| \|= | a = a \| b |
| ^= | a = a ^ b |
| <<= | a = a << b |
| >>= | a = a >> b |
| >>>= | a = a >>> b |

---

# 4. Relational (Comparison) Operators

| Operator | Example |
|----------|---------|
| == | a == b |
| != | a != b |
| > | a > b |
| < | a < b |
| >= | a >= b |
| <= | a <= b |

---

# 5. Logical Operators

| Operator | Example |
|----------|---------|
| && | a && b |
| \|\| | a \|\| b |
| ! | !a |

---

# 6. Bitwise Operators

| Operator | Example |
|----------|---------|
| & | a & b |
| \| | a \| b |
| ^ | a ^ b |
| ~ | ~a |

---

# 7. Shift Operators

| Operator | Example |
|----------|---------|
| << | a << 2 |
| >> | a >> 2 |
| >>> | a >>> 2 |

---

# 8. Ternary Operator

| Operator | Syntax |
|----------|--------|
| ?: | condition ? value1 : value2 |

Example
``
`int max = (a > b) ? a : b;`



### `Difference between a++ and ++a`

# Increment (++) Operator

`++` increases the value of a variable by **1**.

There are two types:

- Pre Increment (`++a`)
- Post Increment (`a++`)

---

# 1. Pre Increment (++a)

**Rule:**

> Increment first → Then use the value.

Example 1

```java
int a = 5;

System.out.println(++a);
```

Step-by-step

```text
a = 5

++a
↓

a = a + 1
↓

a = 6

println(6)
```

Output

```text
6
```

Memory after execution

```text
a = 6
```

---

Example 2

```java
int a = 5;

int b = ++a;

System.out.println(a);
System.out.println(b);
```

Step-by-step

```text
a = 5

++a
↓

a becomes 6

↓

Assign 6 to b
```

Final

```text
a = 6
b = 6
```

---

# 2. Post Increment (a++)

**Rule:**

> Use the current value → Then increment.

Example 1

```java
int a = 5;

System.out.println(a++);
```

Step-by-step

```text
a = 5

println(a)

↓

prints 5

↓

a becomes 6
```

Output

```text
5
```

Memory after execution

```text
a = 6
```

---

Example 2

```java
int a = 5;

int b = a++;

System.out.println(a);
System.out.println(b);
```

Step-by-step

```text
a = 5

Assign current value (5) to b

↓

a becomes 6
```

Final

```text
a = 6
b = 5
```

---

# Difference

## Pre Increment

```java
int a = 5;
int b = ++a;
```

Result

```text
a = 6
b = 6
```

---

## Post Increment

```java
int a = 5;
int b = a++;
```

Result

```text
a = 6
b = 5
```

---

# Trace Questions

### Q1

```java
int a = 10;

System.out.println(a++);
System.out.println(a);
```

Execution

```text
a = 10

Print 10

a becomes 11

Print 11
```

Output

```text
10
11
```

---

### Q2

```java
int a = 10;

System.out.println(++a);
System.out.println(a);
```

Execution

```text
a = 10

a becomes 11

Print 11

Print 11
```

Output

```text
11
11
```

---

### Q3

```java
int a = 5;

int b = ++a + 10;

System.out.println(b);
```

Execution

```text
a = 5

++a

↓

a = 6

↓

6 + 10

↓

16
```

Output

```text
16
```

---

### Q4

```java
int a = 5;

int b = a++ + 10;

System.out.println(b);
System.out.println(a);
```

Execution

```text
a = 5

Use current value

↓

5 + 10 = 15

↓

a becomes 6
```

Output

```text
15
6
```

---

### Q5

```java
int a = 5;

System.out.println(a++ + ++a);
```

Execution

```text
Initially

a = 5

First operand

a++

Use 5

a becomes 6

Second operand

++a

a becomes 7

Use 7

Expression

5 + 7 = 12
```

Output

```text
12
```

Final

```text
a = 7
```

---

### Q6

```java
int a = 1;

System.out.println(++a + ++a);
```

Execution

```text
a = 1

First ++a

a = 2

Use 2

Second ++a

a = 3

Use 3

2 + 3 = 5
```

Output

```text
5
```

Final

```text
a = 3
```

---

# Decrement (--)

Exactly the same rules.

Pre Decrement

```java
--a
```

Decrease first → Use later

---

Post Decrement

```java
a--
```

Use first → Decrease later

---

# Memory Trick

```text
++a

↓

Change

↓

Use
```

```text
a++

↓

Use

↓

Change
```

---


```
Interview Rule

Whenever you see `++` or `--`, don't try to solve it in your head.

Follow this order:

1. Write the initial value.
2. Check whether it's pre or post.
3. Update the variable if needed.
4. Replace the expression with the value it contributes.
5. Continue evaluating the rest of the expression.

This method works for every increment/decrement question.
```

# Java Control Statements

Control Statements decide the **flow of program execution**.

Java has **3 types**:

1. Selection (Decision-Making) Statements
2. Iteration (Looping) Statements
3. Jump Statements

---

# 1. Selection (Decision-Making) Statements

Used to choose between multiple paths.

- if
- if-else
- else-if ladder
- nested if
- switch

---

## if

```java
if(condition){
    // code
}
```

Flow

```text
Condition

True  → Execute

False → Skip
```

Example

```java
int age = 20;

if(age >= 18){
    System.out.println("Eligible");
}
```

---

## if-else

```java
if(condition){
    // code
}
else{
    // code
}
```

Flow

```text
Condition

True  → if block

False → else block
```

Example

```java
int age = 16;

if(age >= 18){
    System.out.println("Adult");
}
else{
    System.out.println("Minor");
}
```

---

## else-if Ladder

```java
if(condition1){

}
else if(condition2){

}
else if(condition3){

}
else{

}
```

Only the **first true condition** executes.

Example

```java
int marks = 82;

if(marks >= 90){
    System.out.println("A");
}
else if(marks >= 80){
    System.out.println("B");
}
else if(marks >= 70){
    System.out.println("C");
}
else{
    System.out.println("Fail");
}
```

---

## Nested if

```java
if(condition1){

    if(condition2){

    }

}
```

Example

```java
if(age >= 18){

    if(hasLicense){
        System.out.println("Can Drive");
    }

}
```

---

## switch

```java
switch(expression){

case value:
    break;

case value:
    break;

default:
}
```

Example

```java
int day = 3;

switch(day){

case 1:
    System.out.println("Monday");
    break;

case 2:
    System.out.println("Tuesday");
    break;

case 3:
    System.out.println("Wednesday");
    break;

default:
    System.out.println("Invalid");
}
```

---

## break in switch

Without break

```java
case 1:
System.out.println("One");

case 2:
System.out.println("Two");
```

Output

```text
One
Two
```

With break

```java
case 1:
System.out.println("One");
break;
```

Output

```text
One
```

---

# 2. Iteration (Looping) Statements

Used to execute a block repeatedly.

- while
- do-while
- for
- enhanced for (for-each)

---

## while

```java
while(condition){

}
```

Flow

```text
Condition

True → Execute → Check Again

False → Exit
```

---

## do-while

```java
do{

}while(condition);
```

Flow

```text
Execute Once

↓

Check Condition

↓

Repeat if True
```

Runs **at least once**.

---

## for

```java
for(initialization; condition; update){

}
```

Flow

```text
Initialization

↓

Condition

↓

Body

↓

Update

↓

Condition
```

---

## Enhanced for (For-Each)

```java
for(type variable : collection){

}
```

Example

```java
int arr[] = {10,20,30};

for(int x : arr){

    System.out.println(x);

}
```

---

# 3. Jump Statements

Used to alter the normal flow.

- break
- continue
- return

---

## break

Terminates the loop immediately.

```java
for(int i=1;i<=10;i++){

    if(i==5)
        break;

    System.out.println(i);

}
```

Output

```text
1
2
3
4
```

---

## continue

Skips the current iteration.

```java
for(int i=1;i<=5;i++){

    if(i==3)
        continue;

    System.out.println(i);

}
```

Output

```text
1
2
4
5
```

---

## return

Exits the current method.

```java
return;
```

or

```java
return value;
```

---

# Summary

| Category  | Statements                              |
| --------- | --------------------------------------- |
| Selection | if, if-else, else-if, nested if, switch |
| Iteration | while, do-while, for, enhanced for      |
| Jump      | break, continue, return                 |

### Array
## 1. Declaring an Array

```
int[] numbers;
```

or (less commonly)

```
int numbers[];
```

Both are correct, but `int[] numbers` is the preferred style.

---

## 2. Creating an Array

```
int[] numbers = new int[5];
```

This creates an array that can hold **5 integers**.

Memory representation:

```
Index:    0   1   2   3   4
Value:    0   0   0   0   0
```

Every element gets a **default value**.

|Data Type|Default Value|
|---|---|
|int|0|
|double|0.0|
|char|'\u0000'|
|boolean|false|
|String|null|

---

## 3. Initializing an Array

### Method 1

```
int[] marks = new int[5];

marks[0] = 85;
marks[1] = 90;
marks[2] = 78;
marks[3] = 88;
marks[4] = 95;
```

### Method 2 (Shortcut)

```
int[] marks = {85, 90, 78, 88, 95};
```

---

## 4. Accessing Elements

```
System.out.println(marks[0]);
System.out.println(marks[3]);
```

Output

```
85
88
```

Remember:

- First element → index **0**
- Last element → **length - 1**

---

## 5. Modifying Elements

```
marks[2] = 100;

System.out.println(marks[2]);
```

Output

```
100
```

---

## 6. Finding Array Length

```
System.out.println(marks.length);
```

Output

```
5
```

Notice:

- Arrays use **`length`** (property)
- Strings use **`length()`** (method)

---

## 7. Traversing an Array

### Using a for loop

```
int[] marks = {85, 90, 78, 88, 95};

for(int i = 0; i < marks.length; i++)
{
    System.out.println(marks[i]);
}
```

Output

```
85
90
78
88
95
```

---

### Using Enhanced for loop (For-each)

```
int[] marks = {85, 90, 78, 88, 95};

for(int x : marks)
{
    System.out.println(x);
}
```

Here,

```
x
```

stores one element at a time.

---

## 8. Arrays of Strings

```
String[] names = {"John", "Alice", "Bob"};

System.out.println(names[1]);
```

Output

```
Alice
```

## 10. Multidimensional Arrays (2D Array)

```
int[][] matrix =
{
    {1,2,3},
    {4,5,6},
    {7,8,9}
};

System.out.println(matrix[1][2]);
```

Output

```
6
```

Memory

```
1 2 3
4 5 6
7 8 9
```

---

## 11. Common Errors

### Array Index Out of Bounds

```
int[] arr = {10,20,30};

System.out.println(arr[3]);
```

Output

```
Exception in thread "main"
java.lang.ArrayIndexOutOfBoundsException
```

Valid indices are only:

```
0
1
2
```

---

## 12. Important Points

- Arrays store **same type** of elements.
- Index starts from **0**.
- Size is **fixed** after creation.
- Arrays are **objects** in Java and are stored on the heap; the array variable itself is a reference.
- Use `array.length` to get the size.



### Array of objects
```
class Student
{
    String name;
}

public class Main
{
    public static void main(String[] args)
    {
        Student[] students = new Student[2];

        students[0] = new Student();
        students[0].name = "Santosh";

        students[1] = new Student();
        students[1].name = "Rahul";

        System.out.println(students[0].name);
    }
}
```
# Line 1

```
class Student
{
    String name;
}
```

This defines a class called `Student`.

Every `Student` object created from this class will have one instance variable:

```
String name;
```

No object has been created yet.

---

# Line 2

```
Student[] students = new Student[2];
```

Break this into two parts.

### Part 1

```
Student[]
```

This means:

> "I want an array that stores references to `Student` objects."

---

### Part 2

```
new Student[2]
```

Java creates an array that has space for **2 Student references**.

At this moment, **no Student objects exist.**

Memory looks like this:

```
students
    |
    V

+--------+--------+
| null   | null   |
+--------+--------+
    0        1
```

Each element is `null` because no object has been assigned yet.

---

# Line 3

```
students[0] = new Student();
```

Again, split it.

## First

```
new Student()
```

Java creates a new `Student` object.

Its instance variable gets its default value.

```
Student Object

-------------
name = null
-------------
```

---

## Then

Java stores the reference to this object inside index `0`.

Memory becomes:

```
students

+-----------+--------+
| Reference | null   |
+-----------+--------+
      |
      |
      V

Student Object

-------------
name = null
-------------
```

Notice carefully:

The array does **not** contain the Student object.

It contains a **reference** to that object.

---

# Line 4

```
students[0].name = "Santosh";
```

Java executes this in three steps.

### Step 1

```
students[0]
```

Go to index `0`.

```
students

+-----------+--------+
| Reference | null   |
+-----------+--------+
```

Java gets the reference stored there.

---

### Step 2

```
.name
```

Using that reference, Java reaches the Student object.

```
Student Object

-------------
name = null
-------------
```

---

### Step 3

```
= "Santosh";
```

The value of `name` changes.

```
Student Object

--------------------
name = "Santosh"
--------------------
```

Memory now:

```
students

+-----------+--------+
| Reference | null   |
+-----------+--------+
      |
      |
      V

Student Object

--------------------
name = "Santosh"
--------------------
```

---

# Line 5

```
students[1] = new Student();
```

Another object is created.

This is **not** the same object.

A completely new Student object is created.

Memory:

```
students

+-----------+-----------+
| Reference | Reference |
+-----------+-----------+
      |            |
      |            |
      V            V

Student        Student
--------       --------
name=Santosh   name=null
```

Now there are **two Student objects**.

---

# Line 6

```
students[1].name = "Rahul";
```

Java accesses the second object and changes its `name`.

Memory:

```
students

+-----------+-----------+
| Reference | Reference |
+-----------+-----------+
      |            |
      |            |
      V            V

Student        Student
--------       --------
name=Santosh   name=Rahul
```

---

# Line 7

```
System.out.println(students[0].name);
```

Java executes it like this:

### First

```
students[0]
```

Get the reference stored at index `0`.

↓

### Second

Follow that reference to the Student object.

↓

### Third

Access

```
.name
```

↓

Value found:

```
Santosh
```

So the output is

```
Santosh
```

---

# Complete Memory at the End

```
Stack                               Heap

students -----------------------> Array Object
                                  +-----------+-----------+
                                  | Reference | Reference |
                                  +-----------+-----------+
                                        |           |
                                        |           |
                                        V           V

                                  Student      Student
                                  --------     --------
                                  name         name
                                  Santosh      Rahul
```

---

# Very Important Interview Question

What happens if you remove this line?

```
students[0] = new Student();
```

So the code becomes:

```
Student[] students = new Student[2];

students[0].name = "Santosh";
```

After the first line, memory is:

```
students

+--------+--------+
| null   | null   |
+--------+--------+
```

Now Java tries to execute:

```
students[0].name
```

But `students[0]` is `null`, so there is no `Student` object whose `name` can be accessed.

Therefore Java throws:

```
Exception in thread "main"
java.lang.NullPointerException
```

---

## Summary

- `Student[] students` → Declares a reference to an array of `Student` references.
- `new Student[2]` → Creates **one array object** with two elements initialized to `null`.
- `new Student()` → Creates **one Student object**.
- `students[0] = new Student()` → Stores the reference to that object in index `0`.
- `students[0].name = "Santosh"` → Accesses the object at index `0` and changes its `name`.
- Each call to `new Student()` creates a **different object** on the heap.

Once you're comfortable with this, the next concept is **sharing references** (e.g., `students[1] = students[0];`), which explains why changing one reference can affect another. It's one of the most important Java concepts to understand.

### Question

**Write a Java program to store and display the details of `n` students using an array of objects.**

Requirements:

- Create a `Student` class with the following instance variables:
    - `String name`
    - `int age`
    - `int roll`
- In the `main()` method:
    - Read the number of students `n` from the user.
    - Create an array of `Student` objects of size `n`.
    - Accept the name, age, and roll number for each student.
    - Store the details in the corresponding `Student` object.
    - Display the details of all students using an enhanced `for` loop.

### Sample Input

```
Enter no of students
3

Santosh
19
101

Rahul
20
102

Amit
18
103
```

### Sample Output

```
Santosh 101 19
Rahul 102 20
Amit 103 18
```

---

### Interview/Exam Variation

Sometimes the question is phrased as:

> **Create a class `Student` with data members `name`, `age`, and `roll`. In the `main()` method, create an array of `Student` objects, accept the details of `n` students from the user, and display all the student details.**
```
import java.util.Scanner;

class Student
{
    String name;
    int age;
    int roll;
}

public class studentobj
{
    public static void main(String args[])
    {
        Scanner sc = new Scanner(System.in);

        System.out.println("Enter no of students");
        int n = sc.nextInt();

        Student[] students = new Student[n];

        for(int i = 0; i < n; i++)
        {
            students[i] = new Student();

            students[i].name = sc.next();
            students[i].age = sc.nextInt();
            students[i].roll = sc.nextInt();
        }

        for(Student x : students)
        {
            System.out.println(x.name + " " + x.roll + " " + x.age);
        }

        sc.close();
    }
}
```


### three important lines

```
Student[] students = new Student[n];
```

➡️ Creates an **array of `Student` references**. Every element is initially `null`.

---

```
students[i] = new Student();
```

➡️ Creates the actual `Student` object and stores its reference in the array.

---

```
for(Student x : students)
```

➡️ `x` is a reference variable that points to each `Student` object in the array one by one.

Those three lines are the heart of the program. Everything else is just taking input and printing output.