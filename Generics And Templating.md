Generics allow for one function definition to apply to many different types of variables. The following is a basic example of how to use it.
```java
import std.traits.Comparable;

T max<T>(T a, T b) where T implements Comparable
	=> a if a > b else b; 
	
T min<T>(T a, T b) where T implements Comparable
	=> a if a < b else b; 

```
In the above example, note what we are using the `where` clause to restrain the type to one that has implemented the comparable trait. The following is an example of how you can make use of multiple generic types.
```java
import std.traits.PrimativeInt;

// Making use of an inline enum to be able to return either type.
(T, F) max<T, F>(T a, F, b) 
	where T implements PrimativeInt && F implements PrimativeInt
	=> a if a > b else b; 
(T, F) min<T, F>(T a, F, b) 
	where T implements PrimativeInt && F implements PrimativeInt
	=> a if a < b else b; 
```


## Where clauses
Where clauses can be though of as a single line of compile time code that returns a boolean value. (See <a href = "./Compile Time Execution.md">Compile Time Execution</a>) this makes where clauses much more powerful than other languages.
```java
// A function that can **only** work during compile time, that takes a type as a parameter. 
comptime bool _isValid(Type type){
	type.toString().startsWith("i") // Only accept types that start with i
}


T max<T>(T a, T b) where _isValid!(T)
	=> a if a > b else b;
```
