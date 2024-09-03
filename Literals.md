
## Strings:

Quote character types:

| Type                | Ex            | Desc                       | Usage                                              |
| ------------------- | ------------- | -------------------------- | -------------------------------------------------- |
| Backtick            | ``` ` ```     | Templated String           | ``` `Result: $()` ```                              |
| Single Quote        | ``` ' ```     | Single character           | ``` '😀'``` can be unicode                         |
| Double Quote        | ``` " ```     | Typical string             | ```"Hello world!"```                               |
| Triple Double Quote | ``` """ ```   | Multiline String           | ```"""Hello world! /* multiple lines */ """```     |
| Triple BackTick     | ``` `​`​` ``` | Multiline Templated String | ``` `​`​`Result: $() /* multiple lines */`​`​` ``` |

String prefixes:


| Type                        | Ex          | Desc                                                                                                                                                                                                                             |
| --------------------------- | ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Raw                         | ``` r" ```  | Disables string escapes (not applicable for Templated Strings)                                                                                                                                                                   |
| Indentation Correction      | ``` I" ```  | Correct the indentation of a Multiline String, removing indentation based on indentation level of start of string. This will throw a compiler error if the indentation level inside the string is less than that of the outside. |
| Indentation correction cont | ``` II" ``` | The ```II``` denotes that it will remove an additional level of indentation. T                                                                                                                                                   |
| Bytes                       | ``` b" ```  | Instead of creating a string, it will create a byte array based on the string literal.                                                                                                                                           |


Some string prefixes can be **COMBINED**,  while other combinations will lead to a compiler error. Ex:
```java
[u8] genHtml(i32 num){
    // Templated bytes with corrected indentation
    bII`​`​`
	    <html>
	        <body>
	            <center>
	                <h2>
	                    BEHOLD THE MAGIC NUMBER: $(num)
	                </h2>
	            </center>
			</body>
        </html>
    `​`​` // Note: lack of semicolon = return value
}
```

However the following would not work:
```java
String genTemplate(){
	// Refuses to compile due the impossibility of a **raw**, templated, and indentation corrected string. 
	rII`​`​`
		Bla Bla Bla
	`​`​`
}
```

## Number:
Numbers can have three optional components: a prefix, a suffix, and as many underscores as your heart can bare. The prefix is to denote what base of number it is, with the default being decimal.  The suffix 

Number prefixes: 

| Type        | Pre      | Ex                 |
| ----------- | -------- | ------------------ |
| Binary      | ```0b``` | ```0b01010101```   |
| Octal       | ```0o``` | ```0o1234567```    |
| Decimal     | ```0d``` | ```0d69```         |
| Hexadecimal | ```0x``` | ``` 0xFEEDBEEF ``` |

Number suffixes:

In addition to prefixes, numbers can also be given a suffix denoting the type it will occupy.  See <a href ="DataTypes.md#Integer values">DataTypes/Integer values</a>
Ex:
```java
var x = 0xFEED_BEEF_u128
```
