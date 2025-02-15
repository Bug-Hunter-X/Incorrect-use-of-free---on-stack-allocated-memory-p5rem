# Incorrect use of free() on stack-allocated memory

This repository demonstrates a common error in C programming: attempting to free memory allocated on the stack using the `free()` function.  The `free()` function is designed for dynamically allocated memory obtained using functions like `malloc()`, `calloc()`, or `realloc()`.  Attempting to use `free()` on stack-allocated memory (like local variables) leads to undefined behavior and potential crashes.

The `bug.c` file contains the erroneous code.  The `bugSolution.c` file provides a corrected version.

## How to reproduce

1. Compile `bug.c` using a C compiler (like GCC): `gcc bug.c -o bug`
2. Run the executable: `./bug`
3. The program might crash or exhibit unpredictable behavior.

## How to fix

The solution is to remove the `free(ptr);` line from the code. Stack-allocated memory is automatically managed by the system when the function ends, so manual freeing isn't needed (and is harmful).