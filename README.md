// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

/**
 * @title ZenToken
 * @dev Simple ERC-20 Token example, with initial supply and basic ownership.
 */
contract ZenToken is ERC20, Ownable {

    constructor(uint256 initialSupply) ERC20("ZenToken", "ZEN") {
        _mint(msg.sender, initialSupply * 10 ** decimals());
    }

    /**
     * @notice Mint new tokens (only by owner)
     * @param to address to receive tokens
     * @param amount number of tokens to mint
     */
    function mint(address to, uint256 amount) public onlyOwner {
        _mint(to, amount);
    }

    /**
     * @notice Burn tokens from your own balance
     * @param amount number of tokens to burn
     */
    function burn(uint256 amount) public {
        _burn(msg.sender, amount);
    }
}
