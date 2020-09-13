# Knowledge check

- Solidity smart contracts are run on:

  - Ethereum blockchain. incorrect. this is the name of the platform Solidity targets, but not what test are run on
  - The Ethereum virtual machine. correct.
  - A virtual machine. incorrect.
  - A sandbox environment. incorrect

- Events in contracts describe actions that are taken in the contract. What is the correct syntax to define an event?
  - event PurchasedItem;
  - event PurchasedItem(address buyer, uint price);
  - emit PurchasedItem(address buyer, uint price);
  - PurchasedItem(address buyer, uint price);

- What is an example of a user-defined type in Solidity?

  - State variables
  - Structs
  - Addresses
  - Arrays

- What is typically the first line of a smart contract source file?

  - A contract definition. incorrect. The contract definition is required as part of the source file, but it is not the first line.
  - A pragma directive. correct. Pragma is the keyword that you use to ask the compiler to check whether its version of Solidity matches the one required.
  - A solidity version. incorrect. A solidity version is part of the pragma directive, but does not include the keyword for the compiler to check.
  - An event. incorrect. Events are typically part of ever smart contract, but are not required, and exist inside the contract definition.
