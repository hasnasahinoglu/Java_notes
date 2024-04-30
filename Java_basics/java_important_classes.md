# Math

### Math.PI

### Math.pow(base, exponent)
### Math.sqrt(number)  // only for sqrt
### Math.abs(number)
### Math.ceil(double)
### Math.floor(double)
### Math.round(double x)
### Math.toRadians(der) // der to rad
### Math.sin(radian)  // the value of the sin
### Math.cos(radian)
### Math.tan(radian)
### Math.exp(double a)
Returns e raised to the power of a.
Math.exp(1) returns 2.71
### Math.log(double a)
Returns the national logarithm of a
Math.log(2.71) returns 1
### Math.log10(double 1)
### Math.max(a, b)
### Math.min(a, b)
### Math.random()
Returns a random double value in the range [0.0, 1.0)

Math.random() * 10 returns between 0 and 9
50 + Math.random() * 50 return between 50 and 99
# Scanner


# JOptionPane

# java.util.Arrays
Provides static methods to perform many operations such as 
sorting, copying, filling, searching...
### Arrays.sort(arr)
```java
    int[] numbers = {6,4,7,3,4,4};
    Arrays.sort(numbers);
    System.out.println(Arrays.toString(numbers));
    // output 
    // [3, 4, 4, 4, 6, 7]
```


### Arrays.binarySearch(arr, theVariable)
```java
    int[] numbers = {2, 4, 6, 8, 10, 12};
    int index = Arrays.binarySearch(numbers, 8);
    System.out.println("Found in the index " + index);
    // output
    // Found in the index 3
```

### Arrays.copyOf(originalArray, lenght)
```java
    int[] originalArray = {1, 2, 3, 4, 5};
    int[] copiedArray = Arrays.copyOf(originalArray, 3);
    System.out.println(Arrays.toString(copiedArray));
    // output
    // [1, 2, 3]
```



### Arrays.equals(arr1, arr2)
```java
    int[] array1 = {1, 2, 3};
    int[] array2 = {1, 2, 3};
    boolean result = Arrays.equals(array1, array2);
    System.out.println("Are they equal?: " + result);
    // output
    // Are they equal?: true
```

### Arrays.fill(arr, theValueToBeFilledWith)
```java
    int[] numbers= new int[5];
    Arrays.fill(numbers, 10);
    System.out.println(Arrays.toString(numbers));
    // output
    // [10, 10, 10, 10, 10]
```


### Arrays.toString(arr)
```java
    int[] numbers = {1, 2, 3, 4, 5};
    String arrayString = Arrays.toString(numbers);
    System.out.println(arrayString);
    // output
    // [1, 2, 3, 4, 5]
```

# Date

# Random
create an instance and then use the functions
Random r=new Random();
r.nextInt(int number); --> return a number between 0 and the number

# BigInteger
If you need to compute with very large integers or high-precision floating-point values,  
you can use the BigInteger and BigDecimal classes  
in the java.math package.  
Both are immutable.  
You can use new BigInteger(String) and new BigDecimal(String) to create an instance of BigInteger and BigDecimal,  
use the add, subtract, multiply, divide,
and remainder METHODS (they can not be calculated directly) to perform arithmetic operations,  
and use the compareTo method to compare  

For example, the following code creates two BigInteger
objects and multiplies them.
BigInteger a = new BigInteger("9223372036854775807");
BigInteger b = new BigInteger("2");
BigInteger c = a.multiply(b); // 9223372036854775807 * 2


> Example : Dynamic programming with BigIntegers  
(simulating hexagons in a matrix)
```java
import java.math.BigInteger;
import java.lang.Math;

public class Kata {
  
public static BigInteger theBee(int n) {
    // creating matrix
        BigInteger[][] matrix = new BigInteger[2*n-1][2*n-1];
        for(int i=0; i< matrix.length; i++){ 
            for(int j=0; j<matrix[i].length; j++){
                matrix[i][j] = BigInteger.ZERO;
            }
        }
        
    // Adding through the matrix (except the last row and last column)
        matrix[0][0] = BigInteger.ONE;
        for(int i=0; i< matrix.length-1; i++){
            for(int j=0; j<matrix[i].length-1; j++){
                if(Math.abs(i-j)>=n){
                    matrix[i][j] = BigInteger.ZERO;
                }
                matrix[i][j+1] = matrix[i][j+1].add(matrix[i][j]);
                matrix[i+1][j] = matrix[i+1][j].add(matrix[i][j]);
                matrix[i+1][j+1] = matrix[i+1][j+1].add(matrix[i][j]);
            }
        }

    // Adding the last layers
        for(int k=n-1; k<2*n-2; k++){
            matrix[2*n-2][k+1] = matrix[2*n-2][k+1].add(matrix[2*n-2][k]);
            matrix[k+1][2*n-2] = matrix[k+1][2*n-2].add(matrix[k][2*n-2]);
        }
        
    //return the last cell
        return matrix[2*n-2][2*n-2];
    }
}

```
