# Header Files

### talk about
- importance of header files
- breaking up code between two files
- `#include`
- header guards & `pragma once`
- what goes in a function header?
  - function prototypes
  - doccumentation
  

## Why do these exist?

Header files serve two purposes for C/C++ prorammers. Firstly, it allows us to propegate function and class declarations to other files without recreating functions in every file we want to use those functions in.

If we have an addition function defined in a `math.cpp` file, and we want to use it in `application.cpp`, adding a `math.hpp` header file would allow us to use the code from `math.cpp` without recreating
