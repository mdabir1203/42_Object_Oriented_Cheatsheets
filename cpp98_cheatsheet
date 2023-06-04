from fpdf import FPDF

class PDFCheatsheet(FPDF):
    def __init__(self):
        super().__init__()
        self.page_width = 210  # Page width in mm (A4 size)
        self.page_height = 297  # Page height in mm (A4 size)
        self.margin = 10  # Margin in mm


class CheatsheetPDF(FPDF):
    def __init__(self):
        super().__init__()
        self.add_page()
        self.set_font('Arial', 'B', 12)
        self.cell(0, 10, 'C++ Cheatsheet', align='C')
        self.ln(10)
        self.set_font('Courier', '', 10)
        self.line_height = 5
        self.max_lines_per_page = 60  # Adjust this value as needed
        self.current_line = 0

    def add_cheatsheet(self, title, code):
        lines = code.split('\n')
        # Add title
        self.set_font('Arial', 'I', 10)
        self.cell(0, 10, title, align='L')
        self.ln(10)

        # Add code
        for line in lines:
            if line.startswith('//'):
                self.set_text_color(0, 0, 255)  # Set color for comments
            else:
                self.set_text_color(0)  # Set color back to default

            self.cell(0, self.line_height, line)
            self.ln(self.line_height)

        # Add spacing after the section
        self.ln(10)

pdf = CheatsheetPDF()

pdf.add_cheatsheet("Preprocessor", """
// Comment to end of line
/* Multi-line comment */
#include  <stdio.h>         // Insert standard header file
#include "myfile.h"         // Insert file in current directory
#define X some text         // Replace X with some text
#define F(a,b) a+b          // Replace F(1,2) with 1+2
""")

pdf.add_cheatsheet("Literals", """
255, 0377, 0xff             // Integers (decimal, octal, hex)
123.0                      // double (real) numbers
'a'                        // Character (literal)
'\\n', '\\\\', '\\'', '\\"' // Newline, backslash, single quote, double quote
\"string\\n\"              // Array of characters ending with newline and \\0
\"hello\" \"world\"         // Concatenated strings
""")

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

pdf.add_cheatsheet("Functions", """
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



pdf.add_cheatsheet("Classes", """

class T {                   // A new type
private:                    // Section accessible only to T's member functions
    int x;                  // Member data
public:                     // Accessible to all
    void f();               // Member function
    void g() { return; }    // Inline member function
    void h() const;         // Does not modify any data members
    int operator+(int y);   // t+y means t.operator+(y)
    int operator-();        // -t means t.operator-()
    T(): x(1) {}            // Constructor with initialization list
    T(const T& t): x(t.x) {}// Copy constructor
    T& operator=(const T& t)
    { x = t.x; return *this; } // Assignment operator
    ~T();                   // Destructor (automatic cleanup routine)
    explicit T(int a);      // Allow t=T(3) but not t=3
    T(float x): T((int)x) {}// Delegate constructor to T(int)
    operator int() const
    { return x; }           // Allows int(t)
    static int y;           // Data shared by all T objects
    static void l();        // Shared code. May access y but not x
    class Z {};             // Nested class T::Z
    typedef int V;          // T::V means int
};

void T::f() {               // Code for member function f of class T
    this->x = x;            // this is the address of self (means x=x;)
}

int T::operator+(int y) {
    return x + y;
}

int T::operator-() {
    return -x;
}

void T::h() const {
    // Implementation of h()
}

T::~T() {
    // Destructor implementation
}

explicit T::T(int a) {
    // Constructor implementation
}

void T::l() {
    // Implementation of static member function l()
}

void i();                   // Declaration of global function i()

class U;                    // Forward declaration of class U

class U: public T {         // Derived class U inherits all members of base T
public:
    void g(int);            // Override method g
};

void U::g(int) {
    // Implementation of overridden method g
}

class V: private T {};      // Inherited members of T become private

class W: public T, public U {
    // Multiple inheritance
};

class X: public virtual T {
    // Classes derived from X have base T directly
};



//All classes have a default copy constructor, assignment operator, and 
//destructor, which perform the corresponding operations on each data member and
//each base class as shown above. There is also a default no-argument constructor
//(required to create arrays) if the class has no constructors. Constructors,
//assignment, and destructors do not inherit.


""")


pdf.add_cheatsheet("Templates", """

template <class T> T f(T t);// Overload f for all types
template <class T> class X {// Class with type parameter T
  X(T t); };                // A constructor
template <class T> X<T>::X(T t) {}
                            // Definition of constructor
X<int> x(3);                // An object of type "X of int"
template <class T, class U=T, int n=0>
                            // Template with default parameters")

""")

pdf.add_cheatsheet("Namespaces", """

Namespaces
namespace N {class T {};}   // Hide name T
N::T t;                     // Use name T in namespace N
using namespace N;          // Make T visible without N::

""")

pdf.add_cheatsheet("Memor(dynamic memory management)", """

memory 
#include <memory>           // Include memory (std namespace)

auto_ptr<int> x;         // Empty auto_ptr to an integer on heap. 
                         //   Provides basic ownership transfer.

x = auto_ptr<int>(new int(12)); // Allocate value 12 on heap

auto_ptr<int> y = x;        // Transfer ownership from x to y. x becomes empty.
cout << *y;                 // Dereference y to print '12'

if (y.get() == x.get()) {   // Raw pointers (here x == y)
    cout << "Same";  
}  

y.reset();                  // Reset y, releases ownership and deletes the object

if (y.get() != x.get()) { 
    cout << "Different";  
}  

if (y.get() == NULL) {      // Compare against NULL (here returns true)
    cout << "Empty";  
}  

y = auto_ptr<int>(new int(15));   // Assign new value
cout << *y;                 // Dereference y to print '15'
cout << *x;                 // Dereference x to print 'undefined' (x is now empty)

auto_ptr<B> t;
auto_ptr<B> r;
r = auto_ptr<B>(dynamic_cast<B*>(t.get())); // Converts t to an auto_ptr<B>

""" )


pdf.add_cheatsheet("math.h, cmath (floating point math)", """

#include <cmath>            // Include cmath (std namespace)
sin(x); cos(x); tan(x);     // Trig functions, x (double) is in radians
asin(x); acos(x); atan(x);  // Inverses
atan2(y, x);                // atan(y/x)
sinh(x); cosh(x); tanh(x);  // Hyperbolic sin, cos, tan functions
exp(x); log(x); log10(x);   // e to the x, log base e, log base 10
pow(x, y); sqrt(x);         // x to the y, square root
ceil(x); floor(x);          // Round up or down (as a double)
fabs(x); fmod(x, y);        // Absolute value, x mod y
""")

pdf.add_cheatsheet("assert.h", """

#include <cassert>        // Include assert (std namespace)

int main() {
    int x = 5;
    assert(x == 5);      // If x is not equal to 5, assert will print a message and abort

    #define NDEBUG       // Turn off assert (must be defined before including <cassert>)
    #include <cassert>   // Include assert again to apply the NDEBUG macro

    assert(x == 10);     // Since NDEBUG is defined, this assert will not have any effect

    return 0;
}

""")


pdf.output('c++98_cheatsheet.pdf', 'F')
