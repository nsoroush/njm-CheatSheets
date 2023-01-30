# Rust CheatSheet :)

===============================================================
I created this Rust Cheat Sheet when I was learning Rust. I've been taking the [ZTM academy course](https://zerotomastery.io/courses/learn-rust/), and I used an example and some slides from the course sources taught by [Jayson Lennon](https://zerotomastery.io/about/instructor/jayson-lennon/). I'm sharing this now to assist those who want to learn Rust :)

===============================================================

Contents
--------

**Introduction:** **[`Why Rust?`](#numbers)__,__[`Strings`](#strings)__,__[`Boolean`](#boolean)__,__[`Match`](#match)__,__[`Dictionaries`](#dictionaries)__,__ [`Tuples`](#tuples)__,__[`Sets`](#sets)__,__[`None`](#none)** 

**Data Collections:** **[`Tuple`](#tuple)__,__[`Enum`](#enumeration)__,__[`Structure`](#structure)__,__[`Lists`](#lists)__,__[`Data Structures Hashmap`](#data-structures;-hashmap)__,__ [`Tuples`](#tuples)__,__[`Sets`](#sets)__,__[`None`](#none)** 

**Working With Data:** **[`Option`](#option),**




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


