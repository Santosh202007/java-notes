 # 1. What is a String?

A **String** is a sequence of characters.

```
String s = "Hello";
```

Unlike C/C++, Java Strings are **objects**, not character arrays.

```
String name = new String("Santosh");
```

---

# 2. Strings are immutable

Once created, they **cannot be changed**


```
String s = "Hello";
s.concat(" World");

System.out.println(s);
```

Output

```
Hello
```

Because `concat()` creates a new String instead of modifying the old one.

Correct:

```
s = s.concat(" World");
```

Output

```
Hello World
```

### Advantages

- Thread Safe
- Secure
- String Pool works efficiently
- Faster hashing

---

# 3. Ways to Create Strings
## Method 1

```
String s = "Hello";
```

Memory:

```
Heap
┌───────────────────────────────┐
│      String Pool              │
│  ┌─────────────────────────┐  │
│  │ "Hello"                 │◄─┼── s
│  └─────────────────────────┘  │
└───────────────────────────────┘
```

The JVM first checks the **String Pool**.

- If `"Hello"` is already there → reuse it.
- If not → create it **inside the String Pool**.

The **String Pool itself is a special area inside the Heap.**

So yes, an object is created on the heap, but specifically in the **String Pool**.

---

## Method 2

```
String s = new String("Hello");
```

Many beginners think only one object is created.

Actually **two objects can be involved.**

### Step 1

The literal `"Hello"` is checked in the String Pool.

If not present:

```
Heap
┌───────────────────────────────┐
│ String Pool                   │
│  "Hello"                      │
└───────────────────────────────┘
```

### Step 2

`new String("Hello")` forces Java to create **another object** outside the pool.

```
Heap

String Pool
┌──────────────┐
│ "Hello"      │
└──────────────┘
       ▲
       │
Heap (Normal Objects)
┌──────────────┐
│ "Hello"      │◄── s
└──────────────┘
```

So now there are **two String objects** containing `"Hello"`.

---

## Why create another object?

Because `new` **always creates a fresh object**, even if an identical string already exists.

That's why:

---

```
String s1 = "Hello";
String s2 = new String("Hello");

System.out.println(s1 == s2);
```

Output:

```
false
```

Because

```
String Pool
┌─────────────┐
│ "Hello"     │◄── s1
└─────────────┘

Normal Heap
┌─────────────┐
│ "Hello"     │◄── s2
└─────────────┘
```

Different objects → different addresses.

---



> **Method 1:** Creates (or reuses) a String object in the **String Pool** (which is part of the heap).
> 
> **Method 2:** Creates a **new String object in the normal heap** and also uses the **String Pool** for the literal if it isn't already present.



### 1. Normal syntax (String Literal)

```
String s = "Hello";
```

- JVM checks the **String Pool**.
- If `"Hello"` already exists → `s` points to that object.
- If it doesn't exist → creates it in the **String Pool**, then `s` points to it.

```
String Pool
+---------+
| "Hello" | <── s
+---------+
```

---

### 2. Using `new`

```
String s = new String("Hello");
```

- JVM first checks the **String Pool** for `"Hello"` (creates it if needed).
- Then `new` **always creates another object** in the normal heap.
- `s` points to this **new heap object**, **not** to the pooled one.

```
String Pool
+---------+
| "Hello" |
+---------+

Normal Heap
+---------+
| "Hello" | <── s
+---------+
```


## Question to track memory
```
public class Main {

    public static void main(String[] args) {

        String s1 = "Java";              // Literal

        String s2 = "Python";            // New literal

        String s3 = "Java";              // Reuse String Pool

        String s4 = new String("Java");  // Heap Object

        String s5 = s1;                  // Reference Copy

        String s6 = new String("C");     // Creates Pool + Heap

        String s7 = "C";                 // Reuse Pool

        String s8 = s6;                  // Heap Reference Copy

    }
}
```

### answers
# Initially

```
STACK
-------------------------

STRING POOL
-------------------------

HEAP
-------------------------
```

---

# Line 1

```
String s1 = "Java";
```

JVM checks String Pool.

❌ "Java" not found.

Creates it.

```
STACK
-------------------------
s1
 |
 |
 v

STRING POOL
-------------------------
+----------------+
| "Java"         |  P1
+----------------+
        ^
        |
        s1

HEAP
-------------------------
Empty
```

---

# Line 2

```
String s2 = "Python";
```

```
STACK
-------------------------
s1 ------+
         |
s2 --+   |
      |  |

STRING POOL
-------------------------
P1                 P2
+---------+      +-----------+
| "Java"  |      | "Python"  |
+---------+      +-----------+
     ^                ^
     |                |
    s1               s2

HEAP
-------------------------
Empty
```

