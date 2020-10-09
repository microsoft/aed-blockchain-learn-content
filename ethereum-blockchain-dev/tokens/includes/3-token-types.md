# Token types

[Ethereum Improvement Proposals](https://eips.ethereum.org/) (EIPs) describe standards for the Ethereum platform, including core protocol specifications, client APIs, and contract standards. What this means is that community members can make proposals of new standards for every part of the platform.

Token standards in particular are defined in what's called [Ethereum Request for Comments](https://eips.ethereum.org/erc) or ERC for short. While new standards are continuously being proposed and accepted, there are primary ERC types that have been adopted widely.

Those four token standards are:

- **ERC20**
- **ERC721**
- **ERC777**
- **ERC1155**

Let's explore each type of token, taking a moment to understand what makes each one significant and unique.

## ERC20

The most widely known and used token is the [ERC20](https://eips.ethereum.org/EIPS/eip-20). ERC20 is the technical standard used for smart contracts on the Ethereum blockchain for token implementation. It has a simple interface for basic tokens.

An ERC20 token contract keeps track of fungible tokens: any one token is exactly equal to any other token; no tokens have special rights or behavior associated with them. This makes ERC20 tokens useful for things like currency exchange, voting rights, or staking.

There are six different functions defined with ERC20 which include basic functionality issues, like how the tokens are transferred and how users can access token data. The six functions are:

- `totalSupply()`: returns the amount of tokens in existence
- `balanceOf(account)`: returns the amount of tokens owned by account
- `transfer(recipient, amount)`: moved specified amount to the recipient
- `allowance(owner, spender)`: returns the remaining tokens that the spender is allowed to spend on behalf of the owner
- `approve(spender, amount)`: sets the amount as the allowance of the spender
- `transferFrom(sender, recipient, amount)`: moved the amount specified from sender to recipient
- `_transfer(sender, recipient, amount)`: moves token from sender to recipient
- `_mint(address account, uint256 amount)`: creates amount of tokens and assigns to an account

## ERC721

[ERC721](https://eips.ethereum.org/EIPS/eip-721) is the top solution for non-fungible tokens, often referred to as NFTs for short. Like all other tokens, NFTs represent ownership of both virtual and physical assets. These assets might likely include the following:

- Collectible items like antiques, cards, or art
- Physical assets like houses or cars
- Negative value assets like loans

Each token is unique and has ownership and status which must be tracked.

The ERC721 token is a more complex standard than ERC20. Where the core functions have some similarities, each one has function arguments that specify the token ID.

The core functions available are:

- `balanceOf(owner)`: returns number of tokens in owner's account
- `ownerOf(tokenId)`: returns the owner of the token
- `safeTransferFrom(from, to, tokenId)`: safely transfers token based on tokenId
- `approve(to, tokenId)`: gives permission to transfer token to another account
- `getApproved(tokenId)`: returns the account approved for tokenId
- `setApprovalForAll(operator, _approved)`: approve or remove operator access
- `isApprovedForAll(owner, operator)`: returns if the operator is allowed to manage all assets for the owner
- `safeTransferFrom(from, to, tokenId, data)`: safely transfers tokenId from from to to
- `_transfer(from, to, tokenId)`: transfers tokenId
- `_safeMint(to, tokenId)`: safely mints tokenId and transfers

## ERC777

[ERC777](https://eips.ethereum.org/EIPS/eip-777) is a richer standard for fungible tokens, enabling new use cases and building on learnings from previous token standards. It is backwards compatible with ERC20, which means that you can interact with these tokens as if they were ERC20. ERC777 allows more complex interactions when trading tokens.

The core functions include:

- `totalSupply()`: returns the amount of tokens in existence
- `balanceOf(owner)`: returns the balance of tokens the owner has
- `send(recipient, amount, data)`: send a specified amount to the recipient
- `burn(amount, data)`: destroys the specified amount of tokens
- `isOperatorFor(operator, tokenHolder)`: returns true if an account is an operator of tokenHolder
- `authorizeOperator(operator)`: make an account an operator of the caller
- `revokeOperator(operator)`: reove an account's operator status
- `defaultOperators()`: returns a list of default oeprators
- `operatorSend(sender, recipient, amount, data, operatorData)`: moves the amount of tokens from the sender to the recipient
- `operatorBurn(account, amount, data, operatorData)`: destroys an amount of tokens specified
- `_mint(account, amount, userData, operatorData)`: creates a specified amount of tokens and assigns to the account

## ERC1155

[ERC1155](https://eips.ethereum.org/EIPS/eip-1155) is a standard for managing multi-token types, allowing for a single contract to represent multiple fungible and non-fungible tokens.

ERC1155 draws on ideas from ERC20, ERC721, and ERC777.

The design of this token type allow for massive gas savings for a couple different reasons. First, because you can use this token contract for multiple tokens, this means less deployments with less complexity. It also has batched operations which means a single function call can be simpler and less gas-intensive.

The core functions include:

- `balanceOf(account, id)`: returns the amount of token type id
- `balanceOfBatch(accounts, ids)`: batched version of balanceOf
- `setApprovalForAll(operator, approved)`: grant or revoke permission to operator
- `isApprovedForAll(account, operator)`: returns true if operator is approved to transfer account's tokens
- `safeTransferFrom(from, to, id, amount, data)`: transfers amount of token type id
- `safeBatchTransferFrom(from, to, ids, amounts, data)`: batched function of safeBatchTransferFrom
- `_mint(account, id, amount, data)`: creates specified amount of token type id
- `_mintBatch(to, ids, amounts, data)`: batched version of _mint
- `_burn(account, id, amount)`: destroys a specified amount of token type id
- `_burnBatch(account, ids, amounts)`: batched version of _burn
