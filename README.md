# Contexte

NexBuy, une marketplace e-commerce, a déclenché une alerte fraude niveau ROUGE. Le système a détecté des schémas transactionnels anormaux sur ~3% des transactions du dernier trimestre, soit une exposition financière estimée entre 180 000 € et 490 000 €.

## Besoin

Conduire une analyse forensique complète sur 4 970 transactions (90 jours) pour identifier les transactions suspectes avant 17h00.

## Objectifs

- Explorer et nettoyer le dataset (valeurs manquantes, montants aberrants)
- Concevoir sur papier les pipelines MapReduce pour 5 pistes d'analyse
- Implémenter en PySpark les 5 pistes :

    Piste A — Profil horaire (heures anormales via z-score)
    Piste B — Burst client (> 5 transactions en 2h ou > 1500€/24h)
    Piste C — Géographie suspecte (billing ≠ delivery + carte prépayée/crypto)
    Piste D — Nouveaux comptes (< 7 jours, distribution des montants)
    Piste E — Score composite 0-100 (top 50 transactions suspectes)

- Optimiser avec .cache(), partitionnement, éviter les shuffles inutiles
- Visualiser (1 graphique par piste)
- Valider les résultats contre le label is_fraud
  