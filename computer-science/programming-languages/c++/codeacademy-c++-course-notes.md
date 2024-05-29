# Codeacademy C++ course notes

## Intro

C++ is a compiled, strongly typed language.

<figure><img src="../../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

To print on terminal:

```cpp
std::cout << "Something\n";
```

Basic structure

```cpp
#include <iostream> // Pre-processor directive, includes library iostream
int main() { // Required function
   // Single-line comment
   /*
   Multiple-line comment
   */
   const double quarter = 0.25; // Constant variables cannot be changed during execution (const)
   int score = 0; // Declare and initialize int variable, type(int) - name(score) - end of statement(;)
   std::cin >> score; // User input assigned to the variable score
   std::cout << "Hello World!" << score << "\n"; // Print to terminal
   
   // Cast or type conversion
   double weight1;
   int weight2;

   weight1 = 154.49;
   weight2 = (int) weight1; // weight2 is now 154 as an integer
   
   return 0; // Returning 0 indicates the operating system that the code executed successfully. Optional
}
```

To compile:

```bash
g++ name-of-the-file.cpp -o name-of-the-output
./name-of-the-output
# If output name is not given, the default is a.out
# To link more than one file
g++ name-of-the-file.cpp functions.cpp -o name-of-the-output
./name-of-the-output
```

Basic data types:\
\- int: integer\
\- double: floating-point numbers\
\- char: individual characters\
\- string: sequence of characters\
\- bool: true/false values

Datatype modifies:\
\- signed\
\- unsigned\
\- short\
\- long

Arithmetic operators:\
\- +: addition\
\- -: substraction\
\- \*: multiplication\
\- /: division\
\- %: modulo (divides and gives the remainder)

Conditionals:\
\- if, else if, else\
\- switch

Relational operators:\
\- ==\
\- !=\
\- >\
\- <\
\- >=\
\- <=

Logical operators:\
\- &&\
\- ||\
\- !

Loops:\
\- while\
\- for

Errors:\
\- Compile-time errors\
\- Link-time errors\
\- Run-time errors\
\- Logic errors

### Vectors

```cpp
#include <vector>

int main() {
    std::vector<type> variable_name1 // Any type, declare
    std::vector<double> variable_name2 = {1, 2 , 3}; // Initialization with values
    std::vector<double> variable_name3(3); // Initialization only with amount of elements
    variable_name2[0]; // Accessing vector element on index
    variable_name2.push_back(4); // Add a space and an element at the end of the vector e.g: {1, 2, 3, 4}
    variable_name2.pop_back(); // Remove elements at the end of the vector e.g: {1, 2, 3}
    variable_name2.size(); // Size. e.g: 3
}
```

### Arrays

The main difference with vectors is the size cannot be changed. Lower-level constructs.

```cpp
int main() {
    int favoriteNums[4]; // Declaration including size
    int favoriteNums[] = {7, 9, 15, 16}; // Initialization
    favoriteNums[0]; // Accessing array element on index
}
```

### Functions

Also known as methods or procedures.

```cpp
#include <cmath> // To include math functions

return_type function_name(parameterType parameter) { // Return type can be std::string and std::vector as well
    return output;
}

void function_name(parameters) { // Function with no return uses void
    // also called subroutine
}

void function_name(int param1, int param2 = 1) {
    // param1 required, param2 optional with default 1
    // Required params comes first
}

// Function overload depending on type, functions with the same name, 
// different behavior depending on arguments passed (types or amount)
void print_cat_ears(char let) {
  std::cout << " " << let << "   " << let << " " << "\n";
  std::cout << let << let << let << " " << let << let << let << "\n";
}

void print_cat_ears(int num) {
  std::cout << " " << num << "   " << num << " " << "\n";
  std::cout << num << num << num << " " << num << num << num << "\n";
}
print_cat_ears('A');
print_cat_ears(4);
```

### Scope

```cpp
#include <iostream>

std::string sea_animal = "manatee"; // Variable defined on global scope
void favorite_animal(std::string best_animal) {
  std::string animal = best_animal; // Variable defined on local scope, only accessible inside the function
  std::cout << "Best animal: " << animal << "\n";
}

int main() {
  favorite_animal("jaguar");
  std::cout << sea_animal << "\n";
  std::cout << animal << "\n";
}
```

