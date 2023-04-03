## Document Properties

| Client         | UniSwap                                     |
| :------------- | :--------------------------------------------- |
| Title          | Smart Contract Audit Report                    |
| Target         | UniSwap NFTPositionManager                      |
| Version        | 1.0                                            |
| Author         | [Godswill Akpan](https://github.com/geeakpan) |
| Classification | Public                                         |
| Version | Date           | Author                                         | Description   |
| :------ | :------------- | :--------------------------------------------- | :------------ |
| 1.0     | April 02, 2023 | [Godswill Akpan](https://github.com/geeakpan) | Final Release |


## Table of contents



The NonfungiblePositionManager contract inherits from several other contracts that define various features required for the contract's operation. These include:

INonfungiblePositionManager: a minimal interface specifying the required functions for a contract to be used as a Uniswap V3 position NFT manager.
Multicall: a contract that allows multiple external function calls to be batched into a single transaction, saving on gas fees.
ERC721Permit: an extension of the ERC721 standard that allows the owner of a token to sign a permit, allowing another address to transfer the token on their behalf without the need for an additional signature.
PeripheryImmutableState: a base contract defining the immutable state variables shared across all periphery contracts, such as the Uniswap V3 factory address and the WETH9 token address.
PoolInitializer: a contract that provides the function for initializing a new Uniswap V3 pool.
LiquidityManagement: a contract that provides the functions for adding and removing liquidity to a Uniswap V3 pool.
PeripheryValidation: a contract that provides validation for Uniswap V3 function inputs.
SelfPermit: a contract that provides the function for generating permits that allow an owner to execute an action on their own tokens.
The NonfungiblePositionManager contract defines a Position struct that stores the details of a given Uniswap V3 position NFT, including the token ID, operator address, pool ID, tick range, liquidity, fee growth, and owed tokens. The contract also defines a series of mappings that allow the contract to map Uniswap pool keys to pool IDs, cache pool keys, and store position data based on token IDs.

The contract implements the positions() and mint() functions defined by the INonfungiblePositionManager interface. The positions() function retrieves the details of a given position token using the token ID, while the mint() function allows users to add liquidity to a Uniswap V3 pool and mint a new NFT representing their position in the pool.

Other functions include cachePoolKey(), which caches a pool key to save on storage costs, and _safeTransfer(), which safely transfers a given token to a recipient address. Finally, the contract defines a constructor that initializes the contract with the Uniswap V3 factory address, the WETH9 token address, and the address of the token descriptor contract used to generate token URIs.
