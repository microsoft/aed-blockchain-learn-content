# Write an ERC20 token contract

Now, let's add a new token smart contract to the project.

## Create the new token contract

We're going to create a token contract to reward miner's for creating new blocks in the blockchain.

To begin, hover over the contracts folder in the Explorer and select the New File option. Save the file name as: `ERC20MinerReward.sol`. Copy the contents from below to that contract.

```solidity
pragma solidity ^0.6.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract ERC20MinerReward is ERC20 {

    event LogNewAlert(string description, address indexed _from, uint256 _n);

    constructor() public ERC20("MinerReward", "MRW") public {}

    function _reward() public {
        _mint(block.coinbase, 20);
        emit LogNewAlert('_rewarded', block.coinbase, block.number);
    }
}
```

## What this all means

Now, let's walk through the parts of this contract. We begin with importing the contract from OpenZeppelin that we want to use on line 3 after the pragma directive. This notation allows the contract to find the ERC20 contract definition we'll use in our own contract.

Then we define an event called **LogNewAlert** which will be emitted or called later on in the contract.

The constructor defines the token name as **MinerReward** and the symbol or **MRW**.

When the reward function is called, the current block's miner **block.coinbase** will receive 20 MRW tokens, and an event gets emitted.


## Build the contract

After saving the contract file, right-click and select to **Build Contracts**. Make sure that it builds successfully before you move on.

## Wrap up

This example above is a pretty straightforward implementation of An ERC20 token. You can see how easy it is to write your own token contracts which inherit functions and events from a defined ERC token standard.

The important thing to remember is that the term “token” is simply a metaphor. It refers to assets and/or access rights that are collectively managed by a network of computers, or a blockchain network.

Tokens are an important part to incorporate into your blockchain network.

To get more familiar with tokens, explore the other token contracts available from OpenZeppelin and try out creating your own token contracts.
