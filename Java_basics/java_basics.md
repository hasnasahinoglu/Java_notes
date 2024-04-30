# Data Types

```
Integral --> byte  - 1 byte
        |--> short - 2 byte
        |--> int   - 4 btye
        |--> long  - 8 byte

Floating --> float  - 4 byte
Point   |--> double - 8 byte

char - 2 byte 
(it stores unicode charactes as well as the ASCII characters)

boolean - true or false

These primitives also have their own classes -wrappers- such as Long, Byte as well as their own methods. (Take care the first letters beign upper case.)

String is the class name so the first letter is uppercase
```


A variable should be initialised in some cases;  
Data fields in a class do not have to be initialized, their default values will be set  
if they are not initialised.  
But a local variable in a method has to be initialised manually.

Variable name should start with alphabet or _ or $ 

camelCase is the common usage.

## Wrapper Classes 
All the primitives have their wrapper classes as well as their methods, constants etc.

A primitive type value can be converted into a class type object.   
Converting a primitive value to a wrapper object is called boxing. The reverse conversion is
called unboxing.  
Java automatically converts these into each other when its needed. This is called *autoboxing* and *autounboxing*

Autoboxing → Integer x = 5;  
Autounboxing → int y = new Integer(5);
```java
Integer[] intArray = {1, 2, 3};
System.out.println(intArray[0] + intArray[1] + intArray[2]);

/*
In line 1, the primitive values 1,2, and 3 are automatically boxed 
into objects 
new Integer(1), new Integer(2), and new Integer(3). 
In line 2, the objects 
intArray[0], intArray[1], and intArray[2] 
are automatically unboxed 
into int values than added together.
*/
```

Defining a primitive amd creating an object using wrappers are different:
```java
int x1 = 5;
int x2 = 5;
Integer x3 = 5;
int x4 = new Integer(5);  //!??
Integer x5 = new Integer(5);
Integer x6 = new Integer("5");

    // comparing references

	System.out.println((x1==x2));  // true
    System.out.println((x1==x3));  // true
    System.out.println((x1==x3));  // true
    System.out.println((x1==x4));  // true
	System.out.println((x1==x5));  // true
	System.out.println((x1==x6));  // true

    System.out.println((x3==x4));  // true
    System.out.println((x3==x5));  // false
    System.out.println((x3==x6));  // false

    System.out.println((x4==x5));  // true
    System.out.println((x4==x6));  // true

    System.out.println((x5==x6));  // false

// Similar things also occurs with String class...
```

### Scope of local variables 
A local variable: a variable defined inside a method.  
Scope: the part of the program where the variable can be referenced.  
The scope of a local variable starts from its declaration and continues to the end of the block that contains the variable.  
A local variable must be declared before it can be used.


### Type casting 
is the same as C.

Implicit casting:
```java
double d=3; (type widening)
```

Explicit casting:
```java
int i = (int) 3.0; (type narrowing)
int i = (int) 3.9; (Fraction part is truncated)
```



> Here is an exemple of type casting an the usage of a wrapper class. Static parse methods can be used for **converting Strings to other types** with the help of wrapper classes.
```java
public class Main {

	public static void main(String[] args) {
		
		String input = JOptionPane.showInputDialog("double", "Enter a integer number");
		
        // casting string to double and then casting it integer again 
		System.out.println("The last digit is the "+(int)(Double.parseDouble(input)%10));

        // Other wrappers also have parse and the a lot of other methods. It is just an example
    }
}
```



## Literals

| Data Type | Literal that it takes | Example|
|-----------|-----------------------|-|
| byte | int | byte x = 5; | 
| short | int | short x = 5; |
| int | int | int x = 5;|
| long | L or l | long x = 999999999L; |
| float | F or f | float x = 3.14f // float x=(float)3.14 type casting is also possible| 
| double | D or d or nothing | double x = 3.141592; |
| char | '' | char x = 'A'; |
| boolean | true / false | boolean x = true;


# Compiler? Interpreter?

C/C++ are compiler based languages.  
Javascript is an interpreted language. (Interpreter is the browser)  
Java is a hybrid language.

```
First.java
    |________> Compile --> javac
    |
First.class
    |________> Interprete --> java
    |    
   JVM <--> Operating 
            system
```
```
file name --> First.java
class name --> First

in cmd:

to compile: javac First.java   
(First.class-bytecode- will be generated)
to interprete: java First 
(the first class will be executed  by the JVM)
```

# Operators

## Arithmetic operators

```
+ 
-
*
/
% (works with float numbers also)
```
> ```
> precedence:
> 1) * / %
> 2) + -
>```

Arithmetic operators only can not be used with the boolean data type.  
(It even can be used with char)

> Note that, 
> Do not use floating-point values for equality checking.  
Since floating-point values are approximations for some values, using them could result inaccurate results.

### Conversion rules
1. If one of the operands is double, the other is converted into double
2. OTHERWISE, if one of the operands is float, the other is converted into float
3. OTHERWISE, if one of the operands is long, the other is converted into long
4. OTHERWISE, both operands are converted into int.

```
double * something = double

float * something but double = float

long * something but double or float = long

Otherwise => int


```



## Increment / Decrement

post++ post-- (use the value, then alter it)  
++pre  --pre (alter the value, then used the altered value)

```java
int x=5, y;
y = x++; // first assign, then increment

// y=5, x=6
```

