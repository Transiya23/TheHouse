# TheHouse
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract SocialDatingApp {
    struct User {
        string username;
        string bio;
        address 0x75aa0a940ce414e2c0b81f186df3fdaae2774715;
        uint256 tokenBalance;
    }

    mapping(address => User) public users;

    // Event to emit when a user is registered
    event UserRegistered(string username, address walletAddress);

    // Function to register a new user
    function registerUser(string memory _username, string memory _bio) public {
        require(bytes(_username).length > 0, "Username cannot be empty");
        require(bytes(_bio).length > 0, "Bio cannot be empty");
        require(users[msg.sender].walletAddress == address(0), "User already registered");

        users[msg.sender] = User({
            username: _username,
            bio: _bio,
            walletAddress: msg.sender,
            tokenBalance: 0 // Initial token balance set to 0
        });

        emit UserRegistered(_username, msg.sender);
    }

    // Function to update token balance (simplified version)
    function updateTokenBalance(uint256 _newBalance) public {
        require(users[msg.sender].walletAddress != address(0), "User not registered");
        users[msg.sender].tokenBalance = _newBalance;
    }

    // Add more functions to handle dating app interactions and crypto asset tracking
}

