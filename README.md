## DegenToken Smart Contract
This repository contains the Solidity code for the DegenToken (DGN) smart contract, a BEP-20 token with the following features:

## Standard ERC20 compliance: Implements the ERC20 standard for interoperability with other DeFi applications.

Ownable: Only the contract owner can mint new tokens.
Burnable: Token holders can burn their DGN tokens.
Custom event: Emits a TokensRedeemed event when a user burns tokens.
Dependencies:

## OpenZeppelin Contracts:

@openzeppelin/contracts/token/ERC20/ERC20.sol
@openzeppelin/contracts/access/Ownable.sol
@openzeppelin/contracts/token/ERC20/extensions/ERC20Burnable.sol
Deployment:

## Install dependencies:

npm install @openzeppelin/contracts
Compile the contract:
solc DegenToken.sol --bin --abi -o Compiled
Deploy the contract to your desired blockchain network.
Usage:

## Minting:

Only the contract owner can call the mint function to create new tokens.

## Transferring:

Use the standard ERC20 transfer function to transfer tokens between accounts.


## Burning:

Call the burnTokens function to permanently remove tokens from circulation.

## Redeeming:

Call the redeemTokens function to burn tokens and trigger the TokensRedeemed event. This could be used for a specific token utility within your application.

## Balance:

Use the getBalance function to retrieve the current balance of the calling address


## Additional Notes:

The decimals function is overridden to return 0, indicating whole units for the DGN token (no decimals).

The transferTokens function includes a check to ensure the sender has sufficient token balance before transferring.