```java
int x=5, y;
y = ++x;  // first increment, then assign
// y=6, x=6
```

```java
int a=2, b=5, x=4, c;
c = a * x++ + b;
//= 2 * 4 + 5
// then x = 5
```
>good example:
```java
int x=5, y=4, z;
z = 2*x++ + 3* ++x;
// z = 2*5 + 3*7
// z = 31
```

```java
char x = 'A';
x++;
System.out.println(x);
// It prints B, so it even works with the char data type
```

Only can not be used with the booleans.

## Bitwise Operators

Only works with the integer type.  
It performs operations bit by bit.

| Operator | Symbol | Example|
|-----------|-----------------------|-|
| AND | & |  | 
| OR| / (Actually it is straight)| | |
| XOR | ^  | |
| LEFT SHIFT product with 2^theNumber| >> |
| RIGHT SHIFT divide with 2^theNumber| << |
| unsigned LEFT SHIFT | >>> |
| NOT | ~ | x=10, y=~x --> y=-11 ( flips each bit of its operand.)

## Logical Operators

Unlike bitwise operators.  
Logical operators work with boolean operands, not bits.

| Operator | Symbol | Example|
|-----------|-----------------------|-|
| AND | && |  | 
| OR| // (Actually it is straight)| | |
| XOR | ^  | |
| NOT | ! | 

> An interesting example of difference between logical and bitwise operators.
```java
public class Main {
	public static void main(String[] args) {
		
		int x = 10;
		int y = 20;
		
		// checks both of the conditions
		if (x==10 & y==20) {
			System.out.println("yes");
		}
		
		// does not check the second condition if the first condition is false
		if (x==10 && y==20) {
			System.out.println("yes");
		}
	}
}
```


# Printing

## System.out.print and System.out.println

They are jsut like same but println also moves curser to the next line.

Do not give two paramaters.

Adding and concatenation is possible but be careful: 

```
int x = 10, y = 20;
System.out.println(x + y + " Sum");
                     |   |
                     |   |_> concatenate
                     |_> add

// output --> 30 Sum
```

```
int x = 10, y = 20;
System.out.println("Sum " + x + y);
                          |   |
                          |   |_>concatenate
                          |_>concatenate

// output --> Sum 1020
```

```
int x = 10, y = 20;
System.out.println("Sum " + (x + y));
                          |    |
                          |    |_>add
                          |_>concatenate

// output --> Sum 30
```

## System.out.printf and System.out.format

This is just same as printf in the C language.

### Format specifier:

>%[argumentIndex$][flag][width][.precision]conversion

>example:
```
System.out.printf("%2$020.2f %1$s","Pi", 3.14159);
                    | | | ||-> it is a float                    --> conversion
                    | | | |__> show 2 numbers after dot         --> precision
                    | | |____> fit in 20 spaces                 --> width
                    | |______> fill the blank spaces with zeros --> flag
                    |________> second argument will be set here --> argument index
```

#### Argument index:
Can be used to change the order of the arguments  
and also be used to be able to use them more than once.
```java
int x = 10;
float y = 3.1f;
System.out.printf("%2$f %1$d %1$d %1$d",x,y);

// output --> 
// 3,100000 10 10 10
```

#### Flag and Width
> Width:
```java
System.out.printf("%10d",10);

// put the integer in 10 spaces
// as long as the integer is short as 10 space

// output-->
//         10
```

> Flag:
```
'+'
'-'
'0'
' '
'('
','
```

```java
// + --> puts a plus if the integer is positive

System.out.printf("%+10d",10);

// output
//        +10
```

```java
// - --> align the given thing left

System.out.printf("%-10d",10);

// output
// 10        
```

```java
// 0 --> fills the blank spaces with zeros

System.out.printf("%020d", 10);

// output
// 00000000000000000010
```

```java
// space --> to get positive and negative numbers aligned

System.out.printf("% d \n",10);
System.out.printf("% d \n",-10);

// output
//  10 
// -10      
```

```java
// ( --> puts the number inside paranthesis if the number is negative

System.out.printf("%(d \n",10);
System.out.printf("%(d \n",-10);

// output
// 10 
// (10)       
```

```java
// , --> makes the number more readable

System.out.printf("%d \n",1000000);
System.out.printf("%,d \n",1000000);

// output
// 1000000 
// 1.000.000      
```

#### .precision

```java
// .n --> show n numbers after dot

System.out.printf("%020.2f", 3.14159);

// output
// 00000000000000003,14     
```


#### Conversion

char --> c  
int --> d, o(octal), x(hexadecimal)  
float --> f, e(scientific), g(scientific)  
String --> s  
boolean --> b  


# String Class

```
int x = 5;
 |  |   |_> literal
 |  |_____> variable name
 |________> data type


 String str = "Java";
    |    |       |__> string object, also a string literal 
    |    |__________> referance  --> holding the beginnig address of that object
    |_______________> class name 
```

Literals also occupy space in memory.

For example:
```java
int x = 5; 
// x is a variable, it will occupy space in memory
// and 5 will be stored in x

int z = 2*x;
// z is a variable, it will occupy space
// and 2*x will be stored there
```
 

But what about 2?

2 is a literal and it also has to occupy space  
and a literal occupies space in 'pool'.


It also goes for the string literals.  
Java maintains a pool of string constant, so  
String literals are created in a 'string constant pool'.


