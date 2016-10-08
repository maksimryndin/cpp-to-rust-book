# Let's Start Simple

The usual introduction to any language is "Hello, World!".  A simple programme that prints that message out to the console.

Here is how we might write it for C:

```c
#include <stdio.h>

int main(int argc, char *argv[]) {
  printf("Hello, World!\n");
  return 0;
}
```

We could write it the same way for C++, or we could use the C++ stream classes if we preferred:

```c++
#include <iostream>

using namespace std;

int main(int argc, char *argv[]) {
  cout << "Hello, World!" << endl;
  return 0;
}
```

And here is the equivalent in Rust:

```rust
fn main() {
  println!("Hello, World!");
}
```

There are some obvious points of similarity. Here are some observations.

* C/C++ and Rust follow the convention of having a main() function as the entry point into code. Note that Rust's main doesn't return anything. It's effectively a void method.
* There is a general purpose print statement.
* The general structure in terms of main, use of { } and semi-colons is mostly the same. In both languages a { } represents a block of code and a semi-colon is a separator between statements.
* Rust looks a little bit more terse than either C or C++ because it automatically includes references to part of its standard runtime.

The println!() is actually a macro that expands into code that writes to the standard output. We know it's a macro because it ends in a ! character but you may treat it like a function call for now. We'll see how Rust macros differ to those in C/C++ later.

## Compiling our code

Open a command prompt and set up your compiler environments. In C++ you’d compile your code like this:

```
gcc hw.cpp -o hw (or cl /o hw.exe hw.cpp)
```
And in Rust

```
rustc hw.rs
```

And to run either

```
./hw (or .\hw.exe)
Hello, World!
```

Again there are points of similarity:

* There is a shell command that compiles the code and creates an executable from it.
* The binary runs in the same way.
* In addition but not obvious is that Rust uses the LLVM bitcode compiler to generate its code. So:
  - It shares part of its toolchain with clang and gcc-llvm compilers. The front end is different but the backend is the same.
  - Rust executables are debuggable through gdb or other such debuggers