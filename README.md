# Biryani Token (BIRYANI) Smart Contract

## Overview

The Biryani Token (BIRYANI) is an ERC20-compliant token built on the Ethereum blockchain. This token includes additional functionalities like minting, burning, and redeeming tokens for different types of biryani. The contract also supports transferring tokens between accounts.

## Features

1. **Minting Tokens**: The owner of the contract can mint new tokens.
2. **Burning Tokens**: Any token holder can burn their tokens.
3. **Transferring Tokens**: Token holders can transfer their tokens to other accounts.
4. **Redeeming Tokens for Biryani**: Token holders can redeem their tokens for different types of biryani (Chicken, Mutton, and Egg).

## Smart Contract Details

### Prerequisites

The smart contract is written in Solidity and requires Solidity version ^0.8.0. It also depends on OpenZeppelin's ERC20, Ownable, and ERC20Burnable contracts.

### Contract Structure

1. **Imports**: The contract imports the ERC20, Ownable, and ERC20Burnable contracts from the OpenZeppelin library.
2. **Events**: 
    - `LogMessage(string message)`: Logs generic messages.
    - `BiryaniRedeemed(address indexed player, uint256 amount, string productName)`: Logs details when biryani is redeemed.
3. **Enum**: 
    - `BiryaniType { Chicken, Mutton, Egg }`: Enum to represent different types of biryani.
4. **State Variables**: 
    - `biryaniRates`: A mapping to store the token rates for different types of biryani.
    - `recentlyRedeemedBiryani`: Stores the type of the most recently redeemed biryani.

### Functions

- **Constructor**: Initializes the contract with the owner's address and sets the initial biryani prices.
- **setPrices()**: Internal function to set the prices for different types of biryani.
- **mintTokens(address beneficiary, uint256 amount)**: Allows the owner to mint new tokens to a beneficiary's address.
- **burnTokens(uint256 amount)**: Allows a token holder to burn a specified amount of their tokens.
- **transferTokens(address recipient, uint256 amount)**: Allows a token holder to transfer tokens to another address.
- **redeemForBiryani(uint256 tokenAmount)**: Allows a token holder to redeem their tokens for biryani. The type of biryani is determined based on the token amount provided.
- **showRedeemedItem()**: Returns the name of the most recently redeemed biryani.
- **getBiryaniTypeName(BiryaniType _type)**: Internal pure function to convert `BiryaniType` enum values to their corresponding string names.

## Usage

### Deploying the Contract

To deploy the contract, you need to provide the initial owner's address. For example:

```solidity
address initialOwner = 0xYourEthereumAddress;
BiryaniToken biryaniToken = new BiryaniToken(initialOwner);
```

### Minting Tokens

Only the owner can mint tokens:

```solidity
biryaniToken.mintTokens(0xBeneficiaryAddress, amount);
```

### Burning Tokens

Any token holder can burn their tokens:

```solidity
biryaniToken.burnTokens(amount);
```

### Transferring Tokens

Token holders can transfer their tokens to other accounts:

```solidity
biryaniToken.transferTokens(0xRecipientAddress, amount);
```

### Redeeming Tokens for Biryani

Token holders can redeem their tokens for biryani:

```solidity
biryaniToken.redeemForBiryani(tokenAmount);
```

### Viewing the Most Recently Redeemed Biryani

To view the name of the most recently redeemed biryani:

```solidity
string memory lastRedeemedBiryani = biryaniToken.showRedeemedItem();
```

## License

This project is licensed under the MIT License. See the LICENSE file for more details.

## Acknowledgements

This contract uses OpenZeppelin's ERC20, Ownable, and ERC20Burnable contracts. Thanks to the OpenZeppelin team for their high-quality library.
