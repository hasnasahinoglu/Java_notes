# Object Oriented Programming

### Principles pf OOP :

1. Abstraction
2. Encapsulation
3. Inheritance - Specialization
4. Polymorphism - Generalization

#### Generalization
There is already some clasese which have similarities,  
and they can be grouped or  
a super class which can refer all these sub classes can be created
It is named as generalization  
**Interfaces** are made for this.
```
            SmartPhone  --> new created
             ^  ^  ^
           __|  |  |__
          |     |     |
     IPhone  Samsung   Vivo  --> already was there
```

#### Specialization 
There is already a class  
a new class will be created which have all the features that already exist class has 
and some new extra features
This process named as specialization
**Inheritance** is used to achivie this.
```
            IPhoneX  --> already was there
               |
               |
            IPhoneXS  --> new created
```

#### Abstract classes
To be continued....

## Class vs Object

Classes are description kits for creating objects  
Class --> plan for the object, on paper  
Object --> real thing, really exist
An object can be defined in terms of its  
1. Properties  --> written as variables, data members
2. Behaviors  --> methods

The operations of the behavior will affect the properties

```
class Television
{
    private int channel;  
    private int volume; 
    
    public void changeChannel()
    {
    
    }
    public void changeVolume()
    {
    
    }
}

public class test1 {

    public static void main(String[] args) {
        Television t=new Television();
        t.changeChannel();
    }
}

All the methods:
main()
changeChannel()
changeVolume()
will be created in "method area"

Referances:
t
will be created in stack

An object  
which have properties like 
channel and 
volume 
will be created in heap
```

>Example --> class Rectangle
```java
class Rectangle
{
    public double length;
    public double breadth;

    public double area(){
        return length * breadth;
    }

    public double perimeter(){
        return 2*(length+breadth);
    }

    public boolean isSquare(){
        return length==breadth;
    }
}

public class Test {

    public static void main(String[] args) {
        Rectangle r = new Rectangle();
        r.length = 10.5;
        r.breadth = 10.5;

        System.out.println("Area: " + r.area());
        System.out.println("Perimeter: " + r.perimeter());
        System.out.println("Is it a square: " + r.isSquare());
    }
}

// output
// Area: 110.25
// Perimeter: 42.0
// Is it a square: true
```

>Example --> class Cylinder
```java
class Cylinder
{
    public double radius;
    public double height;

    public double lidarea(){
        return Math.PI * radius * radius;
    }
    public double circumference(){
        return 2*Math.PI*radius;
    }
    public double totalSurfaceArea(){
        return 2*lidarea() + circumference()*height;
    }

    public double volume(){
        return lidarea()*height;
    }

}

public class Test {

    public static void main(String[] args) {
        Cylinder c=new Cylinder();
        c.radius = 7;
        c.height = 10;

        System.out.println("Lid area: " + c.lidarea());
        System.out.println("Total area: " + c.totalSurfaceArea());
        System.out.println("Volume: " + c.volume());
    }
}
```
>Example --> class Student
```java
class Student
{
    public int no;
    public String name;
    public String course;
    public int m1,m2,m3;

    public float average(){
        return (float)(m1+m2+m3)/3;
    }

    public String toString(){
        return "No: "+no+"\n" + "Name: "+name+"\n" + "Course: "+course+"\n";
    }
}

public class Test {

    public static void main(String[] args) {
        Student s=new Student();
        s.m1 = 80;
        s.m2 = 90;
        s.m3 = 100;

        System.out.println("Average: " + s.average());
        System.out.println("Details: \n" + s); 
        // when you call only "s"
        // it will call s.toString method if the method is exist
    }
}
```

## Data Hiding
Generally we do not want user to access and modify the data directly.  
So we hide the data.  
If we want user to set some properties,  then we use property methods:  
getProperty();  
setProperty();

>Example --> class Rectangle
```java
class Rectangle
{
    private double length;
    private double breadth;

    public double getLength(){
        return length;
    }
    public void setLength(double l){
        if(l>0) // we avoid user setting length negative
            length = l;
        else
            length = 0;
    }

    public double getBreadth(){
        return breadth;
    }
    public void setBreadth(double b){
        if(b>0)
            breadth = b;
        else
            breadth= 0;
    }


    public double area(){
        return length * breadth;
    }

    public double perimeter(){
        return 2*(length+breadth);
    }

}

public class Test {

    public static void main(String[] args) {
        Rectangle r = new Rectangle();
        r.setLength(10.5);
        r.setBreadth(5.5);
        // properties are private
        // but the methods to set the properties are public

        System.out.println("Area: " + r.area());
        System.out.println("Perimeter: " + r.perimeter());
    }
}
```

