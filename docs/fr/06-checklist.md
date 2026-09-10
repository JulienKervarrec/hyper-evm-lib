# 6. Checklist avant intégration HyperEVM–HyperCore

1. Fixer la révision de la bibliothèque et la documentation Hyperliquid consultée.
2. Écrire pour chaque méthode l’identité HyperCore qui agit : souvent `address(this)`.
3. Restreindre les fonctions publiques qui déclenchent CoreWriter et borner leurs paramètres.
4. Identifier l’unité de chaque montant, la borne `uint64` et le reste potentiel de conversion.
5. Prévoir les deux directions du pont ainsi que le HYPE nécessaire aux frais côté Core.
6. Traiter une action émise, son exécution HyperCore et sa lecture ultérieure comme trois étapes.
7. Valider token, index, paire et quote token avant d’appeler un précompile.
8. Ne pas utiliser une lecture du même bloc comme accusé d’exécution d’une écriture CoreWriter.
9. Journaliser les identifiants utiles sans exposer de clé, secret RPC ou donnée privée.
10. Prévoir arrêt, reprise et récupération lorsqu’une étape asynchrone échoue.
Ce parcours est documentaire : aucune installation, compilation, transaction, requête RPC ou exécution de tests.
Pour vérifier, partir des [tests amont](../../test) et des [exemples](../../src/examples) dans un environnement isolé adapté.

Retour au [sommaire](README.md).
