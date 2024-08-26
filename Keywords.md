## Function specific

| Keyword      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **pure**     | Guarantees and enforces that this function is pure (see [Wikipedia/Pure_Function](https://en.wikipedia.org/wiki/Pure_function)) these function can be run in both the runtime and compile time. <br><br>Examples include: sin, cos, min, max, and other math related functions.                                                                                                                                                                                           |
| **comptime** | Enforces that a function can only be run during compilation. Along with only allowing the calling of functions that can be run at compile time.<br>If used as a function parameter, it can be inlined in, this can be useful with things like string constants. <br><br>Examples include: compiler_error!(), and macros.                                                                                                                                                  |
| **runtime**  | Prevents a function from being able to be called during compilation. This can be implicitly applied to a function if it calls a runtime only function.<br><br> It is considered best practice to mark a function that is publicly exposed as (I.E in a library) as runtime if it makes use of runtime functions.<br><br>Examples include:                                                                                                                                 |
| **inline**   | Force a function to be always inlined. This is used for optimization on small functions. These can be thought of as a less powerful form of macros.                                                                                                                                                                                                                                                                                                                       |
| **static**   | Inside a function scope, static variables are maintained between function calls. This means that if you have a function *foo*, with a static variable *count*, which is returned and incremented with each call, the function will keep track of how many times it is called.<br><br>**NOTE: ** STATIC VARIABLES ARE NOT MAINTAINED ACROSS THREADS. (unless they are defined as atomic)<br>**NOTE: ** Static variables *are* maintained across all instances of generics. |

## Defining things

| Keyword     | Description                                                              |
| ----------- | ------------------------------------------------------------------------ |
| **pub**     | Makes an object, be it function, struct, or enum, public for all to see. |
| **private** | This keyword is unnecessary, all things are private by **default**.      |
|             |                                                                          |

## General Keywords

| Keyword   | Description                                                                                                             |
| --------- | ----------------------------------------------------------------------------------------------------------------------- |
| **where** | See: <a href="./Generics And Templating.md">Generics And Templating</a>                                                 |
| **const** | Specifies that an variable in unchanging. This will prevent you from updating the variable later with a compiler error. |
|           |                                                                                                                         |
