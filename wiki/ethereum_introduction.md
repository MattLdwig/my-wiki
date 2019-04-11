---
title: Introduction au développement Ethereum
path: /dev/Ethereum/introduction
---

31 octobre 2008: Publication du whitepaper Bitcoin.
2013: Publication du whitepaper Ethereum.

Objectifs d'Ethereum = créer des DAC (Decentralized Autonomous Corporation).
Introduit l'idée de 'Smart Contracts'.

## Network Ethereum

Utilisé pour transférer des fonds et stocker des données.
Multiples (main network, testnet, networks privés ...)
Formés par un ou plusieurs nodes.

Interfacage avec un network Ethereum:
* web3.js pour les dev
* Metamask ou Mist Brower pour les consumers

Pour recevoir des tokens de test sur le network Rinkeby: [Rinkeby Faucet](rinkeby-faucet.com) ou [Faucet Rinkeby](faucet.rinkeby.io)

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

## Blockchain

Block Time = Temps requis pour trouvé la bonne combinaison de hash + nonce qui correspondra à la condition (correspond à la difficulté).
Target Block Time ETH = 15 sec

## Smart Contract

Compte contrôlé par du code. Contient:
* balance
* storage (data stocké pour ce contrat)
* code (raw machine code)

** Smart Contract spécifique à un network contrairement aux comptes classiques**.

Schéma: (Computer contient **Contract Source**) --> (Network contient **Contract Instance**). Même principe que Class et Instance en JS:

```
class Car {
    ...
}

const mustang = new Car();
```

## Solidity

Écrit dans des `.sol` files.
Typés (contrairement à JS), similaire à JS dans bien des cas mais avec de grosses différences.

Schéma Solitidy: (Contract Definition) --> Solidity Compiler --> Byte code ready for deployement
                                                             --> Application Binary Interface (ABI) Interfacage du JS en Bytecode

Premier contrat:

```
pragma solidity ^0.4.17;

contract Inbox {
    string public message;
    
    function Inbox(string initialMessage) public {
        message = initialMessage;
    }
    
    function setMessage(string newMessage) public {
        message = newMessage;
    }
    
    function getMessage() public view returns(string) {
        return message;
    }
}
```

Fonction Types les plus communes:

* public: peut être appeler par n'importe qui
* private: peut être appeler uniquement par le contrat
* view ou constant: se contente de retourner des datas
* pure: ne modifie ni ne lit aucune donnée du contrat
* payable: demande un certain montant d'Eth pour être exécuter

**Important**: Déclarer une variable *public* dans le storage va créer automatiquement une fonction du même nom qui retourne la variable.

Comptes servant à créer une transaction de contrat:

* nonce -> Nombre de fois où l'envoyeur à envoyé une transaction (nonsense)
* to -> **vide**
* **data -> Bytecode compilé du contrat**
* value -> montant d'Ether à envoyé au destinataire (ici le contrat)
* gasPrice -> Montant d'Ether que l'envoyeur a choisi de payé par unité de gas pour que la transaction soit completée
* startGas/gasLimit -> Unités de gas que la transaction peut consommer
* v -> Données cryptographique utilisées pour générer l'adresse de l'envoyeur. Généré depuis la PK de l'envoyeur.
* r -> Données cryptographique utilisées pour générer l'adresse de l'envoyeur. Généré depuis la PK de l'envoyeur.
* s -> Données cryptographique utilisées pour générer l'adresse de l'envoyeur. Généré depuis la PK de l'envoyeur.

**Important**: Pour changer quoi que ce soit sur la blockchain Ethereum => Transaction.

Running Contract Functions

Appeler une fonction (Call):
* Ne peut pas modifier les données du contrat
* Peut retourner des données
* S'exécute immédiatement
* Gratuit

Envoyé une transaction à une fonction (Transact):
* Peut modifier les données du contrat
* Prend du temps à s'exécuter
* Retourne le hash de la transaction et rien d'autre!
* Coûte de l'argent

## Wei vs Ether

1 Ether = 1,000,000,000,000,000,000 Wei
Minimum fraction = 1 Wei

## Gas & Transaction

Gas = coût d'éxécuter d'une fonction


