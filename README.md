ImprovedToken Solidity Smart Contract

Overview
The ImprovedToken smart contract is a simple Ethereum token implementation in Solidity. It allows for minting and burning tokens, with public variables to store token details and a mapping to keep track of balances.

Requirements
Public Variables:

Token Name
Token Abbreviation (Symbol)
Total Supply
Mapping:

A mapping of addresses to balances (address => uint)
Mint Function:

Takes two parameters: an address and a value
Increases the total supply by the given value
Increases the balance of the specified address by the given value
Burn Function:

Takes two parameters: an address and a value
Deducts the value from the total supply and the balance of the specified address
Ensures the balance of the specified address is greater than or equal to the amount to be burned
Contract Details
Public Variables
Name: The name of the token (e.g., "MyTOKEN")
symbol: The abbreviation or symbol of the token (e.g., "MTA")
quantity: The total supply of the token
Mapping
balances: A mapping that stores the balance of each address
Functions
mint
solidity
Copy code
function mint(address _address, uint amount) public
Parameters:
_address: The address to which the tokens will be minted
amount: The amount of tokens to mint
Description:
Increases the total supply by the specified amount
Increases the balance of the specified address by the specified amount
burn
solidity
Copy code
function burn(address _address, uint amount) public
Parameters:
_address: The address from which the tokens will be burned
amount: The amount of tokens to burn
Description:
Checks if the balance of the specified address is greater than or equal to the amount to be burned
If the condition is met, it decreases the total supply by the specified amount
Decreases the balance of the specified address by the specified amount
Contract Code
solidity
Copy code
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.18;

contract ImprovedToken {

    // Public variables
    string public Name = "MyTOKEN";
    string public symbol = "MTA";
    uint public quantity = 0;

    // Mapping to store balances
    mapping (address => uint) public balances;

    // Mint function
    function mint(address _address, uint amount) public {
        quantity += amount;
        balances[_address] += amount;
    }

    // Burn function
    function burn(address _address, uint amount) public {
        if (balances[_address] >= amount) {
            quantity -= amount;
            balances[_address] -= amount;
        }
    }
}

Usage
Deploy the Contract:

Deploy the ImprovedToken contract on the Ethereum blockchain using a compatible Solidity compiler.
Mint Tokens:

Call the mint function with the desired address and amount to mint new tokens.
Burn Tokens:

Call the burn function with the desired address and amount to burn existing tokens, ensuring the address has sufficient balance.
