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
   int score = 0; // Declare and initialize int variable, type(int) - name(score) - end of statement(;)
   std::cin >> score; // User input assigned to the variable score
   std::cout << "Hello World!" << score << "\n"; // Print to terminal
   return 0; // Returning 0 indicates the operating system that the code executed successfully. Optional
}
```

To compile:

```bash
g++ name-of-the-file.cpp -o name-of-the-output
./name-of-the-output
// If output name is not given, the default is a.out
```

Basic data types:\
\- int: integer\
\- double: floating-point numbers\
\- char: individual characters\
\- string: sequence of characters\
\- bool: true/false values

Arithmetic operators:\
\- +: addition\
\- -: substraction\
\- \*: multiplication\
\- /: division\
\- %: modulo (divides and gives the remainder)
