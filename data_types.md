## Data types

A data type is a set of values and the allowable operations on those values.  

Java programming language is a statically typed language. It means that every  
variable and every expression has a type that is known at compile time. Java  
language is also a strongly typed language because types limit the values that a  
variable can hold or that an expression can produce, limit the operations  
supported on those values, and determine the meaning of the operations.  

Strong static typing helps detect errors at compile time. Variables in  
dynamically typed languages like Ruby or Python can receive different data types  
over the time. In Java, once a variable is declared to be of a certain data  
type, it cannot hold values of other data types.  

There are two fundamental data types in Java: primitive types and reference
types. 

Primitive types:

- boolean
- char
- byte
- short
- int
- long
- float
- double


There is a specific keyword for each of these types in Java. Primitive types are  
not objects in Java. Primitive data types cannot be stored in Java collections  
which work only with objects. They can be placed into arrays instead.  

The reference types:

- class types
- interface types
- array types

There is also a special null type which represents a non-existing value.  

In Ruby programming language, everything is an object. Even basic data types.  

```ruby
#!/usr/bin/ruby

4.times { puts "Ruby" }
```

This Ruby script prints four times "Ruby" string to the console. We call a times  
method on the 4 number. This number is an object in Ruby.  

Java has a different approach. It has primitive data types and wrapper classes.  
Wrapper classes transform primitive types into objects.  

## Boolean values

In Java the boolean data type is a primitive data type having one of two values:  
`true` or `false`.

```java
import java.util.Random;

void main() {

    String name = "";
    Random r = new Random();
    boolean male = r.nextBoolean();

    if (male == true) {

        name = "Robert";
    }

    if (male == false) {

        name = "Victoria";
    }

    System.out.format("We will use name %s%n", name);
    System.out.println(9 > 8);
}
```

The program uses a random number generator to simulate our case.


## Integers

Integers are a subset of the real numbers. They are written without a fraction  
or a decimal component. 

Integers fall within a set `Z = {..., -2, -1, 0, 1, 2,...}`. Integers are infinite.  

Computers can practically work only with a subset of integer values, because  
computers have finite capacity. Integers are used to count discrete entities. We  
can have 3, 4, or 6 humans, but we cannot have 3.33 humans. We can have 3.33  
kilograms, 4.564 days, or 0.4532 kilometers.  


| Type  | Size     | Range                                   |
|-------|----------|-----------------------------------------|
| byte  | 8 bits   | -128 to 127                             |
| short | 16 bits  | -32,768 to 32,767                       |
| char  | 16 bits  | 0 to 65,535                             |
| int   | 32 bits  | -2,147,483,648 to 2,147,483,647         |
| long  | 64 bits  | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 |

Table: Integer types in Java

These integer types may be used according to our needs. We can then use the byte  
type for a variable that stores the number of children a woman gave birth to.  
The oldest verified person died at 122, therefore we would probably choose at  
least the short type for the age variable. This will save us some memory.  

Integer literals may be expressed in decimal, hexadecimal, octal, or binary  
notations. If a number has an ASCII letter L or l suffix, it is of type long.  
Otherwise it is of type int. The capital letter L is preferred for specifying  
long numbers, since lowercase l can be easily confused with number 1.  

```
int a = 34;
byte b = 120;
short c = 32000;
long d = 45000;
long e = 320000L;
```

We have five assignments. Values 34, 120, 32000, and 45000 are integer literals  
of type `int`. There are no integer literals for `byte` and `short` types. If  
the values fit into the destination type, the compiler does not complain and  
performs a conversion automatically. For long numbers smaller than  
`Integer.MAX_VALUE`, the `L` suffix is optional.  

```
long x = 2147483648L;
long y = 2147483649L;
```

For long numbers larger than `Integer.MAX_VALUE`, we must add the `L` suffix.  

When we work with integers, we deal with discrete items. For instance, we can  
use integers to count apples.  

```java
void main() {

    int baskets = 16;
    int applesInBasket = 24;

    int total = baskets * applesInBasket;

    System.out.format("There are total of %d apples%n", total);
}
```

In our program, we count the total amount of apples. We use the multiplication
operation.

```java
int baskets = 16;
int applesInBasket = 24;
```

The number of baskets and the number of apples in each basket are integer values.

```java
int total = baskets * applesInBasket;
```

Multiplying those values we get an integer, too.  