## Creating a string
Constructors are methods that are used for creating objects. They have the same names as the class they are in.
We use constructors for creating string objects.

```
Class referanseName=new Constructor();
// new is a keyword we use for creating an object in 'heap'
```

Here are the some constractors for creating a string:
```java
String(char[])
String(byte[])
String("string")
```
```java
char c[] = {'A', 'B', 'C','D'};
String str1=new String(c);
System.out.println(str1);

byte b[] = {65, 66, 67, 68};
String str2=new String(b);
System.out.println(str2);

// output -->
// ABCD
// ABCD
```

```java
String str3=new String("Java");
System.out.println(str3);

// output -->
// Java
```
In the third examination, two objects will be created:

str3=new -->  
Java(object) will be created in 'heap'  
and str3 will be a referance to that object

But we are mentioning a literal by saying "Java",   
This will has to occupy a space, it is a literal,   
So it will be created in 'pool'  
And there is no referance to that object 


Let's look at the very first example now:
```java
String str4="Java";
System.out.println(str4);

// output -->
// Java
```
Are we saying 'new'? No.  
So nothing will be created in heap.  
There is just a literal.  
And the literal will occupy space in 'pool'.   
So this object will be created in pool.  
And str4 is referance that points onto that pool object.

Let's look at another example now:
```java
String str1="Java";
// nothing will be created in heap
// an object (Java) will be created in pool since it is a literal
// and str1 will be a referance to that object

String str2="Java";
// nothing happens in heap again
// there is an object for Java already in the pool
// so nothing will be created in pool too
// Just str2 will also be a referance to the object Java in the pool

String str3=new String("Java");
// A new object will be created in heap
// there is an object for the literal Java already, so nothing happens in the pool
// str3 will be a referance to the new object Java in the heap
```

Since str1, str2 and str3 are referances,  
they hold the addresses of the objects thay point to,  
so we can compare them to see whether they are pointing the same object or not:
```java
String str1="Java";
String str2="Java";
String str3=new String("Java");
System.out.println(str1==str2);
System.out.println(str1==str3);

// output -->
// true
// false

// str1 and str2 are pointing the same object that created to store the literal Java in the pool. So they are same.
// but str3 is pointing the object that created in the heap, so it holds a different address from the others.
```

## String Methods

String objects cannot be modified.  
So for example when we call .toLowerCase method  
it will return a new string object,  
not change the same string.

```java
String str="Java";

String strLower=str.toLowerCase();
// same object is not modified, a new object has been created(in heap, not in pool)

str=str.toLowerCase(); // is also possible
// So basically:
// make a new string (lowercased version of str), and then assign it to str
// now str is pointing on the new string, not the original one but the lowercased version.
```

>examples:

```java
String str=" Java Language ";


// int length()
int l = str.length();
System.out.println(l);
// 15

// String toLowerCase()
String strLower=str.toLowerCase();
System.out.println(strLower);
//  java language

// String toUpperCase()
String strUpper=str.toUpperCase();
System.out.println(strUpper);
//  JAVA LANGUAGE

// String trim()
String strBlanksRemoved=str.trim();
System.out.println(strBlanksRemoved);
// Java Language

// String substring(int begin)
String substring1=str.substring(6);
System.out.println(substring1);
// Language

// String substring(int begin, int end-not includes the end-)
String substring2=str.substring(6,10);  // 10 is not included
System.out.println(substring2);
// Lang

// String replace(char old, char new)
String strReplaced=str.replace('a', 'b');
System.out.println(strReplaced);
//  Jbvb Lbngubge
```

```java
String web="www.abcd.org";


// boolean startsWith(String s)
boolean checkStart = web.startsWith("www");
System.out.println(checkStart);
// true

// boolean endsWith(String s)
boolean checkEnd = web.endsWith(".org");
System.out.println(checkEnd);
// true

// char charAt(int index)
char letter= web.charAt(3);
System.out.println(letter);
// .

// int indexOf(String s)
int checkDot = web.indexOf(".");
System.out.println(checkDot);
// 3

// int indexOf(String s, startPoint)
int checkDotFromIndex = web.indexOf(".",4);
System.out.println(checkDotFromIndex);
// 8

// int lastIndexOf(String s)
int checkLastDot = web.lastIndexOf(".");
System.out.println(checkLastDot);
// 8

// int lastIndexOf(String s, startPoint)
int checkLastDotFromIndex = web.lastIndexOf(".",7);
System.out.println(checkLastDotFromIndex);
// 3
```

```java
String str1="JAVA";
String str2="java";
String str3="java";
String str4=new String("java");


// boolean equals(String s) // checks characters
boolean checkString1 = str2.equals(str3);
System.out.println(checkString1);
// true

// boolean equals(String s) // Case sensitive
boolean checkString2 = str1.equals(str2);
System.out.println(checkString2);
// false

// boolean equalsIgnoreCase(String s) // Ignores Case sensitivity
boolean checkString3 = str1.equalsIgnoreCase(str2);
System.out.println(checkString3);
// true

// boolean equals(String s) // checks characters
boolean checkString4 = str2.equals(str4);
System.out.println(checkString4);
// true

System.out.println(str2==str4);  // checks references
// false

System.out.println(str2==str3);  // checks references
//true

// int compareTo(String s)  // compares alphabetically
// returns -, 0 or + number
int compareString5 = str1.compareTo(str2);
System.out.println(compareString5);
// -32

// int compareToIgnoreCase(String s)  // Ignores case sensitivity
// returns -, 0 or + number
int compareString6 = str1.compareToIgnoreCase(str2);
System.out.println(compareString6);
// 0

// boolean contains(String s) // searchs for a string
boolean findString = str1.contains("j");
System.out.println(findString);
// false

// String concat(String s) // concatenates two strings
String concatStrings=str1.concat(str2);
System.out.println(concatStrings);
// JAVAjava

// IMPORTANT!
// String.valueOf(); --> Turns any type of data into string
int x = 3;
String turnToString=String.valueOf(x);
System.out.println(turnToString + 3); // plus used for concatenation
// 33
// it prints 33, not 6, so turnToString is "3"
```

