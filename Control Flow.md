Gurn's Control flow, for the most part, is just C with some modifications.

## If statements

```java
// Multiline
if (CONDITION){
	...
}


// Singleline
if (CONDIITON)
	...
```
## Else

```java
// Multiline
if (CONDITION){
	...
}else{
	...
}

// Singleline
if (CONDITION)
	...
else
	...
```
## Else if
```java
// Multiline
if (CONDITION){
	...
}else if (CONDITION){
	...
}


// Singleline
if (CONDITION)
	...
else if (CONDITION)
	...
```
## While loop
```java
// Multiline
while(CONDITION){
	...
}

// Singleline
while(CONDITION)
	...
```
## Do while
```java
do {
	...
} while(CONDITION);
```
## For loop
```java
// Multiline
for (T NAME; ITERATOR){
	...
}

// Singleline
for (T NAME; ITERATOR)
	...
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
	0 => {...}, // Multiline
	1 => panic!("Shit"), // Singleline
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