Integers can be specified in four different notations in Java: decimal, octal,  
hexadecimal, and binary. Decimal numbers are used normally as we know them.  
Octal numbers are preceded with a 0 character and followed by octal numbers.  
Hexadecimal numbers are preceded with `0x` characters and followed by  
hexadecimal numbers. Binary numbers start with `0b` and are followed by binary  
numbers (zeroes and ones).  


```java
void main() {

    int n1 = 31;
    int n2 = 0x31;
    int n3 = 031;
    int n4 = 0b1001;

    System.out.println(n1);
    System.out.println(n2);
    System.out.println(n3);
    System.out.println(n4);
}
```

We have four integer variables. Each of the variables is assigned a value with a  
different integer notation.  

```java
int n1 = 31;
int n2 = 0x31;
int n3 = 031;
int n4 = 0b1001;
```

The first is decimal, the second hexadecimal, the third octal, and the fourth  
binary.


Big numbers are difficult to read. If we have a number like 245342395423452, we  
find it difficult to read it quickly. Outside computers, big numbers are  
separated by spaces or commas. 

The underscore cannot be used at the beginning or end of a number, adjacent to a  
decimal point in a floating point literal, and prior to an `F` or `L` suffix.  

```java
void main() {

    long a = 23482345629L;
    long b = 23_482_345_629L;

    System.out.println(a == b);
}
```

This code sample demonstrates the usage of underscores in Java.  

```java
long a = 23482345629L;
long b = 23_482_345_629L;
```

We have two identical `long` numbers. In the second one we separate every three  
digits in a number. Comparing these two numbers we receive a boolean `true`. The  
`L` suffix tells the compiler that we have a `long` number literal.  

Java `byte`, `short`, `int` and `long` types are used do represent fixed  
precision numbers. This means that they can represent a limited amount of  
integers. The largest integer number that a `long` type can represent is  
9223372036854775807. If we deal with even larger numbers, we have to use the  
`java.math.BigInteger` class. It is used to represent immutable arbitrary  
precision integers. Arbitrary precision integers are only limited by the amount  
of computer memory available.  

```java
void main() {

    System.out.println(Long.MAX_VALUE);

    BigInteger b = new BigInteger("92233720368547758071");
    BigInteger c = new BigInteger("52498235605326345645");

    BigInteger a = b.multiply(c);

    System.out.println(a);
}
```

With the help of the `java.math.BigInteger` class, we multiply two very large  
numbers.  

## Arithmetic overflow

An arithmetic overflow is a condition that occurs when a calculation produces a  
result that is greater in magnitude than that which a given register or storage  
location can store or represent.  

```java
void main() {

    byte a = 126;

    System.out.println(a);
    a++;

    System.out.println(a);
    a++;

    System.out.println(a);
    a++;

    System.out.println(a);
}
```

## Floating point numbers

Real numbers measure continuous quantities, like weight, height, or speed.  
Floating point numbers represent an approximation of real numbers in computing.  
In Java we have two primitive floating point types: `float` and `double`.  

The `float` is a single precision type which store numbers in 32 bits. The  
`double` is a double precision type which store numbers in 64 bits. These two  
types have fixed precision and cannot represent exactly all real numbers. In  
situations where we have to work with precise numbers, we can use the  
`BigDecimal` class.  

Floating point numbers with an `F/f` suffix are of type `float`, `double`  
numbers have `D/d` suffix. The suffix for `double` numbers is optional.  

Let's say a sprinter for 100m ran 9.87s. What is his speed in km/h?  

```java
void main() {

    float distance;
    float time;
    float speed;

    distance = 0.1f;

    time = 9.87f / 3600;

    speed = distance / time;

    System.out.format("The average speed of a sprinter is %f km/h%n", speed);
}
```

In this example, it is necessary to use floating point values. The low precision  
of the `float` data type does not pose a problem in this case.  


The `float` and `double` types are inexact.

```java
void main() {

    double a = 0.1 + 0.1 + 0.1;
    double b = 0.3;

    System.out.println(a);
    System.out.println(b);

    System.out.println(a == b);
}
```

The code example illustrates the inexact nature of the floating point values.  

When we work with money, currency, and generally in business applications, we  
need to work with precise numbers. The rounding errors of the basic floating  
point types are not acceptable.  

```java
void main() {

    float c = 1.46f;
    float sum = 0f;

    for (int i=0; i<100_000; i++) {

        sum += c;
    }

    System.out.println(sum);
}
```

The `1.46f` represents 1 euro and 46 cents. We create a sum from 100000 such  
amounts.  

```java
for (int i=0; i<100_000; i++) {

    sum += c;
}
```

In this loop, we create a sum from 100000 such amounts of money.

