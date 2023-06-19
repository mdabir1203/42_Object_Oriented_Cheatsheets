# 42_Object_Oriented_Cheatsheets

## Cheatsheet for C++98 standard as we have to follow the standard based on the subject

`c

## Headers
// Comment to end of line
/* Multi-line comment */
#include  <stdio.h>         // Insert standard header file
#include "myfile.h"         // Insert file in current directory
#define X some text         // Replace X with some text
#define F(a,b) a+b          // Replace F(1,2) with 1+2
""")
``
```c

## Literals
255, 0377, 0xff             // Integers (decimal, octal, hex)
123.0                      // double (real) numbers
'a'                        // Character (literal)
'\\n', '\\\\', '\\'', '\\"' // Newline, backslash, single quote, double quote
\"string\\n\"              // Array of characters ending with newline and \\0
\"hello\" \"world\"         // Concatenated strings
""")

´´´

```c

pdf.add_cheatsheet("Declarations", """
int x;                      // Declare x to be an integer (value undefined)
int x=255;                  // Declare and initialize x to 255
short s; long l;            // Usually 16 or 32 bit integer (int may be either)
char c='a';                 // Usually 8 bit character
unsigned char u=255;
signed char s=-1;           // char might be either
unsigned long x =
  0xffffffffUL;             // short, int, long are signed
float f; double d;          // Single or double precision real (never unsigned)
bool b=true;                // true or false, may also use int (1 or 0)
int a, b, c;                // Multiple declarations
int a[10];                  // Array of 10 ints (a[0] through a[9])
int a[]={0,1,2};            // Initialized array (or a[3]={0,1,2}; )
char s[]="hello";           // String (6 elements including '\\0')
typedef char* String;       // Typedef: String is an alias for char*
enum weekend {SAT,SUN};     // weekend is a type with values SAT and SUN
enum weekend day;           // day is a variable of type weekend
enum weekend{SAT=0,SUN=1};  // Explicit representation as int
""")

´´´


´´´c

pdf.add_cheatsheet("Storage Classes", """
int x;                      // Auto (memory exists only while in scope)
static int x;               // Global lifetime even if local scope
extern int x;               // Information only, declared elsewhere
""")

pdf.add_cheatsheet("Statements", """
x=y;                        // Every expression is a statement
int x;                      // Declarations are statements
;                           // Empty statement
{                           // A block is a single statement
    int x;                  // Scope of x is from declaration to end of block
}
if (x) a;                   // If x is true (not 0), evaluate a
else if (y) b;              // If not x and y (optional, may be repeated)
else c;                     // If not x and not y (optional)

while (x) a;                // Repeat 0 or more times while x is true

for (x; y; z) a;            // Equivalent to: x; while(y) {a; z;}

do a; while (x);            // Equivalent to: a; while(x) a;

switch (x) {                // x must be int
    case X1: a;             // If x == X1 (must be a const), jump here
    case X2: b;             // Else if x == X2, jump here
    default: c;             // Else jump here (optional)
}
break;                      // Jump out of while, do, or for loop, or switch
continue;                   // Jump to the bottom of while, do, or for loop
return x;                   // Return x from function to caller
""")

```

```c

`##pdf.add_cheatsheet("Functions", """


int f(int x, int y);        // f is a function taking 2 ints and returning int
void f();                   // f is a procedure taking no arguments
void f(int a=0);            // f() is equivalent to f(0)
int f();                    // Default return type is int
inline void f();            // Optimize for speed
void f() { statements; }    // Function definition (must be global)
T operator+(T x, T y);      // a+b (if type T) calls operator+(a, b)
T operator-(T x);           // -a calls function operator-(a)
T operator++(int);          // postfix ++ or -- (parameter ignored)
extern "C" { void f(); }    // f() was compiled in C
""")

```

# Add additional information about main function
pdf.add_cheatsheet("Functions", """
int main() { statements... }                     // or
int main(int argc, char* argv[]) { statements... }
// argv is an array of argc strings from the command line.
// By convention, main returns status 0 if successful, 1 or higher for errors.
""")

# Add information about function overloading and operators
pdf.add_cheatsheet("Functions", """
//  Function parameters and return values may be of any type.
//  A function must either be declared or defined before it is used.
   It may be declared first and defined later. 
// Every program consists of a set of global variable declarations and a set of 
   function definitions (possibly in separate files), one of which must be:

// Overloading functions with different parameters
void foo(int x);
void foo(double x);

