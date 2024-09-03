There are 3 types of functions in the language, compile-time only, run-time only, and functions that can be run at both. 

## Compile time parameters
```java
// Generate a unique memcpy for each size, making it the optimal way to copy data. (For relativly small values)
String fastMemCpy(comptime usize size, u8* dst, u8* src){
	const usize u64_chuncks = size % 8;
	const usize single_bytes = size / 8;
	const usize bytes_afteru64 = u64_chuncks * 8;
	
	comptime for offset in 0..u64_chuncks{
		dst |> *u64[offset] = src |> *u64[offset]
	}
	
	comptime for offset in 0..single_bytes{
		dst[offset + bytes_afteru64] = src[offset + bytes_afteru64];
	}
}
```

# Macros

Macros in Gurn are different to Macros you may see in C and Rust. Gurn macros are still functions, however these functions are called at compile time as opposed to a simple contemplating format that other languages fall into. Evan Rust forces Procedural to be in a completely separate crate, forcing them to be hacky and stand on their own. This is entirly different in Gurn, although Gurn supports that form of templating, it is discouraged. 

In this example, two different functions are given, one is declared as a `comptime` function, the other just takes comptime parameters. 
```java

comptime int add_macro(int x, int y) => x + y;
int const_add(comptime int x, comptime int y )=> x + y;

const int a = add_macro!(1, 2); // a = 3 is the assembly emmited by the compiler

int b = const_add(1, 2); // A unique function is generated, with the known constants of x = 1 and y = 2 and will return the sum of theses two. After optimization we are calling a function that simply returns "3" (unless inlined)
```

### Constants In Constants out

The simplest form of macros simply take in a constant and return another constant
```java
// Note with comptime functions `comptime` is not needed for the arguments
comptime int add(int x, int y) => x + y;

const int a = add!(1, 3); // a = 4 is the assembly emmited by the compiler
```

### Code in code out
This form of macros is what most over compiled languages feature, a system of no more than simple templating, where the macros call is replaced with the returned code. Here the magic `template` decorator tells the compiler that both the args and the return value are provided by the compiler, not user code. 
**The largest restriction is that you must have an even number of parenthesis inside the macro arguments,  otherwise it can't be properly parsed.**

```java
// Using tokens
@template(ret, args)
comptime [Token] numberOne([Token] args) => [Token::Number(1)];

// Using strings
@template(ret, args)
comptime String numberOne(String args) => "1";

const var number = numberOne!();
```

### Constants in code out
However emitting code does not mean you can't take constants 
```java
import std.traits.PrimativeInt;

// Using tokens
@template(ret)
comptime [Token] onePlus(T num) where T implements PrimativeInt
		=> [Token::Number(num + 1)];

// Using strings
@template(ret)
comptime String onePlus(T num) where T implements PrimativeInt
		=> format!("{}", num + 1);


const var number = onePlus(1); // number = 2
```
### Code in constants out
Probably the most powerful of Gurn's macros system, the ability to take in arbitrary test data and return a Gurn object. 
```java
@template(args)
comptime Json parseJson(String input){
	parseJsonString(input).unwrap()
}

// Usage
const Json some_parsed_json = parseJson!({
	"foo": "bar",
	"baz": [1, 2, 3, 4]
}); // parseJson is done at compile time
```