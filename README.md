# Voting app on the Ethereum blockchain

The objective of this workshop is to create a smart contract that will be deployed on the Ethereum blockchain allowing users to vote for one of the available candidates. It will also be possible to vote by proxy, a user will be able to give his agreement to another user to vote for him.


# Getting started

* The smart contract will be developed on [Remix](https://remix.ethereum.org)
* [Solidity](https://docs.soliditylang.org/fr/latest/index.html)

## Task 0
Remix is a tool for developing smart contracts, it also allows to compile and deploy them easily and quickly.

Development section <kbd>↓</kbd>  
![Remix](https://github.com/ChoKssa/Workshop-VotingApp-Solidity/blob/main/assets/remix_file_explorer.PNG)

Compilation section <kbd>↓</kbd>  
![Remix](https://github.com/ChoKssa/Workshop-VotingApp-Solidity/blob/main/assets/remix_compiler.PNG)

Deployment Section <kbd>↓</kbd>  
![Remix](https://github.com/ChoKssa/Workshop-VotingApp-Solidity/blob/main/assets/remix_deploy.PNG)


## Task 1
In the contracts/ folder, create a "Ballot.sol" file.  
Add these lines to the file:  
```solidity
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.13;
```
Then create a contract named "Ballot". All the rest of the code will be in this contract.  

## Task 2
Create a ***public*** variable "organizer" of type ***address***.  
Add a ***constructor*** that takes no parameters. The constructor must store the address of the person who deployed the contract in the "organizer" variable.  
> How do I find out the caller's address ? 🤔

## Task 3
Create a ***modifier*** named "onlyOrganizer" that checks if the address of the person calling the contract is the organizer.  
> [modifiers](https://docs.soliditylang.org/en/v0.8.20/structure-of-a-contract.html#function-modifiers)

## Task 4  
Create a ***structure*** called "Voter" which contains:
- A variable of type bool named "voted" to find out if the person has already voted,
- A variable of type uint256 named "weight" (weight is accumulated by delegation),
- A variable of type address named "delegatedAddress" (person delegated to),
- A variable of type uint256 named "vote" (index of the voted proposal).

Create another ***structure*** called "candidate" which contains:
- A variable of type string named "name", 
- A variable of type uint256 named "voteCount".

## Task 5
Create a ***mapping*** with a keyed address and the value Voter.  
Create a public array of "Candidate" named "candidates".  
> [mapping](https://docs.soliditylang.org/en/v0.8.7/types.html#mapping-types)  
> [arrays](https://docs.soliditylang.org/fr/latest/types.html#arrays)  

## Task 6
Modify the constructor to take an array of bytes32 representing the list of candidates' names.
Add these names in "candidates".

## Task 7
Create a function called "giveRightToVote" taking an address parameter. This function gives the right to vote to the address given in parameter to vote.  
This function can only be called from outside the contract.  
Attention, the right to vote is given only if the address given in parameter has not already voted and its weight is equal to 0.  
***Only the organizer can call this function.***

## Task 8
Create a function called "vote" taking a unit256 as parameter. This function allows the caller to vote (if possible) by indicating the index of the candidate given in parameter.  
This function can only be called from outside the contract.  

## Task 9
Create a function called "delegate" taking a parameter of type address. This function transfers the caller's voting rights to the address given in parameter.  
This function can only be called from outside the contract. ***Beware of error handling!***  

## Task 10
Create a function called "winnerName" taking no parameters. This function returns the name of the candidate with the most votes.  
This function is read-only and can only be called from outside the contract.  

## Task 11
Add an end date for voting. The end date must be initialized when the contract is deployed.  
The organizer should be able to change this date at any time.
***Only the organizer***

## Final task
Create a Dapp allowing anyone to interact with your own contract !  
To do this, deploy your contract on the Goërli testnet and create an application in ReactJS to interact with this contract.
  
  
# Congratulations, you're done! 🥳🥳🥳
