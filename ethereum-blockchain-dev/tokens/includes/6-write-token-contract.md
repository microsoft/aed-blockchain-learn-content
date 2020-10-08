# Write an ERC20 token contract

## Create the new token contract

Now, let's add a new smart contract to the project. Hover over the contracts folder in the Explorer and select the New File option. Save the file name as: `Token20.sol`. Copy the contents from below to that contract.

```solidity
pragma solidity ^0.6.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract ERC20MinerReward is ERC20 {

    event LogNewAlert(string description, address indexed _from, uint256 _n);

    constructor() ERC20("MinerReward", "MRW") public {
        _mint(msg.sender, 1000);
    }

    function _reward() public {
        _mint(block.coinbase, 20);
        emit LogNewAlert('_rewarded', block.coinbase, block.number);
    }
}
```

## What this all means

Now, let's walk through the parts of this contract. We begin with importing the contract from OpenZeppelin that we want to use on line 3 after the pragma directive. This notation allows the contract to find the ERC20 contract definition we'll use in our own contract.

## Wrap up

That was a lot that we covered in that example. The important thing to remember is that the term “token” is simply a metaphor. It refers to assets and/or access rights that are collectively managed by a network of computers, or a blockchain network.

Tokens are an important part of incorporating into your network.

To get more familiar with tokens, explore the other token contracts available from OpenZeppelin.
