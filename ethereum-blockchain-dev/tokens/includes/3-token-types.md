# Token types

[Ethereum Improvement Proposals](https://eips.ethereum.org/) (EIPs) describe standards for the Ethereum platform, including core protocol specifications, client APIs, and contract standards. Community members can make proposals of new standards for the platform. Token standards in particular are defined in what's called [Ethereum Request for Comments](https://eips.ethereum.org/erc) (ERCs). While new standards are always being proposed and accepted, there are primary ERC types that have been adopted widely.

Those four token standards are:

- ERC20
- ERC721
- ERC777
- ERC1155

Let's explore each type of token, taking a moment to understand what makes each one significant and unique.

## ERC20

The most widely known and used token is the [ERC20](https://eips.ethereum.org/EIPS/eip-20). ERC20 is the technical standard used for smart contracts on the Ethereum blockchain for token implementation. It has a simple interface for basic tokens.

An ERC20 token contract keeps track of fungible tokens: any one token is exactly equal to any other token; no tokens have special rights or behavior associated with them. This makes ERC20 tokens useful for things like currency exchange, voting rights, or staking.

The ERC-20 token defines a common list of rules that all Ethereum tokens must follow.

Example:
Create a token contract for game currency.

```solidity
pragma solidity ^0.6.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract GLDToken is ERC20 {
    constructor(uint256 initialSupply) public ERC20("Gold", "GLD") {
        _mint(msg.sender, initialSupply);
    }
}
```

There are six different functions defined which include basic functionality issues, like how the tokens are transferred and how users can access token data. The six functions are:

- `totalSupply()`: returns the amount of tokens in existence
- `balanceOf(account)`: returns the amount of tokens owned by account
- `transfer(recipient, amount)`: moved specified amount to the recipient
- `allowance(owner, spender)`: returns the remaining tokens that the spender is allowed to spend on behalf of the owner
- `approve(spender, amount)`: sets the amount as the allowance of the spender
- `transferFrom(sender, recipient, amount)`: moved the amount specified from sender to recipient

## ERC721

[ERC721](https://eips.ethereum.org/EIPS/eip-721) is the top solution for non-fungible tokens, often referred to as NFTs. NFTs represent ownership of both digital and physical assets. The range of these assets is wide, of course, but likely includes the following:

- Collectible items like antiques, cards, or art
- Physical assets like houses or cars
- Negative value assets like loans

Each token is unique and has ownership and status which must be tracked.

The ERC721 token is a more complex standard than ERC20. Where the core functions have some similarities, each one has function arguments that specify the token ID.

Example:
Create a token contract to track items in a game

```solidity
pragma solidity ^0.6.0;

import "@openzeppelin/contracts/token/ERC721/ERC721.sol";
import "@openzeppelin/contracts/utils/Counters.sol";

contract GameItem is ERC721 {
    using Counters for Counters.Counter;
    Counters.Counter private _tokenIds;

    constructor() public ERC721("GameItem", "ITM") {}

    function awardItem(address player, string memory tokenURI)
        public
        returns (uint256)
    {
        _tokenIds.increment();

        uint256 newItemId = _tokenIds.current();
        _mint(player, newItemId);
        _setTokenURI(newItemId, tokenURI);

        return newItemId;
    }
}
```

Functions:

- `balanceOf(owner)`: returns number of tokens in owner's account
- `ownerOf(tokenId)`: returns the owner of the token
- `safeTransferFrom(from, to, tokenId)`: safely transfers token based on tokenId
- `approve(to, tokenId)`: gives permission to transfer token to another account
- `getApproved(tokenId)`: returns the account approved for tokenId
- `setApprovalForAll(operator, _approved)`: approve or remove operator access
- `isApprovedForAll(owner, operator)`: returns if the operator is allowed to manage all assets for the owner
- `safeTransferFrom(from, to, tokenId, data)`: safely transfers tokenId from from to to

## ERC777

[ERC777](https://eips.ethereum.org/EIPS/eip-777) is a richer standard for fungible tokens, enabling new use cases and building on past learnings. It is backwards compatible with ERC20, which means that you can interact with these tokens as if they were ERC20.

It is focused around allowing more complex interactions when trading tokens. It brings tokens and Ether closer together.

Example:
Create a contract token for game currency

```solidity
// contracts/GLDToken.sol
// SPDX-License-Identifier: MIT
pragma solidity ^0.6.0;

import "@openzeppelin/contracts/token/ERC777/ERC777.sol";

contract GLDToken is ERC777 {
    constructor(uint256 initialSupply, address[] memory defaultOperators)
        public
        ERC777("Gold", "GLD", defaultOperators)
    {
        _mint(msg.sender, initialSupply, "", "");
    }
}
```

Functions:
- `name()`
- `symbol()`
- `granularity()`
- `totalSupply()`
- `balanceOf(owner)`
- `send(recipient, amount, data)`
- `burn(amount, data)`
- `isOperatorFor(operator, tokenHolder)`
- `authorizeOperator(operator)`
- `revokeOperator(operator)`
- `defaultOperators()`
- `operatorSend(sender, recipient, amount, data, operatorData)`
- `operatorBurn(account, amount, data, operatorData)`

## ERC1155

[ERC1155](https://eips.ethereum.org/EIPS/eip-1155) is a standard for managing multiple token types, allowing for a single contract to represent multiple fungible and non-fungible tokens.

ERC1155 draws on ideas from ERC20, ERC721, and ERC777.

The design of this token type allow for massive gas savings for a couple different reasons. First, because you can use this token contract for multiple tokens, this means less deployments with less complexity. It also has batched operations which means a single function call can be simpler and less gas-intensive.

Example:

Create a token contract that tracks game items

```solidity
// contracts/GameItems.sol
// SPDX-License-Identifier: MIT
pragma solidity ^0.6.0;

import "@openzeppelin/contracts/token/ERC1155/ERC1155.sol";

contract GameItems is ERC1155 {
    uint256 public constant GOLD = 0; //fungible
    uint256 public constant SILVER = 1;
    uint256 public constant THORS_HAMMER = 2; //nonfungible
    uint256 public constant SWORD = 3;
    uint256 public constant SHIELD = 4;

    constructor() public ERC1155("https://game.example/api/item/{1}.json") {
        _mint(msg.sender, GOLD, 10**18, "");
        _mint(msg.sender, SILVER, 10**27, "");
        _mint(msg.sender, THORS_HAMMER, 1, "");
        _mint(msg.sender, SWORD, 10**9, "");
        _mint(msg.sender, SHIELD, 10**9, "");
    }
}
```
Functions:

- `balanceOf(account, id)`
- `balanceOfBatch(accounts, ids)`
- `setApprovalForAll(operator, approved)`
- `isApprovedForAll(account, operator)`
- `safeTransferFrom(from, to, id, amount, data)`
- `safeBatchTransferFrom(from, to, ids, amounts, data)`