// Operator overloading
T operator+(T x, T y);      // a+b (if type T) calls operator+(a, b)
T operator-(T x);           // -a calls function operator-(a)
T operator++(int);          // postfix ++ or -- (parameter ignored)
""")

# Add note about new operators not being creatable
pdf.add_cheatsheet("Functions", """
// Operators except :: . .* ?: may be overloaded.
// Precedence order is not affected.
// New operators may not be created.
""")

# Add note on Expressions

pdf.add_cheatsheet("Expressions", """
T::X                        // Name X defined in class T
N::X                        // Name X defined in namespace N
::X                         // Global name X

t.x                         // Member x of struct or class t
p->x                        // Member x of struct or class pointed to by p
a[i]                        // i'th element of array a
f(x, y)                     // Call to function f with arguments x and y
T(x, y)                     // Object of class T initialized with x and y
x++                         // Add 1 to x, evaluates to original x (postfix)
x--                         // Subtract 1 from x, evaluates to original x
typeid(x)                   // Type of x
typeid(T)                   // Equals typeid(x) if x is a T
dynamic_cast<T>(x)          // Converts x to a T, checked at run time.
static_cast<T>(x)           // Converts x to a T, not checked
reinterpret_cast<T>(x)      // Interpret bits of x as a T
const_cast<T>(x)            // Converts x to same type T but not const

sizeof x                    // Number of bytes used to represent object x
sizeof(T)                   // Number of bytes to represent type T
++x                         // Add 1 to x, evaluates to new value (prefix)
--x                         // Subtract 1 from x, evaluates to new value
~x                          // Bitwise complement of x
!x                          // true if x is 0, else false (1 or 0 in C)
-x                          // Unary minus
+x                          // Unary plus (default)
&x                          // Address of x
*p                          // Contents of address p (*&x equals x)
new T                       // Address of newly allocated T object
new T(x, y)                 // Address of a T initialized with x, y
new T[x]                    // Address of allocated n-element array of T
delete p                    // Destroy and free object at address p
delete[] p                  // Destroy and free array of objects at p
(T) x                       // Convert x to T (obsolete, use static_cast<T>(x))

x * y                       // Multiply
x / y                       // Divide (integers round toward 0)
x % y                       // Modulo (result has sign of x)

x + y                       // Add, or &x[y]
x - y                       // Subtract, or number of elements from *x to *y
x << y                      // x shifted y bits to the left (x * pow(2, y))
x >> y                      // x shifted y bits to the right (x / pow(2, y))

x < y                       // Less than
x <= y                      // Less than or equal to
x > y                       // Greater than
x >= y                      // Greater than or equal to

x & y                       // Bitwise and (3 & 6 is 2)
x ^ y                       // Bitwise exclusive or (3 ^ 6 is 5)
x | y                       // Bitwise or (3 | 6 is 7)
x && y                      // x and then y (evaluates y only if x (not 0))
x || y                      // x or else y (evaluates y only if x is false (0))
x = y                       // Assign y to x, returns new value of x
x += y                      // x = x + y, also -= *= /= <<= >>= &= |= ^=
x ? y : z                   // y if x is true (nonzero), else z
throw x                     // Throw exception, aborts if not caught
x , y                       // evaluates x and y, returns y (seldom used))



""")

´´´













--------------------------------------------------------------------------------------------------------------------------------------------
## Sample Photo:

![image](https://github.com/mdabir1203/42_Object_Oriented_Cheatsheets/assets/66947064/b4b11350-0801-4290-8301-28179d174366)

--------------------------------------------------------------------------------------------------------------------------------------------
## [Download Pdf](https://github.com/mdabir1203/42_Object_Oriented_Cheatsheets/files/11644703/c%2B%2B98_cheatsheet.15.pdf)


-------------------------------------------------------------------------------------------------------------------------------
If you find anything missing or wrong please feel free to add a pull request

---------------------------------------------------------------------------------------------------------------------------------------
1. For modifications : look into the class function call "pdf.addCheatsheet" and modify it. 
2. Run `pip install pypdf`
3. Then run `python cpp98_cheatsheet.py`
------------------------------------------------------------------------------------------------------------------------

## Things to add up : 
Feel free to suggest or write a github issue.

--- Inspired from this guy : https://github.com/mortennobel/cpp-cheatsheet


# If this makes your life easy . Feel free to give a sponsor or fund me through a project of yours Your help will be appreciated with gratitude and prayers
