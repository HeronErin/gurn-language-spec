## Basic Syntax

The language is itself is similar to that of Rust, however it is variable declaration and function return types are closer to that of C.

```rust
// i32 may return no value
i32? foo(i32 o){
	return o; // You can return with the keyword
}

// i32 may return an error
i32! bar(i32 o){
	o // Or return by omitting semicolon
}


void! main(){
	i32 bar = 1234i32 + foo(0)?; // Bubble up no value
	i32 bar = bar(0)!; // Bubble up error, and replaces old bar value
	var baz = bar; // implict copy, implicit type
	if (baz == 1234)
		println!("{}" ,baz);
	else
		todo!();
}
```