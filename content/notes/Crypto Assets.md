> These are tokens that live on blockchains

Each have unique addresses, and are typically transferred and interacted with using [[solidity]]

+ WETHGateway
	+ Swap our ETH with WETH for interoperability
		+ Found on ETHERSCAN
+ Swap ETH for WETH
	+ wrapped ether
	+ address
		+ brownie-config
			+ networks
				+ kovan
					+ weth_token: address
		+ Interfaces
			+ iweth.sol
				+ has functions for erc20
