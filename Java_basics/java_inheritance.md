# Inheritance
## How to create a class that inherits from another class
The keyword is "**extends**"


```java
class Circle{  // super class / parent class / base class
    public double radius;
    public double area(){
        return Math.PI * radius * radius;
    }
    public double perimeter(){
        return 2*Math.PI*radius;
    }
    public double circumference(){
        return perimeter();
    }
}

class Cylinder extends Circle{  // sub class / child class  / derived class
    public double height;
    public double volume(){
        return area()*height;
    }
}

public class Main{
    public static void main(String[] args) {
        Cylinder c=new Cylinder();
        c.radius = 7;
        c.height = 10;
        System.out.println("Area: " + c.area());
        System.out.println("Volume: " + c.volume());

    }
}
```

## Data Field in Inheritance
Sub class has all the variables and all the methods that super class has.
But it depends when it comes to access or alter them.  
For example,
Sub class has the variable of super class which is "private"
But it CAN NOT ACCESS OR CHANGE IT DIRECTLY.
Sub class can access this private data of super class only if there is a setter or some another methods which are not private.

## Constructors in Inheritance 
#### What about the constructors?

To create an object from child class,  
an object from parent class must be created.  
So the constructor of parent class is called first.

> Example: 
```java
class Parent{
    public Parent(){
        System.out.println("Parent Constructor");
    }
}

class Child extends Parent{
    public Child(){
        System.out.println("Child Constructor");
    }
}

class GrandChild extends Child{
    public GrandChild(){
        System.out.println("Grand Child Constructor");
    }
}


public class Main{
    public static void main(String[] args) {
        GrandChild g=new GrandChild();
        // output -->
        // Parent Constructor
        // Child Constructor
        // Grand Child Constructor
    }
}
```

So each constructors has the super() call in their fisrt line -hidden-  

Constructors also call an another constructor with this() call

this() and super() can not be called in the same constructor


### Calling a parametrised constructor of super class

To past some parameters to super class in constructing process  
a constructor that can pass values to super class must be creted.

> Example
```java
class Rectangle{
    int length;
    int breadth;

    Rectangle() {
        length = breadth = 1;
    }
    Rectangle(int l, int b){
        length = l;
        breadth = b;
    }
}

class Cuboid extends Rectangle{
    int height;

    Cuboid(){
        height = 1;
    }
    Cuboid(int h){
        height = h;
    }
    Cuboid(int l, int b, int h){  // taking 3 parameters, 2 values for its parent and 1 value for itself
        super(l,b); // super class constructor with two parameters will be called
        // and super() must always be the first line in the constructor
        height=h;
    }

    int volume(){
        return length * breadth * height;
    }
}

public class Main{
    public static void main(String[] args) {
        Cuboid c1=new Cuboid();
        System.out.println(c1.volume());
        // output --> 1

        Cuboid c2=new Cuboid(10);
        System.out.println(c2.volume());
        // output --> 10

        Cuboid c3=new Cuboid(5,3,10);
        System.out.println(c3.volume());
        // output --> 150
    }
}
```

## this and super
### this
*this* is a referance to the current object
```java
class Rectangle{
    int length;
    int breadth;

    Rectangle(int l, int b){
        this.length = l;
        this.breadth = b;
    }

    void display(){
        System.out.println("Length: "+this.length);
        System.out.println("Breadth: "+this.breadth);
    }
}


public class Main{
    public static void main(String[] args) {
        Rectangle r1=new Rectangle(5,10);
        r1.display(); 

        Rectangle r2=new Rectangle(10,20);
        r2.display();

    }
}
```
```
Here
this.length --> r1.lenght
           |__> r2.length

"this" works as same as referances r1 and r2
but just works with the current object
```
#### When usage of *this* mandatory?
Especially when resolving name conflicts
```java
class Rectangle{
    int length;
    int breadth;

    Rectangle(int length, int breadth){
        // length = l is valid
        // when property name and the parameter name are the same
        // length = length causes name conflict
        // so use this.length --> to refer to property name
        this.length = length;
        this.breadth = breadth;
    }

    void display(){
        System.out.println("Length: "+this.length);
        System.out.println("Breadth: "+this.breadth);
    }
}


public class Main{
    public static void main(String[] args) {
        Rectangle r1=new Rectangle(5,10);
        r1.display();

        Rectangle r2=new Rectangle(10,20);
        r2.display();

    }
}
```

### super

Just as "this" is a reference to the current object,  
"super" is a referance to the super class(the properties that are coming from the super class) 
To access to member of a super class, term "super" is used.

this --> refers to all properties and methods that the current object has  
if there are two properties or methods with the same name which one of them come with the super class,  
then "this" refers to the property or the object that created in the sub class

super --> refers to the properties and methods that come from the super class