---

# Line 3

```
String s3 = "Java";
```

JVM finds `"Java"`.

No object created.

```
STACK
-------------------------
s1 ----\
         \
s3 -------> P1

s2 --------> P2

STRING POOL
-------------------------
P1(Java)

P2(Python)

HEAP
-------------------------
Empty
```

Notice

```
s1
 \
  \
   ---> Java

  /
 /
s3
```

Both references point to the **same object**.

---

# Line 4

```
String s4 = new String("Java");
```

Step 1

Looks for `"Java"`.

Already exists.

Step 2

Creates NEW object.

```
STACK
-------------------------
s1 ----\
         \
s3 -------> P1(Java)

s2 --------> P2(Python)

s4 ----------------------+

STRING POOL
-------------------------
P1(Java)

P2(Python)

HEAP
-------------------------

H1
+---------+
| "Java"  |
+---------+
     ^
     |
     s4
```

Now there are

```
Java
```

in two places.

---

# Line 5

```
String s5 = s1;
```

Only reference copy.

```
STACK
-------------------------

s1 ----\
         \
s3 ------ \
           \
s5 ---------> P1(Java)

s2 ----------> P2(Python)

s4 ----------> H1(Java)

STRING POOL
-------------------------

Java

Python

HEAP
-------------------------

Java
```

Notice

```
s1

s3

s5
```

all have the **same address**.

---

# Line 6

```
String s6 = new String("C");
```

This is the interesting one.

Step 1

"C" isn't in the pool.

Create it.

Step 2

Create another object because of `new`.

```
STACK
-------------------------------------------------

s1 ----\
         \
s3 ------ \
           \
s5 ---------> P1(Java)

s2 ------------------> P2(Python)

s4 ------------------> H1(Java)

s6 ------------------> H2(C)

STRING POOL
-------------------------------------------------

P1
+---------+
| Java    |
+---------+

P2
+---------+
| Python  |
+---------+

P3
+---------+
| C       |
+---------+

HEAP
-------------------------------------------------

H1
+---------+
| Java    |
+---------+

H2
+---------+
| C       |
+---------+
```

Notice

For this ONE line

```
new String("C")
```

**Two objects** were created.

One in Pool

One in Heap

---

# Line 7

```
String s7 = "C";
```

Pool already contains C.

Reuse.

```
STACK
-------------------------------------------------

s1 ----\
         \
s3 ------ \
           \
s5 ---------> P1(Java)

s2 ------------------> P2(Python)

s4 ------------------> H1(Java)

s6 ------------------> H2(C)

s7 ------------------> P3(C)

STRING POOL
-------------------------------------------------

P1 Java

P2 Python

P3 C

HEAP
-------------------------------------------------

H1 Java

H2 C
```

Notice

```
s6
```

does **NOT**

point to

```
P3
```

because

```
new
```

made it point to Heap.

---

# Line 8

```
String s8 = s6;
```

Reference copy.

```
STACK
-------------------------------------------------

s1 ----\
         \
s3 ------ \
           \
s5 ---------> P1(Java)

s2 ------------------> P2(Python)

s4 ------------------> H1(Java)

s6 ----\
         \
s8 -------> H2(C)

s7 ------------------> P3(C)

STRING POOL
-------------------------------------------------

P1
+---------+
| Java    |
+---------+

P2
+---------+
| Python  |
+---------+

P3
+---------+
| C       |
+---------+

HEAP
-------------------------------------------------

H1
+---------+
| Java    |
+---------+

H2
+---------+
| C       |
+---------+
```

---

# Final Memory (Clean Diagram)

```
                    STACK
═══════════════════════════════════════════════════

s1 ─────┐
s3 ─────┤
s5 ─────┘──────────────► P1

s2 ────────────────────► P2

s4 ────────────────────► H1

s6 ─────┐
s8 ─────┘──────────────► H2

s7 ────────────────────► P3


═══════════════════════════════════════════════════
               STRING POOL
═══════════════════════════════════════════════════

P1
+------------------+
| "Java"           |
+------------------+

P2
+------------------+
| "Python"         |
+------------------+

P3
+------------------+
| "C"              |
+------------------+


═══════════════════════════════════════════════════
                 HEAP
═══════════════════════════════════════════════════

H1
+------------------+
| "Java"           |
+------------------+

H2
+------------------+
| "C"              |
+------------------+
```

---

### Key observations