### Regular Expressions

The method we use --> String.matches()

#### Matching symbols :

| Regular Expression | Description |
|--------------------|-------------|
| . | Any single character |
| [abc] | A single character matches one of the given |
| [abc][vz] | first character mathces one of the first given and second character mathes one of the second |
| [^abc] | not mathces with one of the characters given |
| [a-z1-7] | in the range of a-z or 1-7|
| A/(straight line)B | A or B  |
| XZ | Exactly XZ |

#### Meta characters :

| Regular Expression | Description |
|-------------------|-------------|
| \d | digit |
| \D | not digit |
| \s | space |
| \S | not space |
| \w | alphabet or digit |
| \W | neither alphabet or digit | 

#### Quantifiers :

| Regular Expression | Description |
|-------------------|-------------|
| * | 0 or more time |
| + | 1 or more time |
| ? | 0 or 1 time |
| {n} | n times |
| {min,max} | between min and max times |

> Example : String methods --> Let's play with an email address 

```java
String str = "programmer@gmail.com";

// check whether it is an email or not
System.out.println("Is it an email address? : " + String.valueOf(str.matches("\\w*@\\w+[.][a-z]*")));
//\\w* --> alphabet or digit, 0 or more times
// @ --> then @ sign
// \\w* --> alphabet or digit, 1 or more times
// [.] --> then . sign
// [a-z]* --> alphabet, 0 or more times


// find out if it is a gmail account
int indexAtSign = str.indexOf("@");

int indexFirstDot = str.indexOf(".");

String domain = str.substring(indexAtSign+1,indexFirstDot);

System.out.println("Is it a gmail account? : " + String.valueOf(domain.equals("gmail")));

// extract the username
String userName = str.substring(0,indexAtSign);
System.out.println("User name : " + userName);

// extract domain name
String domainName = str.substring(indexAtSign+1, str.length());
System.out.println("Domain name : " + domainName);


// output
// Is it an email address? : true
// Is it a gmail account? : true
// User name : programmer
// Domain name : gmail.com
```

> Example : Regular expression --> Let's check if the number is really binary or hexadecimal
```java
int binary=10110001;
String strBinary=String.valueOf(binary);
System.out.println("Is the binary only contains 0 or 1?: " + strBinary.matches("(0|1)*"));

int hex=0x123AEF;
String strHex = hex + ""; // it is also a way to turn an integer into string
System.out.println("Is the strHex only contains hexadecimal numbers?: " + strHex.matches("[A-F0-9]*"));
System.out.println(strHex);
String strHex2=String.valueOf(hex);
System.out.println("Is the strHex2 only contains hexadecimal numbers?: " + strHex2.matches("[A-F0-9]*"));
System.out.println(strHex2);
// I will create a hex number in a string because it is converting hex into decimal form
String strHex3 = "234ABF";
System.out.println("Is the strHex3 only contains hexadecimal numbers?: " + strHex3.matches("[A-F0-9]*"));
System.out.println(strHex3);

// output
// Is the binary only contains 0 or 1?: true
// Is the strHex only contains hexadecimal numbers?: true
// 1194735
// Is the strHex2 only contains hexadecimal numbers?: true
// 1194735
// Is the strHex3 only contains hexadecimal numbers?: true
// 234ABF
// Is the date is a proper date? :true
```

> Example : Regular expression --> Let's play with the spaces

```java
String str = "a!B@c#1$2%3";
// remove special characters
String strRemovedSpecials = str.replaceAll("[!@#$%]", "");
strRemovedSpecials = str.replaceAll("[^a-zA-Z0-9]", ""); // it is also the same
System.out.println(strRemovedSpecials);
// aBc123

// remove alphanumerics
String str = "a!B@c#1$2%3";
String onlySpecials = str.replaceAll("(?i)[a-z0-9]", ""); // (?i) for ignoring case sensivity inside regular expression
System.out.println(onlySpecials);

String str2 = "  ab   cd  fg  ";
    // remove extra spaces
String str2RemovedSpaces = str2.trim().replaceAll("\\s+", " ");
// first cut the spaces in the beginning and the end with trim()
// then replace all one or more spaces with " ".
System.out.println(str2RemovedSpaces);

// let's count the words in the string based on the spaces
str2 = str2.trim().replaceAll("\\s+", " "); // removing extra spaces
String words[] = str2.split("\\s");
// split() method takes a regular expression and splits the string based on this expression
// it returns an array of divided words
System.out.println(words.length);
// length of the words array is the number of words in the str2
// 3
```

# String Builder Class
Very strong class, similar to String but does not inherit from it.  

