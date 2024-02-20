# Static - Final - Singleton Class

## Static

### Static variables

These variables as not directly belongs to created objects, they are belong to class.  
So it means, if this value being altered via one of the objects created from this class, it will affect all the objects from that class.  
In this case, it can also be used as shared data. There will be only one copy of a static member, common for all the objects.

Static members can be called by using directly class name. No need to create an object to access a data of class(static members)

Static members of a class are created inside method area, not in heap.

### Static methods

They have the same features with static variables,  
but they can not access non-static values in a class.

Terms like "this" and "super" can not be used inside static members because they refer to an object, not to the class 
itself.


```java
class Test{
    static int x=10;
    int y=20;

    void show() {
        System.out.println(x +" "+ y);
    }

    static void display(){
        // non-static members (y) can not be accesses in static methods
        // System.out.println(x +" "+ y); --> not valid
        System.out.println(x);
    }
}
public class Main{
    public static void main(String[] args) {
        Test t1=new Test();
        t1.display();
        // output --> 10
        Test.display();
        // output --> 10

        Test t2=new Test();
        t2.x=20;
        t2.display();
        // output --> 20
        t1.display();
        // output --> 20
    }
}

```

Static methods can be overloaded  
but they can not be overridden, they can only be hidden.  
Static methods cannot be overridden because they belong to the class itself rather than to instances of the class.  
When you define a static method in a subclass with the same signature as a static method in the superclass,  
it is not considered overriding;  
instead, it's called method hiding.  
This means that the subclass has its own version of the static method, which is completely independent of the superclass's static method.  
The method that gets called depends on the reference type of the object at compile time, not on the actual type of the object at runtime. So it is not overriding.
>Example
```java
class Superclass {
    static void staticMethod() {
        System.out.println("Superclass static method");
    }
}

class Subclass extends Superclass {
    static void staticMethod() {
        System.out.println("Subclass static method");
    }
}

public class Main {
    public static void main(String[] args) {
        Superclass obj1 = new Subclass();
        Subclass obj2 = new Subclass();

        // Calls Superclass static method
        obj1.staticMethod();
        // output --> Superclass static method

        // Calls Subclass static method
        obj2.staticMethod();
        // output --> Subclass static method
    }
}

```


### Static nested classes

If so many static variables and static methods are created in class,
another class which is static can be created in that class and all these static members can be put in the static class. This static class can be also accessed by the outside of the outer class.

Only inner classes can be static.

### Static blocks

A set of statments can be written as a block and declared as static.  
Inside static blocks, only static members can be accessed.

Even main method is executed after static block. If there is static blocks inside the public class, they will be executed first.
If a class is called inside main method, first the static blocks and the static members will be loaded with that class
They can not be declared inside a method

```java
class Test{
    static {
        System.out.println("static block 1");
    }
    static {
        System.out.println("static block 2");
    }
}
public class Main{
    public static void main(String[] args) {

        System.out.println("main method");
        Test t1=new Test();
        // output -->
        // main method
        // static block 1
        // static block 2
    }
}

```

## Final
It is like constant in C

### Final variables
Values that can not be modified.

Final variables are written in capital letters, it is a notatiion followed in Java.
They can be declared but not be used without an initialization.
They can be initialized 
1. when they are declared,  
(They can be initialized afterwards (only once) if they are *inside a method*)
2. inside static block
3. constructor of a class (it should be intitialized in every constructor overloaded)

```java
public class Main{
    static final int x=10; // can not be initialized afterward as it is not inside a method

    final int y;
    {// can be initialized afterward inside an instance block
        y=5;
    }

    static final int z;
    static
    { // can be initialized afterward inside a static block if the variable is also static
        z=5;
    }

    final int t;
    // constructor
    public Main(){
        t=10; // initializing inside the constructor
    }

    public static void main(String[] args) {

        final float PI=3.14159f;
        System.out.println(PI);

        final double e; // can be initialized afterward as it is inside a method
        e=2.718281;
        System.out.println(e);
    }
}

```


### Final methods
Final methods can not be overriden.

```java
class Test{
    public final void show(){
        System.out.println("final method");
    }
}

class Test1 extends Test{
    // public void show() --> not valid, can not be overridden
}
public class Main{

    public static void main(String[] args) {

    }
}
```


### Final classes
Final classes can not be extended.

## Singleton Class
A class which can create only one object.

We make the constructor "*private*",  
So it can not be called outside of the class.
When the constructor can not be called outsice of the class, a new object can not be created. Then how to create an object from this class?  
With using a static method since they can be accessable via the class itself

In this case,  
we prepare a reference inside the class. and assign it as *null*  
Then we use this referance inside a static method (with checking whether it is null -the object is created already or not-)  
and access the private constructor inside this method. 
So only one object can be created from this class 

```java
class Machine{
    private float value1;
    public void getValue1(){
        System.out.println(value1);
    }

    static private Machine OurMachine = null; // prepare a reference to return when the object is created
    // Machine is the data type,
    // it is the reference,
    // we create a reference from this class
    // it must be static because we use this reference in a static method
    // and static methods can only access variables which are also static
    // it also must be private because we do not want it to be accessible and alterable from the outside

    // constructor
    private Machine(){
        value1 = 10;
    }

     static public Machine getMachine(){
        if(OurMachine == null){
            OurMachine = new Machine();
        }
        return OurMachine;
    }
}


public class Main{
    public static void main(String[] args) {
        Machine MyMachine = Machine.getMachine(); // creating MyMachine reference from class Machine
        MyMachine.getValue1(); // an object is created successfully
        // output --> 10.0

        Machine MyMachine2 = Machine.getMachine();  // can another object be created?
        System.out.println(MyMachine==MyMachine2);  // no, they are the same reference.
        // output --> true
    }
}

```

> Example --> Generating student number automatically inside the constructor
```java
import java.util.*;
class Student{
    private String no;

    public String getNo() {
        return no;
    }

    private static int counter=1; // it is static because it has to be shared across all objects
    // it has to be a variable for the class itself, not an individual property for each object created
    private String generateNo(){
        Date d=new Date();
        String number="Student_" + d.getYear()%100 +"_"+ counter;
        counter++;
        return number;
    }

    // constructor
    public Student(){
        no = generateNo();
    }
    }
public class Main{
    public static void main(String[] args) {
        Student s1=new Student();
        System.out.println(s1.getNo());

        Student s2=new Student();
        System.out.println(s2.getNo());
    }
}

```
