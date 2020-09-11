# Basics of Solidity

All Solidity contracts typically have the following:
- Pragma directives
- State Variables
- Functions
- Events
There is of course, more than that you need to know to program more advanced smart contracts, but this is enough to get you going.

If you have an understanding of this, you can get started writing a contract right away.

## Pragma directives
Pragma is the keyword that you use to ask the compiler to check whether its version matches the one required by the pragma. If it matches that means your source file can run successfully, if not then the compiler will error.

To find the current version of Solidity, visit: https://solidity.readthedocs.io/.

Then you can copy the version over to your source file.

A version pragma directive looks like:
`pragma solidity ^0.7.0;`

This line means that the source file will compile with a compiler greater than the version 0.7.0, but does not work on a compiler starting in version 0.8.0., because there will be no breaking changes until that version. The exact version of the compiler is not fixed, so that bugfix releases are still possible.

## State variables
State variables are key to any Solidity source file. 

They are variables whose values are permanently stored in contract storage.

``` 
pragma solidity >0.7.0;

contract SimpleMarketplace {
    uint price; // State variable  
```

Note that source files for contracts always start with the definition `contact ContractName`.

In this example, the state variable is named **itemNumber** with type **uint**. The integer type uint indicates that this will store an unsigned integer with 256 bits. That means it can hold zero and positive numbers in the range of 0 to 2^256 -1. 

For all variable definitions you must specify the type whether that's an integer, boolean, or address, and you also must specify the variable name.

Additionally, you can specify the visibility of a state variable as:
- **public:** part of the conract interface
- **internal:** only accessed internally from the current contract
- **private:** only visible for the contract they are defined in

## Functions
Functions are executable units of code within a contract. Functions describe a single action to take to achieve one task. They are reusable and can also be called from other contract files. They behave very similarly to functions in other programming lagnauge.

A simple example to define a function is this:
```
pragma solidity >0.7.0;

contract SimpleMarketplace {
    function buy() public payable { // Function
        // ...
    }
}
```

Function Calls can happen internally or externally and have different levels of visibility towards other contracts. Functions accept parameters and return variables to pass parameters and values between them.

### Function modifiers
Function modifiers can be used to change the behavior of functions. They work by checking a condition before the function executes. For example, checking that only a merchant can be able to list an item for sale.

```
pragma solidity >0.7.0;

contract SimpleMarketplace {
    address public seller;

    modifier onlySeller() { // Modifier
        require(
            msg.sender == seller,
            "Only seller can put an item up for sale."
        );
        _;
    }

    function listItem() public view onlySeller {
    }
}
```

## Events

Events describe actions that are taken in the contract.  Events have parameters like functions do that need to be specified when the event is called.

To call an event, you must use the keyword **emit** with the event name and it's parameters. When this happens, the event is triggered and this creates a log in the blockchain.


```
contract SimpleMarketplace {
    event PurchasedItem(address buyer, uint price);

    function buy() public payable {
        // ...
        emit PurchasedItem(msg.sender, msg.value);
    }
}
```

Events are inheritable members of contracts. When you call them, they cause the arguments to be stored in the transaction’s log - a special data structure in the blockchain. These logs are associated with the address of the contract, are incorporated into the blockchain, and stay there as long as a block is accessible (forever as of now, but this might change with Serenity). The Log and its event data is not accessible from within contracts (not even from the contract that created them).