- **String Pool objects:** `"Java"`, `"Python"`, `"C"` → **3 objects**
- **Heap objects:** `new String("Java")`, `new String("C")` → **2 objects**
- **Total `String` objects:** **5**

References sharing the **same address**:

- `s1`, `s3`, `s5` → pooled `"Java"`
- `s6`, `s8` → heap `"C"`

References with the **same value but different addresses**:

- `s1` (pool `"Java"`) and `s4` (heap `"Java"`)
- `s6` (heap `"C"`) and `s7` (pool `"C"`)

# 4. String Pool

Java stores string literals inside a special memory called the **String Pool**.

```
String a = "Java";
String b = "Java";
```

Only one object is created.

```
Pool

Java
 ↑
a
b
```

---

Using `new`

```
String a = new String("Java");
String b = new String("Java");
```

Creates

```
Pool -> Java

Heap -> Java
Heap -> Java
```

---

# 5. == vs equals()

## ==

Checks reference.

```
String a = "Hello";
String b = "Hello";

System.out.println(a == b);
```

Output

```
true
```

---

```
String a = new String("Hello");
String b = new String("Hello");

System.out.println(a == b);
```

Output

```
false
```

Different objects.

---

## equals()

Checks content.

```
String a = new String("Hello");
String b = new String("Hello");

System.out.println(a.equals(b));
```

Output

```
true
```

---

# Interview Question

Which one should be used?

✔ Use `equals()` to compare strings.

---

# 6. String Methods
## length()

```
String s = "Programming";

System.out.println(s.length());
```

Output

```
11
```

---

## charAt()

```
String s = "Programming";
System.out.println(s.charAt(0));
```

Output

```
P
```

---

## substring()

```
String s = "Programming";

System.out.println(s.substring(3));
```

Output

```
gramming
```

---

```
System.out.println(s.substring(3,7));
```

Output

```
gram
```

---

## indexOf()

```
String s = "Programming";

System.out.println(s.indexOf('g'));
```

Output

```
3
```

---

## lastIndexOf()

```
String s = "Programming";
System.out.println(s.lastIndexOf('g'));
```

Output

```
10
```

---

## contains()

```
String s = "Programming";

System.out.println(s.contains("gram"));
```

Output

```
true
```

---

## startsWith()

```
String s = "Programming";
s.startsWith("Pro")
```

Output

```
true
```

---

## endsWith()

```
String s = "Programming";
s.endsWith("ing")
```

Output

```
true
```
## equalsIgnoreCase()

```
String a = "JAVA";

System.out.println(a.equalsIgnoreCase("java"));
```

Output

```
true
```

---

## toUpperCase()

```
System.out.println(s.toUpperCase());
```

---

## toLowerCase()

```
System.out.println(s.toLowerCase());
```

---

## trim()

Removes leading and trailing spaces.

```
String s = "   Java   ";

System.out.println(s.trim());
```

---

## replace()

```
String s = "banana";

System.out.println(s.replace('a','o'));
```

Output

```
bonono
```

---

## replaceAll()

Uses Regular Expressions.

```
String s = "abc123";

System.out.println(s.replaceAll("[0-9]",""));
```

Output

```
abc
```

---

## split()

```
String s = "Java,Python,C++";

String arr[] = s.split(",");
```

Result

```
Java
Python
C++
```

---

## isEmpty()

```
String s = "";

System.out.println(s.isEmpty());
```

Output

```
true
```

---

## isBlank() (Java 11)

```
String s = "   ";

System.out.println(s.isBlank());
```

Output

```
true
```

---

# 7. String Concatenation

Using +

```
String a = "Hello";
String b = "World";

System.out.println(a+b);
```

Output

```
HelloWorld
```

---

Using concat()

```
a.concat(b);
```

---

# 8. String Comparison

```
compareTo()
```

Returns

```
0 -> Equal

Positive -> First greater

Negative -> Second greater
```

Example

```
System.out.println("abc".compareTo("abd"));
```

Output

```
-1
```

---

# 9. String to Character Array

```
char arr[] = s.toCharArray();
```

---

# 10. Character Array to String

```
char arr[]={'J','a','v','a'};

String s = new String(arr);
```

---

# 11. String to Integer

```
String s = "123";

int x = Integer.parseInt(s);
```

---

# 12. Integer to String

```
int x = 123;

String s = String.valueOf(x);
```

or

```
Integer.toString(x);
```

---

# 13. Reverse a String

Method 1

```
String s = "Java";

String rev = "";

for(int i=s.length()-1;i>=0;i--)
{
    rev += s.charAt(i);
}

System.out.println(rev);
```

Output

```
avaJ
```

---

Method 2 (StringBuilder)

