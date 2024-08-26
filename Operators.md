## Mathematical

| Operator | Name     | Desc                                             |
| -------- | -------- | ------------------------------------------------ |
| **+**    | Add      | Binary - Add two numbers                         |
| **-**    | Subtract | Binary - Subtract two numbers                    |
| **/**    | Divide   | Binary - Divide two numbers                      |
| **\* **  | Multiply | Binary - Multiply two numbers together           |
| **%**    | Modulus  | Binary - The remainder after an integer devision |

## Bitwise

| Operator | Name | Desc                                         |
| -------- | ---- | -------------------------------------------- |
| **&**    | And  | Binary - Bitwise AND two integers            |
| **^**    | Xor  | Binary - Bitwise XOR two integers            |
| **\|**   | Or   | Binary - Bitwise OR two integers             |
| **!**    | Not  | Unary - Gets the Bitwise not for an integers |

## Types

| Operator | Name        | Desc                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| -------- | ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| &        | Reference   | When used as a unary with an object, gets a reference to an object.<br><br>When used as a unary on a type denotes that the type is a reference to an object.                                                                                                                                                                                                                                                                                                                                                             |
| \*       | Dereference | When used as a unary on an **referenced object**, will dereference that object.<br>When used as a unary on a type denotes that the type is a **raw pointer**.<br>When used as a unary on a **raw pointer**, will either lookup or set that pointer. <br><br>The difference between a reference object and a raw pointer is that raw pointers are ignored bu garbage collection, along with the fact pointer arithmetic will be enabled. Pointers also can be cast too and from usize and isize without loss of data.<br> |
| \[...]   | Array       | When used with a single type, denotes an array of that type.<br>When used with multiple types, denote a tuple with those types.                                                                                                                                                                                                                                                                                                                                                                                          |
| (...)    | Inline enum | When containing a value, the result *could* be any of those types.<br>Ex: `(i8, i16, i32)`<br><br>When used with empty brackets, denotes a [Unit type](https://en.wikipedia.org/wiki/Unit_type), aka no data.                                                                                                                                                                                                                                                                                                            |
|          |             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |