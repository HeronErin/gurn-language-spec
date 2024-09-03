Gurn's Control flow, for the most part, is just C with some modifications.

## If statements

```java
if (CONDITION){
	...
}
```
## Else

```java
if (CONDITION){
	...
}else{
	...
}
```
## Else if
```java
if (CONDITION){
	...
}else if (CONDITION){
	...
}
```
## While loop
```java
while(CONDITION){
	...
}
```
## Do while
```java
do {
	...
} while(CONDITION);
```
## For loop
```java
for (T NAME; ITERATOR){
	...
}
```
however the type can be inferred
```java
for (NAME; ITERATOR){
	...
}
```
## Match statement
The match statement is just like the switch statement most languages have, however it allows for the computing of Enum varieties.
The simple case:

```rust
i8 x = 0;
match (x){
	0 => {...},
	1 => panic!("Shit"),
	_ => todo!() // Guard clause for all other i8 values
}
```
Using with Enums:
```rust
var x = Some(Some(1));
match x{
	Some(Some(number)) => todo!(),
	Some(None) => todo!(),
	None => todo!(),
	// no guard clause needed as no other plausibility exist for the Option type
}
```