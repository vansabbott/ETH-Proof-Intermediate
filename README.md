# ETH-Proof-Intermediate
The challenge involves using 3 error handling statements. I will walk you through the assessment for function and errors in the intermediate course on ETH plus AVAX. The project requirement was to implement error handling in a smart contract. I will explain the code and demonstrate the use of require, revert, and assert statements to ensure the proper execution of transactions

## Description

Requirements:
1. Contract successfully uses require()
2. Contract successfully uses assert()
3. Contract successfully uses revert() statements

## Getting Started

### Installing

The code will be under Error Handling in the ETH-Proof-Intermediate repository on my github.

### Executing program

To run the code, we use the Remix IDE. After compilation of the code, we can deploy the code. Under the deployed contracts window, we can view out contract with the name bal. The contract will display the Deposit function, Withdraw function and balances call button. We can deposit an amount to a specific address, withdraw money and even call balances to check the available balance in the address. The updated balance can be viewed by calling the balances option to check the final balance.

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.13;
contract bal{
    event bank(address indexed from, address indexed id, uint value);

    mapping(address => uint) public balances;

    function Deposit(address id,uint value) public payable{
        balances[id]+=value;
        emit bank(msg.sender,id,value);
    }

    function Withdraw(address id, uint value) public payable{
        require(value<=balances[id],"Insufficient Balance");  //Require statement
        if(balances[id]<value){                               //Revert statement
             revert("Error");
        }
        assert(balances[id] >= value);                        //Assert statement
        balances[id]-=value;
        emit bank(msg.sender,id,value);      
    }
} 

## Help

You need to be careful of the amount that you withdrae in a transaction. The condition set in the withdraw function checks for the amount of total balance the address holds and compares to the amount to be withdrawn. So if the value of balance in the id < withdraw value, the code will show an error.  

## Authors

Contributors names and contact info

Vansh Abbott
vansh.abbott10@gmail.com


## License

This project is licensed under the [NAME HERE] License - see the LICENSE.md file for details