```
String s = "Java";

String rev = new StringBuilder(s).reverse().toString();

System.out.println(rev);
```

---

# 14. Palindrome

```
String s = "madam";

String rev = new StringBuilder(s).reverse().toString();

System.out.println(s.equals(rev));
```

Output

```
true
```

---

# 15. Count Vowels

```
String s = "Programming";

int count = 0;

for(int i=0;i<s.length();i++)
{
    char c = Character.toLowerCase(s.charAt(i));

    if(c=='a'||c=='e'||c=='i'||c=='o'||c=='u')
        count++;
}

System.out.println(count);
```

---

# 16. Count Words

```
String s = "Java is awesome";

String words[] = s.split(" ");

System.out.println(words.length);
```

---

# 17. Remove Spaces

```
String s = "Ja va";

System.out.println(s.replace(" ",""));
```

Output

```
Java
```

---

---

# 20. Frequently Asked Interview Programs

- Reverse String
- Check Palindrome
- Count Vowels
- Count Words
- Remove Spaces
- Remove Duplicate Characters
- Count Frequency of Characters
- Find First Non-Repeated Character
- Check Anagram
- Reverse Words
- Compress String (`aaabb → a3b2`)
- Toggle Case
- Capitalize First Letter of Every Word
- Find Duplicate Characters
- Count Digits, Alphabets, and Special Characters
- Check if Two Strings are Rotations
- Longest Common Prefix
- Validate Email (Regex)
- Reverse Each Word in a Sentence

---

# 21. Important Interview Differences

|Topic|String|StringBuilder|StringBuffer|
|---|---|---|---|
|Mutable|❌ No|✅ Yes|✅ Yes|
|Thread Safe|✅ Yes (immutable)|❌ No|✅ Yes|
|Performance|Slow for repeated modifications|Fastest|Slower than StringBuilder|
|Synchronization|Not needed|No|Yes|

---

# 22. Most Important Methods to Memorize

- `length()`
- `charAt()`
- `substring()`
- `contains()`
- `equals()`
- `equalsIgnoreCase()`
- `compareTo()`
- `indexOf()`
- `lastIndexOf()`
- `startsWith()`
- `endsWith()`
- `replace()`
- `replaceAll()`
- `split()`
- `trim()`
- `isEmpty()`
- `isBlank()`
- `toUpperCase()`
- `toLowerCase()`
- `toCharArray()`
- `String.valueOf()`
- `Integer.parseInt()`
- `concat()`

## Note:(memory understanding)

```
String name = "navin";
name = name + " reddy";

System.out.println(name);

String s1 = "Navin";
String s2 = "Navin";

System.out.println(s1 == s2);
```
Let's see **exactly** what happens inside memory.

---

# Step 1

```
String name = "navin";
```

Java first checks the **String Constant Pool (SCP)**.

```
Heap
────────────────────────────────────────────

String Constant Pool

101
+---------+
| "navin" |
+---------+

Normal Heap
(empty)
```

Now the variable stores the reference (address).

```
Stack                     Heap
------                    -----------------
name ------------------> 101 ("navin")
```

Notice:

The variable **does not store the string**.

It stores the **address** of the String object.

```
name = 101
```

---

# Step 2

Now execute

```
name = name + " reddy";
```

This is **not modifying** the original object.

Internally Java performs something similar to

```
String temp = "navin reddy";
name = temp;
```

Now Java checks the pool.

Is `"navin reddy"` already there?

No.

So Java creates another object.

```
String Pool

101
+---------+
| "navin" |
+---------+

105
+---------------+
| "navin reddy" |
+---------------+
```

Now

```
Before

name --->101


After

name --->105
```

The old object still exists.

```
101 -> "navin"
```

No variable is pointing to it anymore.

It becomes **eligible for Garbage Collection**.

Notice

Nothing changed inside

```
"navin"
```

Instead,

Java created

```
"navin reddy"
```

This is why Strings are called **immutable**.

---

# Why didn't Java modify "navin"?

Suppose

```
String a = "Java";
String b = "Java";
```

Memory

```
Pool

101
+--------+
| "Java" |
+--------+

Stack

a --->101
b --->101
```

Both variables point to the **same object**.

Now imagine if Strings were mutable.

```
a = a + " Programming";
```

If Java modified the object itself...

```
101

"Java Programming"
```

Then

```
b
```

would also become

```
Java Programming
```

even though you never changed `b`.

That would be disastrous.

So Java never changes String objects.

Instead,

```
Old object
↓

"Java"

New object

"Java Programming"
```

---

# Step 3

```
String s1 = "Navin";
String s2 = "Navin";
```