```java
    StringBuilder sb1=new StringBuilder("Hello ");

    // concatenate
    sb1.append("World");

    // return the String value
    System.out.println(sb1.toString());  // Hello World

    // replace
    sb1.replace(8, sb1.length(), "Java"); 

    // reverse
	System.out.println(sb1.reverse());  // avaJ olleH
```

> Example: Write a method: (Kata: Stop gninnipS My sdroW!)  
Take a string, reverse the words that has 5+ letter  
Return the new String  
(using split - join)
```java
public String spinWords(String sentence) {
    String[] words = sentence.split(" ");
    for (int i=0; i<words.length; i++) {
      if (words[i].length() >= 5) {
        words[i] = new StringBuilder(words[i]).reverse().toString();
      }
    }
    return String.join(" ",words);
  }
```


# Conditions

#### Relational Operators : 
```
<
>
<=
>=
==
!=
```

#### Logical Operators : 
```
&& --> AND
:: --> OR
!  --> NOT
```

## Conditional Statements

### if-else
>example: Find the radix of a number
```java
String number= "10101"; // binary
String number2= "12347"; // octal
String number3= "25978"; // decimal
String number4= "A25BF"; // hexadecimal

if(number.matches("[01]+")){
    System.out.println("binary");
}
else if (number.matches("[0-7]+")){
    System.out.println("octal");
}
else if (number.matches("[0-9]+")){
    System.out.println("decimal");
}
else if (number.matches("[0-9A-F]+")){
    System.out.println("hexadecimal");
}
else {
    System.out.println("None of the basic radixes");
}
```

If a method has to return a value and also includes a conditional statement,  
then the "**else**" case in the condition has to be set in the method,  
even all the conditions has been covered by else-if cases.

>Example
```
Not correct, compile error occurs:

static int sign(int n) {
    if(n==0) {
        return 0;
    }
    else if(n<0) {
        return -1;
    }
    else if(n>0) {
        return 1;
    }
}

// Even all the cases are covered by else if statement(a number can be positive, negative or zero, not anything else)  
// compiler thinks like there is a case (else case) haven't been covered but a return type (which is "int" in this case) is declared. 
--> Compilation error
```

Here is the correct version:
```java
static int sign(int n) {
    if(n==0) {
        return 0;
    }
    else if(n<0) {
        return -1;
    }
    else {
        return 1;
    }
}
```

> Example --> Guessing number game with JOptionPane
```java
public class Main {	

	public static void main(String[] args) {
	int range = 1 + Integer.parseInt(JOptionPane.showInputDialog("Guessing range? :")); 
	int response,guess,buttom = 0;
	String[] options = {"Lower", "Higher", "Good Shot"};
		do {
			guess = (range -buttom)/2 + buttom;
			response = JOptionPane.showOptionDialog(null, "Guess: "+guess+ "  buttom "+buttom + "  range "+ range, "Guessing Game",  JOptionPane.DEFAULT_OPTION,
					JOptionPane.QUESTION_MESSAGE, null,
					options, options[0]);
			if (response == 0) {
				range = guess;
			}
			else if(response == 1){
				buttom = guess;
			}
		}while(response != 2);
	JOptionPane.showMessageDialog(null,"Good game!");
	}
}
```


### switch-case

#### Java supports:  
byte  
short  
int  
char  
String  
as the argument of switch

### Ternary

(Condition)? true : false;


## Loops

### while --- do-while --- for

>Example--> Take a number, extract digits, reverse it, and them print it in words
```java
// display a number in words even with tailing 0

int n=0;
Scanner scn=new Scanner(System.in);
do{
    n=scn.nextInt();
} while(!(n>0));

int r;
String str=""; // will be reversed number

while(n>0){
    r=n%10;
    str=str + r; // concatenate
    n/=10;
}
for(int i=str.length()-1; i>=0; i--){
    switch (str.charAt(i)){
        case '0': System.out.print("zero ");
            break;
        case '1': System.out.print("one ");
            break;
        case '2': System.out.print("two ");
            break;
        case '3': System.out.print("three ");
            break;
        case '4': System.out.print("four ");
            break;
        case '5': System.out.print("five ");
            break;
        case '6': System.out.print("six ");
            break;
        case '7': System.out.print("seven ");
            break;
        case '8': System.out.print("eight ");
            break;
        case '9': System.out.print("nine ");
            break;
    }
}
```

> Example --> Monte Carlo Simulation (using random method)
```java
public class Main {	
	public static void main(String[] args) {
	final int NUMBER_OF_TRIALS = 100000000;
	int numberOfHits = 0;
	
	for(int i=0; i<NUMBER_OF_TRIALS; i++){
		double x = Math.random() * 2.0 - 1;
		double y = Math.random() * 2.0 -1;
		
		if (x*x + y*y <= 1)
			numberOfHits++;
	}
	
	double pi = 4.0 * numberOfHits / NUMBER_OF_TRIALS;
	System.out.println("Pi is : " + pi);
	// output --> Pi is : 3.14147652
	}
}
```


