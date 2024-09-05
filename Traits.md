[Object-oriented programming](https://en.wikipedia.org/wiki/Object-oriented_programming) is the concept most other languages subscript to for representing complex datatypes, however Gurn knows the horrors of Java, and Gurn refuses to make the same mistakes. This is why Gurn makes use of Traits, it fills the same niche without the same mess.

A *trait* defines the functionality a particular type has and can share with
other types. We can use traits to define shared behavior in an abstract way. We
can use *trait bounds* to specify that a generic type can be any type that has
certain behavior.

> Note: Traits are similar to a feature often called *interfaces* in other
> languages, although with some differences.

## Defining a simple trait
A trait can be defined similar to the following:
```rust
trait DrawableObject{
	// These functions need to be implemented by objects
	void draw(self);
	i32 getId(self) => -1; // Default implementation
}
```
## Making use of traits
```rust
struct Point(u8, u8, u8);
impl DrawableObject for Point{
	void draw(self){
		...
	}
}

void drawAll([DrawableObject] objects){
	for(object; objects)
		object.draw();
}
```