
### Keywords
+ `pragma` are instructions for compilers
+ `public`
+ `address`:  160-bit state variable that does not allow arithmetic. Store hash of public keypair, contract addresses. 
+ `mapping`: maps one thing type (address) to another (uint)
+ `event`: send/receive events that clients cn listen to cheaply. Args are received by listener to track transactions. 
+ `constructor`: called during creation of contract. 
+ `msg` : global variable that contains stateful access to chain. For example, `msg.sender`. 
+ `require`

+ Complex types
```C++
// This declares a new complex type which will
 // be used for variables later.
 // It will represent a single voter.
 struct Voter {
	 uint weight; // weight is accumulated by delegation
	 bool voted; // if true, that person already voted
	 address delegate; // person delegated to
	 uint vote; // index of the voted proposal
 }

// This is a type for a single proposal.
 struct Proposal {
	 bytes32 name; // short name (up to 32 bytes)
	 uint voteCount; // number of accumulated votes
 }

```

+ **static typing**
	+ `public` and `private` have a deeper meaning here. `public` functions of data are visible to *every* ETH node or contract.
		+ In the toy example, *anyone* can set a variable on the chain.
		+ Impose access restrictions via soliditiy too. 
	+ A transaction is an executed method on a contract
	+ Imposes rights and permissions management through programming structs
		+ "call" a contract -> execute some of its logic

 ```solidity
 // SPDX-License-Identifier: GPL-3.0
 pragma solidity >= 0.4.16 <0.9.0 

 contract simpleStorage {
	unint publicVar

	function set(uint x) public {
		storedData = x;
	}

	function get() public view returns (unit) {
		return storedData;
	}	
 }
 
 ```


### Contract Outline

```
How to deposit ETH to and from [[defi platforms|Aave]] lending pools, using the following steps:
1.  Load the `LendingPoolAddressesProvider` contract.
2.  Retrieve the `LendingPool` address.
3.  Load the `LendingPool`_._
4.  Deposit ETH to the `LendingPool`_._
```


### #todo: Interfaces