```
$ java CountingMoney.java
146002.55
```

The calculation leads to an error of 2 euros and 55 cents.

To avoid this margin error, we utilize the `BigDecimal` class. It is used to  
hold immutable, arbitrary precision signed decimal numbers.  

```java
import java.math.BigDecimal;

void main() {

    BigDecimal c = new BigDecimal("1.46");
    BigDecimal sum = new BigDecimal("0");

    for (int i=0; i<100_000; i++) {

        sum = sum.add(c);
    }

    System.out.println(sum);
}
```


Java supports the scientific syntax of the floating point values. Also known as  
exponential notation, it is a way of writing numbers too large or small to be  
conveniently written in standard decimal notation.  

```java
import java.math.BigDecimal;
import java.text.DecimalFormat;

void main() {

    double n = 1.235E10;
    DecimalFormat dec = new DecimalFormat("#.00");

    System.out.println(dec.format(n));

    BigDecimal bd = new BigDecimal("1.212e-19");

    System.out.println(bd.toEngineeringString());
    System.out.println(bd.toPlainString());
}
```

We define two floating point values using the scientific notation.  

## Enumerations

An enum type is a special data type that enables for a variable to be a set of  
predefined constants. A variable that has been declared as having an enumerated  
type can be assigned any of the enumerators as a value. Enumerations make the  
code more readable. Enumerations are useful when we deal with variables that can  
only take one out of a small set of possible values.  

```java
enum Days {

    MONDAY,
    TUESDAY,
    WEDNESDAY,
    THURSDAY,
    FRIDAY,
    SATURDAY,
    SUNDAY
}

void main() {

    Days day = Days.MONDAY;

    if (day == Days.MONDAY) {

        System.out.println("It is Monday");
    }

    System.out.println(day);

    for (Days d : Days.values()) {

        System.out.println(d);
    }
}
```

In our code example, we create an enumeration for week days.  

It is possible to give some values to the enumeration constants.  

```java
enum Season {

    SPRING(10),
    SUMMER(20),
    AUTUMN(30),
    WINTER(40);

    private int value;

    private Season(int value) {
        this.value = value;
    }

    public int getValue() {

        return value;
    }
}

void main() {

    for (Season season : Season.values()) {
        System.out.println(season + " " + season.getValue());
    }
}
```

The example contains a Season enumeration which has four constants.

## Strings and chars

A String is a data type representing textual data in computer programs. A string  
in Java is a sequence of characters. A char is a single character. Strings are  
enclosed by double quotes.  

```java
void main() {

    String word = "ZetCode";

    char c = word.charAt(0);
    char d = word.charAt(3);

    System.out.println(c);
    System.out.println(d);
}
```

The program prints Z character to the terminal.


## Arrays

Array is a data type which handles a collection of elements. Each of the  
elements can be accessed by an index. All the elements of an array must be of  
the same data type.  

```java
void main() {

    int[] numbers = new int[5];

    numbers[0] = 3;
    numbers[1] = 2;
    numbers[2] = 1;
    numbers[3] = 5;
    numbers[4] = 6;

    int len = numbers.length;

    for (int i = 0; i < len; i++) {

        System.out.println(numbers[i]);
    }
}
```

In this example, we declare an array, fill it with data and then print the  
contents of the array to the console.  


## The null type

Java has a special `null` type. The type has no name. As a consequence, it is  
impossible to declare a variable of the `null` type or to cast to the `null`  
type. The `null` represents a `null` reference, one that does not refer to any  
object. The `null` is the default value of reference-type variables. Primitive  
types cannot be assigned a `null` literal.  

In different contexts, the `null` means an absence of an object, an unknown  
value, or an uninitialized state.  

```java
import java.util.Random;

String getName() {

    Random r = new Random();
    boolean n = r.nextBoolean();

    if (n == true) {

        return "John";
    } else {

        return null;
    }
}

void main() {

    String name = getName();
    System.out.println(name);
    System.out.println(null == null);

    if ("John".equals(name)) {

        System.out.println("His name is John");
    }
}
```

We work with the `null` value in the program.


## Default values

Uninitialized fields are given default values by the compiler. Final fields and  
local variables must be initialized by developers.  

The following table shows the default values for different types.  

Here is the data you provided in a markdown table format:  

| Data type | Default value |
|-----------|---------------|
| byte      | 0             |
| char      | '\u0000'      |
| short     | 0             |
| int       | 0             |
| long      | 0L            |
| float     | 0f            |
| double    | 0d            |
| Object    | null          |
| boolean   | false         |

