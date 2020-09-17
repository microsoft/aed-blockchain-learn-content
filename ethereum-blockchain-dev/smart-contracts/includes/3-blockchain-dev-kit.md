# Exercise: Install the Blockchain Development Kit for Ethereum

## Get started

[Blockchain Development Kit for Ethereum](https://marketplace.visualstudio.com/items?itemName=AzBlockchain.azure-blockchain) is an extension you can use in Visual Studio Code. The extension makes it easy to create, build, and deploy smart contracts on Ethereum ledgers.

Simply go to **Extensions** and search for **Blockchain Development Kit** and install it.

:::image type="content" source="media\bdk-install.png" alt-text="Install Blockchain Development Kit":::

## Dependencies to install

To use the Blockchain Development Kit, you will need to make sure you have the following installed:

### Python

- Need version 2.7.15 or greater
- Please note, you must have Python installed in your `PATH` variable.
- Note: Most computers will come with Python pre-installed, however it might not be up-to-date. To check if you do have Python installed, open up a terminal and type `python`
  - If installed, it will print out the version of Python that you have on your computer
- To install Python, visit[the Python downloads page](https://www.python.org/downloads/) and click on the **Download Python X.X.X** button. Note that the image shows the download option for a Mac computer. If you have a Linux or Windows computer you will be presented with that download option.

:::image type="content" source="media\python-download.png" alt-text="Download Python":::

- Follow the prompts to download Python, and make sure to select the option to **Add Python to PATH** if that's presented to you.

### Node

- Need version 10.15.x or greater
- To install Node, visit the [Node.js downloads page](https://nodejs.org/download/). Select the installer for your platform

:::image type="content" source="media\node-download.png" alt-text="Download Node":::

- To confirm Node.js is installed, open your terminal and type: `node`. If installed successfully, the terminal will return the version of Node.js installed. You can also confirm that npm is installed by typing `npm` in the terminal.

### Git

- Need version 2.10.x or greater
- Visit the [Git downloads page](https://git-scm.com/downloads) and select your platform. Follow the instructions to download Git.

:::image type="content" source="media\git-download.png" alt-text="Download Git":::

- Note that the image shows the download option for a Mac computer. If you have a Linux or Windows computer you will be presented with that download option.
- Once installed, open your terminal and type `git`. If installed successfully, the terminal will return a list of git commands available.

## Create a New Solidity Project with the extension

Once you have all the dependencies installed, you can now use the Blockchain Development Kit to create your first project.

1. Start by adding a new empty directory to your computer for the project. Note: You can open your terminal and type `mkdir newSolidityProject` to create a new directory. Keep note of where this new empty directory is, but you don't need it yet.
2. Open Visual Studio Code.
3. Go to View -> Command Palette. In the search box type: `Blockchain: New Solidity Project`. You'll notice that as you begin to type "Blockchain" a list of commands will be presented.

:::image type="content" source="media\new-solidity-project.png" alt-text="New Solidity project":::

1. For the type of solidity project, select **Create basic project**.
1. Use the UI file explorer pop up to find the folder you created in step 1. Select the folder and in the bottom right-hand of the window you'll see **Project creating...**
1. Sit back and wait for your new Solidity project to be created.

Once it is, open the Explorer and take a look at all the files that were created in the project.

In this project, you will have a boiler plate of Solidity code that you can use. Notice that you have directories for:

- **contracts:** Contains the **HelloBlockchain.sol** and **Migrations.sol** contracts
- **migrations:** Contains an initial migration and a deploy contract.
- **test:** Contains a test for the HelloBlockchain contract written in JavaScript

You'll also have some other config files:

- **package.json:** To define project details and dependencies
- **truffle-config.json:**. To define dependencies and configuration for Truffle

For now we will only focus on the **contracts/** directory.

## Compile the project

We will start by using the **HelloBlockchain.sol** smart contract inside of the contracts folder.

1. Go to contracts/HelloBlockchain.sol
Right click HelloBlockchain.sol
2. Click on **Build Contracts** to compile the smart contract. Note that you might need to change the pragma directive at the top to use `solidity ^0.7.0;`
3. Select View -> Output to see information about the compiled contract

:::image type="content" source="media\build-contracts.png" alt-text="Build contracts":::
