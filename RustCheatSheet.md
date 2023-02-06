# Final- Rust CheatSheet :)

===============================================================
I created this Rust Cheat Sheet when I was learning Rust. I've been taking the [ZTM academy course](https://zerotomastery.io/courses/learn-rust/), and I used an example and some slides from the course sources taught by [Jayson Lennon](https://zerotomastery.io/about/instructor/jayson-lennon/). I'm sharing this now to assist those who want to learn Rust :)

===============================================================

Contents
--------

**Introduction:** **[`Why Rust?`](#why-rust)__,[`rustup and cargo`](#rustup-and-cargo)__,__[`Documentation and Comments`](#Documentation-and-Comments)__,__[`Strings`](#strings)__,__[`Boolean`](#boolean)__,__[`Match`](#match)__,__[`Dictionaries`](#dictionaries)__,__ [`Tuples`](#tuples)__,__[`Sets`](#sets)__,__[`None`](#none)** 

**Data Structures:** **[`Tuple`](#tuple)__,__[`Enum`](#enumeration)__,__[`Structure`](#structure)__,__[`Lists`](#lists)__,__[`Data Structures Hashmap`](#data-structures;-hashmap)__,__ [`Tuples`](#tuples)__,__[`Sets`](#sets)__,__[`None`](#none)__,__[`Slice`](#slice)** 

**Working With Data:** **[`Option`](#option),**

## Introduction to Rust

### Why Rust
1. First-class multithreading
   a. Compiler error to improperly access shared data
2. Type system:
    a. Can uncover bugs at compile time
    b. Makes refactoring simple
    c. Reduces the number of tests needed
3. Module system makes code separation simple
4. Adding a dependency is 1 line in a config file
5. Tooling:
    a. Generate docs, lint code, auto format

### rustup and cargo
`Rustup` is used to install and manage Rust toolchains. Toolchains are complete installations of Rust compiler and tools.

***Command Description:***
```bash
$rustup show                    //Show currently installed & active toolchains
$rustup update                  //Update all toolchains
$rustup default TOOLCHAIN       //Set the default toolchain
$rustup component list          //List available components
$rustup component add NAME      //Add a component (like Clippy or offline docs)
$rustup target list             //List available compilation targets
$rustup target add NAME         //Add a compilation target
```
***Cargo***
`Cargo` is a tool used to build and run Rust projects.
***Command Description***
```bash=
$cargo init                  //Create a new binary project
$cargo init --lib            //Create a new library project
$cargo check                 //Check code for errors
$cargo clippy                //Run code linter (use rustup component add clippy to install)
$cargo doc                   //Generate documentation
$cargo run                   //Run the project
$cargo --bin NAME            //Run a specific project binary
$cargo build                 //Build everything in debug mode
$cargo build --bin NAME      //Build a specific binary in debug mode
$cargo build --release       //Bulld everything in release mode
$cargo build --target NAME   //Build for a specific target
$cargo --explain CODE        //Detailed information regarding an compiler error code
$cargo test                  //Run all tests
$cargo test TEST_NAME        //Run a specific test
$cargo test --doc            //Run doctests only
$cargo test --examples       //Run tests for example code only
$cargo bench                 //Run benchmarks
```
### Documentation and Comments
`Rust` has support for `doc` comments using the rustdoc tool. This tool can be invoked
using `cargo doc` and it will generate HTML documentation for your crate. In addition to
generating documentation, the tool will also test your example code.

```rust=
/// Documentation comments use triple slashes.
///
/// They are parsed in markdown format, so things
/// like headers, tables, task lists, and links to other types
/// can be included in the documentation.
///
/// Example code can also be included in doc comments with
/// three backticks (`). All example code in documentation is
/// tested with `cargo test` (this only applies to library crates).
fn is_local_phone_number(num: &str) -> bool {
    use regex::Regex;
    let re = Regex::new(r"[0-9]{3}-[0-9]{4}").unwrap();
    re.is_match(num)
}
```



## Data Structures

===================================================
### Primitive Data Types
**1- Signed Integers:**

| Type | Default | Range |
| -------- | -------- | -------- |
| i8     | 0     | -128..127     |
| i16 | 0 | -32768..32767
| i32 | 0 | -2147483648..2147483647
| i64 | 0 | -9223372036854775808..9223372036854775807
| i128 | 0 | min: -170141183460469231731687303715884105728
| i128 | 0 | max: 170141183460469231731687303715884105727
| isize | 0 | `<pointer size on target architecture>`

**2- Unsigned Integers:**
    
| Type | Default | Range |
| -------- | -------- | -------- |
| u8 | 0 | 0..255| 
| u16 | 0 | 0..65535| 
| u32 | 0 | 0..4294967295| 
| u64 | 0 | 0..18446744073709551615| 
| u128 | 0 | 0..340282366920938463463374607431768211455| 
| usize | 0 | `<pointer size on target architecture>`| 
    
**3- Floating Point Numbers**
| Type | Default | Range |Type | Default | Range |
| -------- | -------- | -------- | -------- | -------- | -------- |
| f32 | 0 | 32-bit floating point| f64 | 0 | 64-bit floating point| 

    
**4- &str/Characters**

### Some useful methods for `&str`
1. `&str.len()` return the lentgh of the string as usize.

```rust=
let my_str = "Najmeh"
let len = my_str.len(); //6
```
2. `.chars()` convert string to chars,
3. `.count();` return the lenght of the chars

    
| Type | Notes|
| -------- | -------- |
| char | Unicode scalar value. Create with single quotes `''`| 
| String | UTF-8-encoded string| 
| &str| Slice into `String` / Slice into a static `str`. Create with double quotes `""` or `r#""#` for a raw mode (no escape sequences, can use double quotes)| 
| OsString | Platform-native string| 
| OsStr | Borrowed OsString| 
| CString | C-compatible nul-terminated string| 
| CStr | Borrowed CString| 

#### Escape Sequences & Raw Strings
```rust=
let s = r#"This is a strinng \n "#;
```

**Other Data Types:**

| Type | Notes|
| -------- | -------- |
| bool | `true` or `false`| 
| unit | `()` No value / Meaningless value| 
| fn | Function pointer| 
| tuple | Finite length sequence| 
| array | Fixed-sized array| 
| slice | Dynamically-sized view into a contiguous sequence| 
 
### Variables
* Variables assign data to a temporary memory location
* Variables can start uninitialized, but they must be set before usage.
* In rust variable are immutable by default:
* ***Syntax:***
```rust=
let my_num = 1; 
    my_num = 6; //ERROR because the variable is immutable
```
* `mut` keyword changes to mutable (can be changed)
```rust=
let mut my_num = 1;
    my_num = 6; //OK 
```
* ***Name Convention:***
```rust=
let use_snake_case_for_variables = "OK";
```
* `Rust` infers types, but we can use annotations as well:
```rust=
let my_num: i32 = 50;
```
* Underscore can be used to set numeric type and also to make it easier to read long numbers
```rust=
let my_float = 14.5_f32; 
let my_number = 99_u8;
let num = 1_234_567; 
```
* ***char vs &str***
```rust=
let my_char : char = 'a'; 
let my_str  : &str = "ok";
```



* variables can be shadowed:
```rust=
let my_char : char = 'a'; 
let my_char : char = 'z'; 
```
### Constants
`const` keyword will create a new constant value:
* Type annotations are required
* Naming conventions is SCREAMING_SNAKE_CASE
 ```rust=
const PEACE: char = '☮'; 
const MY_CONST: i32 = 4; 
```
* We use `once_cell` crate if we need lazy initialization of a constant:
```rust=
use once_cell::sync::OnceCell;
const HOME_DIR: OnceCell<String> = OnceCell::new();
```
* use `.set` to set the value (can only be done once)
```rust=
HOME_DIR.set(std::env::var("HOME").expect("HOME not set"));
```
* use `.get` to retrieve the value:
 ```rust=
HOME_DIR.get().unwrap();
```

**Type Annotations:** 
* Required for function signatures
* Type annotations are mostly optional within function bodies
* Occasionally required if compiler cannot infer the type
* Explicit type annotations can be specified when using `let` bindings

```rust=
let i :u32 = 2; // we can't change i anymore
let mut a = i32 = 5; // we could change a because it is mut var:)
    a += 1;
```

### Numeric Types & Basic Arithmetic

```rust

10 + 3  // addition: 13
10 - 3  // subtract: 7
10 * 3  // multiply: 30
10 / 3  // division: 3.3333333333333335
10 % 3  // 1 --> modulo operator - return the reminder. 

use num_integer::Roots;
let num = 9;
num.sqrt(); // = 3

let num = -10.0;
num.abs(); // = 10

use num_integer::Roots;
let n_square_root = 8.nth_root(3); // 2
```

### Type 
```rust=
fn type_of<T>(_: &T) {
    println!("{}", std::any::type_name::<T>())
}

fn main() {
    let s = "Hello";
    let i = 1234;
    let f = 0.32;
    type_of(&s); // &str
    type_of(&i); // i32   
    type_of(&f); // 
    type_of(&{ ||  1 }); //main::{{closure}}
    }
```

### Operators
```rust=
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
```

**2- Bitwise**
```rus=
P & Q   // P and Q
P \| Q  // P or Q
P ^ Q   // P xor Q
P &= Q  // and then assign
P \|=   // or then assign
P ^=    // xor then assign
<<      //left shift
<<=     //left shift and assign
>>      //right shift
>>=     //right shift and assign

```
**3- Comparison**
```rust=
a == b //equal
a != b //not equal
a < b  //less than
a <= b //less than or equal
a > b  //greater than
a >= b //greater than or equal
```
**4- Logical**
```rust=
P && Q   //and
P \|\| Q // or
P ! Q    //not 
```  
### println! and format!
**Println!** is a macro 
```rust=
let c : f64 = 4.123456789;
println!("c is {:.3}",c); //3 digit after .
//Output: c is 4.123

println!("c is {:8.3}",c); //8 digit padding.
//Output: c is    4.123

println!("c is {:08.3}",c); // consider 8 digit and put 0 instead the missing ones.
//Output: c is 0004.123
```

**format!** Creates a String using interpolation of runtime expressions.
```rust=
    let a = 4;
    let b = 6;
    for index in 0..2{
    let my_str = format!( "{}:  a = {} and b = {} ",index, a, b);
    println!("{:?}", my_str);
    }
   
```
## Borrow and defrence



## Control Flow
`Rust` provides multiple control flow mechanisms to use for different situations:

**1. if else**
```rust= 
if condition1 {
    body
    }else if { body 
} else {body}
```

*Example:*
```rust=
max = 10 , min = 4 , num =12
let num = if num > max {
    max
    } else if num < min {
    min
    } else {
    num
    };   // num = 10
```


**2. loop**
```rust=
loop {
    body
    break;
}
```
**3. for**
* Ranges can be used to iterate over numbers
```rust=
for i in 0..10{ // 0..=10 includes 10
    body
}
```
* if we want to costumize the step we use :
```rust=
extern crate itertools; // 0.7.8
use itertools::Itertools;

fn main() {
    for i in (0..=10).step(2) {
        println!("i = {}", i);
    }
}
```
**4. while**
```rust=
while condition{
    body
}
```


***if let***
* `if let` will destructure data only if it matches the provided pattern. 
* It is commonly used to operate on data within an `Option` or `Result` .
```rust=
let something = Some(1);
if let Some(inner) = something {
// use `inner` data
assert_eq!(inner, 1);
}
```
```rust=
enum Foo {
    Bar,
    Baz,
    }
let bar = Foo::Bar;
if let Foo::Baz = bar {
// when bar == Foo::Baz
} else {
// anything else
}
```
* `if let` is an expression, so it can be assigned to a variable.


* ***let if syntax:***
`if` is an expression, so it can be assigned to a variable.
```rust=
let maybe_num = Some(1);
let definitely_num = if let Some(num) = maybe_num 
    { num 
    } else { 10 };
assert_eq!(definitely_num, 1);
```
### while let
* while let will continue looping as long as a pattern match is successful.
*  The let portion of `while let` is similar to `if let`  it can be used to destructure data for utilization in the loop.
```rust=
let mut maybe = Some(10); // if `maybe` is a `Some`, bind the inner data to `value` and execute the loop
while let Some(value) = maybe {
    println!("{maybe:?}");
    if value == 1 {
    // loop will exit on next iteration because the pattern match will fail
        maybe = None;
        } else {
            maybe = Some(value - 1);
    }
}
```

* loop is expression and returns a value
```rust=
let mut iterations = 0;
let total = loop {
    iterations += 1;
    if iterations == 5 {
        // using `break` with a value will evaluate the loop
        break iterations;
        }
    };
// total == 5
```


**Labling:**
we can  labele the loops for clarity and it must start with single quote ('):
```rust=
let mut r = 0;
let mut c = 0;
// label named 'row
'row: while r < 10 {
    // label named 'col
    'col: while c < 10 {
        if c == 3 {
            break 'row; // break from 'row, terminating the entire loop
            }
        if c == 4 {
            continue 'row; // stop current 'col iteration and continue from 'row
        }
        if c == 5 {
            continue 'col; // stop current 'col iteration and continue from 'col
    }
        c += 1;
    }
    r += 1;
}
```


###  Strings
* Two commonly used types of strings: 
1. ***String***:
    1.  owned, automatically borrowed,
    2.  Use .to_owned() or String::from() to create an owned copy of a string slice
    
3. ***&str*** – borrowed String slice.
* Must use an owned String to store in a struct
* Use `&str` when passing to a function

```rust=
let my_str : &str = "This is a slice";
let my_string : String = String::from("This is a string")
```
=====================need to be added====

### iteration()
* Rust's `for` loop is to iterate over collections that implement the `Iterator trait`.
```rust=
// iterate through a collection
let numbers = vec![1, 2, 3];
for num in numbers {
// values are moved into this loop
}
```
* `.into_iter()` is implicitly called when using `for`
```rust=
let numbers = vec![1, 2, 3];
for num in numbers.into_iter() {
// values are moved into this loop
}
```
* use .iter() to borrow the values
```rust=
let numbers = vec![1, 2, 3];
for num in numbers.iter() {
// &1
// &2
// &3
}
`


====================================================
Vector to string 
```rust=
  let a = vec!["a","b","c"].join("*") ;
    println!("{}", a);
// a*b*c
```


### Data Structures; Hashmap
* Collection that stores data as key-value pairs
* Data is located using the “key”
* The data is the “value”
* Similar to definitions in a dictionary
* Very fast to retrieve data using the key

***Syntax:***
```rust=
use std::collections::HashMap;

let mut stock = HashMap::new();
```
***Add new entry:***
```rust=
stock.insert("Chair", 5); // insert the data into the hashmap
stock.entry("Chair").or_insert(50);
stock.entry("Couch").or_insert(50);
```
**Diff** between `entry` and `insert`: the first one will add only if the key does not exist already.

***Go through the keys:***
```rust=
 for key in stock.values(){
        println!("{}", key);
    }
```
***Go through the values:***
```rust=
 for value in stock.values(){
        println!("{}", value);
    }
```
***Iteration over the hashmap:***
```rust=
 for value in stock.values(){
        println!("{}", value);
    }
```
***Accessing Values in a Hash Map:***
```rust=
println!(r#""Chair" :{:?}"#,stock.get("Chair").copied().unwrap_or(0));
println!(r#""Chair" :{:?}"#,stock.get("Chair").unwrap());
```
***Hash Maps and Ownership***  For types that implement the Copy trait, like `i32`, the values are copied into the hash map. For owned values like String, the values will be moved and the hash map will be the owner of those values.

***Others***
1. `len()`	Returns the length of the HashMap.
1. `contains_key()` Checks if a value exists for the specified key.
1. `clone()`: Creates and returns a copy of the HashMap.

### Traits
* Traits declare behavior that may be implemented by any structures or enumerations.
* Traits are similar to interfaces in other programming languages.
* create a new trait
```rust=
trait Notify {
    // implementers must define this function
    fn notify(&self) -> &str;
    }

struct Phone {
    txt: String,
    }
struct Email {
    subject: String,
    body: String,
}
```
* implement the `Notify` trait for the `Phone` struct:
```rust=
impl Notify for Phone {
    fn notify(&self) -> &str {
        &self.txt
        }
}
```
* implement the `Notify` trait for the `Email` struct:
```rust=
impl Notify for Email {
    fn notify(&self) -> &str {
        &self.subject
    }
}
```
* create a new Phone
```rust=
let phone = Phone {
    txt: String::from("foo"),
};
```
* create a new Email
```rust=
let email = Email {
    subject: String::from("my email"),
    body: String::from("bar"),
    };
phone.notify(); // "foo"
email.notify(); // "bar"
```
### Associated Types
* Associated types allow trait implementers to easily set a specific type for use in a trait.
```rust=
trait Compute {
    // associated type to be defined by an implementer
    type Target;
    // use Self::Target to refer to the associated type
    fn compute(&self, rhs: Self::Target) -> Self::Target;
}

struct Add(i32);
struct Sub(f32);

impl Compute for Add {
    // set the associated type to i32
    type Target = i32;
    fn compute(&self, rhs: Self::Target) -> Self::Target {
        self.0 + rhs
        }
    }
impl Compute for Sub {
    // set the associated type to f32
    type Target = f32;
    fn compute(&self, rhs: Self::Target) -> Self::Target {
        self.0 - rhs
    }
}
let add = Add(1);
let two = add.compute(1);
let sub = Sub(1.0);
let zero = sub.compute(1.0);
```
## Trait Objects
* Trait objects can be used to insert multiple objects of different types into a single collection.
* They are also useful when boxing closures or working with unsized types.
* create a trait to refill some resource
```rust=
trait Refill {
    fn refill(&mut self);
    }
```
* some structures to work with:
```rust=
struct Player { health_points: i32 }
struct MagicWand { magic_points: i32 }
struct Vehicle { fuel_remaining: i32 }
```
* set the maximum values for the structures
```rust=
impl Player { const MAX_HEALTH: i32 = 100; }
impl MagicWand { const MAX_MAGIC: i32 = 100; }
impl Vehicle { const MAX_FUEL: i32 = 300; }
```
* trait implementations for all 3 structures
```rust=
impl Refill for Player {
    fn refill(&mut self) {
    self.health_points = Self::MAX_HEALTH;
    }
}
impl Refill for MagicWand {
    fn refill(&mut self) {
    self.magic_points = Self::MAX_MAGIC;
    }
}
impl Refill for Vehicle {
    fn refill(&mut self) {
    self.fuel_remaining = Self::MAX_FUEL;
    }
}
```
* instantiate some structures
```rust=
let player = Player { health_points: 50 };
let wand = MagicWand { magic_points: 30 };
let vehicle = Vehicle { fuel_remaining: 0 };
    // let objects = vec![player, wand, vehicle];
    // ERROR: cannot have a Vector containing different types
    // Type annotation is required here. `dyn` keyword indicates
    // "dynamic dispatch" and is also required for trait objects.
let mut objects: Vec<Box<dyn Refill>> =
                vec![
                Box::new(player), // must be boxed
                Box::new(wand),
                Box::new(vehicle)
                ];
```
* iterate over the collection and refill all of the resources:
```rust=
for obj in objects.iter_mut() {
        obj.refill();
}
```
## Slice
Example
```rust=
let a = [1, 2, 3]; 
let b = [5, 1, 2, 3, 4, 5];
let t = b.windows(3).any(|l| l == a);
```


```
struct Person {
    name: String,
    fav_color: String,
    age: i32,
}

fn print(data: &str) {
    println!("{:?}", data);
}

fn main() {
    let people = vec![
        Person {
            name: String::from("George"),
            fav_color: String::from("green"),
            age: 7,
        },
        Person {
            name: String::from("Anna"),
            fav_color: String::from("purple"),
            age: 9,
        },
        Person {
            name: String::from("Katie"),
            fav_color: String::from("blue"),
            age: 14,
        },
    ];

    for person in people {
        if person.age <= 10 {
            print(&person.name);
            print(&person.fav_color);
        }
    }
}
```