Table: Default values for uninitialized instance variables  

The next example will print the default values of the uninitialized instance  
variables. An instance variable is a variable defined in a class for which each  
instantiated object of the class has a separate copy.  

```java
byte b;
char c;
short s;
int i;
float f;
double d;
String str;
Object o;

void main() {

    System.out.println(b);
    System.out.println(c);
    System.out.println(s);
    System.out.println(i);
    System.out.println(f);
    System.out.println(d);
    System.out.println(str);
    System.out.println(o);
}
```

In the example, we declare eight member fields. They are not initialized. The  
compiler will set a default value for each of the fields.  

## Type conversions

We often work with multiple data types at once. Converting one data type to  
another one is a common job in programming. The term type conversion refers to  
changing of an entity of one data type into another. In this section, we deal  
with conversions of primitive data types. Reference type conversions will be  
mentioned later in this chapter. The rules for conversions are complex; they are  
specified in chapter 5 of the Java language specification.  

There are two types of conversions: *implicit* and *explicit*. Implicit type  
conversion, also known as coercion, is an automatic type conversion by the  
compiler. In explicit conversion the programmer directly specifies the  
converting type inside a pair of round brackets. Explicit conversion is called  
type casting.  

Conversions happen in different contexts: assignments, expressions, or   
method invocations.

```java
int x = 456;
long y = 34523L;
float z = 3.455f;
double w = 6354.3425d;
```

In these four assignments, no conversion takes place. Each of the variables is  
assigned a literal of the expected type.  

```java
int x = 345;
long y = x;

float m = 22.3354f;
double n = m;
```

In this code two conversions are performed by Java compiler implicitly.  
Assigning a variable of a smaller type to a variable of a larger type is legal.  
The conversion is considered safe, as no precision is lost. This kind of  
conversion is called implicit widening conversion.  

```java
long x = 345;
int y = (int) x;

double m = 22.3354d;
float n = (float) m;
```

Assigning variables of larger type to smaller type is not legal in Java. Even if  
the values themselves fit into the range of the smaller type. In this case it is  
possible to loose precision. To allow such assignments, we have to use the type  
casting operation. This way the programmer says that he is doing it on purpose  
and that he is aware of the fact that there might be some precision lost. This  
kind of conversion is called explicit narrowing conversion.  

```java
byte a = 123;
short b = 23532;
```

In this case, we deal with a specific type of assignment conversion. 123 and  
23532 are integer literals, the a, b variables are of byte and short type. It is  
possible to use the casting operation, but it is not required. The literals can  
be represented in their variables on the left side of the assignment. We deal  
with implicit narrowing conversion.  

```java
private static byte calc(byte x) {
...
}

byte b = calc((byte) 5);
```
The above rule only applies to assignments. When we pass an integer literal to a  
method that expects a byte, we have to perform the casting operation.  

## Numeric promotions

Numeric promotion is a specific type of an implicit type conversion. It takes  
place in arithmetic expressions. Numeric promotions are used to convert the  
operands of a numeric operator to a common type so that an operation can be  
performed.  

```java
int x = 3;
double y = 2.5;
double z = x + y;
```

In the third line we have an addition expression. The `x` operand is int, the `y`  
operand is double. The compiler converts the integer to double value and adds  
the two numbers. The result is a double. It is a case of implicit widening  
primitive conversion.  

```java
byte a = 120;
a = a + 1; // compilation error
```

This code leads to a compile time error. In the right side of the second line,  
we have a byte variable a and an integer literal 1. The variable is converted to  
integer and the values are added. The result is an integer. Later, the compiler  
tries to assign the value to the a variable. Assigning larger types to smaller  
types is not possible without an explicit cast operator. Therefore we receive a  
compile time error.  

```java
byte a = 120;
a = (byte) (a + 1);
```

This code does compile. Note the usage of round brackets for the `a + 1`  
expression. The (byte) casting operator has a higher precedence than the  
addition operator. If we want to apply the casting on the whole expression, we  
have to use round brackets.  

```java
byte a = 120;
a += 5;
```

Compound operators perform implicit conversions automatically.  

```java
short r = 21;
short s = (short) -r;
```

Applying the `+` or `-` unary operator on a variable a unary numberic promotion  
is performed. The short type is promoted to int type. Therefore we must use the  
casting operator for the assignment to pass.  

```java
byte u = 100;
byte v = u++;
```

In case of the unary increment `++`, decrement `--` operators, no conversion is  
done. The casting is not necessary.  
