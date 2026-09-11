# 10 — Invariants défensifs d’intégration

Avant production, vérifier l’adresse système, l’identifiant d’action et l’encodage attendu par CoreWriter.
Bornder les identifiants de marché et traiter une précompile vide ou en échec comme une donnée indisponible.
Ne jamais utiliser un instantané de début de bloc comme confirmation d’une écriture du même appel.
Refuser les conversions qui débordent, deviennent nulles ou perdent une précision non autorisée.
Exiger un pont retour avant d’autoriser un actif lié et journaliser l’intention de réconciliation.
Séparer états « émis », « observé » et « finalisé » dans le contrat comme dans l’interface.
Ce parcours est documentaire : aucune installation, compilation, transaction RPC ou exécution de tests.
Les assertions doivent être confrontées aux contrats et tests du dépôt avant déploiement.
