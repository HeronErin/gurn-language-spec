
## User defined datatypes

### Structs
The most base form of all datatypes supported in the language. The structure is as follows:
```
{keywords} struct NAME[<[GENERICS]>] [where GENERIC CONDITIONS] {
	...
}
```
The following is an example of a struct:
```java
pub struct Foo<T, F> where T implements std.traits.Comparable{
	T a,
	T b
}
```

### Enums
Enums are one of the most useful things of this language, and is most similar to that of Rust. Enums can act as they do in other languages, however are typically used in a way that allows them to carry other data depending on their Enum variety. An Enums structure is defined bellow:
```
{keywords} [genericType] enum NAME[<[GENERICS]>] [where GENERIC CONDITIONS]
```

The following is an example of a basic Enum that makes use of a custom generic type:
```java
// In this case the size of a Foo is the same as an i8
pub i8 enum Foo{
	bar = 0,
	baz
}
```
This example makes use of the Enum's ability to store extra data:
```java
// In this case the size of a Foo is that of a u16 + u128 (as a u128 is the largest variety, and a u16 is the generic type size)
pub u16 enum Foo {
	bar(u8, u8, u8) = 0, // 0 here is an optional *tag* that identifes a Foo as a bar. 
	bar(u128)
}
```

You can obtain the tag of a variety using the `._tag` property all Enum varieties contain. In addition, and enum variety can be constructed using the tag with a simple cast. The following code is an example of how to do so:
```java
pub u8 enum Foo {
	bar = 0,
	baz(u8) = 1
}
pub void main(){
	Foo x = (0) |> Foo; // x == Foo.bar
	Foo y = (1, 16) |> Foo; // x == Foo.baz(16)
	
	Foo z = (16, 0) |> Foo; // Throws a runtime error 
}
```



## Built-ins
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

| Length  | Name | What other languages call it |
| ------- | ---- | ---------------------------- |
| 32-Bit  | f32  | float                        |
| 64-Bit  | f64  | double                       |
| 128-Bit | f128 | N/A                          |
| Arch    | real | *float*                      |
### Booleans:
The datatype name for a boolean is `bool`, and like most sensible languages the values for a boolean are `true` and `false`. Note that any non zero values are also considered `true`, and as such any `i8` or `u8` values can be easily cast to `bool` without loss of information. Much like languages like C, a `bool` can be thought of as no more than an alias for an `i8` **HOWEVER** keep in mind you that functions can be implemented on `bool` without being implemented on `i8`, so in that respect it is not an alias for an `i8`!
### Arrays:
Unlike Rust, I see no need to be a functional language, and as such, the default array type will be allowed to grow dynamically (assuming it is not declared as a constant). 
### Strings:
Unlike what certain languages not to be named call them (*caught* Java), strings are not primitives! Due to the nature of mankind, we do not all speak English, and as such ASCII should not be all that is supported. Because of this, a datatype it needed to handle this, and that is where strings come in. Internally, strings are stored as UTF-8 byte array, however since UTF-8 is not the most convenient thing for the average programmer to use, the String type abstracts it away. For string syntax see <a href ="Literals.md#Strings">Literals/Strings</a>
### Char:
Up to four bytes of a UTF-8 character. Stored internally as an `[u8; <=4]` along with being freely cast to one

### Pointers

Pointers are supported in the language, however their use should be avoided. This is due to the fact that they **are not garbage collected!** This means that you must manually drop a pointer to avoid a memory leak.  A pointer can be either obtains by calling the raw `malloc()` function, or as a return value of a function. The `*` operator can be used to dereference a pointer. Pointers **not** guaranteed to be thread safe. Most of what is true with references are also true with pointers, beside not being garbage collected.

### References

The reference to an object can be obtained by using the `&` unary operator. When modifying a reference it will modify the original. References are **not** guaranteed to be thread safe, and as such shared references between threads should be done with an atomic object. 

When dereferencing an object within an assignment it will denote assigning the value it points to:
```c
u32 x = 5;
&u32 xRef = &x;

*xRef = 1;

println!(x); // > 1
```

When dereferencing an object inside an expression it will either copy the value it points to, or the reference to it, depending on the object type. If it is a primitive type, or if a struct has the `valtype` attribute, it will copy the value. However most by default structs are themselves reference types. 
```java
u32 x = 5;
&u32 xRef = &x;

var z = *xRef + 1;
// z = 6
// x = 5


// Assuming SomeStruct is the default ref type:
var someStruct = SomeStruct{x: 1, y: 2};
var someStructRef = &someStruct;

var notACopy = *someStructRef;
notACopy.x++;
// someStruct = {x: 2, y: 2}
// someStructRef = &{x: 2, y: 2}
// notACopy = {x: 2, y: 2}
``` 

