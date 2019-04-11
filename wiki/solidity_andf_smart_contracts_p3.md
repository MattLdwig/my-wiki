---
title: Introduction au développement Ethereum
path: /dev/Ethereum/introduction
---

# Partie 3

## Types

**string**: seq of char 
**bool**: Boolean value
**int**: Integer, positive or negative (no decimal). `int` = int256 (nombre de bit), présence également de `int8` (de - 128 à 127), `int16` (-32.768 à 32.767)...
**uint**: Unsigned Int, positive (no decimal). `uint` = uint256.
**fixed/ufixed**: Fixed point number (num with a decimal). `ufixed` -> positive
**address**: Dispose d'une méthode attachée pour l'envoi de monnaie.

## 'msg' Global Variable

Disponible lors de l'invocation d'une fonction (call ou send).

**msg.data**: Champs Data pour le call ou la transaction qui a invoqué la fonction
**msg.gas**: Montant de gas disponible pour l'invocation de la fonction
**msg.sender**: Adresse du compte qui a démarré l'invocation de la fonction
**msg.value**: Montant d'Ether (en wei) qui a été envoyé lors de l'invocation de la fonction.

## Arrays

Création d'un array public = génération automatique d'une fonction call qui peut prendre comme argument la position de l'élément à retourner.

**fixed array**: Array qui ne contient qu'un seul type d'élément. Ne peut pas changer de taille. Ex `int[3]`, `bool[2]`.
**dynamic array**: Array qui ne contient qu'un seul type d'élément. Peut changer de taille. Ex `int[]`, `bool[]`.
**mapping**: Collection de key value paires. Similaire aux objects JS ou au dictionary Python. 
Les clés doivent être du même types, idem pour les values (mais clés et valeurs peuvent avoir des types différents). Ex `mapping(string => string)`, `mapping(int => bool)`.

**struct**: Collection de key value paires qui peuvent avoir différents types. 
Ex 
```
struct Car {
    string make;
    string model;
    uint value;
}
```

**Limite**: Si créer un nested dynamic array ne pose pas de problème en Solidity, la fonction n'est pas possible lors de la communication avec le front (ABI, JS, Web3). 
Problème, les strings en Solidity sont représentées comme des dynamic arrays. Impossible donc de transférer des arrays de strings en JS !!!

## Functions modifier

```
modifier restricted() {
    require(msg.sender == manager);
    _;
}
```