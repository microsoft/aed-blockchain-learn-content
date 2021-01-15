# Exercise - Deploy to the Ropsten test network

Now that we have a smart contract, and have successfully deployed it to our development network, we will focus this exercise on deploying to the Ropsten test network.

## Exercise overview

For this tutorial, we will deploy to **Ropsten** using **MetaMask** with test-ether. The process for deploying requires setting up an [Infura](http://www.infura.io/) account. We'll use the [TruffleSuite](https://www.trufflesuite.com/) development tools and VS Code to create, compile and deploy the smart contract first to a development network and then to the **Ropsten** testnet. Once deployed, we can use [ropsten.etherscan.io](https://ropsten.etherscan.io/) to inspect the blocks which have been deployed to the testnet.

Deploying to a test network requires **test ethers**, which do not have value. Every blockchain interaction with a smart contract costs some fees (gas) and the interaction is known as a **transaction**. To get **test ethers** use an an Ether Faucet. For the **Ropsten** test network, **test ethers** can be acquired from a **Ropsten Ethereum Faucet**.

## Project setup

### Metamask

If you haven’t done so already, install and set up Metamask by visiting [www.metamask.io](www.metamask.io) and following the prompts.

### Add Ether to Metatmask Ropsten test network

Using your Metamask account, connect to the Ropsten test network. If you don’t have any test Ether already, get some from the Ropsten Test Faucet at [https://faucet.ropsten.be](https://faucet.ropsten.be).

1. Open MetaMask
2. Connect to Ropsten
3. Copy the address of your account to the clipboard

:::image type="content" source="media\Metamask_0_Eth_Connect.png" alt-text="Screenshot showing the Metamask browser extension to copy the account address":::

4. Open a browser window or tab, and navigate to: [https://faucet.ropsten.be/](https://faucet.ropsten.be/)
5. Request ether by entering your testnet account address and clicking on the button “Send me test Ether”.

:::image type="content" source="media\Ropsten_Test_Faucet_Request_Ether.png" alt-text="Screenshot showing how to request test ether on the Ropsten faucet":::

6. Go back to **Metamask** and verify that you now have Ether in your account.

:::image type="content" source="media\Metamask_Ropsten_Test_with_1_Ether.png" alt-text="Screenshot showing the Metamask browser extension with 1 Ether":::

### HDWalletProvider

You'll need [HDWalletProvider](https://www.npmjs.com/package/@truffle/hdwallet-provider) as a wallet enabled web3 provider to provide your secret mnemonic and connection network address and [fs](https://www.npmjs.com/package/fs) to read from your filesystem. For this part of the installation, you will need to run the following commands in your project directory from a terminal window:

1. npm init
2. npm install fs
3. npm install @truffle/hdwallet-provider

Wait for the installations of fs and HDWalletProvider to complete. You may see a number of warnings but unless there are errors, they can be ignored.

### Setting up Infura account and linking the endpoints to the Ropsten Test Network

[Infura](https://infura.io/) development suite provides instant, scalable **API** access to the Ethereum networks. Setting up an account is easy and has no cost.

**Infura overview:**

- Infura is a hosted Ethereum node cluster which gives users the ability to run an application on a public network. Infura gives users the ability to:
  - Interact with Ethereum networks like Ropsten, Rinkeby or the Mainnet.
  - Deploy contracts to Ethereum networks.
  - Interact with contracts on Ethereum networks.
- Sign up and get started with Infura - go to [www.infura.io](http://www.infura.io/)
  - Set up an account and confirm your email address
  - Once you have an account, set up a project and select the endpoints to point to a **Ropsten** test network.
  - It should look similar to the Test Project below.

:::image type="content" source="media\Infura_Test_Project.png" alt-text="Screenshot showing the process of creating an Infura project.":::

## Connect to Ropsten

Make sure the *todolist* project folder is open in Visual Studio Code.

In the **Truffle** configuration file, *./truffle-config.js*,  un-comment the lines for **HDWallet Provider**, **InfruaKey**, **fs** and **mnemonic**:

```javascript
 const HDWalletProvider = require('@truffle/hdwallet-provider');
 const infuraKey = "fj4jll3k.....";
 
 const fs = require('fs');
 const mnemonic = fs.readFileSync(".secret").toString().trim();
```

Go to your **Infura** account, and copy the **InfuraKey** for the **endpoint** by clicking on the clipboard:

:::image type="content" source="media\Ropsten_EndPoint.png" alt-text="Screenshot focused on the Ropsten endpoint to copy.":::

Copy the numeric part of the key to the **./truffle-config.js** - below is a sample, your key will be different:

```javascript
const infuraKey = "4205b62c0a104f1e95d9771a48068d04";
```

Create a file called **.secret** and copy your **mnemonic seed** to that file. The **mneumonic seed phrase** can be found in the settings portion of your **Metamask** account. Do not share this with anyone or they will be able to access your account! If you are using **git**, include **.secret** in your **.gitignore** file.

:::image type="content" source="media\Reveal_Metamask_Seed_Phrase.png" alt-text="Screenshot to show how to reveal seed phrase in Metamask.":::

The code below will read the seed phrase from the file **.secret** and trim all the white spaces:

```javascript
const mnemonic = fs.readFileSync(".secret").toString().trim();
```

Now define the network by un-commenting the *Ropsten* network settings in **truffle-config.js**. Make sure that your configuration looks like the following:

```javascript
ropsten: {
   provider: () => new HDWalletProvider(mnemonic, `https://ropsten.infura.io/v3/${infuraKey}`),
   network_id: 3,       // Ropsten's id
   gas: 5500000,        // Ropsten has a lower block limit than mainnet
   confirmations: 2,    // # of confs to wait between deployments. (default: 0)
   timeoutBlocks: 200,  // # of blocks before a deployment times out  (minimum/default: 50)
   skipDryRun: true     // Skip dry run before migrations? (default: false for public nets )
 },
```

## Deploy to Ropsten

To deploy to Ropsten run the following command from the Visual Studio Code terminal: **truffle migrate --network ropsten**

If your connection is successful, you will see the following output:

```output
Compiling your contracts...
===========================
> Everything is up to date, there is nothing to compile.

Warning: Both truffle-config.js and truffle.js were found. Using truffle-config.js.

Compiling your contracts...
===========================
> Everything is up to date, there is nothing to compile.


Starting migrations...
======================
> Network name:    'ropsten'
> Network id:      3
> Block gas limit: 8000029 (0x7a121d)


1_initial_migration.js
======================

   Deploying 'Migrations'
   ----------------------
   > transaction hash:    0x2f456acc5f842ddf0eb151742e47dd6e8ec5e48d73b1f150e2908cb56e0bf174
   > Blocks: 1            Seconds: 29
   > contract address:    0x789101d0B0Ffa4f8f87E67AF8ff8F84bD519752D
   > block number:        9398701
   > block timestamp:     1609784599
   > account:             0x896587D82C895F30433cade401068C2791A6936F
   > balance:             0.99616138
   > gas used:            191931 (0x2edbb)
   > gas price:           20 gwei
   > value sent:          0 ETH
   > total cost:          0.00383862 ETH

   Pausing for 2 confirmations...
   ------------------------------
   > confirmation number: 1 (block: 9398702)
   > confirmation number: 2 (block: 9398703)

   > Saving migration to chain.
   > Saving artifacts
   -------------------------------------
   > Total cost:          0.00383862 ETH


2_deploy_contracts.js
=====================

   Deploying 'TodoList'
   --------------------
   > transaction hash:    0xad8066308e9cc8503400c86a43674d856a71e02696e2c21b3e55f566df5afc36
   > Blocks: 0            Seconds: 8
   > contract address:    0x48112BE8d0E6e7bA892aFa2d4Ab58e9c43dd37De
   > block number:        9398706
   > block timestamp:     1609784870
   > account:             0x896587D82C895F30433cade401068C2791A6936F
   > balance:             0.98513544
   > gas used:            508959 (0x7c41f)
   > gas price:           20 gwei
   > value sent:          0 ETH
   > total cost:          0.01017918 ETH

   Pausing for 2 confirmations...
   ------------------------------
   > confirmation number: 1 (block: 9398707)
   > confirmation number: 2 (block: 9398708)

   > Saving migration to chain.
   > Saving artifacts
   -------------------------------------
   > Total cost:          0.01017918 ETH


Summary
=======
> Total deployments:   2
> Final cost:          0.0140178 ETH
```

## Verify deployment of contract

## On Metamask

Inspect Metamask to verify that the ether used to deploy the contract

![](./Images/Metamask_balance_after_deploying_to Ropsten.png)

## On Ropsten Etherscan

Go to [ropsten.etherscan.io](ropsten.etherscan.io), enter in the contract address and inspect your contract.

:::image type="content" source="media\Ropsten_Etherscan_with_deployed_contract.png" alt-text="Screenshot showing the contract deployed in Etherscan .":::

You can also open a new terminal window within Visual Studio Code and similar to interacting with your contract on the ganache development blockchain, you can interact with your contract with the **truffle console**. The sample code below displays two networks which are active. Continue to interact with and inspect transactions using *truffle console* and *Ropsten Etherscan*.
