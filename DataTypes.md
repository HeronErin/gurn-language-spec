
### Integer values:

| Length  | Signed | Unsigned |
| ------- | ------ | -------- |
| 8-Bit   | i8     | u8       |
| 16-Bit  | i16    | u16      |
| 32-Bit  | i32    | u32      |
| 64-Bit  | i64    | u64      |
| 128-Bit | i128   | u128     |
| Arch    | isize  | usize    |
### Floating point values:

| Length | Value | What other languages call it |
| ------ | ----- | ---------------------------- |
| 32-Bit | f32   | float                        |
| 64-Bit | f64   | double                       |
### Booleans:
The datatype name for a boolean is `bool`, and like most sensible languages the values for a boolean are `true` and `false`. Note that any non zero values are also considered `true`, and as such any `i8` or `u8` values can be easily cast to `bool` without loss of information. Much like languages like C, a `bool` can be thought of as no more than an alias for an `i8` **HOWEVER** keep in mind you that functions can be implemented on `bool` without being implemented on `i8`, so in that respect it is not an alias for an `i8`!
### Arrays:
Unlike Rust, I see no need to be a functional language, and as such, the default array type will be allowed to grow dynamically (assuming it is not declared as a constant). 
### Strings:
Unlike what certain languages not to be named call them (*caught* Java), strings are not primitives! Due to the nature of mankind, we do not all speak English, and as such ASCII should not be all that is supported. Because of this, a datatype it needed to handle this, and that is where strings come in. Internally, strings are stored as UTF-8 byte array, however since UTF-8 is not the most convenient thing for the average programmer to use, the String type abstracts it away. For string syntax see [Literals/Strings](Literals.md#Strings)
### Char:
Up to four bytes of a UTF-8 character. Stored internally as an `[u8; <=4]` along with being freely cast to one
