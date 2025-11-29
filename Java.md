JAVA BASICS:

What is Java?

Java is a high-level, object-oriented programming language that was originally developed by Sun Microsystems (now owned by Oracle) and released in 1995.

Characterstics :

1.Platform Independent-compile to bytecode and run anywhere
2.Object-Oriented-Java is designed around the concept of objects and classes
3.Simple and Easy to learn
4.Secure
5.Robust-Java has strong memory management, exception handling, and a powerful         type-checking mechanism
6.Multithreaded
---------------------------------------------------------------------------------
Variables :

A variable in Java is a named memory location used to store data.
It acts as a container that holds values which can change during program execution.

1.Local Variables

Declared inside a method, constructor, or block.

Created when method is called, destroyed after method ends.

Must be initialized before use.

No default value.

void show() {
    int x = 10;  // local variable
    System.out.println(x);
}

2.Instance Variables (Non-static)

Declared inside a class but outside methods.

Each object has its own copy of these variables.

Default values assigned (0, null, false, etc. if not initialized).

class Student {
    String name;   // instance variable
    int age;       // instance variable
}

3. Static Variables (Class Variables)

Declared with static keyword.

Shared among all objects of the class.(Memory allocation only once)

Only one copy exists in memory.

Can be accessed using class name.

class Student {
    static String school = "ABC School";  // static variable
}
---------------------------------------------------------------------------------
Data types:

🔹 Primitive Data Types

These are the basic building blocks of data in Java.

Provided by Java itself.

Store actual values (not references).

Faster and use less memory.

Always lowercase (e.g., int, boolean, char).

8 types: byte, short, int, long, float, double, char, Boolean

🔹 Non-Primitive (Reference) Data Types

These are created by the programmer (except String).

Store reference (memory address) of objects, not the actual value.

More powerful → can store multiple values.

Start with capital letter (e.g., String, Array, Class).

Examples: String, Array, Class, Interface, Enum, Objects.
---------------------------------------------------------------------------------What are Keywords in Java?

Keywords are predefined words in Java with a special meaning.

They cannot be used as variable names, method names, or class names.

Java has 53(51 used-2 unused(goto,const)) keywords (depending on version).
---------------------------------------------------------------------------------
Operators :
✅ Quick Summary

Arithmetic → + - * / % ++ --  → basic math.

Relational → == != > < >= <=  → comparisons

Logical → && || !  → combine booleans.

Assignment → = += -= *= /= %= → modify values.

Unary → + - ++ -- !  → one operand.

Ternary → ?:  → short if-else.

Bitwise → & | ^ ~ << >> >>>  → work at bit level.
---------------------------------------------------------------------------------

Java Class 
