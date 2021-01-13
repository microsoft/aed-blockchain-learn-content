# Overview of public Ethereum networks

The [Ethereum](https://ethereum.org/?azure-portal=true) protocol is made up of multiple public networks. Different Ethereum networks can have different properties, uses, functionality and consensus mechanisms. There are four different test networks, called testnets, and one production network, called mainnet.

## An overview of mainnet

[Mainnet](https://ethereum.org/en/glossary/#mainnet), short for "main network" is the one real public Ethereum blockchain. Applications that are deployed to the mainnet can exchange and use information and interact with one another.

Once deployed, the applications can leverage the full potential of decentralized blockchain. There is no centralized authority and mainnet is fully decentralized. There can be different types of tokens and applications deployed to mainnnet. Once deployed on the mainnet, transactions are immutable and cannot be changed. In addition, each transaction has real costs associated with it which requires actual Ether (ETH). All blocks on the Ethereum mainnet can be viewed using [Etherscan](https://etherscan.io/) which shows the latest mined blocks and transactions. All blocks can be inspected.

:::image type="content" source="media\etherscan.png" alt-text="Screenshot showing the homepage of Etherscan":::

## Ethereum Testnets, Faucets and Deployment

Deploying directly to mainnet is not recommended and very high risk. There are four public testnets, each with a different deployment method and process. They are used to stage and test applications in a live public environment prior to deploying to the mainnet.

 Most testnets require that test ether that is accessed from what are called *faucets*. Using a faucet protects the testnet from spam attacks since the ether is controlled by trusted parties. This has become the primary way to acquire ether for a specific testnet. The community manages these public test networks for the benefit of developers and testing.

### Testnet Comparison

Let’s take a look at the different [Ethereum testnets](https://ethereum.org/en/developers/docs/networks/#testnets) and associated properties.

[**Ropsten**](https://ropsten.etherscan.io/?azure-portal=true)

Ropsten is a [Proof of Work](https://www.investopedia.com/terms/p/proof-work.asp?azure-portal=true) consensus protocol, closest to mainnet in functionality. Named after a Swedish subway station and has been around since 2016. It is said to have the best reproduction of the conditions on the the mainnet, and can be used with all clients.

- Features:
  - Supports Geth and OpenEthereum clients
  - Network Id: 3
  - Block time: sub-30 seconds
  - Faucet: [https://faucet.ropsten.be/](https://faucet.ropsten.be/)
  - Explorer: [https://ropsten.etherscan.io/](https://ropsten.etherscan.io/)
  - GitHub: [https://github.com/ethereum/ropsten](https://github.com/ethereum/ropsten)

[**Kovan**](https://kovan-testnet.github.io/website/?azure-portal=true)

[Proof of authority](https://academy.binance.com/en/articles/proof-of-authority-explained/?azure-portal=true) (PoA) testnet is named after a subway station in Singapore. Ether can't be mined. It has to be requested from the faucet and is controlled by trusted parties. Because of this property, it is immune to spam attacks.

- Features:
  - Supports Geth and OpenEthereum clients
  - Network Id: 42
  - Block time: 4 seconds
  - Faucet: [https://faucet.kovan.network/](https://faucet.kovan.network/)
  - Explorer: [https://kovan.etherscan.io/](https://kovan.etherscan.io/)
  - GitHub: [https://github.com/kovan-testnet/proposal](https://github.com/kovan-testnet/proposal)

[Rinkeby](https://www.rinkeby.io/?azure-portal=true)

Proof of Authority, PoA, testnet started by the Ethereum team in April 2017 is named after a metro station in Stockholm.

- Features:
  - Only supports [Geth](https://geth.ethereum.org/?azure-portal=true) client
  - Network Id: 4
  - Block time: 15 seconds
  - Faucet: [https://faucet.rinkeby.io/](https://faucet.rinkeby.io/)
  - Explorer: [https://rinkeby.etherscan.io/](https://rinkeby.etherscan.io/)
  - GitHub: [https://github.com/ethereum/EIPs/issues/225](https://github.com/ethereum/EIPs/issues/225)
  - Website: [https://www.rinkeby.io](https://www.rinkeby.io)

[Görli](https://goerli.net/?azure-portal=true)

Proof of Authority cross-client testnet and named after a Berlin subway station. This testnet has the goal of being both widely usable across various clients and supports Clique Proof of Authority (PoA). It is robust enough to guarantee consistent availability and was started by the Goerli Initiative in 2018.

- Features:
  - Supports multiple clients like Geth, Pantheon, Nethermind, and OpenEthereum
  - Network Id: 5
  - Block time: 15 seconds on average
  - Faucet: [https://faucet.goerli.mudit.blog/](https://faucet.goerli.mudit.blog/)(Need to request the developers)
  - Status Dashboard: [https://stats.goerli.net/](https://stats.goerli.net/)
  - Explorer: [https://goerli.etherscan.io/](https://goerli.etherscan.io/)
  - GitHub: [https://github.com/goerli/testnet](https://github.com/goerli/testnet)
  - Website: [https://www.goerli.net](https://www.goerli.net)

**Ropsten** has conditions as close as possible to **mainnet** and was historically the first major **testnet**. It has had some attacks and vulnerabilities which have been addressed (DDOS and 51% attack). **Kovan**, **Goerli** and **Rinkeby** are stable and have increased usage. Generally, prior to deploying to **mainnet**, it’s advised to deploy to and test on multiple **testnets**.

## Clients and API's for deploying to **Testnets** and **Mainnet**

Ethereum is designed to offer different clients, developed by different teams using different programming languages. This makes the network stronger and more diverse. The ideal goal is to achieve diversity without any client dominating to reduce any single points of failure.

### Clients

Below is a summary of some common [Ethereum clients](https://ethereum.org/en/developers/docs/nodes-and-clients/#clients):

[**Geth Client**](https://geth.ethereum.org/?azure-portal=true)

Go Ethereum (Geth for short) is one of the original implementations of the Ethereum protocol. Currently, it is the most widespread client with the biggest user base and variety of tooling for users and developers. It is written in Go, fully open source and licensed under the GNU LGPL v3.

[**OpenEthereum**](https://github.com/openethereum/openethereum) (was Parity)

OpenEthereum's goal is to be the fastest, lightest, and most secure Ethereum client. We are developing OpenEthereum using the Rust programming language. OpenEthereum is licensed under the GPLv3 and can be used for all your Ethereum needs.

[Nethermind](https://nethermind.io/)

Nethermind provides the world's fastest .NET Ethereum Client and P2P Data Marketplace, along with consulting services for those looking to build Ethereum blockchain solutions.

[Besu](https://besu.hyperledger.org/en/stable/)

Hyperledger Besu is an open-source Ethereum client developed under the Apache 2.0 license and written in Java. It runs on the Ethereum public network, private networks, and test networks such as Rinkeby, Ropsten, and Görli. Besu implements Proof of Work (Ethash) and Proof of Authority (IBFT 2.0 and Clique) consensus mechanisms.

### APIs

[Infura](https://infura.io/?azure-portal=true)

The Infura API suite provides instant access over HTTPS and WebSockets to the Ethereum and IPFS networks. It provides a simple, easy to use interface for connecting to the endpoints of a testnet and supports **Ropsten** , **Gorli** , **Kovan** and **Rinkby**.

![](./Images/Infura_Image1.png)

Infura supports both **Truffle Suite** and the **VS Code Blockchain Development Kit for Ethereum.**

![](./Images/VSCode_Blockchain_Dev_Kit.png)

[**Metamask**](https://metamask.io/?azure-portal=true)

If you have reviewed the previous blockchain modules in this series, you will already have a good understanding of **MetaMask** and how to use it. When deploying to either a **testnet** or **mainnet** , the metamask client provides a robust interface and wallet for connecting to and interacting with Ethereum blockchains. Be careful when using the Main Ethereum network, **mainnet**.

Using **MetaMask** to send **Ether** and tokens on a **testnet** is straightforward. As we've seen in previous tutorials, the client provides an easy interface to select and use different Ethereum networks. For interacting with development networks, it's simple with **MetaMask** to connect to **Localhost 8545** or **Custom RPC** to connect with **ganache-cli** , **ganache app** and **truffle develop**. Similarly, MetaMask has predefined connections to the public testnets **Ropsten** , **Kovan** , **Rinkeby** and **Goerli**.

![](./Images/MetaMask_Mainnet1.png)
