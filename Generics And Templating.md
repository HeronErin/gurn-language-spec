Generics allow for one function definition to apply to many different type of variables. The following is a basic example of how to use it.
```java
import std.traits.Comparable;

T max<T>(T a, T b) where T instanceof Comparable
	=> a if a > b else b; 
	
T min<T>(T a, T b) where T instanceof Comparable
	=> a if a < b else b; 

```
In the above example, note what we are using the `where` clause to restrain the type to one that has implemented the comparable trait. The following is an example of how you can make use of multiple generic types.
```java
import std.traits.PrimativeInt;

// Making use of an inline enum to be able to return either type.
(T, F) max<T, F>(T a, F, b) 
	where T instanceof PrimativeInt && F instanceof PrimativeInt
	=> a if a > b else b; 
(T, F) min<T, F>(T a, F, b) 
	where T instanceof PrimativeInt && F instanceof PrimativeInt
	=> a if a < b else b; 
```


