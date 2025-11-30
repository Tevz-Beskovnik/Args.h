ARGS
==========

A all in one, single file argument parsing library for C++.

## Inclusion

To include the library into your project define the required `args.h` defines. Make sure they are places above the include statement as shown bellow:

```cpp
#define ARGS_INIT
#define ARGS_LIST \
    BOOLEAN_ARG(foo, "bar")

#define ARGS_PROGRAM_DESCRIPTION "This is a test program"

#include "args.h"
```

> **_NOTE:_**  If not defined `args.h` defines a very bare bones set of initializing defines to avoid errors.

## Usage

Argument definitions are implemented in they style of c macros and all go into the base `ARGS_LIST` macro. `args.h` provides 4 different argument types:
- Required arguments,
- optional arguments, with default values,
- list arguments,
- boolean arguments 

**Required argument:**

`REQUIRED_ARG({parameter name}, {type}, {description})`

```cpp
#define ARGS_LIST \
    REQUIRED_ARG(file, std::string, "Input file to be processed")
```

**Optional argument:**

`OPTIONAL_ARG({parameter name}, {type}, {description}, {default value})`

```cpp
#define ARGS_LIST \
    OPTIONAL_ARG(process, int, "Process type to use {1, 2, 3}", 1)
```

**Boolean argument:**

`BOOLEAN_ARG({parameter name}, { description})`

```cpp
#define ARGS_LIST \
    BOOLEAN_ARG(help, "Print this message")
```

**List argument:**

`LIST_ARG({parameter name}, {type}, {description}, {required})`

```cpp
#define ARGS_LIST \
    LIST_ARG(opts, float, "Optional coeffs", false)
```

The library knows nothing more about the arguments then their requirement rules. All other semantic checking should be done after parsing on the users end.

The header provides automatic generation of the help page, the help parameter, and display of it when the requirement rules are not met of if the `--help` flag is in the executable call.

### Parsing arguments



## Supported types

All types that are supported by the `stringstream` operator are supported, everyting else is up to future implementation as my needs see it, or just PR :).

> **_NOTE:_**  Quoted input strings with spaces are not supported, aswell as pointer types. If you need to read a string from the input be sure to use the C++ `std::string` object and not `char *`.

