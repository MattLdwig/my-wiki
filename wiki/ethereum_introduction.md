---
title: Introduction au développement Ethereum
path: /dev/Ethereum/introduction
---

31 octobre 2008: Publication du whitepaper Bitcoin
2013: Publication du whitepaper Ethereum

Objectifs d'Ethereum = créer des DAC (Decentralized Autonomous Corporation).
Introduit l'idée de 'Smart Contracts'.

## Network Ethereum

Utilisé pour transférer des fonds et stocker des données.
Multiples (main network, testnet, networks privés ...)
Formés par un ou plusieurs nodes.

Interfacage avec un network Ethereum:
* web3.js pour les dev
* Metamask ou Mist Brower pour les consumers

Pour recevoir des tokens de test sur le network Rinkeby: [Rinkeby Faucet](rinkeby-faucet.com)

## Transactions

Transaction = Object contenant différentes propriétés:
* nonce -> Nombre de fois où l'envoyeur à envoyé une transaction (nonsense)
* to -> adresse du destinataire
* value -> montant d'Ether à envoyé au destinataire
* gasPrice -> Montant d'Ether que l'envoyeur a choisi de payé par unité de gas pour que la transaction soit completée
* startGas/gasLimit -> Unités de gas que la transaction peut consommer
* v -> Données cryptographique utilisées pour générer l'adresse de l'envoyeur. Généré depuis la PK de l'envoyeur.
* r -> Données cryptographique utilisées pour générer l'adresse de l'envoyeur. Généré depuis la PK de l'envoyeur.
* s -> Données cryptographique utilisées pour générer l'adresse de l'envoyeur. Généré depuis la PK de l'envoyeur.
