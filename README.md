AI Track - InteractionLogger

Overview

The InteractionLogger is a Solidity smart contract designed to log user interactions on the Ethereum blockchain. Each interaction is recorded with the user's address and the timestamp when the interaction occurred. This contract enables transparent and immutable logging of user activities.  

Features

Logs user interactions with their Ethereum address and timestamp.

Stores interactions on-chain in an array.

Emits an event (InteractionLogged) whenever an interaction is recorded.

Allows retrieval of specific interactions by index.

Provides the total number of logged interactions.

Smart Contract

Contract Name: InteractionLogger

pragma solidity ^0.8.0;

contract InteractionLogger {
    struct Interaction {
        address user;
        uint256 timestamp;
    }

    Interaction[] public interactions;

    event InteractionLogged(address indexed user, uint256 timestamp);

    function logInteraction() public {
        interactions.push(Interaction(msg.sender, block.timestamp));
        emit InteractionLogged(msg.sender, block.timestamp);
    }

    function getInteraction(uint256 index) public view returns (address, uint256) {
        require(index < interactions.length, "Index out of bounds");
        Interaction storage interaction = interactions[index];
        return (interaction.user, interaction.timestamp);
    }

    function getTotalInteractions() public view returns (uint256) {
        return interactions.length;
    }
}

Functions

logInteraction()

Records the caller's address and the current timestamp.

Stores the interaction in an array.

Emits an InteractionLogged event.

getInteraction(uint256 index)

Retrieves an interaction at the specified index.

Returns the user's address and timestamp.

Requires that the provided index is within bounds.

getTotalInteractions()

Returns the total number of logged interactions.

Deployment

Compile the contract using Solidity 0.8.0 or later.

Deploy it to an Ethereum-compatible blockchain.

Use a web3-enabled interface (e.g., Hardhat, Truffle, Remix, or Web3.js) to interact with the contract.

Usage

Users call logInteraction() to register their interaction.

Any user can view past interactions using getInteraction(index).

The total number of interactions can be retrieved using getTotalInteractions().

License

This project is open-source and available under the MIT License.

# AI_TRACK
