---
title: Introduction au développement Ethereum
path: /dev/Ethereum/introduction
---

# Partie 2

Schéma de déployement:

Contract -> Solidity Compiler 
    -> Bytecode -> (Contrat Instance sur Ganache/testRPC)
    -> ABI -> Web3 -> Communication avec le Contrat Instance

## Web3

*Web3 Versioning:* 
V0.x.x => Primitive interface, only callbacks for async code
V1.x.x => Support des promises + async/await

`Web3` => Constructor
`web3` => Instance

Web 3 -> web3 <- Provider <- Ganache

Provider = Relai de communication entre l'instance web3 et le network (ici Ganache).

Web3 et contrats (informations nécessaires aux actions)
------
Goal | ABI | Bytecode | Adresse du contrat déployé |
Interagir avec le contrat | ✔️ | ❌ | ✔️ |
Créer un contrat | ✔️ | ✔️ | ❌ |
------

## Mocha

Trois functions principales:

* it : Run un test et fait une assertion
* describe: groupe une collection de it fonctions
* beforeEach: exécute some general setup code

```
class Car {
    park() {
        return 'stopped';
    }
    drive() {
        return 'vroom';
    }
}

let car;

beforeEach(() => {
    car = new Car();
});

describe('Car', () => {
    it('can park', () => {
        assert.equal(car.park(), 'stopped');
    });

    it('can drive', () => {
        assert.equal(car.drive(), 'vroom');
    })
});
```