#### Types of properties
A property that has both get and set methods is both  
readable and writable property.  
Sometimes a property should be  
only readable or  
only writeable.   
Then we do not define both these methods. For example  
Producer program --> only set method  
Consumer program --> only get method is should be available for the property we talk about.


## Constructor

Constructor is a method that being called whenever an object is created. 

By default, even if constructor is not defined in the class, compiler creates a constructors.

Constructor can be defined in the class and also can be overloaded.

If a parametarised constructor has been declared in the class, compiler does not create a no-parametere constructor.  
Thus, "A a=new A()" declaretion is invalid if there are only parametarised constructors in the class.

Constructor has to be same name as the class name. 

It should not have a return type.

Constructors usually declared as puclic but they can also be private.

They are useful because when an object is created, at the same time some of the properties also can be set.

For example:

```java
class Rectangle
{
    private double length;
    private double breadth;

    public double area(){
        return length * breadth;
    }
}

public class Test {

    public static void main(String[] args) {
        // I want a rectangle
        Rectangle r = new Rectangle();

        System.out.println("Area: " + r.area());
        // output --> Area: 0.0
    }
}
// Constructor is not defined
// So compiler creates a constructor by default
// And the properties assigned as 0
```

```java
class Rectangle
{
    private double length;
    private double breadth;

    public Rectangle(){
        length = 1;
        breadth = 1;
    }
    public double area(){
        return length * breadth;
    }
}

public class Test {

    public static void main(String[] args) {
        // I want a rectangle with the predefined properties
        Rectangle r = new Rectangle();

        System.out.println("Area: " + r.area());
        // output --> Area: 1.0
    }
}
// Constructor is defined
// So defined constructor takes precedence
// And the properties assigned as 1 by this constructor
```

```java
class Rectangle
{
    private double length;
    private double breadth;

    public Rectangle(){
        length = 1;
        breadth = 1;
    }
    public Rectangle(double l, double b){
        length = l;
        breadth = b;
    }

    public double area(){
        return length * breadth;
    }
}

public class Test {

    public static void main(String[] args) {
        // I want a rectangle with the properties I give here
        Rectangle r = new Rectangle(10.0, 5.5);

        System.out.println("Area: " + r.area());
        // output --> Area: 55.0
    }
}
// Constructor is overloaded
// So defined and suitable constructor takes precedence.
// And the properties assigned as 10 and 5.5
```

## Array of Objects

```java
class Subject {
    private String subId;
    private String name;
    private int maxMark;
    private int markObtain;

    // constructor
    public Subject(String subId, String name, int max){
        /* when the name of the parameter
        and the name of the property is the same
        subId = subId is not convenient (which subId will be assigned?) so
        this.subId --> property name
        this.subId = subId --> this means :
        assign the value of the given parameter subId to the property subId
         */
        this.subId = subId;
        this.name = name;
        maxMark = max;
    }

    // get methods
    public String getSubId(){return subId;}
    public String getName(){return name;}
    public int getMaxMark(){return maxMark;}
    public int getMarkObtain(){return markObtain;}

    // set methods
    public void setMaxMark(int mm){
        maxMark = mm;
    }
    public void setMarkObtain(int m){
        markObtain = m;
    }

    // other methods
    boolean isQualifies(int m){
        return markObtain>=maxMark/10*4;
    }
    public String toString(){
        return "\nSubject ID:"+subId+"\nName :"+name+"\nMark Obtained :"+markObtain;
    }
}

class Student{
    private String no;
    private String name;
    private String dept;
    private Subject subsSelected[];

    // constructor
    public Student(String no, String name, String dept){
        this.no = no;
        this.name = name;
        this.dept = dept;
    }

    // get methods
    public String getNo(){return no;}
    public String getName(){return name;}
    public String getDept(){return dept;}
}

public class ArrayOfObjects {

    public static void main(String[] args) {
        // creating array of objects
        Subject subs[]=new Subject[3];
        // same as: Subject[] subs=new Subject[3];
        // in C: struct myStruct structArr[3]; //define an array, elements are structs

        // subs is referring the array of three references
        // and these three references are referring three separate objects

        // to create all these three object:
        subs[0]=new Subject("s101", "DS", 100);
        subs[1]=new Subject("s102", "Algorithms", 100);
        subs[2]=new Subject("s103", "Operating Systems", 100);

        for(Subject x:subs) // data type of x is the Subject class
            System.out.println(x);
        // calling all elements of the subs one by one
        // and calling an element with its name means calling toString method
    }
}
```

To be continued...
