# Changingownersolidity
  // SPDX-License-Identifier: GPL-3.0

pragma solidity ^0.8.2;
import "hardhat/console.sol";

 contract Owner{
    address private owner;
    event Ownerset(address indexed oldOwner, address indexed newOwner);

    modifier isOwner() {
     require(msg.sender == owner, "Caller is not owner" );
     _;
      }

      constructor() {
         console.log("Owner Contract deployed by:", msg.sender);
         owner= msg.sender;
         emit Ownerset(address(0), owner);
      }
      function changeowner(address newOwner) public isOwner{
         emit Ownerset(owner, newOwner);
         owner = newOwner;
      }
      function getOwner() external view returns (address){
         return owner;
      }
 }
