# Reference types
Another common type you'll deal with when writing contracts are reference types. The main difference is that values of reference types can be modified through different names.

When using a reference type, you must explicitly provide the data area where the type is stored in a data location. Other examples of reference types are arrays and structs.

## Data location
Every reference type specifies a data location where the data is stored. The three options for specifying the data area where the type is stored are:

- **memory** lifetime limited to external function call
- **storage** location where state variables are stored
- **calldata** special data location that contains the function arguments

They always create an independent copy.

Example:

```solidity
contract C {

    uint[] x;
    // the data location of values is memory
    function buy(unit[] memory values) public {
        x = value; // copies array to storage
        uint[] storage y = x; //data location of y is storage
        g(x); // calls g, handing over reference to x
        h(x); // calls h, and creates a temporary copy in memory
    }

    function g(uint[] storage) internal pure {}
    function h(uint[] memory) public pure {}
}
```

## Arrays

Arrays are a way to store similar data in a set data structure. Arrays in Solidity are similar to arrays in other programming languages. They can either have a fixed or dynamic size.

They can be defined as type **uint**, **memory**, **bytes**

Examples:

```solidity

```

### Array members

- **length**:
- **push()**:
- **push(x)**:
- **pop**:

Examples:
```solidity

```

## Structs

Structs are custom types that a user can define to represent real world objects.

Examples:

```solidity

```

## Mapping types

Mappings are key value pairs that are encapsulated (packaged together) ; these are closest to dictionaries or Objects in JavaScript. We typically use mapping to model real world objects and do faster lookups. The values could take on various types (including complex types like structs) making this flexible and human friendly to work with (i.e you can access values by mapping_instance.key).
