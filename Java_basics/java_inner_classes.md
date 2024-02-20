# Inner Classes

A class can be created in an another class, that becomes innerclass.  

Type of inner classes:
1. Nested inner class
2. Local inner class
3. Anonymous inner class:
4. Static inner class

## Nested Inner Class
Creating a class inside another class

Inner class can directly access the members of outer class.  
But outer class can only access the members of inner class with creating an object, not directly.

Inner class can only be used by outer class. Not any other class. (Actually it can be reached by other classes but it is useless)     
Actually the main purpose of creating an inner class is reducing the complexity in the outer class.

```java
class Outer{
    int x=10;

    class Inner{
        int y=20;
        void innerDisplay(){
            System.out.println("Property of outer class, x: " + x);
            System.out.println("Property of inner class, y: " + y);
        }
    }

    void outerDisplay(){
        Inner i=new Inner();
        i.innerDisplay();
        // System.out.println(y); --> is not valid, y is not directly accessible for outer class
        System.out.println(i.y);
    }
}
public class Main{
    public static void main(String[] args) {
        Outer o=new Outer();
        o.outerDisplay();

        // to create an object of inner class
        // first an object from outer class must be created
        // here is the syntax:
        Outer.Inner i=new Outer().new Inner();
        i.innerDisplay();
        System.out.println(i.y);
    }
}

```

```
Outer.Inner i=new Outer().new Inner();
               |    |       |___|__> object of inner
               |____|______________> object of outer
```

#### will a class file be created for inner class?

Java creates a className.class file for all the classes in a project while compiling. For inner classes-->  
Outer.class  
Outer$Inner.class  
files will be created.


## Local Inner Class
Creating a class inside a method in another class.

That inner class will only visible and useful inside the method.

These inner classes can also be abstract.

```java
class Outer{
    int x=10;

    void display(){
        class Inner{
            void innerDisplay(){
                System.out.println("Inner Display method");
            }
        }
        Inner i=new Inner();
        i.innerDisplay();

        // an anoymoys object (an object without a reference) also can be created here:
        // new Inner().display
    }
    
}

public class Main{
    public static void main(String[] args) {
        Outer o=new Outer();
        o.display();
    }
}

```

## Anonymous Inner Classes
An anonymous class can be created while creating an object.
```java
abstract class My{
    abstract void display();
}

class Outer{
    public void method(){
        My m=new My(){
            public void display(){
                System.out.println("The abstract method is overridden");
            }
        };
        m.display();

        // also an anonymous object can be created here
        new My(){public void display(){System.out.println("The abstract method is overridden");}}.display();
    }
}
```
My is an abstract class(it can also be written as an interface in this case).  
Normally we can create a reference  
but we can not create an object from an abstract class
But here, in the method of Outer class  
we do not put a semicolon after  
My m=new My()  
instead we override the methods that we need to override to create an object  
In this case a new class which the display method ovverridden and will be created. This class is nameless so it is why it is called as "anonymous"
In this way we can create an object from an abstract class or an interface in a method.
This anonymous class can extend only one class OR can implement only one interface.
It can also access members of outer class.

## Static Inner Classes
Static inner classes are the static members of outer classes.  
And the object of static inner classes can be created and accessed from outside the outer class. No need to create an object of outer class.  

Static inner classes can access the members of outer classes which are also static.

```java
class Outer{
    static int x=10;
    int y=20;

    static class Inner{
        void display(){
            System.out.println(x);
            // System.out.prin   tln(y); --> is not valid cause y is not static
        }
    }
}

public class Main{
    public static void main(String[] args) {
        // no need to crete an object of outer class
        Outer.Inner i=new Outer.Inner();
        i.display();
    }
}
```


