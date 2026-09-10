# 3. Conversions : zéro, troncature et bornes uint64

[HLConversions](../../src/common/HLConversions.sol) lit `evmExtraWeiDecimals` depuis les informations du token.
Si la valeur est positive, `evmToWei` divise le montant EVM par `10^extra` : la division entière supprime le reste.
Si elle est négative, la fonction multiplie ; dans les deux cas, le résultat est converti en `uint64` avec `SafeCast`.
[CoreWriterLib](../../src/CoreWriterLib.sol) rejette un résultat égal à zéro avec `CoreWriterLib__EvmAmountTooSmall`.
Ce garde-fou évite qu’un transfert entier devienne nul, mais il ne garantit pas une conversion sans perte lorsque le quotient reste non nul.
Avant un pont, une application peut comparer `weiToEvm(evmToWei(x))` à `x` et afficher ou refuser le reste.
Pour `bridgeToEvm(..., isEvmAmount=false)`, un montant supérieur à `uint64.max` est rejeté explicitement.
Les unités `wei`, `sz`, prix spot normalisé et prix perp normalisé ne sont pas interchangeables.
Nommer les unités dans les variables et les événements réduit les erreurs d’intégration.

Suite : [Ponts : HYPE, USDC et tokens liés ne suivent pas le même chemin](04-ponts.md).
