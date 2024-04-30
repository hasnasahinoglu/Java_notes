# Packages

Collection of classes, interfaces and other packages.

A class can be imported whether in the first lines with the term of import  
or mentioning the class file in the code itself.

```java
// import java.lang.String;

public class Main {
    public static void main(String[] args) {
        java.lang.String str=new java.lang.String();
    }
}
```

## Access modifiers
### There are 4 type of access modifiers
1. default
2. private
3. protected
4. public

>A class can inculude:
>1. variables
>2. methods
>3. inner classes


>A class can be used for:
>1. creating an object (hasA)
>2. being inherited by another class (isA)
 
 ```java
class Demo1{

}

class Demo2 extends Demo1{
    // a class inheriting from another class
    // isA --> Demo2 *is A* Demo1

}

public class Main {
    public static void main(String[] args){
        Demo1 d=new Demo1();
        // a class is used as an object in another class
        // hasA --> Main *has A* object of Demo1
    }
}

 ```


The outer class can only be default or public.

> ### Access Modifiers Table
```
                default     private     protected   public

Same class         O           O            O         O

Same Pack          O           X            O         O
Sub class

Same Pack          O           X            O         O
non-sub class

Diff Pack          X           X            O         O  
Sub class

Diff Pack          X           X            X         O
non-sub class
```

Private are only accessible only within the same class.
Private data field can not be accessable from inside an another class, 
even with creating an instance of that class and trying to access of that private data is not valid.

Public are accessible from everywhere.

Default are only accessible whithin the same Package.

Protected are accessible everywhere except different package non-sub class.

```java
package MyPack1;

public class P1 {  // same class
    int a=10;
    private int b=20;
    protected int c=30;
    public int d=40;
}

class P2 extends P1{  // same Pack, subclass
    int x = a;
    protected int z = c;
    public int t = d;
}

class P3{  // same Pack, non-subclass
    P1 p1=new P1();

    int x=p1.a;
    protected int z=p1.c;
    public int t=p1.d;
}
```

```java
package MyPack2;

import MyPack1.*;

class Q1 {  // different Pack, non-subclass
    P1 p1=new P1();

    public int t = p1.d;
}

class Q2 extends P1{  // different Pack, subclass
    protected int z=c;
    public int t=d ;
}

```

Package names should be uniq to avoid name conflict.
Thus the packege names usually given by reversed URL of the copmany. Since URL is unique,  the package name will also be unique.

URL --> http://www.university.com  
package name can be --> com.university.academics

