## Basic Syntax

The language is itself is similar to that of Rust, however it is variable declaration and function return types are closer to that of C.

```rust
Result<i32, Error> foo(i32 o){
	return Ok(o); // You can return with the keyword
}


Result<(), Error> main(){
	i32 bar = 1234i32 + foo(0)?; // Bubble up error
	var baz = bar; // implict copy, implicit type
	if (baz == 1234)
		println!("{}" ,baz);
	else
		todo!();
	Ok(()) // Or implict return by returning unit type
}
```