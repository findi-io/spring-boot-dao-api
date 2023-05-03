# spring-boot-dao-api
wrap web3 dao related function using spring boot and oauth2, expose api using swagger

## background
Blockchain is not only for crypto gambling. Smart contract brings great protential to build common trust based on reliable source code. 
So far web3 advocates distributed architecture as key feature, using different cryptography and authentication mechanism, which draws clear boundary between web2 technologies. 
From my opinion, integrate both web2 and web3 technologies is the key to succeed a better result from end user perspective. Inspired by [solidity-google-auth](https://github.com/lucashenning/solidity-google-auth) and [CodeforDAO](https://github.com/CodeforDAO/contracts), here I want to build such a framework for common DAO use cases.

## architecture
 ![architecture diagram](/assets/images/dao.png)

 main considerations:
 1. Oauth2 is a well used authentication method, instead of having a dedicate private key, having a proxy contract with jwt validation can achieve the same.
 2. Having two ERC20 token, DAO token for ownership, vote for decision. Treasury token for mapping fiat currency to react with real world. From funding perspective, mint DAO token for Equity financing, and mint Treasury token for debt financing.
 3. Blockchain is useful to build the trust layer. In this architecture, we use spring boot to build an application layer on top of blockchain, and use [besu plugin](https://github.com/ConsenSys/besu-plugins) from Consensys to export event to kafka, and building webhooks to react to onchain events.