```java
class Rectangle{
    int length;
    int breadth;
    int x=10;

    Rectangle(int length, int breadth){
        this.length = length;
        this.breadth = breadth;
    }

    void display(){
        System.out.println("Length: "+length);
        System.out.println("Breadth: "+breadth);
    }
}

class Cuboid extends Rectangle{
    int height;
    int x=20;

    Cuboid(int length, int breadth, int height){
        super(length,breadth);
        this.height = height;
    }

    void display(){
        super.display();
        System.out.println("Height: "+ height);
        System.out.println("super.x : "+ super.x);
        System.out.println("x : "+ x);
        // System.out.println("x : "+ this.x); also same
    }
}


public class Main{
    public static void main(String[] args) {
        Cuboid c=new Cuboid(10,10,5);
        c.display();
    }
}
```

## Method Overriding
Redefining a method of superclass in subclass  

static of final methods can not be overriden  

The method that overriden in the sub class should have same or more relax access specifier(private-protected-public) than the method in the super class

Private methods can not be overridden  
since the sub method can not access or change or see these private datas  
although it has it through the inheritance.  
An unaccessable or unseen can not be overridden.

```java
class Super{
    public void display(){
        System.out.println("Hello");
    }
}

class Sub extends Super{
    public void display(){
        System.out.println("Hello World");
    }
}

public class Main{
    public static void main(String[] args) {
        Super su=new Super();
        su.display();
        // output --> Hello

        Sub sb=new Sub();
        sb.display();
        // output --> Hello World
        /*
         sb has two methods
         display method that comes from super and its own display method
         but can two methods have the same signature? --> so it is overriding
         the method coming from the super will be SHADOWED
        */

    }
}
```

### Dynamic Method Dispatch
```java
class Super{
    public void display(){
        System.out.println("Hello");
    }
}

class Sub extends Super{
    @Override // it is just an annotation
    public void display(){
        System.out.println("Hello World");
    }
}

public class Main{
    public static void main(String[] args) {
        // I have a reference of SUPER class --> "su"
        // "su" is holding an object of SUB class
        // that object has two methods:
        // display() that it inherits from super class (Shadowed method)
        // its own display()

        Super su=new Sub();
        su.display(); // whose method will be called?
        // output --> Hello World

        // the method will be called depending on the object
        // not upon reference
        // object's own method will be called, not it inherits
        // so here, overridden method is called.
    }
}
```
#### Let's look at an example

These are the classes
```java
class TV{
    public void switchON()
    {System.out.println("TV is switched ON");}
    
    public void changeChannel()
    {System.out.println("TV channel is Changed");}
}


class SmartTV extends TV{
    @Override
    public void switchON()
    {System.out.println("SmartTV is switched ON");}

    @Override
    public void changeChannel()
    {System.out.println("SmartTV channel is changed");}

    public void browse()
    {System.out.println("SmartTV is browsing");}
}
```
SmartTV is a new and more technologic version of normal TV.  
It has the all the methods that TV has,  
But they are overriden,  
Both normal TV and SmartTV can be switched on and they can change the channel
but the way SmartTV does these things is different now.  
And also SmartTV can browse. So it have some extra features

```
        class              Object
    (design paper)      (really exist)
       (manual)

          TV                 t1 --> swithcON()
                               |__> changeChannel()

        SmartTV              t2 --> swithcON()  -Overriden-
                               |__> changeChannel() -Overriden-
                               |__> browse()
```

> Using a TV manual for a TV:
```java
public class Main{
    public static void main(String[] args) {
        TV t1=new TV();
        t1.switchON();
        t1.changeChannel();

        // output -->
        // TV is switched ON
        // TV channel is Changed
    }
}
```


> Using a SmartTV manual for a SmartTV:
```java
public class Main{
    public static void main(String[] args) {
        SmartTV t2=new SmartTV();
        t2.switchON();
        t2.changeChannel();

        // output -->
        // SmartTV is switched ON
        // SmartTV channel is changed
    }
}
```

> Using a TV manual for a SmartTV:
```java
public class Main{
    public static void main(String[] args) {
        TV t2=new SmartTV();
        t2.switchON();
        t2.changeChannel();
        // t2.browse --> error
        // something like this method is not defined in the manual

        // output -->
        // SmartTV is switched ON
        // SmartTV channel is changed
    }
}
```
Overriden methods will work  
But the methods that the object supposed to has (not inherited or overriden ones--> in this case browse()) is not available

It is like a grandpa trying to use a SmartTv  
He can swith on, or change the channel  
But he does not know about extra feautures,  
it is not defined in the manual of normal(ancient) TV.

> Using SmartTV manual for a TV:  

It is not allowed.  
You are trying to change the channel with a remote control(overriden method),  
but the TV is ancient.  
or you can not try browsing on a normal TV

It is like a child trying to use the ancient TV of his grandpa's.
He is trying to find the remote control but the TV does not even work remote.
Or he is trying to browse on TV but the TV does not even has an ethernet port.


In conculusion,
The grapdpa can use the SmartTV but does not know how to browse
But the child can not even use the ancient TV of his grandpa's

Tv t2=new SmartTV() --> is allowed, but the extra features can not be used
SmartTV t1=new TV() --> it is not even allowed

