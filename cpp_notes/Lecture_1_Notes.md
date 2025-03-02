
## Based on the class Introduction to C++ and Object Oriented Programming 2024 taught by Wouter Verkerke (Nikhef) 


## Notes:
* CPP is an OOP language 
* CPP is Fast, strong control over memory use
* **Polymorphism** is the ability to treat objects of different
types the same way
	- Example: Retrieve position at a flight length of 5 cm for different trajectories 
- Different versions of cpp, add flags to activate:
	- In gcc 4.[3456] must add flag ‘-std=c++0x’ to activate 
	- In gcc 4.[78] must add flag ‘-std=c++11’ to activate




## Hello World:

```cpp
// my first program in C++
#include <iostream>
int main () {
std::cout << "Hello World!" << std::endl;
return 0;
} 
```
- comments in cpp are `//`
- lines starting with a `#` are directives for the preprocessor 
	- how cpp does import statements 
- functions are defined with `int name () { function code here }`
	- the main function can take command line options naturally

- `std::cout << "string""`
	- `cout` means printing to standard output 
	- The names std::cout and std::endl are declared in the ‘header file’ included through the ‘#include ’ preprocessor directive.
	- `std::endl` directive represents the ‘carriage return /
	


## Data Types
* Variables need to be declared with what data type, some examples are:
	* More advanced types are in the "standard library"

| Type                      | Description                                              |
|---------------------------|----------------------------------------------------------|
| `char`                    | ASCII character, 1 byte                                  |
| `int`, `signed int`, `unsigned int`, `short int`, `long int` | Integer. Can be signed, unsigned, long or short. Size varies and depends on CPU architecture (2, 4, 8 bytes) |
| `float`, `double`         | Floating point number, single and double precision      |
| `bool`                    | Boolean, can be true or false (1 byte)                  |
| `enum`                    | Integer with a limited set of named states, e.g., `enum fruit { apple, pear, citrus }` or `enum fruit { apple=0, pear=1, citrus }` |

	
* Uses `{}` often


## Defining data objects - variables:

```cpp
int main() { int j ; // definition – initial value undefined
int k = 0 ; // definition with assignment initialization
int l(0) ; // definition with constructor initialization
int m = k + l ; // initializer can be any valid C++ expression
int a,b=0,c(b+5); // multiple declaration – a,b,c all integers }

// You can also define constants
const float pi = 3.14159268 ; // constant data object, must be initalized 
const int n = 3 

// Literal Constants for integer types
int j = 16 ; // decimal
int j = 0xF ; // hexadecimal (leading 0x)
int j = 020 ; // octal (leading 0)
unsigned int k = 4294967280U ; // unsigned literal


// Literal constants for character types
// just the single char, not a string
char ch = ‘A’ ; // Use single quotes


// Auto declaration type (C++ 2011)
// In C++ 2011, you can also omit an explicit type in
// declarations of objects that are immediately initialized
auto j = 16 ; // j is integer
auto j = 2.3 ; // j is double
auto j = true ; // j is bool

```

* Hex, octal literals good for bit patterns( hex digit = 4 bits, octal digit = 3 bits)
* Unsigned literals good for numbers that are too large for signed integers (e.g. between 2^32/2 and 2^32-1)
* What does it mean for an int to be signed?


## Arrays:

```cpp
// Defining arrays
// Array dimensions in definition must be constants
// cpp is 0 indexed

Type name[size] ;
Type name[size1][size2]…[sizeN] ;

const int n=3 ;
float x[n] ; // x is an array 

float x[3] = { 0.0, 5.7 , 2.3 } ; // x is an array with given values
```


## Declaration versus definition of data:

Defining variables is two fold:
* allocate memory for object
* assigning a name to call that memory space => no longer exists when the program is compiled 


## References:
* C++ allows to create ‘alias names’, a different symbolic name referencing an already allocated data object
* This sounds like a shallow copy? points at the same memory



```cpp

‘Type& name = othername’ // This is the syntax

// Example:
int x ; // Allocation of memory for int 
        // and declaration of name ‘x’ 
int& y = x ; // Declaration of alias name ‘y’ 
             // for memory referenced by ‘x’ 

x = 3 ; cout << x << endl ; // prints ‘3’ 
cout << y << endl ; // also prints ‘3’
```


## Pointers:
* Pointer is a variable that contains a memory address
* Somewhat similar to a reference in functionality, but fundamentally different in nature: a pointer is always an object in memory itself
* Definition: `‘TYPE* name’` makes pointer to data of type `TYPE`


Working with pointers:
– Operator & takes memory address of symbol object (=pointer value)
– Operator * turns memory address (=pointer value) into symbol object



Example:
```cpp
// Creating and reading through pointers
int x = 3, y = 4 ;
int* px ; // allocate px of type ‘pointer to integer’
px = &x ; // assign ‘memory address of x’ to pointer px

cout << px << endl ; // Prints 0x3564353, memory address of x
cout << *px << endl ;// Prints 3, value of x, object pointed to by px


// Modifying pointers and objects pointed to 
*px = 5 ; // Change value of object pointed to by px (=x) ;
cout << x << endl ; // Prints 5 (since changed through px)
px = &y ; // Reseat pointer to point to symbol named ‘y’
cout << px << endl ; // Prints 0x4863813, memory address of y
cout << *px << endl ;// Prints 4, value of y, object pointed to by px

```

Pointers are Fundamentally related to arrays:

- Pointer `(pa+1)` points to next element of an array
- This works regardless of the type in the array
* In fact a itself is a pointer of type int* pointing to a[0]
* The Basic Rule for arrays and pointers:  `a[i]` is equivalent to `*(a+i)` ???

```cpp 
int a[3] = { 1,2,3} ; // Allocates array of 3 integers 
int* pa = &a[0] ; // Pointer pa now points to a[0] 
cout << *pa << endl ; // Prints ‘1’ cout << *(pa+1) << endl ; // Prints ‘2’
```


## Pointers and arrays of char – strings
- `char[]` holds strings and is therefore most commonly used array
- Initialization of character arrays:
	- String literals in double quotes are of type ‘`char *`’, i.e. `const char* blah = “querty”;` is equivalent to `const char tmp[7] = {‘q’,’w’,’e’,’r’,’t’,’y’,0} ;
const char* blah = tmp ;`

* character arrays are ended with the null char `\0`
* you can detect the end of the string, without knowing the original defintion


##On slide 21

## Strings, and string manipulation 
