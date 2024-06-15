## ETH-AVAX-Module-4
## DegenToken
## DegenToken is an ERC20-compliant token built on the Ethereum blockchain. This token contract allows for minting, burning, and redeeming tokens, with the transfer functionality inherited from the OpenZeppelin ERC20 contract.

## Features

## Minting: Only the owner of the contract can mint new tokens.

## Burning: Any token holder can burn their tokens.

## Redemption: Token holders can initiate a token redemption process.

## Transfer: Standard ERC20 transfer functionality with optional custom logic.


## Installing

Clone the repository

git clone https://github.com/yourusername/DegenToken.git
cd DegenToken
Install dependencies
Make sure you have Node.js and npm installed, then run:
npm install @openzeppelin/contracts


## Deployment
To deploy the contract, you'll need to provide the token name, symbol, and initial supply.

Example deployment script using Hardhat:


const { ethers } = require("hardhat");

async function main() {
    const [deployer] = await ethers.getSigners();

    console.log("Deploying contracts with the account:", deployer.address);

    const DegenToken = await ethers.getContractFactory("DegenToken");
    const token = await DegenToken.deploy("Degen Token", "DGN", 1000000);

    console.log("DegenToken deployed to:", token.address);
}

main()
    .then(() => process.exit(0))
    .catch((error) => {
        console.error(error);
        process.exit(1);
    });

## Contract Details

Constructor
The constructor initializes the token with a name, symbol, and initial supply, and sets the deployer as the owner.

constructor(
    string memory tokenName,
    string memory tokenSymbol,
    uint256 initialSupply
) ERC20(tokenName, tokenSymbol) {
    _mint(msg.sender, initialSupply * 10**decimals()); // Mint initial supply with decimals
    owner = msg.sender;
}

## Minting

Only the owner can mint new tokens.

function mint(address recipient, uint256 amount) public onlyOwner {
    _mint(recipient, amount);
}


## Burning
Any token holder can burn their tokens.


function burn(uint256 amount) public {
    _burn(msg.sender, amount);
}
Redeeming Tokens
Token holders can initiate a redemption process.


function redeemTokens(uint256 amount) public {
    require(balanceOf(msg.sender) >= amount, "Insufficient balance");
    emit RedemptionRequested(msg.sender, amount);
}

## Transfer

The standard ERC20 transfer function with optional custom logic.



function transfer(address recipient, uint256 amount) public override returns (bool) {
    return super.transfer(recipient, amount);
}
