Enums, also known in C as tagged unions, acts as both a useful datastructure and Gurns primary error handling system.



## Implicit Enum Conversion
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
