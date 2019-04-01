---
title: CryptoZombie
path: /dev/Ethereum/CryptoZombie/chap-1
---
```
pragma solidity ^0.4.19; 
// déclaration de la version de Solidity à utiliser

contract ZombieFactory { 
// Contrat

    event NewZombie(uint zombieId, string name, uint dna);
    // Évènement, permet d'intéragir avec la partie Front de l'application

    uint dnaDigits = 16;
    // uint = entier non signé (entiers non négatifs).
    uint dnaModulus = 10 ** dnaDigits;
    // 10 puissance dnaDigits

    struct Zombie {
    // struct = équivalent des objets en js
        string name;
        uint dna;
    }

    Zombie[] public zombies;
    // Array. 
    // Zombie[] déclare un array basé sur la struc Zombie,
    // public rend les données contenues dans le tableau lisible par d'autres contrats, 
    // zombies est le nom du tableau

    function _createZombie(string _name, uint _dna) private {
    // Fonction, rendue privée pour éviter qu'elle ne soit accessible à tous (convention: noms des fonctions privées commencent par _)    
    // déclaration du type des arguments (le _ est une convention, pour éviter la confusion avec les variables globales)
        uint id = zombies.push(Zombie(_name, _dna)) - 1;
        // push d'un nouveau zombie dans le tableau zombie et récupération de son index
        NewZombie(id, _name, _dna);
        // appel de l'event NewZombie
    }

    function _generateRandomDna(string _str) private view returns (uint) {
    // Fonction view, peut seulement lire des données (existent aussi les fonctions pure, qui n'ont accès à aucune donnée de l'app)
    // En Solidity => déclaration du type de valeur retournée (returns(uint))
        uint rand = uint(keccak256(_str));
        // Récupération du hash 256 de la string, puis conversion en uint pour éviter les erreurs dûes aux différences de types.
        return rand % dnaModulus;
    }

    function createRandomZombie(string _name) public {
        uint randDna = _generateRandomDna(_name);
        _createZombie(_name, randDna);
    }

}
```