### Importing

```cpp
// main.cpp
#include "fns.hpp"

int main() {
    myFunction(0);
}

// Calling a template
print_cat_ears(2);
print_cat_ears("a");
```

```cpp
// Header
// fns.hpp or fns.h
int myFunction(int number);
// Can include inline functions
// Default parameters comes in here

// Function templates, add data types as parameters, are entirely created on header files

template <typename T>
void print_cat_ears(T item) {
  std::cout << " " << item << "   " << item << " " << "\n";
  std::cout << item << item << item << " " << item << item << item << "\n";
}
```

```cpp
// fns.cpp
int myFunction(int number) {
    return number;
};
```

To compile

```bash
g++ main.cpp fns.cpp -o name-of-the-output
```

### Classes

User-defined types. Servers as a blueprint for objects which are instances of the class. Declaration goes on headers.

<pre class="language-cpp"><code class="lang-cpp">// city.hpp
class City {
  int population; // Attribute, private as well
  std::string name;

<strong>public: // By default everything in the class is private, everything inside public is accessible outside of the class
</strong>  City(std::string new_name, int new_population); // Constructor
  ~City; // Destructor
  int get_population(); // method

//It's possible to add private here as well.
private:
  int another_one;  
};
</code></pre>

```cpp
// city.cpp
#include "city.hpp" // include the header

int City::get_population() {
  return population;
}

// Constructor, same name as the class and no return type. Instantiate an object
// with specific attributes
City::City(std::string new_name, int new_pop) {
  name = new_name;
  population = new_pop;
}
// OR
City::City(std::string new_name, int new_pop)
  // members get initialized to values passed in 
  : name(new_name), population(new_pop) {}
  
// Destructor, housekeeping and preventing memory leaks
// Will be called automatically when:
// - The object moves out of scope.
// - The object is explicitly deleted.
// - When the program ends.
City::~City() {
  // Something, if necessary.
}
```

```cpp
// main.cpp
#include "city.hpp"

void main() {
    City ankara("Ankara", 5445000);
}
```

### Object-oriented programming

Benefits:

* **Encapsulation:** in OOP, you bundle code into a single unit where you can determine the scope of each piece of data.
* **Abstraction:** by using classes, you are able to generalize your object types, simplifying your program.
* **Inheritance:** because a class can inherit attributes and behaviors from another class, you are able to reuse more code.
* **Polymorphism:** one class can be used to create many objects, all from the same flexible piece of code.

### References

```cpp
#include <iostream>

void my_function(int &i){} // Pass variable by reference
void my_function(int i){} // Pass variable by value

int triple(int const &i) { // That const will prevent that we change the value
// and the reference would prevent making a copy of the argument.
  return i * 3;
}

int main() {
  int soda = 99;
  int &pop = soda; // Reference variable is an alias for something else, & in declaration
  // 1. Anything we do to the reference also happens to the original.
  // 2. Aliases cannot be changed to alias something else.
  // Used to pass original variables to functions, two reasons:
  // 1. Modify the value of the function arguments.
  // 2. Avoid making copies of a variable/object for performance reasons.
  
  std::cout << &soda << "\n"; // Printing the memory address of the soda variable, & not in declaration
}
```

### Pointers

Inheritance from C, avoid as much as possible. Pointers are variables that store the memory address of the original variable.

```cpp
#include <iostream>

int main() {
  int power = 9000;
  int* ptr = &power; // * for pointer, &variable to retrieve the variable's memory address
  int blah = *ptr; // * Dereference operator to obtain the value pointed to by a variable
  
  int* ptr2; // Address of somewhere.
  int* ptr3 = nullptr; // Keyword, typesafe pointer value representing empty pointer.
}
```

### Manual memory management

```cpp
ptr = new int[num]; // Memory allocated
delete ptr; // Memory released

// Smart pointers
// unique_ptr: a smart pointer that owns and manages another object through and 
// disposes of that object when the unique_ptr goes out of scope.
// shared_ptr: a smart pointer that retains shared ownership of an object 
// through a pointer. Several shared_ptr objects may own the same object.
```