> Example --> Graph of Sınus
```java
public class Main {	
	public static void printStar(double number) {
		int numberOfStars = (int) (number *10);
		if(numberOfStars >= 0) {
			System.out.print("          ");  // 10 blanks for the upper part
		}else {
			for (int i=0; i<(10 - Math.abs(numberOfStars)); i++)  // number of blanks for the lower part
			System.out.print(" ");
		}
		for (int i=0; i<Math.abs(numberOfStars); i++)  // printing stars
		System.out.print("*");

	}

	public static void main(String[] args) {
		int f = 20;  // frequency
		for(int der=0; der<360; der++) {
			double sin = Math.sin(Math.toRadians(der*f));
			printStar(sin);
			System.out.println();
			try {
				Thread.sleep(50);
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
		}
	}
}

```


To exit from the program:
```java
System.exit(0);
```
Can be used in loops for example, instead of breaking the loop

# Arrays

```
             |-> data type of the elements 
             |  |-> size of the array
int A[]=new int[5];
 |  |  | |     |  
 |  |  | |_____|___> object is created in heap 
 |  |  |___________> referance created (in heap or stack, it depends)
 |  |______________> array name (reference of the array)
 |_________________> data type
```

length is also a property that an array has  
To access the length --> arrayName.length  
(take care, it is not a method)

When an array declared, its default values are set:  
0 --> numeric primitive data type  
'\u0000' --> char  
false --> boolean  


## Creating an array
```java
int A[]=new int[10];

int B[] = {1,2,3,4,5};

int C[];
C=new int[10];

int []D=new int[5];
int[] D=new int[5];
```
When you do not initialized, it will automatically fill the spaces wih zeros.
To declare and initialize an array:

```
int A[] = {1,2,3,4,5};
```

To access all the elements, for loop can be used but "for-each loop" will be more convenient 

## Creating a two dimensional array 

```java
int A[][]=new int[3][4]; // creating

int A[][];  //another way of creating
A=new int[3][4];

int []B[]=new int[5][5]; // another way

int[] E,F[];  // E is one, F is two dimensional
E=new int[5];
F=new int[5][5]; 

int A[][]={{1,2,3,4},{2,4,6,8},{1,3,5,7}}; // initialising

int[][] A = new int[]{{1,2,3,4},{2,4,6,8},{1,3,5,7}}; // another way of initialising
```



#### Displaying
for loop:
```java
int[][] A ={{1,2,3,4},{2,4,6,8},{1,3,5,7}};

for(int i=0; i<A.length; i++) {
    for (int j = 0; j < A[0].length; j++)
        System.out.print(A[i][j] + ",");
    System.out.println();
}
```

for-each loop:
```java
int[][] A ={{1,2,3,4},{2,4,6,8},{1,3,5,7}};

for (int x[] : A) {
    for (int y : x)
        System.out.print(y+",");
    System.out.println();
}
```

```
         A[]
          ^   
          ^   y--> 0 1 2 3
        0 [] --> : 1,2,3,4 
        1 [] --> : 2,4,6,8
        2 [] --> : 1,3,5,7
        ^
        ^
        x

A is reference to the array of references  
So x will take values of not integer elements, it will take references to arrays of integers
y takes the values of these integers
```

```
For Example:

String[] words = new String[3]; // referanses created
	
    words[0] = new String("FirstWord"); // an object created

String[] --> Creates reference
String() --> Constructor, creates object
```

## Jagged Array
An array of arrays, but second arrays are not at the same lenght  
Something like this:
```
         A[]
          ^   
          ^   
        0 [] --> : 0,1 
        1 [] --> : 0,1,2,3
        2 [] --> : 0,1,2
```
How to define and display:
```java
int A[][];
A=new int[3][];
A[0]=new int[2];
A[1]=new int[4];
A[2]=new int[3];

for(int x[]:A){
    for(int y:x)
        System.out.print(y);
    System.out.println();
}

// output
// 00
// 0000
// 000
```
```
int A[][]; --> define a two dimensional array

A=new int[3][]; --> defining this part:
"A will be an array of three integer arrays"
                         A[]
                          ^   
                          ^   
                        0 [] 
                        1 [] 
                        2 []


Then define each array separately:
A[0]=new int[2]; --> 0 [] --> : 0,1 
A[1]=new int[4]; --> 1 [] --> : 0,1,2,3
A[2]=new int[3]; --> 2 [] --> : 0,1,2
```


## for-each loop
Accessing all elements in an array  
Only in forward direction
And it is just used for reading the values, you can not modify the elements through for-each loop

```java
for(int x : A)
{
    System.out.println(x);
}
// x is not index, it is the element
```

To exit from the program

>Example--> find the second max integer
```java
int B[] = {1,2,3,6,4,5};

int max,max2;
max = max2 = B[0];

for (int x:B){
    if(x>max)
        max = x;
    else if(x>max2)
        max2 = x;
}
System.out.print("Max: " + max +", Second Max: "+ max2);
```

> Example : Matrix Multiplying 
```
      ______    __________
     |      |  |          |
A[i][k] x B[k][j] => C[i][j]
  |____________________|  
                
```
```java
int[][] A = {{1,1,0},{1,1,1},{1,0,0}};
int[][] B = {{1,0,0},{0,1,0},{0,0,1}}; // Identity Matrix
int[][] C = new int[3][3];

// Calculate
for(int i=0; i<C.length; i++)
    for(int j=0; j<C[i].length; j++)
        for(int k=0; k<B.length; k++)
            C[i][j] += A[i][k]*B[k][j];

// Display
for(int x[]:C) {
    for (int y : x)
        System.out.print(y + " ");
    System.out.println();
}
```

