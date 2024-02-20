# Abstract Classes

There are two types of classes:
Abstract classes
Concrete classes (classes we normally use)

Using concrate (normal) classes,  
both references and objects can be created.
 
Using abstract classes,  
references can be created  
but objects can not be created.

Abstract classes are usefull for generalization


#### Abstract methods

An abstract method is a method that has not a body. So they are undefined methods.

If a class has at least one abstract method, then the class itself also has to be declared as abstract.

A class can be abstract without any methods also, but if it has at least one abstract method, then it has to be abstract.

1. If super class is abstract and does not have any abstract methods, then the sub class can be declared as concrete class and objects can be created from this class
```java
abstract class Super{
    // constructor
    Super(){
        System.out.println("Super constructor");
    }

    // normal method
    void method1(){
        System.out.println("Super method1");
    }
}

class Sub extends Super{

}
public class Main{
    public static void main(String[] args) {
        Sub s1=new Sub();
        s1.method1();
        // output -->
        // Super constructor
        // Super method1
    }
}
```

2. If super class is abstract and has an abstract method,  
then this abstract method will be inherited by the sub class,
and since a class which includes at least one abstract method must also be an abstract class,

Wheter the sub class should also be declared as abstract class (in this way no object can be created via this sub class cause abstract classes can not produce objects)

Or the abstract method that inherited from abstract super class should be overriden in the sub class. In that way any object can be created via this sub class couse class itself remains being a concrete class. (And this is the main purpose of creating the abstract classes)

```java
abstract class Super{
    // constructor
    Super(){
        System.out.println("Super constructor");
    }

    // normal method
    void method1(){
        System.out.println("Super method1");
    }

    // abstract method
    abstract void method2();
}

class Sub extends Super{
    @Override
    void method2(){
        System.out.println("Sub method2 -Overridden-");
    }
}
public class Main{
    public static void main(String[] args) {
        Sub s1=new Sub();
        // reference can be both Sub of Super since abstract classes can produce references.
        s1.method1();
        s1.method2();
        // output -->
        // Super constructor
        // Super method1
        // Sub method2 -Overridden-
    }
}
```

## Why we need abstract classes?

Abstract classes are only made for being inherited. So the purpose is not creating objects.  
The purpose is defining and imposing standart to sub classes.


> Let's look at an example

If you want to open a hospital,  
you need a permission to do that from government.  
They give you the permission based on some condition, they give guidelines:  
"A hospital must have these things..."

You can not build a structure and have some services and say it a hospital.  
You need to follow some standarts.  
Who gives the standarts? --> government (abstract class)

The government says an emergency unit must be established in a hospital.
Then you plan a hospital (create a class),  
take the permission (inherit from the abstract class), 
then you plan an emergency unit (override the emergency method),
So your plan is not abstract now and you can really make an hospital (create an object from this concrete class)


Abstract classes are made for imposing standarts.  
Sub classes (that inherit from abstract class) are made for following the standarts.

```java
abstract class Hospital{
    abstract void emergency();
    abstract void appointment();
    abstract void finance();
}

class MyHospital extends Hospital{
    @Override
    void emergency(){
        System.out.println("Emergency unit is established");
    }

    @Override
    void appointment(){
        System.out.println("Appointment unit is established");
    }

    @Override
    void finance(){
        System.out.println("Finance unit is established");
    }
}
public class Main{
    public static void main(String[] args) {
        // the reference can be both Hospital or MyHospital
        Hospital h=new MyHospital();
        h.emergency();
        h.appointment();
        h.finance();
        // output -->
        // Emergency unit is established
        // Appointment unit is established
        // Finance unit is established
    }
}
```

Abstract classes can not be "*final*"  
Final classes can not be extended.

Also abstract methods can not be "final"  
Abstract methods are meant for overriding  
but final methods can not be overriden.
So abstract and final can not go well with each other.

Abstract classes and abstract methods can not be "static" too.

