## EventToken Solidity Smart Contract - README

### Overview
The `EventToken` smart contract is an ERC20 token implementation using OpenZeppelin libraries, specifically designed for managing event tickets. Users can purchase, transfer, and redeem tokens for event tickets. The contract owner has the ability to mint new tokens as needed.

### Features
- **Minting Tokens:** The contract owner can mint new tokens and assign them to any account.
- **Burning Tokens:** Users can burn their own tokens, which permanently reduces their token balance.
- **Token Transfer:** Users can transfer tokens to others.
- **Ticket Redemption:** Users can redeem their tokens for event tickets, which reduces the available ticket count for the selected event.
- **Viewing Tickets:** Users can view the number of tickets they hold for various events.

### Events
- `LogMessage(string message)`: Emits a message for logging purposes.
- `TicketPurchased(address indexed account, string eventName, uint256 quantity)`: Emitted when a user successfully purchases tickets.

### Contract Details

#### 1. Constructor
- Initializes the contract with predefined ticket costs and available counts for events: Concert, Movie, Workshop, and Festival.

#### 2. Minting Tokens (`mintTokens`)
- **Parameters:**
  - `account`: The address that will receive the minted tokens.
  - `amount`: The number of tokens to mint.
- **Access:** Only the contract owner can mint tokens.

#### 3. Burning Tokens (`burnTokens`)
- **Parameters:**
  - `amount`: The number of tokens to burn from the caller's account.
- **Restrictions:** Caller must have sufficient tokens to burn.

#### 4. Transferring Tokens (`transferTokens`)
- **Parameters:**
  - `recipient`: The address that will receive the transferred tokens.
  - `amount`: The number of tokens to transfer.
- **Restrictions:** Caller must have sufficient tokens to transfer.

#### 5. Redeeming Tickets (`redeemTickets`)
- **Parameters:**
  - `eventName`: The name of the event for which tickets are being redeemed.
  - `quantity`: The number of tickets to redeem.
- **Restrictions:** 
  - The event name must not be empty.
  - The caller must have enough tokens to cover the total cost.
  - There must be enough tickets available for the selected event.

#### 6. Viewing Tickets (`myTickets`)
- **Returns:**
  - `eventNames`: An array of event names for which the caller has tickets.
  - `quantities`: An array of quantities corresponding to each event name.
- **Details:** Allows users to view the number of tickets they hold for each event.

### Installation
1. Install the required dependencies:
   ```bash
   npm install @openzeppelin/contracts
   ```
2. Deploy the contract using a compatible Ethereum development framework like Truffle or Hardhat.

### Usage
- **Mint Tokens:** The owner can call `mintTokens` to create more tokens.
- **Transfer Tokens:** Users can transfer tokens using `transferTokens`.
- **Burn Tokens:** Users can reduce their token balance by burning tokens via `burnTokens`.
- **Redeem Tickets:** Users can exchange their tokens for event tickets using `redeemTickets`.
- **View Tickets:** Users can see their tickets by calling `myTickets`.

### Example Workflow
1. **Owner mints tokens:** 
   ```solidity
   mintTokens(0xYourAddress, 5000);
   ```
2. **User transfers tokens:**
   ```solidity
   transferTokens(0xRecipientAddress, 100);
   ```
3. **User redeems tickets:**
   ```solidity
   redeemTickets("Concert", 2);
   ```
4. **User views their tickets:**
   ```solidity
   (eventNames, quantities) = myTickets();
   ```

### License
This project is licensed under the MIT License.
