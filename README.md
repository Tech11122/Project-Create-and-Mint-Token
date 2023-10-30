# Create and Mint Token

This Solidity smart contract deploys a simple ERC-20 token named "SimpleToken" with the symbol "SIM," allowing the contract owner to mint new tokens, any address to burn their own tokens, and facilitating the transfer of tokens between addresses.

## Description

The "SimpleToken" Solidity contract follows the ERC-20 standard for creating fungible tokens on Ethereum. It inherits from ERC20 and Ownable, initializing with the name "SimpleToken" and symbol "SIM," and mints an initial 1,000,000 tokens for the owner. The contract provides functions for the owner to mint more tokens, for any holder to burn their own tokens, and for users to transfer tokens. Each function includes necessary checks. The SPDX license identifier specifies the MIT License. In summary, this contract serves as a concise and structured starting point for Ethereum token projects.

## Getting Started

### Executing program
To run this program, you can use remix, an online Solidity IDE. Go to this website to start 
https://remix.ethereum.org/#lang=en&optimize=false&runs=200&evmVersion=null&version=soljson-v0.8.18+commit.87f61d96.js

At the remix website go to create file and copy this code
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract CreateToken is ERC20, Ownable {

constructor() ERC20("CreateToken", "LIT") Ownable(msg.sender) {
    // Mint initial tokens to the contract owner
    _mint(msg.sender, 1000000 * (10**uint256(decimals())));
}

    // Function to allow the owner to mint additional tokens
    function mintTokens(address to, uint256 amount) public onlyOwner {
        _mint(to, amount);
    }

    // Function to allow anyone to burn their own tokens
    function burnTokens(uint256 amount) public {
        require(balanceOf(msg.sender) >= amount, "Not enough tokens to burn");
        _burn(msg.sender, amount);
    }

    // Function to transfer tokens to another address
    function transferTokens(address to, uint256 amount) public {
        require(to != address(0), "Invalid address");
        require(balanceOf(msg.sender) >= amount, "Not enough tokens to transfer");
        _transfer(msg.sender, to, amount);
    }
}
```
Now check in the Solidity compiler if its 0.8.20 if correct compile and run the script next go to deploy and run transactions and deploy the code.

## Help
Remember to copy the account to run the program and make sure if the compiler is  0.8.20  

## Authors

Juan Alfonso Q. Magpantay
Metacrafters 