You can call a SmartTV as TV, it is not wrong  
But you can not call a TV as SmartTV, it is wrong

## Polymorphism
One name, different actions
Two methods with same name but they take different actions.

Can be achieved with both overloading and overriding

overloading --> Used for compile-time polymorphism

overriding --> Used for runtime polymorphis

> Example: Polymorphic Cakes
```java

class Cake {
    public void taste (Cake c) {
        System.out.println("In taste of Cake class");
    }
}

class ChocolateCake extends Cake {
    public void taste(Cake c) {
        System.out.println("In taste (Cake version) of ChocolateCake class");
    }
    public void taste(ChocolateCake cc) {
        System.out.println("In taste (ChocolateCake version) of ChocolateCake class");
    }
}

class BirthdayCake extends ChocolateCake {
    public void taste(Cake c) {
        System.out.println("In taste (Cake version) of BirthdayCake class");
    }
    public void taste (ChocolateCake cc) {
        System.out.println("In taste (ChocolateCake version) of BirthdayCake class");
    }
    public void taste(BirthdayCake bc) {
        System.out.println("In taste (BirthdayCake version) of BirthdayCake class");
    }
}

public class Test05{
	public static void main(String[] args) {
		Cake c1 = new Cake();
		Cake c2 = new ChocolateCake();
		Cake c3 = new BirthdayCake();
		
		ChocolateCake cc1 = new ChocolateCake();
		ChocolateCake cc2 = new BirthdayCake();
		
		BirthdayCake bc1 = new BirthdayCake();
		
		c1.taste(c1);
		c1.taste(c2);
		c1.taste(c3);
		c1.taste(cc1);
		c1.taste(cc2);
		c1.taste(bc1);
		
		c2.taste(c1);
		c2.taste(c2);
		c2.taste(c3);
		c2.taste(cc1);
		c2.taste(cc2);
		c2.taste(bc1);
		
		c3.taste(c1);
		c3.taste(c2);
		c3.taste(c3);
		c3.taste(cc1);
		c3.taste(cc2);
		c3.taste(bc1);
		
		cc1.taste(c1);
		cc1.taste(c2);
		cc1.taste(c3);
		cc1.taste(cc1);
		cc1.taste(cc2);
		cc1.taste(bc1);
		
		cc2.taste(c1);
		cc2.taste(c2);
		cc2.taste(c3);
		cc2.taste(cc1);
		cc2.taste(cc2);
		cc2.taste(bc1);
		
		bc1.taste(c1);
		bc1.taste(c2);
		bc1.taste(c3);
		bc1.taste(cc1);
		bc1.taste(cc2);
		bc1.taste(bc1);
		
// "Class of the object" decides which method will be called at the runtime
// "Class of the reference -not the object-" will be taken as the parameter type -always-
	}
}

```
### Checking ancestry- (Actual) Class of the object 
using ***instanceof***

Referance of an object can be  
from the same class as the object  
or from one of the super classes of the object.

#### Upcasting - Downcasting
Use "instanceof"  
To check the class of the object:
```java
class Ball{}

class BasketballBall extends Ball{}
class SoccerBall extends Ball{
	void shoot() {System.out.print("Shoot... ");}
}

public class Test {
	public static void main(String[] args) {

		Object o=(Object)new Ball(); // Explicit casting
		Object o2=new Ball(); // implicit casting
		
		Ball b = new Ball();
		Ball bb = new BasketballBall(); // upcasting
		Ball sb = new SoccerBall();   // upcasting
		SoccerBall sb2 = (SoccerBall)sb;  // downcasting
		// Every object can be upcasted,
        // But not every object can be downcasted:
        // Reference of the class can be casted into class of the object 

		score(b);  // Score Up
		score(bb);  // 3 point
		score(sb);  // Goal

        // This also works because SoccerBall is also a Ball
		score(sb2);  // Goal
	}
	
	static void score(Ball ball) {
        // reference of the parameter object can be Ball 
        // or descendants of Ball

		if(ball instanceof BasketballBall) {
			System.out.println("3 point");
		}
		else if(ball instanceof SoccerBall) {
			((SoccerBall)ball).shoot(); // type casting for removing the compilation error
			System.out.println("Goal");
		}
		else {
			System.out.println("Score Up");
		}
	}
}
```
> Example of Inheritance hierarchy
```
             ____> Orange     ____> McIntosh
    Fruit --|                |
            |____> Apple  ---|
                             |____> GoldenDelicious

Fruit product = new GoldenDelicious();
Orange orange = new Orange();

a. Is product instanceof Fruit? --> YES
b. Is product instanceof Orange? --> NO
c. Is product instanceof Apple? --> YES
d. Is product instanceof GoldenDelicious? --> YES
e. Is product instanceof McIntosh? --> NO
f. Is orange instanceof Orange? --> YES
g. Is orange instanceof Fruit? --> YES
h. Is orange instanceof Apple? --> NO
```

