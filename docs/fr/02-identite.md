# 2. Qui agit réellement sur HyperCore ?

Le contrat appelant CoreWriter agit au nom de sa propre adresse HyperEVM sur HyperCore.
Dans `_canWithdrawFromVault`, [CoreWriterLib](../../src/CoreWriterLib.sol) interroge explicitement `userVaultEquity(address(this), vault)`.
`address(this)` désigne le contrat qui utilise la bibliothèque, pas automatiquement l’EOA ayant initié la transaction.
La documentation officielle illustre également une action envoyée au nom de l’adresse du contrat appelant.
Une interface utilisateur ne doit donc pas présenter l’action comme celle de `msg.sender` sans mécanisme applicatif qui lie ces identités.
Les fonctions `addApiWallet`, `sendAsset` et `setAbstraction` transportent des adresses dans leurs paramètres, mais cela ne change pas l’identité de l’émetteur CoreWriter.
Les contrôles d’autorisation avant l’appel restent entièrement à la charge du contrat intégrateur.
Une fonction publique non protégée peut ainsi exposer les actifs ou permissions du contrat sur HyperCore.
Documenter pour chaque fonction : qui peut l’appeler, quel compte HyperCore agit et qui reçoit le résultat.

Suite : [Conversions : zéro, troncature et bornes uint64](03-decimales.md).
