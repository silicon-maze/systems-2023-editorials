# **Subverting Bounds** 
Category: Miscellanous (Blockchain)

Author: Shubham Rasal

Flag: `MAZE{UnDeRfLoWOrOvErFlOw}`

## Problem Statement

The rebels secret has been locked in a smart contract. It's up to you to undo the act and get the secret out.

## Relevant files / links

Actual challenge link : https://shubham-rasal.github.io/ctf/

## Hint

Do you know how old speedometer works?

## Solution

This challenge is based on the concept of integer underflow specifically in solidity. In fact, its based on uint256 underflow. In the versions before 4.22.1, the underflow was not handled properly and if you decease the value of uint256 by 1, it will get its maximum value.

To take advantage of this, we need to carefully analise the code. The code is as follows:

```solidity

 function transfer(address to, uint amount) public {
        require(balances[msg.sender] - amount >= 0);
        balances[msg.sender] -= amount;
        balances[to] += amount;
    }

```


The first line of the function is a require statement which checks if the balance of the sender is greater than or equal to the amount to be transferred. If it is, then the transfer takes place. But if the balance is less than the amount to be transferred, then the require statement will throw an error and the transfer will not take place.

But due to the underflow vulnerability, if the balance is 0 and the amount to be transferred is 1, then the require statement will check if 0 - 1 >= 0. This will return true and the transfer will take place. But the balance of the sender will be 2^256 - 1. This is because of the underflow vulnerability.

After this if you call the getFlag() function, you will get the flag.