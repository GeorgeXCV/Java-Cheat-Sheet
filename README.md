# Java-Cheat-Sheet
Java is a general-purpose, concurrent, class-based, object-oriented computer programming language. 

## Table of Contents

- [Java API](#java-api)
- [Class](#class)
- [Output](#output)
- [Input](#input)
- [Variables](#variables)
- [Operators](#operators)
- [Control Structures](#control-structures)

## Java API
In the Java  API, classes are grouped into packages. ArrayList is in the package called java.util, which holds a pile of utility classes. You have to know the full name* of the class you want to use in your code.

```java
import java.util.ArrayList;
```

Type the full name each time you use it, (unless the class is in the java.lang package). 

```java
java.util.ArrayList<Dog> list = new java.util.ArrayList<Dog>();
```
Import all classes inside of java.security package

```java
import java.security.*;
```

## Class
In Java, everything goes in a class. You’ll type your source code file (with a .java extension), then compile it into a new class file (with a .class extension). When you run your program, you’re really running a class. Running a program means telling the Java Virtual Machine (JVM) to “Load the Hello class, then start executing its main() method. Keep running ‘til all the code in main is finished.”

When the JVM starts running, it looks for the class you give it at the command line. Then it starts looking for a specially-written method that looks exactly like:

```java
public static void main (String[] args) {      
  // your code goes here     
}
```

Next, the JVM runs everything between the curly braces {  } of your main method. Every Java application has to have at least one class, and at least one main method.


```java
class Bicycle {

// Bicycle's Fields/Variables
public int cadence; // Public: Can be accessed from anywhere
private int speed;  // Private: Only accessible from within the class
protected int gear; // Protected: Accessible from the class and subclasses
String name; // default: Only accessible from within this package
static String className; // Static class variable

// Static block
// Java has no implementation of static constructors, but
// has a static block that can be used to initialize class variables
// (static variables).
// This block will be called when the class is loaded.
static {
  className = "Bicycle";
}

// Constructors are a way of creating classes
// This is a constructor
public Bicycle() {
  // You can also call another constructor:
  // this(1, 50, 5, "Bontrager");
  gear = 1;
  cadence = 50;
  speed = 5;
  name = "Bontrager";
}
// This is a constructor that takes arguments
public Bicycle(int startCadence, int startSpeed, int startGear,
  String name) {
  this.gear = startGear;
  this.cadence = startCadence;
  this.speed = startSpeed;
  this.name = name;
}

// Method Syntax:
// <public/private/protected> <return type> <function name>(<args>)

// Java classes often implement getters and setters for their fields

// Method declaration syntax:
// <access modifier> <return type> <method name>(<args>)
public int getCadence() {
  return cadence;
}

// void methods require no return statement
public void setCadence(int newValue) {
  cadence = newValue;
}
public void setGear(int newValue) {
  gear = newValue;
}
public void speedUp(int increment) {
  speed += increment;
}
public void slowDown(int decrement) {
  speed -= decrement;
}
public void setName(String newName) {
  name = newName;
}
public String getName() {
  return name;
}

//Method to display the attribute values of this Object.
@Override // Inherited from the Object class.
public String toString() {
  return "gear: " + gear + " cadence: " + cadence + " speed: " + speed +
      " name: " + name;
 }
} 
```

### Create Object

You need two classes. One class for the type of object you want to use (Dog, AlarmClock, Television, etc.) and another class to test your new class. The tester class is where you put the main method, and in that main() method you create and access objects of your new class type. The tester class has only one job: to try out the methods and variables of your new object class type.

```java
class Movie { 
  // instance variables
  String title;  
  String genre;  
  int rating;  
  
  // method
  void playIt() {    
    System.out.println(“Playing the movie”);  
   }
  }

 public class MovieTestDrive {  
  public static void main(String[] args) {    
    Movie one = new Movie(); // make a Movie object   
    one.title = “Gone with the Stock”;    
    one.genre = “Tragic”;    
    one.rating = -2;    
    Movie two = new Movie();    
    two.title = “Lost in Cubicle Space”;    
    two.genre = “Comedy”;    
    two.rating = 5;    
    two.playIt();    
    Movie three = new Movie();    
    three.title = “Byte Club”;    
    three.genre = “Tragic but ultimately uplifting”;   
    three.rating = 127;  
    }
  }
```
## Output

```java
// Use System.out.println() to print lines.
        System.out.println("Hello World!");
        System.out.println(
            "Integer: " + 10 +
            " Double: " + 3.14 +
            " Boolean: " + true);

// To print without a newline, use System.out.print().
        System.out.print("Hello ");
        System.out.print("World");

// Use System.out.printf() for easy formatted printing.
        System.out.printf("pi = %.5f", Math.PI); // => pi = 3.14159
 ```
 
## Input
Use Scanner to read input.

```java
// must import java.util.Scanner;
Scanner scanner = new Scanner(System.in);

// read string input
String name = scanner.next();

// read byte input
byte numByte = scanner.nextByte();

// read int input
int numInt = scanner.nextInt();

// read long input
float numFloat = scanner.nextFloat();

// read double input
double numDouble = scanner.nextDouble();

// read boolean input
boolean bool = scanner.nextBoolean();
```

## Variables

```java
// Declare a variable using <type> <name>
int fooInt;

// Declare multiple variables of the same
// type <type> <name1>, <name2>, <name3>
int fooInt1, fooInt2, fooInt3;
```

### Variable Initialization

```java
// Initialize a variable using <type> <name> = <val>
int barInt = 1;

// Initialize multiple variables of same type with same
// value <type> <name1>, <name2>, <name3>
// <name1> = <name2> = <name3> = <val>
int barInt1, barInt2, barInt3;
barInt1 = barInt2 = barInt3 = 1;
```

### Variable Types

```java
// Byte - 8-bit signed two's complement integer
// (-128 <= byte <= 127)
byte fooByte = 100;

// Short - 16-bit signed two's complement integer
// (-32,768 <= short <= 32,767)
short fooShort = 10000;

// Integer - 32-bit signed two's complement integer
// (-2,147,483,648 <= int <= 2,147,483,647)
int bazInt = 1;

// Long - 64-bit signed two's complement integer
// (-9,223,372,036,854,775,808 <= long <= 9,223,372,036,854,775,807)
long fooLong = 100000L;
// L is used to denote that this variable value is of type Long;
// anything without is treated as integer by default.

// Note: byte, short, int and long are signed. They can have positive and negative values.
// There are no unsigned variants.
// char, however, is 16-bit unsigned.

// Float - Single-precision 32-bit IEEE 754 Floating Point
// 2^-149 <= float <= (2-2^-23) * 2^127
float fooFloat = 234.5f;
// f or F is used to denote that this variable value is of type float;
// otherwise it is treated as double.

// Double - Double-precision 64-bit IEEE 754 Floating Point
// 2^-1074 <= x <= (2-2^-52) * 2^1023
double fooDouble = 123.4;

// Boolean - true & false
boolean fooBoolean = true;
boolean barBoolean = false;

// Char - A single 16-bit Unicode character
char fooChar = 'A';

// final variables can't be reassigned,
final int HOURS_I_WORK_PER_WEEK = 9001;
// but they can be initialized later.
final double E;
E = 2.71828;

// Strings
String fooString = "My String Is Here!";

// \n is an escaped character that starts a new line
String barString = "Printing on a new line?\nNo Problem!";

// \t is an escaped character that adds a tab character
String bazString = "Do you want to add a tab?\tNo Problem!";

System.out.println(fooString);
System.out.println(barString);
System.out.println(bazString);

// String Building
// #1 - with plus operator
// That's the basic way to do it (optimized under the hood)
String plusConcatenated = "Strings can " + "be concatenated " + "via + operator.";
System.out.println(plusConcatenated);
// Output: Strings can be concatenated via + operator.

// #2 - with StringBuilder
// This way doesn't create any intermediate strings. It just stores the string pieces, and ties them together
// when toString() is called.
// Hint: This class is not thread safe. A thread-safe alternative (with some impact on performance) is StringBuffer.
StringBuilder builderConcatenated = new StringBuilder();
builderConcatenated.append("You ");
builderConcatenated.append("can use ");
builderConcatenated.append("the StringBuilder class.");
System.out.println(builderConcatenated.toString()); // only now is the string built
// Output: You can use the StringBuilder class.

// StringBuilder is efficient when the fully constructed String is not required until the end of some processing.
StringBuilder stringBuilder = new StringBuilder();
String inefficientString = "";
for (int i = 0 ; i < 10; i++) {
    stringBuilder.append(i).append(" ");
    inefficientString += i + " ";
}
System.out.println(inefficientString);
System.out.println(stringBuilder.toString());
// inefficientString requires a lot more work to produce, as it generates a String on every loop iteration.
// Simple concatenation with + is compiled to a StringBuilder and toString()
// Avoid string concatenation in loops.

// #3 - with String formatter
// Another alternative way to create strings. Fast and readable.
String.format("%s may prefer %s.", "Or you", "String.format()");
// Output: Or you may prefer String.format().

// Arrays
// The array size must be decided upon instantiation
// The following formats work for declaring an array
// <datatype>[] <var name> = new <datatype>[<array size>];
// <datatype> <var name>[] = new <datatype>[<array size>];
int[] intArray = new int[10];
String[] stringArray = new String[1];
boolean boolArray[] = new boolean[100];

// Another way to declare & initialize an array
int[] y = {9000, 1000, 1337};
String names[] = {"Bob", "John", "Fred", "Juan Pedro"};
boolean bools[] = {true, false, false};

// Indexing an array - Accessing an element
System.out.println("intArray @ 0: " + intArray[0]);

// Arrays are zero-indexed and mutable.
intArray[1] = 1;
System.out.println("intArray @ 1: " + intArray[1]); // => 1
```
## Operators

```java
int i1 = 1, i2 = 2; // Shorthand for multiple declarations

// Arithmetic is straightforward
System.out.println("1+2 = " + (i1 + i2)); // => 3
System.out.println("2-1 = " + (i2 - i1)); // => 1
System.out.println("2*1 = " + (i2 * i1)); // => 2
System.out.println("1/2 = " + (i1 / i2)); // => 0 (int/int returns int)
System.out.println("1/2.0 = " + (i1 / (double)i2)); // => 0.5

// Modulo
System.out.println("11%3 = "+(11 % 3)); // => 2

// Comparison operators
System.out.println("3 == 2? " + (3 == 2)); // => false
System.out.println("3 != 2? " + (3 != 2)); // => true
System.out.println("3 > 2? " + (3 > 2)); // => true
System.out.println("3 < 2? " + (3 < 2)); // => false
System.out.println("2 <= 2? " + (2 <= 2)); // => true
System.out.println("2 >= 2? " + (2 >= 2)); // => true

// Boolean operators
System.out.println("3 > 2 && 2 > 3? " + ((3 > 2) && (2 > 3))); // => false
System.out.println("3 > 2 || 2 > 3? " + ((3 > 2) || (2 > 3))); // => true
System.out.println("!(3 == 2)? " + (!(3 == 2))); // => true

// Increment operators
int i = 0;

// If they are placed before the variable, they increment then return;
// after the variable they return then increment.
System.out.println(i++); // i = 1, prints 0 (post-increment)
System.out.println(++i); // i = 2, prints 2 (pre-increment)
System.out.println(i--); // i = 1, prints 2 (post-decrement)
System.out.println(--i); // i = 0, prints 0 (pre-decrement)
```
## Control Structures
Java has three standard looping constructs: while, do-while, and for.

```java
// If
int j = 10;
if (j == 10) {
  System.out.println("I get printed");
} else if (j > 10) {
  System.out.println("I don't");
} else {
  System.out.println("I also don't");
}

// While loop
int fooWhile = 0;
while(fooWhile < 100) {
  System.out.println(fooWhile);
  // Increment the counter
  // Iterated 100 times, fooWhile 0,1,2...99
  fooWhile++;
}
System.out.println("fooWhile Value: " + fooWhile);

// Do While Loop
int fooDoWhile = 0;
do {
  System.out.println(fooDoWhile);
  // Increment the counter
  // Iterated 100 times, fooDoWhile 0->99
  fooDoWhile++;
} while(fooDoWhile < 100);
System.out.println("fooDoWhile Value: " + fooDoWhile);

// For Loop
// for loop structure => for(<start_statement>; <conditional>; <step>)
for (int fooFor = 0; fooFor < 10; fooFor++) {
  System.out.println(fooFor);
  // Iterated 10 times, fooFor 0->9
}
System.out.println("fooFor Value: " + fooFor);

// Nested For Loop Exit with Label
outer:
for (int i = 0; i < 10; i++) {
for (int j = 0; j < 10; j++) {
  if (i == 5 && j ==5) {
    break outer;
    // breaks out of outer loop instead of only the inner one
  }
}
}

// For Each Loop
// The for loop is also able to iterate over arrays as well as objects
// that implement the Iterable interface.
int[] fooList = {1, 2, 3, 4, 5, 6, 7, 8, 9};
// for each loop structure => for (<object> : <iterable>)
// reads as: for each element in the iterable
// note: the object type must match the element type of the iterable.
for (int bar : fooList) {
  System.out.println(bar);
  //Iterates 9 times and prints 1-9 on new lines
}

// Switch Case
// A switch works with the byte, short, char, and int data types.
// It also works with enumerated types (discussed in Enum Types), the
// String class, and a few special classes that wrap primitive types:
// Character, Byte, Short, and Integer.
// Starting in Java 7 and above, we can also use the String type.
// Note: Do remember that, not adding "break" at end any particular case ends up in
// executing the very next case(given it satisfies the condition provided) as well.
int month = 3;
String monthString;
switch (month) {
    case 1: monthString = "January";
            break;
    case 2: monthString = "February";
            break;
    case 3: monthString = "March";
            break;
    default: monthString = "Some other month";
             break;
}
System.out.println("Switch Case Result: " + monthString);
```
