Enums, also known in C as tagged unions, acts as both a useful datastructure and Gurns primary error handling system.



## Implicit Enum Conversion
Gurn automatically will wrap your values in an Enum for you!
```rust
enum Value{
	float(f32),
	int(i32)
}
Value(1.0); // == Value.float(1.0)
Value(1); // == Value.int(1.0)
```
**However if the compiler can't resolve the correct type it errors:**
```java
enum Value{
	float(f32),
	int(i32)
}
Value("Hello"); // Errors


```
## Enum Syntactical Sugar

The two most important enums in Gurn are Option and Result. 
```rust
enum Option<T>{
	Some(T),
	None
}
enum Result<T>{
	Ok(T),
	Err(Error)
}
```
However using this can be quite bulky, which is why Gurn as syntactical sugar around these two basic enums. 
```rust
// Instead of:
Result<Option<i8>> indexByteArray(self, usize index){
	...
	Ok(Some(return_value))
}

// You can do this:
i8?! indexByteArray(self, usize index){
	...
	return_value // Implicitly know to wrap in Ok(Some()) due to variable type
}
```
## Bubbling up errors
Sometimes you either do not want to, or it is not your job to handle an error. And when that happens you just with to return the error.
```Rust
// Unfortinatly this is quite inconvinent and bulky
match foo{
	None => return foo,
	_ => {}
}
```
That is where the `?` and `!` operator are for. They do the matching and returning for you so you can go about your day. Unlike rust you **must** use the respective operator for the correct enum type, `?` for Option, `!` for Result.

You these operators also will automatically convert you enums for you. Here are some examples:
```Rust
void! foo(){
	None? // Becomes Err(OptionError("Option is of value None"))
}
void? foo(){
	Error(OverflowError("Something went wrong"))! // Becomes None
}
``` 
