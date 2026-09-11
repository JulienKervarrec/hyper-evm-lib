# 9 — Ponts bidirectionnels et actifs récupérables

Un token lié doit définir les deux directions avant d’accepter des dépôts réels.
Implémenter le chemin vers HyperCore sans retour vers HyperEVM peut immobiliser les actifs.
Chaque direction doit vérifier l’actif, le destinataire, les décimales et le montant minimal.
Les chemins HYPE, USDC et tokens liés ne sont pas interchangeables : leurs contrats et unités diffèrent.
Un événement EVM doit permettre de reconstruire l’intention sans être présenté comme une preuve de règlement Core.
Les échecs asynchrones exigent une stratégie documentée de réconciliation et de récupération.
La propriété métier est simple : tout actif accepté a un chemin de sortie connu ou un refus explicite.

Suite : [invariants défensifs](10-invariants-defensifs.md).
