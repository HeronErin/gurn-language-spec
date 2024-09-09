## Mathematical

| Operator | Name     | Desc                                             |
| -------- | -------- | ------------------------------------------------ |
| +        | Add      | Binary - Add two numbers                         |
| -        | Subtract | Binary - Subtract two numbers                    |
| /        | Divide   | Binary - Divide two numbers                      |
| \*       | Multiply | Binary - Multiply two numbers together           |
| \%       | Modulus  | Binary - The remainder after an integer devision |

## Bitwise

| Operator | Name                 | Desc                                                                                                                                                                 |
| -------- | -------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **&**    | And                  | Binary - Bitwise AND two integers                                                                                                                                    |
| **^**    | Xor                  | Binary - Bitwise XOR two integers                                                                                                                                    |
| **\|**   | Or                   | Binary - Bitwise OR two integers                                                                                                                                     |
| **~**    | Not                  | Unary - Gets the Bitwise not for an integers, and turns a `true` into a `false`<br><br>Note: **Must preceded the operand, otherwise treated as the Error Operator!** |
| <<       | left shift           | Binary - left shift (signed)                                                                                                                                         |
| >>       | right shift          | Binary - right shift  (signed)                                                                                                                                       |
| <<<      | left unsigned shift  | Binary - left shift (unsigned)                                                                                                                                       |
| >>>      | right unsigned shift | Binary - right shift  (insigned)                                                                                                                                     |
## Logical
| Operator | Name                       | Desc                                                                                                                                                                                 |
| -------- | -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| &&       | Logical And                | Binary - Logical AND two values.  <br><br>Works like bitwise AND, however will not execute right branch if left branch is false. The preferred AND method for working with booleans. |
| \|\|     | Logical or                 | Binary - Logical OR two values.  <br><br>Works like bitwise or, however will not execute right branch if left branch is true. The preferred OR method for working with booleans.     |
| >        | Greater than               | Binary - Test if greater than                                                                                                                                                        |
| <        | Lesser than                | Binary - Test if lesser than                                                                                                                                                         |
| <=       | Greater than  or equals to | Binary - Test if greater than or equals to                                                                                                                                           |
| >=       | Lesser than or equals to   | Binary - Test if lesser than or equals to                                                                                                                                            |
| ==       | Is Equal to                | Binary - Test equality                                                                                                                                                               |
## Types

| Operator | Name              | Desc                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| -------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| &        | Reference         | When used as a unary with an object, gets a reference to an object.<br><br>When used as a unary on a type denotes that the type is a reference to an object.                                                                                                                                                                                                                                                                                                                                                             |
| \*       | Dereference       | When used as a unary on an **referenced object**, will dereference that object.<br>When used as a unary on a type denotes that the type is a **raw pointer**.<br>When used as a unary on a **raw pointer**, will either lookup or set that pointer. <br><br>The difference between a reference object and a raw pointer is that raw pointers are ignored by garbage collection, along with the fact pointer arithmetic will be enabled. Pointers also can be cast too and from usize and isize without loss of data.<br> |
| \[...]   | Array             | When used with a single type, denotes an array of that type.<br>When used with multiple types, denote a tuple with those types.<br><br>Ex: `[u8]` for an array of u8s<br>Ex: `[u32, u32]` A tuple of two u32s                                                                                                                                                                                                                                                                                                            |
| (...)    | Inline enum       | When containing a value, the result *could* be any of those types.<br>Ex: `(i8, i16, i32)`<br><br>When used with empty brackets, denotes a [Unit type](https://en.wikipedia.org/wiki/Unit_type), aka no data.                                                                                                                                                                                                                                                                                                            |
| \|>      | Conversion pipe   | Gurn's native casting operator, along with a shorthand for dereferencing. Simply pipe the value you have into the value you want.<br>Ex with types: `-1_i8 \|> u8` returns 255<br>Ex with dereferencing:<br>`i8 x = 0;`<br>`&i8 xRef = &x;`<br>`xRef \|> i8` returns 0                                                                                                                                                                                                                                                   |
| ?        | Optional Operator | When used with a type it is the equivalent of Option\<T><br><br>When used with a value, it bubbles up any `None` values, and unwrapping any `Some(T)` value<br>Ex:<br>`i8? foo = None;`<br>`i8 bar = foo?` compiles, but when run always returns<br><br>`i8? foo = 8`<br>`i8 bar = foo?` sets var to 8                                                                                                                                                                                                                   |
| !        | Error Operator    | When used with a type is the equivalent of Result\<T><br><br>Note: **must follow the operand, otherwise will be confused as a bitwise NOT!**                                                                                                                                                                                                                                                                                                                                                                             |

## Ternary operator
The Ternary operator of Gurn is the same is Python. Both sides must have the same type.
```python
var x = 2 if CONDITION else 3;
```
