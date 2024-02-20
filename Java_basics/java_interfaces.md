# Interfaces

```java
abstract class Hospital{
    abstract void emergency();
    abstract void appointment();
    abstract void finance();
}
```
Abstract classes are used for inheritance and polymorphism.

When an abstract class only have abstract methods and nothing else to be inherited,  
so when only purpose of an abstract class was force the sub class to override the methods that it inherits,
when only purpose of the abstract class is achieving polymorphism,
"Interfaces" can be used instead of abstract classes.

So interfaces are abstract classes that only have abstract methods,  
but when an interface is created there is no need the term of "abstract" anymore. All the methods it has are already abstract and also public.

The term "**implements**" is used with the interfaces.

Objects can not be created from interfaces, like abstract classes  
but references can be created.

> Example
```java
interface Hospital{
    void emergency();
    void appointment();
    void finance();
}

class MyHospital implements Hospital {
    @Override
    public void emergency(){
        System.out.println("Emergency unit is established");
    }

    @Override
    public void appointment(){
        System.out.println("Appointment unit is established");
    }

    @Override
    public void finance(){
        System.out.println("Finance unit is established");
    }
}


public class Main{
    public static void main(String[] args) {
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

Naming an interface like "IName" is a common usage in java to clarify the difference between a class and an interface.

A class can extend only one super class  
but it can implement more than one interfaces

> Let's look at an example
These are the classes and interfaces
```java
class Phone{
    public void call(){
        System.out.println("Phone call");
    }
    public void sms(){
        System.out.println("Phone sending SMS");
    }
}

interface ICamera{
    void click();
    void record();
}

interface IMusicPlayer{
    void play();
    void stop();
}


class SmartPhone extends Phone implements ICamera,IMusicPlayer{
    // own method
    public void videoCall(){
        System.out.println("Smart Phone video calling");
    }

    @Override
    public void click(){
        System.out.println("Smart Phone taking photos");
    }
    @Override
    public void record(){
        System.out.println("Smart Phone recording");
    }

    @Override
    public void play(){
        System.out.println("Smart Phone playing music");
    }
    @Override
    public void stop(){
        System.out.println("Smart Phone stopped music");
    }
}
``` 

When we refer the object as Smatphone,  
we can use all the methods that the object has:

```java
public class Main{
    public static void main(String[] args) {
        SmartPhone p = new SmartPhone();
        p.call();
        p.sms();
        p.videoCall();
        p.click();
        p.record();
        p.play();
        p.stop();
    }
}
```

When we refer the object as only Phone,    
we can only use the methods that phone class has :

```java
public class Main{
    public static void main(String[] args) {
        Phone p = new SmartPhone();
        p.call();
        p.sms();
        // p.videoCall();
        // p.click();
        // p.record();
        // p.play();
        // p.stop();
    }
}
```

When we refer the object as ICamera,    
we can only use the methods that ICamera interface has :   
(couse we refer it as a camera  
we only know about the features a camera has)

```java
public class Main{
    public static void main(String[] args) {
        ICamera p = new SmartPhone();
        // p.call();
        // p.sms();
        // p.videoCall();
        p.click();
        p.record();
        // p.play();
        // p.stop();
    }
}
```

When we refer the object as IMusicPlayer,    
we can only use the methods that IMusicPlayer interface has :   
(couse we refer it as a music player 
we only know about the features a music player has)

```java
public class Main{
    public static void main(String[] args) {
        IMusicPlayer p = new SmartPhone();
        // p.call();
        // p.sms();
        // p.videoCall();
        // p.click();
        // p.record();
        p.play();
        p.stop();
    }
}
```

Interface can have identifiers, properties  
but they should be upper case.
And they are static and final by default, so they are constant

Methods that inside an interface are abstract and they can not have body.
But interfaces can have "static" methods with a body.

```java
interface ICamera{
    int MP = 50;
    static void filter(){
        System.out.println("Filter is applied");
    }
    void click();
    void record();
}

public class Main{
    public static void main(String[] args) {
        ICamera p = new SmartPhone();
        p.click();
        p.record();
        
        // calling an identifier and a static method in the interface
        System.out.println(ICamera.MP);
        ICamera.filter();
        // so, no need to create an object

    }
}
```

An interface can **extend** from another interface
  
Interface can have default methods, and a sub class implements these methods  
they are not have to override these methods to become non abstract.

All the methods (not the ones that defined as defult) are public and abstract in an interface.  
But a private method which also have a body can be created in an interface.
These private methods usually be used in default methods in the same interface.  
So private methods are only useful in default methods. They are not usefull outside the interface.  



