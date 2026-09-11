# 7 — Visibilité entre CoreWriter et précompiles

CoreWriter émet une action destinée à HyperCore ; il ne transforme pas l’état HyperCore pendant l’appel EVM courant.
Les précompiles exposent un instantané établi au début du bloc HyperEVM.
Lire une précompile juste après un write ne prouve donc pas que l’action a été appliquée.
Un contrat doit séparer émission, identification de la demande et observation ultérieure.
Le succès EVM signifie que l’appel a été accepté localement, pas que l’effet métier est final sur HyperCore.
Les interfaces doivent exposer cet état intermédiaire au lieu d’afficher prématurément une réussite définitive.
Pour réconcilier, on associe l’action à un bloc, puis on relit un instantané postérieur.

Suite : [arrondis et précision](08-arrondis-et-precision.md).
