# Java-Cheat-Sheet
Java is a general-purpose, concurrent, class-based, object-oriented computer programming language. 

## Table of Contents

- [Class](#class)
- [Loops](#Loops)
- [Constants](#constants)
- [Functions](#functions)
- [Strings](#strings)
- [Numbers](#numbers)
- [Boolean](#boolean)
- [Pointers](#pointers)
- [Struct](#struct)
- [Linked List](#linked-list)

## Class
In Java, everything goes in a class. You’ll type your source code file (with a .java extension), then compile it into a new class file (with a .class extension). When you run your program, you’re really running a class. Running a program means telling the Java Virtual Machine (JVM) to “Load the Hello class, then start executing its main() method. Keep running ‘til all the code in main is finished.”

When the JVM starts running, it looks for the class you give it at the command line. Then it starts looking for a specially-written method that looks exactly like:

```java
public static void main (String[] args) {      
  // your code goes here     
}
```

Next, the JVM runs everything between the curly braces {  } of your main method. Every Java application has to have at least one class, and at least one main method.

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


## Loops
Java has three standard looping constructs: while, do-while, and for.

```java
int x = 4; 
while (x > 3) {  
  x = x - 1; // or we’d loop forever
} 
```
