### Aave
+ Aave protocol comprises liquidity markets, one for each Chain
	+ Ethereum
		+ Mainnet
		+ Testnet
			+ Kovan 
			+ Ropsten
+ Within each market, we find **Contracts** associated with each liquidity pool. 
	+ **Contract** is a collection of code (functions) and data (state) that resides at **a specific address on the blockchain**. 
		+ As a result, an Aave market is a "deployed contract"
	+ Interaction with contracts is done with dApps overall, but through ABIs specifically
		+ the **compiled version of an API.** 
		+ contracts are stored as **bytecodes** in a binary format into the blockchain under a specific address. 
		+ No one understands binary, so the **ABI** defines the structures and methods that you will use to interact with that binary contract
		+ The ABI indicates to the caller the needed information (functions signatures and variables declarations) to **encode a meaningful**(understood by the VM) call to the bytecode(contract).
		+ Akin to Objects, with View and Write methods that are cryptographically signed. 
		+ "Interaction", in a lending protocol, primarily has to do with:
			+ LendingPool is the "main contract" (ref: docs) because it handles the `deposit()` , `swap()` , `borrow()` , `liquidationCall()`, `flashloan` methods: the dominant interactions with the protocol for lending. 
			+ Also includes View Methods like `getReserveData()`
			+ BUT: is there just one pool per coin within a market? If so, then `getReserveData()` is all you need ...
	+ **Versioned** (v1, v2, v3) to the Protocol
	+ **Reserves** refer to the ERC-20 contracts of the underlying assets
		+ These are coins
			+ ETH/Bitcoin
			+ DAI, USDC : value fixed to dollar or stablecoins. 

+ **Avalanche** is another side chain market on Aave
	+ As an alternative to ETH, it hosts native assets
		+ Uses the EVM
	+ Also hosts 'Bridged' ethereum assets can also be staked
		+ Occurs between EVM-compatible networks (Binanace, Avalanche, Fantom)
	+ An EVM is what is maintained by each Ethereum client
		+ Where are accounts and contracts live
		+ One and only one canonical state
		+ Defines the rules for computing a new valid state from block to block
			+ For example, not spending the same coin twice
		+ Enables smart contracts, missing from Bitcoin
			+ Hence, instead of a distributed ledger, it is a distributed state machine
				+ A data structure
				+ A state machine that can execute arbitrary code
			+ Transcations
				+ Blockchain is a globally shared, transactional database.
					+ Everyone can read
						+ How so?
					+ Transactions added to the database have to be accepted on the whole, immutable. 
				+ Cryptographically signed *instructions* from accounts. Results in message calls or contract creation.
					+ New contracts contain ***compiled** smart contract **bytecode***
						+ This bytecode is executed when another account makes a message call to that contract. 
			+ State
				+ Giant Merkle Patricia Trie, linking accounts by hashses and single root
					+ Accounts
						+ External (humans, controlled by public-private key pairs)
						+ Contract (code stored with account)




+ Gas
	+ Limits amount of work needed to execute transaction. 
		+ Depleted during a transaction
	+ Gas Price * gas is paid by sending account. 
		+ Refunded if leftover, reverted if overshot

