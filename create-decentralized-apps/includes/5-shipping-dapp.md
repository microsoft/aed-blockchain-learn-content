# Exercise - Create a dapp for a shipping contract

In a previous module, we introduced a smart contract to capture the shipping status of an item from Pending to Shipped to Delivered. The contract also adds a counter which keeps track of the number of times that state of the shipping contract is updated and will display that in the frontend interface.

In this exercise, we'll wire up the contract to a simple dapp to see the status and the number of times that state has been updated.

## The shipping contract

The shipping contract that we'll be using in this example is displayed below. Copy the code and add a new file in VS Code to the same project used in the last unit. The new file should be added in the **contracts/** folder.

```solidity
// SPDX-License-Identifier: MIT
pragma solidity >=0.4.21 <0.7.0;

contract Shipping
{
   // Our predefined values for shipping listed as enums
   enum ShippingStatus { Pending, Shipped, Delivered }
   enum ShipmentStatus { Pending, Shipped, Delivered }
  
   // Save enum ShippingStatus in variable status
   ShippingStatus private status;
   ShipmentStatus public shipstatus;
   uint256 public numupdates;

   // Event to launch when package has arrived
   event LogNewAlert(string description);
   // This initializes our contract state (sets enum to Pending once the program starts)
   constructor() public {
       status = ShippingStatus.Pending;
       numupdates = 0;
   }
   // Function to change to Shipped
   function Shipped() public {
       status = ShippingStatus.Shipped;
       shipstatus = ShipmentStatus.Shipped;
       numupdates = numupdates + 1;
   }
  
   // Function to change to Delivered
   function Delivered() public {
       status = ShippingStatus.Delivered;
       shipstatus = ShipmentStatus.Delivered;
       numupdates = numupdates + 1;
       emit LogNewAlert("Your package has arrived");
   }
  
   // Function to get the status of the shipping
   function getStatus(ShippingStatus _status) internal pure returns (string memory) {

    // Check the current status and return the correct name
    if (ShippingStatus.Pending == _status) return "Pending";
    if (ShippingStatus.Shipped == _status) return "Shipped";
    if (ShippingStatus.Delivered == _status) return "Delivered";
  
   }
   // Get status of your shipped item
   function Status() public view returns (string memory) {
        ShippingStatus _status = status;
        return getStatus(_status);
   }
}
```