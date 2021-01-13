# Develop a todo list and deploy to development

## Dependencies:

- js
- Truffle
- VS code
- MetaMask
- Infura
- HDWalletProvider

**Task:**
Develop a simple task manager and utilize it to connect and deploy on the **Ropsten** Test Networks. For this tutorial, we will deploy to **Ropsten** using **MetaMask** with test-ether. The process for deploying requires setting up an [Infura](http://www.infura.io/) account. We will use the [TruffleSuite](https://www.trufflesuite.com/) development tools and VS Code to create, compile and deploy the smart contract first to a development network and then to the **Ropsten** testnet. Once deployed, we can use [**ropsten.etherscan.io**](https://ropsten.etherscan.io/) to inspect the blocks which have been deployed to the testnet.

The previous modules in this series walk through the entire development and deployment process for creating an Ethereum Dapp, Web front end and deploying it to a Development Network and interacting with it using **MetaMask** , **TruffleSuite** and **Drizzle** from within the **VS Code** development environment.

Rather than focus on front end development and other aspects building a Dapp, this tutorial is focused on the deployment of a smart contract to an ethereum testnet.

The [TruffleSuite](https://github.com/trufflesuite) toolkit provides support for deploying to different networks and the configuration file, truffle-config.js, provides the template for connecting to multiple networks. Previously, we have been using a development network.

**Steps:**

1. Create a new directory: $ mkdir todolist

2. Navigate to the new directory: $ cd todolist

3. Initialize the directory as a Truffle project. $ truffle init

4. Open the project in Visual Studio Code. Then from within VS CCode, open the folder **todolist**.

The directory structure should look like:

![](./Images/TodoList_Directory_Structure1.png)

5. From within VS Code, create the file in the contracts directory **TodoList.sol** and copy in the following code:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity >=0.4.22 <0.8.0;
 
contract TodoList {
 uint public taskCount = 0;
 
 struct Task {
   uint id;
   string taskname;
   bool status;
 }
 
 mapping(uint => Task) public tasks;
 
 event TaskCreated(
   uint id,
   string taskname,
   bool status
 );
 
 event TaskStatus(
   uint id,
   bool status
 );
 
 constructor() public {
   createTask("Todo List Tutorial");
 }
 
 function createTask(string memory _taskname) public {
   taskCount ++;
   tasks[taskCount] = Task(taskCount, _taskname, false);
   emit TaskCreated(taskCount, _taskname, false);
 }
 
 function toggleStatus(uint _id) public {
   Task memory _task = tasks[_id];
   _task.status = !_task.status;
   tasks[_id] = _task;
   emit TaskStatus(_id, _task.status);
 }
 
}
```

6. Create a migration for the todo.sol list in the **./migrations** folder by creating a new file called **2\_deploy\_contracts.js** and copy in the following code into that file to deploy the TodoList smart contract:

```javascript
var TodoList = artifacts.require(&quot;./TodoList.sol&quot;);

module.exports = function(deployer) {
	deployer.deploy(TodoList);
};
```

7. In the main project directory, open **./truffle-config.js** and un-comment the code to deploy on the **development network** which will be deployed to localhost port **8545**. If you prefer to use the ganache app, use port **7545** instead.

```javascript
 networks: {
   development: {
     host: "127.0.0.1",
     port: 8545,
     network_id: "*" // Match any network id
   }
 },
```

8. Open a terminal window and start up a development blockchain using **ganache-cli**: $ ganache-cli

9. In Visual Studio Code, open a terminal window to compile and migrate the TodoList contract to the development network by running: `truffle compile` and then
`truffle migrate --reset`

This will deploy the smart contracts to the development network. At this point, test your contract using the truffle console, inspect and modify the smart contracts. Below we can see that we created a single task when initializing the task list. Using **truffle console**, you can continue to interact with the contract, creating and setting tasks and toggling their status.
