# 4. Ponts : HYPE, USDC et tokens liés ne suivent pas le même chemin

Dans [bridgeToCore](../../src/CoreWriterLib.sol), USDC utilise le CoreDepositWallet après une approbation ERC-20.
HYPE est envoyé en valeur native à son adresse système et l’échec de l’appel déclenche une erreur dédiée.
Les autres tokens liés sont transférés vers leur adresse système après lecture de `TokenInfo.evmContract`.
Dans l’autre sens, `bridgeToEvm` émet une action `sendAsset` vers l’adresse système du token.
Le commentaire du code précise qu’un contrat qui rapatrie un token non-HYPE doit détenir assez de HYPE sur Core pour les frais.
Le README du projet avertit qu’implémenter seulement le trajet vers Core peut laisser des actifs inaccessibles.
La [documentation officielle des transferts](https://hyperliquid.gitbook.io/hyperliquid-docs/for-developers/hyperevm/hypercore-less-than-greater-than-hyperevm-transfers) demande aussi de ne pas supposer aveuglément la fongibilité entre Core spot et EVM spot.
Une intégration doit prévoir les deux directions, les frais, les arrondis et un chemin de récupération.
Ne jamais réutiliser le cas HYPE comme modèle générique ERC-20.

Suite : [Précompiles : échec, fraîcheur et index de marché](05-precompiles.md).
