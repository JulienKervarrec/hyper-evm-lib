# 5. Précompiles : échec, fraîcheur et index de marché

[PrecompileLib](../../src/PrecompileLib.sol) appelle les adresses système avec `staticcall`, puis décode le résultat ABI.
Chaque wrapper transforme un `success=false` en erreur dédiée, par exemple `PrecompileLib__SpotPxPrecompileFailed`.
L’erreur identifie le précompile, mais ne prouve pas à elle seule si l’index, l’adresse ou le contexte était invalide.
La documentation officielle avertit qu’une entrée invalide peut consommer tout le gas transmis au cadre d’appel.
Pour retrouver un marché spot depuis un token, `getSpotIndex` retourne l’unique marché ou cherche celui dont le quote token est l’index 0 (USDC).
Si plusieurs marchés existent sans paire USDC, la fonction lève `SpotIndexNotFound` ; l’overload avec quote token permet un choix explicite.
Le TokenRegistry évite de stocker manuellement l’index, mais son adresse et le lien du token restent des dépendances externes.
Après une action CoreWriter, une lecture dans le même flux ne doit pas servir de confirmation immédiate de l’effet attendu.
Conserver le bloc observé et distinguer erreur d’appel, erreur de décodage et donnée métier inattendue.

Suite : [Checklist avant intégration HyperEVM–HyperCore](06-checklist.md).