### Sorting an array
There are many built-in sorting mothod
>Example --> Sorting string array
```java
String arr[] = {"java", "python", "c", "assembly", "php"};

java.util.Arrays.sort(arr);

for (String x: arr)
    System.out.println(x);
```

#### Assigning again or not?
We can not modify the objects.  
For example, when we want to change the length of an array:
```java
int[] A=new int[5];
// to extend the length of the array:

// create a new array
int[] B=new int[2*A.length];

// copy the first array to second
for (int i=0; i<A.length; i++)
    B[i]=A[i];

// assign the second reference to first
// the first array(object) will be garbage
A=B;

// nullify the second reference
B=null;

System.out.print(A.length);
// output --> 10
```
So we create a new object and point it with the first reference. Something like this:
```java
String str="Java";

String strLower=str.toLowerCase();
// same object is not modified, a new object has been created(in heap, not in pool)

str=str.toLowerCase(); // is also possible
```
But most built in methods do this process automatically and does not return something, so we do not assign it again. For example:
```java
java.util.Arrays.sort(arr);
```
There is a method for copying arrays btw:
```
arraycopy(sourceArray, src_pos, targetArray, tar_pos, length);

Example:
System.arraycopy(sourceArray, 0, targetArray, 0, sourceArray.length); 

```

# Arrays vs Array Lists

...to be continued

```java
    // Create
    String[] friendsArray = {"John", "Chris", "Eric", "Luke"};
    //or
    String[] friendsArray2 = new String[4];
    
    ArrayList<String> friendsArrayList =
        new ArrayList<>(Arrays.asList("John", "Chris", "Eric", "Luke"));
    //or
    ArrayList<String> friendsArrayList2 = new ArrayList<>();
    

    //Get element
    System.out.println(friendsArray[1]);
    System.out.println(friendsArrayList.get(1));
    

    //Get size
    System.out.println(friendsArray.length);
    System.out.println(friendsArrayList.size());
    
    // is Empty? (ArrayList only)
    friendsArrayList.isEmpty(); // returns boolean

    // clear (ArrayList only)
    friendsArrayList.clear(); // new size will be zero

    //Add an element
    //You can't do this with Arrays :(
    friendsArrayList.add("Mitch");
    System.out.println(friendsArrayList.get(4));


    //Set an element
    friendsArray[0] = "Carl";
    System.out.println(friendsArray[0]);
    friendsArrayList.set(0, "Carl");
    System.out.println(friendsArrayList.get(0));
    

    //Remove an element
    // Can't do this with arrays :(
    friendsArrayList.remove("Chris");
    System.out.println(friendsArrayList.get(1));


    //Print
    //Doesn't work well for Arrays! Must loop through all elements instead.
    System.out.println(friendsArray);
    System.out.println(friendsArrayList);
```


# Methods
```
                 _________________________> method signature
                |        |            |
returnType methodNAme(parameterType parameter)  // header/heading
{
    Body
}
```

## Calling a Method

### Calling a method inside main method

There are two ways to call a method inside main method.

1. Static methods can call only those methods which are static. Main method is static, so make the method you want to call also static:

>Example
```java
// test1.java --> file name 

import java.lang.*;
public class test1 {  // class which has the same name as the file
    static int max(int x, int y)
    {
        // parameters are names as formal parameters
        if(x>y)
            return x;
        else
            return y;
    }

    public static void main(String[] args) {  // main method
        int a=10, b=5, c;  
        c=max(a,b);  // calling method max
        // max(a,b) --> a and b are actual parameters
        System.out.print(c);
        // output --> 10
    }
}
```

Values of actual parameters will be copied inside formal parameters, and this formal paramaters will have just copies. (like call-by-value)  
If any modifications are done to formal parameters, that will not affect actual parameters

>Example --> incorrect result coused by pass-by-value
```java
public class Main {	
	static void max(int num1, int num2, int max) {
		if(num1>num2)
			max=num1;
		else
			max=num2;
	}

	public static void main(String[] args) {
		int max = 0;
		int a=10, b=20;
		max(a,b,max);
		System.out.println(max);
		// output --> 0
		// not 20
	}
}
```

>Example --> pass-by-address can be achieved with the help of arrays
```java
public class Main {	
	static void max(int arr[]) {
		if(arr[1]>arr[2])
			arr[0]=arr[1];
		else
			arr[0]=arr[2];
	}

	public static void main(String[] args) {
		int max = 0;
		int a=10, b=20;
		int Array[] = {max, a, b};
		max(Array);
		System.out.println(max + " " + Array[0]);
		// output --> 0 20
	}
}
```



2. Make an object of your class, then call the method via that object

>Example:
```java
import java.lang.*;
public class test1 {
    int max(int x, int y)
    {
        if(x>y)
            return x;
        else
            return y;
    }

    public static void main(String[] args) {
        int a=10, b=5, c;

        test1 findMax=new test1(); // create an object of class test1
        c=findMax.max(a,b); // call the method
        System.out.print(c);
        // output --> 10
    }
}
```

### Passing object as parameters
```java
public class test1 {
    static void update(int[] x)
    {
        x[0] = 100;
    }

    public static void main(String[] args) {
        int A[] = {1,2,3,4,5};
        update(A);
        System.out.println(A[0]);
        // output --> 100
    }
}
```

