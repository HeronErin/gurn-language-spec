## Returning from functions

Gurn allows for returning through the typical return keyword
```java
i8 foo(){
	return 0;
}
```
Or by omitting the semicolon
```rust
i8 foo(){
	0
}
```
Or with the shorthand declaration syntax
```rust
i8 foo() => 0;
```

## Variadic Functions
A  [Variadic Functions](https://en.wikipedia.org/wiki/Variadic_function) is a function that can revive a variable amount of arguments. A variadic function can be defined with the following syntax:
```java
void foo(String somethingRequired, ...int extraNumbers){...}
// The true type of extraNumbers is [extraNumbers; lengthOfNumbers]



foo("Hello"); // Valid
foo("Hello", 1); // Valid
foo("Hello", 1, 2); // Valid

foo("Hello", "1", 2); // Not Valid
foo("Hello", 1, "2"); // Not Valid
```extraNumbers