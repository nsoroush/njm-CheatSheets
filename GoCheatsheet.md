# Najmeh GoLang CheatSheet :)

===============================================================

I created this Rust Cheat Sheet when I was learning Go. I've been taking the [ZTM academy course] (https://academy.zerotomastery.io/courses/enrolled/1600953), and I used an example and some slides from the course sources taught by [Jayson Lennon](https://zerotomastery.io/about/instructor/jayson-lennon/). I'm sharing this now to assist those who want to learn Rust :)

===============================================================

Contents:
--------

**Go Fundamentals:** **[`Introduction`](#Introduction)__,__[`Go CLI`](#go-cli)__,
__[`Data Types`](#Data Types)__,__[`Primitive Data Types`](#primitive-data-types)__
,__[` Strings and Runes`](#Strings-and-Runes)__, __[`Operators`](#Operators)__,__[`Variables`](#Variables)__,__[`Type Aliases`](#Type-Aliases)__, 
__[`Constants`](#Constants)__,__[`iota Enumeration Pattern`](#iota-EnumerationPattern)__,__[`empty`](#empty)__,**

====================================================

## Go Fundamentals
### Introduction:
***Why Go:***
* In-demand language used by high profile companies
* Simplistic and easy to understand by design
* Built-in dependency management
    * Package registry
* Familiar C-style syntax
***Technical Features:***
* First-class concurrency primitives
    * Perfect for backend programming
* Type safety enforced by compiler
* Memory-safe; no use-after-free bugs
    * Garbage collected; no need to manage memory
* Compiles to machine code for very fast speeds


### Go CLI    
***Go CLI Tool***
*  Go toolchain provides the go command line utility
* This tool is used to:
    * Update dependencies
    * Build and test projects
    * Manage artifacts
    * Format source code
    
    
***Everday Go Commands:***
* build: builds the project and emits an executable binary
    * build -race : checks for concurrency problems
* run: runs the projects directly; no output executable
* test: runs the project's test suite 
* fmt: formats all source files (usually automated with IDE)
* mod: manages modules and  dependencies 
    * mod tidy: updates dependencies
***Command Description***
```go=
go run ./sourceFile.go    //run source file containing func main()
go build ./sourceFile.go  //build project from file containing func main()
go test run               //test suite
go clean                  //remove cache and build artifacts
go mod tidy               //download dependencies and remove unused dependencies
go mod init               //create new Go project
```


## Data Types

### Data Types in Go
* Go is a statically typed language
    * Data types must be provided by the programmer
* Go uses type inference to determine what type of data it is working with
    * Data types only need to be provided in specific circumstances
    * Can always specify the type if desired
        * Compiler error if wrong type is used

### Primitive Data Types
* All primitive data types in **Go** are numeric
* Type indicated in code is a convention
    * It's possible that the data is invalid for the given type
        * Only applies when working with user input or manuallymanipulating the binary data



**Signed Integer Types**


| Data Type | Min Value | Max Value | Defualt |
| -------- | -------- | -------- | -------- | 
| int8 | -128 | 127| 0|
| int16 | -32768| 32767| 0|
|int | | 0|
|int 32     |      |      | 0|
|int 64     |      |      | 0|

**Unsigned Integer Types**
| Data Type | Min Value | Max Value | Defualt |
| -------- | -------- | -------- |-------- | 
| uint8 | 0 | 255| 0|
| byte | 0| 255| 0|
|uint16  | 0 | 65535 | 0|
|uint | 0 | 4294967295|  0|
|uint 32     |   0   |    4294967295  |  0|
|uint 64     |   0   |      | 0|
|uintptr    |   0   | `<pointer size>`  | 0|

***Other data types:***
float32, float64, complex64, complex128, bool

* float32: 32-bit floating point
* float64: 64-bit floating point
* complex64: 032-bit floating point real and imaginary
* complex128:064-bit floating point real and imaginary
  
### Strings and Runes

* Textual data in Go uses UTF-8 encoding
* Encoding is a way to represent thousands of differentsymbols using code pages
* Code pages are tables which use the first few bytes ofdata to determine which page to use    
* Each symbol in the code page is called a code point
**Example Code Page:**    
    

| 0 | 1 | 2 |
| -------- | -------- | -------- |
| Text     | Text     | Text     |

 ***Runes***  
* Text is represented using the rune type: Similar to char
* Rune  is an alias for int32 (32-bit integer)
    * Always a number: will print numeric value unless properformatting is specified    
* A rune can represent any symbol: Letters, numbers, emoji, etc

    
***Strings***
* A string is the data type for storing multiple runes   
* Strings are just an array of bytes and a string length
    * There is no null termination with a Go string
* When iterating a string, iteration occurs over bytes
    * Bytes are not symbols
    * Special iteration required to retrieve runes/symbols

* Raw strings and raw runes will be displayed as-is (no escape sequences).

| Type     | Default     | Note     |
| -------- | -------- | -------- |
| string | ""| Create with "" (double quotes) or `''` (backticks) for raw string; contains any number of Unicode code points | 
| rune | 0| Create with '' (single quotes) or `''` (backticks) for raw rune; contains a single| 

***Creation***

* Runes are created using single quotes: '
    * Runes: `'a' , 'R' , '\n'`
* Strings are created using double quotes: " 
    * Strings: `" Amount is $22\n"`
* Raw literals are created using backticks: `
    * Raw Literal: ` `Let's code in "Golang!"\n` ` 


### Operators
**1- Mathematical**
Operator Description
```go=
a + b  //+ add
a - b  //- subtract
a * b  //* multiply
a / b  // / divide
a % b  //remainder / modulo
a += 2 //add then assign
a -= 2 //subtract then assign
a *= 3 //multiply then assign
a /= 2 //divide then assign
a %=   //remainder / modulo
a++    //increment
a--    //decrement
```
**2- Bitwise**
```go=
P & Q  // P and Q
P \| Q // P or Q
P ^ Q  // P xor Q
P &= Q // and then assign
P \|=  // or then assign
P ^=   // xor then assign

<< left shift
>> right shift
```
**3- Comparison**
```go=
a == b //equal
a != b //not equal
a < b  //less than
a <= b //less than or equal
a > b  //greater than
a >= b //greater than or equal
```
**4- Logical**
```go=
P && Q   //and
P \|\| Q // or
P ! Q    //not 
```


### Variables

* ***Variables*** provide a way to store & access data in your program
    * Data within can be anything/vary (variable)*     
    * Alias to data in memory
    * Storing data to a variable is called assignment

* Variables have multiple components:
    * Name
    * Data (or lack thereof)
    * Type
**Naming:**
* Go variable naming convention is camelCase
```go=
    myLongVariableName := "hi"
```
* Variable names can only be declared once per scope (function body, package, etc.)
* Use names appropriate for the data
    
Syntax:
```go=
    var var_1 = 3
    var num int = 3
    var number int
    number = 4
    var a, b, c = 1, 2, "sample" //Compound creation
    
    // Block Creation
    var( 
        a int =1
        b int =2
        c = "sample"
    )
    
    // Crat and Assign:
    
    number := 3
    a, b := 1, "sample"
    ```
Variable can be reassigned and assigned to other variables:
```go=
a:= 1
a = 2
var c = a
```
    
     
    ***Defaults***
* Variables that are declared but not assigned will automatically havea default value
    * String default: ""
    * Number default: 0
    * Other default: nil

***"Comma, ok"*** 
* "Comma, ok" idiom allows re-use of last variable in compound create & assign:
```go=
a, ok := 1, 2 // create `a` and `ok`
b, ok := 3, 4 // create `b` and re-assign `ok`
a, ok := 5, 6 // ERROR: `a` has already been created; re-assign `ok`
```



### Type Aliases
    
* Possible to creat type aliases in **Go.**
* Type aliases can help clarify intent.
* They exist as names only, and are equivalent to the aliased type.
* Same in every way to another type, just different name
* Usefull for providing indication of what kine of data is being utiliaed.    
* They exist as names only, and are equivalent to the
* aliased type.
```go=
type UserId int // distance now refers to int
type Direction byte
type Speed float64
type Velocity Speed 

type Distance int // distance now refers to int
type Miles Distance // miles now refers to int via Distance
type Calculate = func(a, b int) int // closure
```
* Converting between types requires parentheses
 ```go
  UserId(5)
  Speed(88.3)
```  

### Constants

* Constants can be created using the const keyword
* Useful when declaring some value that needs to be utilizedthroughout some or all of the program
* Constants starting with a capital letter are public and can be accessed outside the package
* Naming convention is PascalCase.
* Constant names can only be declared once per scope
(function body, package, etc.).
 ```go 
    const Name = "Najmeh" //PascalCase
    // block declaration
    const (
        A = 0
        B = 1
        C = 2
    )
```
### iota Enumerations Pattern
* **`iota`** keyword can be used to automatically assign values
* The iota keyword can be used to assign integers to constants
    * Replicates C-style enums
    * **`const`** is like a variable, but unchanging
    * Common to make groups of constants

* Values can be skipped by using an underscore (_)
* iota values can be expressions (iota + 5)
* Use a receiver function to more easily work with constants and iota 


```go=
type Direction byte
const (
    North Direction = iota // 0
    East                   // 1
    South                  // 2
    West                  // 3
    )
// `String` function used whenever type `Direction` is printed
func (d Direction) String() string { // Array of string, indexed based on the     constant value of Direction.
    // Cannot change order of constants with this implementation.
    return []string{"North", "East", "South", "West"}[d]
func (d Direction) String() string {
    // resistant to changes in order of constants
    switch d {    
        case North:
        return "North"
        case East:
        return "East"
        case South:
        return "South"
        case West:
        return "West"
        default:
        return "other direction"
    }
}
```
### empty