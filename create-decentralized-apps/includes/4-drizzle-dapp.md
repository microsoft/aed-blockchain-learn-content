# Exercise -  Get started with Drizzle

We can use [Truffle Boxes](https://www.trufflesuite.com/boxes) as boilerplates that can contain helpful modules, Solidity contracts & libraries, front-end views and more; all the way up to complete
example dapps.

For this exercise we'll be using [**Drizzle-box**](https://www.trufflesuite.com/boxes/drizzle) to build our first dapp and give you an overview of Drizzle's capabilities.

The **Drizzle** box comes with several out of the box smart contracts to check out and a
simplified **truffle-config.js** designed for development and testing.
If using a prior **truffle project,** first create a clean and empty
folder, **unbox** **Drizzle**, then copy over the current project -
smart contracts, migrations, and other project-specific files.

Using Drizzle to wire smart contacts to a front-end server
----------------------------------------------------------

Unboxing Drizzle results in essentially two separate projects within a
single directory: a **truffle** project and a **drizzle-react client**
project**.** If you already have experience with **Truffle**, then
directory structure will look familiar in the Smart Contract area. The
primary difference will be how you wire it to **Web3** and
configurations modification which need to be taken into account.

Step1: Create a clean, empty directory and scaffold out a drizzle-react
project using the [Truffle Drizzle
Box](https://www.trufflesuite.com/boxes/drizzle) using the
following steps:

-   First, create a new empty directory and unbox Drizzle in that
    directory:

    -   mkdir drizzle_tutorial

    -   cd drizzle_tutorial

    -   truffle unbox drizzle

> ![](media\image7.png)
-   **Unboxing Drizzle** may take a few minutes and will scaffold out a
    react app project. There is no need to run "**create-react-app**".
    Open **VSCode** and the directory structure will look like this:

> ![](media\image8.png)
-   Unboxing drizzle has installed the node module for \@drizzle under
    the ./app/node_modules folder:

> ![](media\image9.png)
-   In the Terminal, run the Truffle development console which spawns a
    development blockchain. This is very useful for compiling, deploying
    and testing locally and creates a list of 10 accounts.

    -   truffle develop

> ![](media\image10.png)
-   From the development console for truffle, compile and migrate the
    smart contracts to the development blockchain. If desired, both
    ganache app and ganache-cli can also be used. Please see
    documentation for how to use it. The development blockchain will be
    running at [http://127.0.0.1:8545](http://127.0.0.1:8545).
    Consequently, ./truffle-config.js will require this same host and
    port address.

> ![](media\image11.png)
The **Truffle Drizzle-Box** comes with three contracts that use the
drizzle components for connecting to a Dapp. The contracts directory
contains the files: **ComplexStorage.sol**, **SimpleStorage.sol** and
**TutorialToken.sol** which are used by the **Drizzle** tutorial.

Using the Truffle develop console, compile these smart contracts:

> ![](media\image12.png)
Deploying and Migrating Smart Contracts
---------------------------------------

-   To deploy a smart contract, Truffle requires a migrations file in
    the migrations folder. The migration files are numbered and executed
    in the order in which they are numbers. The initial migration file
    begins with the number "1" and is called "1_initial_migration.js".
    Additional migration files need a number larger than 1. All of the
    contacts can be migrated using a single file or multiple files.

-   The migrations folder has JavaScript files that help you deploy
    contracts to the network. These files are responsible for staging
    your deployment tasks, and they're written under the assumption that
    your deployment needs will change over time. A history of previously
    run migrations is recorded on-chain through a special Migrations
    contract. (source: [truffle:
    running-migrations](https://www.trufflesuite.com/docs/truffle/getting-started/running-migrations))

-   Take a look in the file **2_deploy_contracts.js** located in the
    migrations folder.

> ![](media\image13.png)
-   From the development console, execute the command migrate to migrate
    and deploy the smart contracts.

> ![](media\image14.png)
>
> ![](media\image15.png)
Testing the Smart Contracts
---------------------------

Truffle has an automated testing framework to facilitate the testing of
contracts. All test files should be located in the test directory. To
learn more, go to the Truffle documentation, in the section testing your
contracts. The Truffle box comes with the file **simplestorage.js** for
testing the smart contract.

In the Truffle console, test the **SimpleStorage** contract using the
**test** command:

![](media\image16.png)

The dApp
--------

The Drizzle Box includes code using the dizzle libraries to connect the
smart contracts to the dapp's front-end. That code exists within the
\`app\` directory.

> ![](media\image17.png)
Wiring up the front-end to the smart contract
---------------------------------------------

The files in the **/app** folder which are of interest for connecting
the smart contract to the Dapp are: **app.js**, **drizzleOptions.js**
and **MyComponent.js.** Using the SimpleStorage contract, below are the
steps for connecting the contract to the front-end:

-   The file **MyComponent.js** creates the component for connecting the
    SimpleStorage smart contract with the front-end.

> ![](media\image18.png)
>
> ![](media\image19.png)
-   **drizzleOptions.js** is used to create an **options** object and
    pass in the desired contract artifacts for **Drizzle** to
    instantiate. The **options** object sets up and instantiates the
    Drizzle store. Note that in this example, Web3 is connecting to
    localhost port
    8545.![](media\image20.png)

-   **App.js** contains the code for the main app. It requires importing
    React and the Drizzle libraries. It must also import the component
    file which interacts directly with the smart contract.

> ![](media\image21.png)
In another terminal:

Open a new terminal window, and from the **./app** folder start up a
local browser using this commands:

-   cd app

-   npm rebuild

-   npm run start

> ![](media\image22.png)
This command starts the web-pack dev server for React and opens up a new
browser window for the React project which should result in the image
below. Once this has been tested, close it by either closing the
terminal window or \<ctrl-c\>. This confirms that react was correctly
installed. React starts a web browser on
[http://localhost:3000](http://localhost:3000) and automatically
opens a browser window.

![](media\image23.png)