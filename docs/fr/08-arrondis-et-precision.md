# 8 — Arrondis, précision et conservation

Les unités EVM et Core peuvent utiliser des nombres de décimales différents.
Une division entière tronque : lorsque les décimales EVM dépassent celles du Core, une partie de la valeur disparaît.
Toute conversion doit annoncer son sens d’arrondi et refuser un résidu si l’opération exige une conservation exacte.
Les bornes du type Core doivent être vérifiées avant le cast, jamais après une troncature.
Un aller-retour EVM → Core → EVM fournit un invariant utile : résultat égal, ou perte explicitement bornée.
Les montants nuls produits par arrondi doivent être rejetés avant d’émettre une action.
L’interface utilisateur doit afficher l’unité source, l’unité cible et le delta d’arrondi.

Suite : [ponts bidirectionnels](09-ponts-bidirectionnels.md).