```
public static void main(String[] args) 
            int A[] = {1,2,3,4,5};
                |           |
in a method :   |           |_> object is created in heap
                |_> reference is created in stack
                A is the reference that holds the address of the array
```

```
    static void update(int[] x)
                         |______> formal parameter which is a reference

        public static void main(String[] args)
            update(A);                      
                   |____________> actual paremeter which is also a reference

    Content inside the actual parameter is copied to the formal parameter
    So x[] has the same value as A[] which 
    is the same address of the same array 
    // new is not mentioned in the update method, so a new object is not created in the memory
    // just a reference (x[]) is created 

    Because of this, x[] and A[] are references of the same array
    So they both can access and modify the object
    It is like (pass-by-address)
```

### So how many ways are there in java for Parameter Passing?

There is only one way to passing paramater in java:  

The content of actual parameters are copied in formal parameters.

That's it.  
Do not be confused with the terms of call-by-value or call-by-address.  
They are done with the same way: Copying the content.

When a primitive (int x=5, char c='A', double pi=3.141 etc.) is passed,  
The content of the actual parameters (which is 5, 'A', or 3.141000) are copied to the formal   parameters.   
So they can not modify the actual parameters.  
So it is like call-by-value.  

When an object (int A[] = {1,2,3}, Strign name="Victor") is passed,  
The content of the actual parameters,  
(which is the content of A --> address of the object array {1,2,3} or  
which is the content of name --> address of the object array "Victor")  
are copied to the formal parameters.  
So the formal parameters have the address of the same object which is created by the main method.  
The caller method --> main method  
The called method --> method we call to use, function  
So in this way, called method is not creating a new object,  
it is creating a variable (a reference) that will hold the address of the object which is created by the caller method. So it can reach and modify the object.  
So it is like call-by-reference.

But the two things are not different, they work with the same logic.  
In conculusion, there is only one way for passing parameter in java: Copying the content.


#### Example of using methods --> Greatest Common Divisor
```java
public class test1 {
    static int findGreatestCommonDivisor(int n1, int n2){
        int GDC = 1;
        for (int i=1; i<=n1; i++)
            if((n1%i)==0 && (n2%i)==0)
                GDC = i;
        return GDC;
    }

    public static void main(String[] args) {
        System.out.print(findGreatestCommonDivisor(15,30)); // give min number first

    }
}
```

```java
public class test1 {
    static int findGreatestCommonDivisor(int m, int n){
        // use a different algorithm
        while(m!=n){
            if(m>n) m=m-n;
            else n=n-m;
        }
        return m;
    }

    public static void main(String[] args) {
        System.out.print(findGreatestCommonDivisor(25,15)); // give min number first
    }
}
```

## Method overloading

Java allows to make methods with the same name  but 
1. Either data type (not return type, take care) of parameters should be different
2. Or the number of parameters must be different

In short, the signature of the methods has to be different  

Only method name and the parameter list is checked, not the return type,  So  
int method(int x, int y)  
float method(int x, int y)  
these are not allowed.

### Ambiguous Invocation
Sometimes, more than one method can match to the call cause of the possible type casting scenarios.
>Example 
```java
public class Main {
	
	public static double max(int num1, double num2) { 
	    if (num1 > num2)
	      return num1;
	    else
	      return num2;
	  }
	  
	  public static double max(double num1, int num2) {
	    if (num1 > num2)
	      return num1;
	    else
	      return num2;     
	  }

	
	public static void main(String[] args) {
		    System.out.println(max(1, 2));  
		 
	}
    // Compilation error --> The method called which is max(int,double) is ambiguous.
    // BOTH of the methods match.
}
```
If there is a perfect match for the method called,  
ambiguity is eliminated.
```java
public class Main {
	
	public static double max(int num1, double num2) { 
	    if (num1 > num2)
	      return num1;
	    else
	      return num2;
	  }
	  
	  public static double max(double num1, int num2) {
	    if (num1 > num2)
	      return num1;
	    else
	      return num2;     
	  }

	  public static double max(int num1, int num2) {
		    if (num1 > num2)
		      return num1;
		    else
		      return num2;     
		  }
	
	public static void main(String[] args) {
		    System.out.println(max(1, 2));  
		 
	}
    // No error
    // Output 2.0
}

```


## Variable arguments (varargs)

It allows you take pass any number of variables. But all the variables should be same data type.

It puts all the values and put them in an array,
```java
public class test1 {
    static void show(int ...A){
        for (int x:A)
            System.out.print(x + ", ");
    }

    public static void main(String[] args) {
        show();  // also works 
        show(10,20,30);  
        show(new int[]{1,2,3,4,5,6});  // this is an anonymous array created in heap, does not have a reference, it will utilized by the method and then be deleted
    }
}
```

Remember that the main method can also take arguments  

```java
public class test1 {

    public static void main(String[] args) {
        for (String str:args)
            System.out.println(str);
    }
}
```

## Recursive methods
It is as same as it was in C.
```java
public class test1 {
    static void  fun(int n){
        if(n>0){
            System.out.print(n);
            fun(n-1);
        }
    }

    public static void main(String[] args) {
        fun(3);
        // output 321
    }
}
```

```java
public class test1 {
    static void  fun(int n){
        if(n>0){
            fun(n-1);
            System.out.print(n);
        }
    }
    
    public static void main(String[] args) {
        fun(3);
        // output 123
    }
}
```
