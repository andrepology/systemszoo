> The task is to get fund/liquidity/pool data from one site, and have it update live on another website, queried every so often

### Specification
+ #spec: v0.2
+ #spec v0.1
	1. Data Acquisition: **[[cron jobs | Every Day ]]**, go to [[defi platforms]] and extract indicators for [[Crypto Assets]].
		+ Indicators: 
			+ APY
			+ Liquidity Pool Size / Available Liquidity / Collateral
	2. Write it to a database
	3. Render it to a client side with a line chart
		+ Load everything from a database

### Data Acquisition
+ A: copy out a tag from the basic site, and put it on another, get it to update every few minutes
+ B: Write a collection of view function (getter) calls on contracts on the Aave protocol, collect and store that data. 
+ C: Extract from APIs, native and external
	+ **Aave** API
		+ updates daily
		+ GET `AddressPoolProvider` using CovalentAPI
			+ ChainIDs are relative to ETH(1) and number the dApps that live on the chain. 
	+ **Yearn**
		+ YearnAPI
	+ **Anchor**
		+ GET using StakingAPI
			+ Just for yield
			+ currency_id #todo are these canonical, like chainID?
	+ **Waves**
		+ GET using DefiLlama
			+ `https://api.llama.fi/protocol/waves-exchange`

#worklog 
+ [[2022-03-29]] : a step back
	+ #pulse : [[planningfallacy]] hit hard. A scraping cron job was *not* the best bet.
	+ I now realise The Graph was the best bet. New rough spec:
		+ Copy out uniswap UI
			+ Great way to learn by imitation
				+ Has gql queries already, as well as components ...
				+ Uses`react-charts`
		+ Clarify existing spec
+ [[2022-03-26]]: simplest possible
	+ A [[Streamlit]] app
		+ Write 1 year to csv
		+ Frontend
			+ Select a Platform
			+ Select a Coin
			+ Display Prices
	+ **Then** start to put together react-flask
		+ because you need to gather info about how to deploy to heroku
		+ because you nee to see how Prefect fits within this
+ [[2022-03-24]] : eveything at once 
	+ [x] Set up wallet
		+ `sniff then stuff outside kangaroo hammer skull cupboard pitch aware hamster square`
	+ Script that pulls from APIs!
		+ these are protocols that have their own coins. Not sure where to go from here.
	+ read up on Aave FAQ and glossary
		+ Deposit crypto assets into a liquidity pool. That initial deposit (lending) qualifies you to borrow. 
			+ The liquidity is over 4 markets
				+ Within a market  (ETH ($13 billion, the biggest chunk)) there are assets supplied
					+ Binance USD
					+ Gemini Dollar
					+ etc
			+ Earn passive income from the deposit, summarised in APY (average per year) or crypto interest. 
				+ ![[Screenshot 2022-03-24 at 2.18.14 PM.png]]
				+ The APY is really high in relation to regular interest rates.
					+ Spotted `yearn.finance` . Hunt for waves now. 
						+ What does this mean though lol. 
						+ Means: API -> Asssets -> ETH -> yearn.finance
			+ Aave coin is used to vote on the protocol. 
			+ Borrowing is through flash loans
		+ Interact with the entire protocol over an ABI. 
			+ #example : isolate a new asset, only borrow a few types of assets. 
	
	+ Staking pool
		+ Staking is the same as depositing?
		+ Can mean
			+ Putting Aave into a pool.
			+ The purpose of staking is to act as a mitigation tool in case of a shortfall event. As an incentive to protect the protocol Safety Module stakers will receive AAVE as Safety Incentives (SI).
	
	+ Getting quite lost in this
		+ Querying the protocol
			+ [GraphQL](https://thegraph.com/hosted-service/subgraph/aave/protocol-v2?selected=playground)
		+ Getting from an API
			+ Where do I get the underlyingAsset id?
				+ Shared at Etherscan?
	+ How do I execute web3.js
	
	+ contracts
		+ expose user-oriented **actions** invoked using
			+ Solidity
				+ with Remix as IDE
			+ web3
				+ web3.js
		+ actions like
			+ deposit
				+ `function deposit( address _reserve, uint256 _amount, uint16 _referralCode)`
					+ notice static typing
					+ notice `address`: address of underling asset
						+ ooh! DAI

### Later
+ Convert currencies
	+ Coingecko
		+ mentioned by defi llama too
+ dApp for view functions on Aave contracts to retrieve PoolAddress. 
	+ For Chains not supported by Covalent
+ Replace with [aave-js](https://github.com/aave/aave-js/blob/master/README.md#reserve-data)
	+ Might need gql queries, good time to learn
		+ See aave-ui or uniswap-ui, both have apollo queries that do this.
	+ [Subgraph](https://docs.aave.com/developers/v/1.0/integrating-aave/using-graphql)
		+ More about [Subgraph](https://docs.aave.com/developers/v/2.0/getting-started/using-graphql#aaves-subgraphs)
		+ Querying subgraph [for APY](https://docs.aave.com/developers/v/2.0/guides/apy-and-apr)