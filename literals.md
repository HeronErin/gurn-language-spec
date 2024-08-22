## Literals

## Strings

Quote character types:

| Type                | Ex            | Description                | Usage                                              |
| ------------------- | ------------- | -------------------------- | -------------------------------------------------- |
| Backtick            | ``` ` ```     | Templated String           | ``` `Result: $()` ```                              |
| Single Quote        | ``` ' ```     | Single character           | ``` '😀'```                                        |
| Double Quote        | ``` " ```     | Typical string             | ```"Hello world!"```                               |
| Triple Double Quote | ``` """ ```   | Multiline String           | ```"""Hello world! /* multiple lines */ """```     |
| Triple BackTick     | ``` `​`​` ``` | Multiline Templated String | ``` `​`​`Result: $() /* multiple lines */`​`​` ``` |
String prefixes:

Some string prefixes can be **COMBINED**,  while other combinations will lead to a compiler error. Ex:
```java
[u8] genHtml(i32 num){
    // Templated bytes with corrected indentation
    bII`​`​`
        <body>
            <center>
                <h2>
                    BEHOLD THE MAGIC NUMBER: $(num)
                </h2>
            </center>
        </html>
    `​`​` // Note: lack of semicolon = return value
}
```



| Type                        | Ex          | Description                                                                                                                                                                                                                      |
| --------------------------- | ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Raw                         | ``` r" ```  | Disables string escapes (not applicable for Templated Strings)                                                                                                                                                                   |
| Indentation Correction      | ``` I" ```  | Correct the indentation of a Multiline String, removing indentation based on indentation level of start of string. This will throw a compiler error if the indentation level inside the string is less than that of the outside. |
| Indentation correction cont | ``` II" ``` | The ```II``` denotes that it will remove an additional level of indentation. T                                                                                                                                                   |
| Bytes                       | ``` b" ```  | Instead of creating a string, it will create a byte array based on the string literal.                                                                                                                                           |


### Raw String Literals

```python
r"c:\games\Sudoku.exe" # String actually contains 
```

