# Setup a new project and integrate OpenZeppelin

And now let’s look at how to incorporate an ERC20 token in our contracts.

## Create a new project

We're going to create a new blockchain project to create a token contract with the help of OpenZeppelin.

Make sure that you already have Truffle and Ganache-CLI installed.

1. Open your terminal and create a new directory called **Token20**. To do that you can type: `mkdir Token20`.
1. Change directories to move inside of the Token20 directory.
1. Type `truffle init` to initialize a new project
1. Wait for your project to be initialized, and then open it in Visual Studio Code.

```output
$ mkdir NewToken
$ cd NewToken/
$ truffle init
✔ Preparing to download box
✔ Downloading
✔ cleaning up temporary files
✔ Setting up box
$ ls
contracts               migrations              test                    truffle-config.js
```

## Setup the project

Once the project has been created and opened in the editor, take a look around the contents.

The product that we're going to be using is the contracts library.

First, you'll want to confirm that you have Node.js installed. If you don't, you can visit the [Node](https://nodejs.org/) website for instructions about how to download it for your platform. To confirm that you have Node.js installed, open the terminal and type: `node`. This will return the version that you have installed on your machine.

Node.js comes with the node package manager (npm) installed as well. This will help you manage other JavaScript built packages and applications.

Going to your terminal, type:
`npm init`

That will open a utility that walks you through the process to create a package.json file which describes the project and stores dependencies that are used in the project. Follow the steps in the utility to easily create a package.json, noting that you can press enter at each prompt to use the default value.

## Setup OpenZeppelin

:::image type="content" source="../media/contract-library.png" alt-text="Visit OpenZeppelin to find out how to install the contracts library":::

In the terminal window, type:
`npm install @openzeppelin/contracts`

Wait for the package to install to your project successfully.

Notice that a couple things happened:

1. The package was added as a dependency in the package.json file
1. There is a node_modules directory that has imported all of the available contracts from OpenZeppelin.
