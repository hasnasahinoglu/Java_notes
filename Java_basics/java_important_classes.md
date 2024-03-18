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
