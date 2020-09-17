# Exercise: Write a smart contract with the Blockchain Development Kit for Ethereum

In the project you created earlier, under the **contracts/** directory, select to create a new file called **Shipping.sol**.

Copy over the contents of this contract below:

```solidity
pragma solidity ^0.7.0;

contract Shipping
{
    // Our predefined values for shipping listed as enums
    enum ShippingStatus { Pending, Shipped, Delivered }
    ShippingStatus public status;

    // This initializes our contract state (sets enum to Pending once the program starts)
    constructor() public {
        status = ShippingStatus.Pending;
    }

    // Function to change to Shipped
    function Shipped() public {
        status = ShippingStatus.Shipped;
    }

    // Function to change to Delivered
    function Delivered() public {
        status = ShippingStatus.Delivered;
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