Java first creates

```
Pool

102

+---------+
| "Navin" |
+---------+
```

Now

```
Stack

s1 ----->102

s2 ----->102
```

Both references are identical.

```
s1 == s2

102 == 102

true
```

---

# What if we use new?

```
String s1 = new String("Navin");
String s2 = new String("Navin");
```

This is completely different.

Java still places the literal inside the pool.

```
Pool

101

"Navin"
```

Then

```
new String("Navin")
```

creates another object in the normal heap.

```
Heap

201

"Navin"
```

Second line

```
new String("Navin")
```

creates

```
202

"Navin"
```

Memory

```
Pool

101
"Navin"


Heap

201
"Navin"

202
"Navin"
```

Variables

```
s1 --->201

s2 --->202
```

Now

```
s1 == s2

201 == 202

false
```

But

```
s1.equals(s2)
```

compares contents.

```
"Navin"

==

"Navin"
```

Result

```
true
```

---

# Why does String Pool exist?

Imagine one million variables.

```
String country = "India";
```

Without pooling

```
Heap

India
India
India
India
India
India
India
...
```

Huge waste of memory.

Instead

```
Pool

500

"India"
```

Every variable simply stores

```
500
```

This saves enormous memory.

# Mutable vs Immutable Strings

## Immutable

Cannot change after creation.

```
String
```

Example

```
String s = "Java";

s.concat(" Programming");
```

Memory

```
Before

101

Java
```

After

```
101

Java

105

Java Programming
```

Original object remains unchanged.

---

## Mutable

Can change without creating another object.

Examples

```
StringBuilder

StringBuffer
```

Example

```
StringBuilder sb = new StringBuilder("Java");

sb.append(" Programming");
```

Memory

```
Heap

201

Java
```

After append

```
Heap

201

Java Programming
```

Notice

Address **did not change**.

The object itself changed.

```
201

↓

Java

↓

Java Programming
```

This is mutation.

---

# Why is String immutable?

Java designers made `String` immutable because it provides several important benefits:

- **Security:** Class names, file paths, URLs, and database credentials often use `String`. If these could change unexpectedly, programs could become unsafe.
- **String Pool:** Multiple variables can safely share the same object because nobody can modify it.
- **Thread Safety:** Multiple threads can read the same `String` simultaneously without synchronization.
- **Hashing Performance:** `String` is heavily used as a key in collections like `HashMap`. Since its contents never change, its hash code can be cached and reused.

---

## String Doubts Notes

### 1. `String a = new String("suresh");`

- If `"suresh"` is not already in the String Pool:
    - One object is created in the **String Pool**.
    - One object is created in the **Heap**.
- `a` points to the **Heap object**.

---

### 2. Does any reference point to the String Pool object?

- No Java variable points to it.
- The **String Pool internally maintains a reference**, so it remains available for reuse.

---

### 3. Will the String Pool object be removed?

- Not immediately.
- The String Pool keeps it for reuse.
- In modern JVMs, pooled strings can be garbage collected if they are no longer reachable, but string literals are generally retained for reuse during the application's lifetime.

---

### 4. What happens when we append text?

```
String a = new String("suresh");
a = a + " kumar";
```

- Java **does not modify** the existing string.
- A **new String object** `"suresh kumar"` is created.
- `a` now points to the new object.
- The old heap object `"suresh"` becomes **eligible for garbage collection** if nothing else references it.

---

### 5. Why is a new object created?

- Because **Strings are immutable**.
- Once created, a String's content cannot be changed.
- Any operation like `+`, `concat()`, `replace()`, etc., creates a **new String object**.
# Interview Summary

|Feature|String|StringBuilder|StringBuffer|
|---|---|---|---|
|Mutable|❌ No|✅ Yes|✅ Yes|
|New object on modification|✅ Yes|❌ No|❌ No|
|Thread-safe|Safe because immutable|❌ No|✅ Yes|
|Fast for repeated changes|❌ No|✅ Yes|Slightly slower than `StringBuilder`|
|Uses String Pool|✅ Yes (for literals)|❌ No|❌ No|

If you can visualize **variables holding references** and the **String Constant Pool vs the normal heap**, you'll be able to answer nearly every String memory question asked in Java interviews.

These are exactly the key interview points from the questions you asked.
## Rule 1: Immutable objects → Modification creates a new object

The original object **cannot** be changed. Any operation that appears to modify it actually returns a **new object**.

## Rule 2: Mutable objects → Modification changes the same object

The object's internal state changes.  
**No new object is created** (unless you explicitly create one).



## String builder and buffer
