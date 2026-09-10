# 1. HyperEVM et HyperCore : deux couches, un protocole

HyperEVM exécute les contrats EVM tandis que HyperCore porte notamment les comptes et marchés natifs de Hyperliquid.
La [documentation officielle](https://hyperliquid.gitbook.io/hyperliquid-docs/for-developers/hyperevm/interacting-with-hypercore) expose deux voies : précompiles de lecture et contrat système CoreWriter pour écrire.
Dans [CoreWriterLib](../../src/CoreWriterLib.sol), chaque action est envoyée au contrat `0x3333…3333` sous forme de bytes encodés.
Le premier octet est la version ; les trois suivants forment l’identifiant d’action en big-endian ; la suite est un `abi.encode` des champs.
Une transaction EVM réussie signifie que l’action a été émise, pas que son effet HyperCore est déjà observable.
La documentation annonce un traitement différé de certaines actions pour éviter un avantage de latence.
Les précompiles reflètent l’état HyperCore disponible lors de la construction du bloc EVM.
Une intégration doit donc modéliser « demandé », « traité » et « observé » comme des états distincts.
Ce parcours suit la révision amont `4eb7ab044d0a368e0c01ec5b38d5ea48a3e3b427`.

Suite : [Qui agit réellement sur HyperCore ?](02-identite.md).
