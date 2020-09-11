# Value Types
In this unit you'll learn about the main value types in Solidity. They are called value types because they will always be passed by value, which means they are always copied when they are used. This unit covers the primary value types that you will be exposed to when writing contracts.


## Booleans
Booleans are defined using the keyword `bool` and always have the values `true` or `false`.

In a statement, whenever there is some comparison that happens, a boolean will be returned. Typically with comparisons, the following operators are used:
- `!` - not
- `&&` - and
- `||` - or
- `==` - equal
- `!=` - not equal

So then I can have statements like:
 ```
 1 == 2 // false
 1 != 2 // true
 ```

## Integers
Integers will be commonly used in Solidity. They represent whole numbers and can either be signed or unsigned and range from 8 up to 256 bits.

- Signed: Include negative numbers. Can represent as `int8`
- Unsigned: From 0 and up. Can represent as `uint256`.

If a number of bits is not specified, and instead an integer is assigned the type of simply `uint` or `int` then  it will be given the default value of 256 bits.

The following operations can be applied to integers:
- comparisons <=, <, ==, !=, >=, >
- bit operators &, |, ^, ~
- shift operators << and >>
- arithmetic operators +, -, unary -, *, /, % (modulo), **

## Address
An address is a type with a 20 byte value that represents an Ethereum user. This type can either be a regular **address** or an **address payable**.

The difference between the two is that an **address payable** type is an address that you can send Ether to, and it contains the additinal members `transfer` and `send`.

Examples:


## Enums
Enums allow you to create a user-defined type in Solidity. They present a number of choices that can be selected and require that at least one selection is chosen.

Example:


## Function types
Function types are types of functions. 