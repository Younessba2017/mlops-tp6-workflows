# Orchestrateur ou intégration continue ? (TP06)

| Critère | Prefect (orchestrateur) | GitHub Actions (CI) |
|---|---|---|
| Ce qui déclenche l'exécution | Planification du lundi ou Quick run dans l'interface | Push Git ou déclenchement manuel |
| Où s'exécute le traitement | Sur notre poste Windows, via serve ou un worker Process | Sur une machine Linux fournie par GitHub |
| Qui surveille, et où | Prefect affiche les états, les tâches, les durées et les journaux | GitHub affiche les étapes et leurs journaux dans Actions |
| Ce qui se passe en cas d'échec | Le workflow passe à Failed ; si la validation échoue, notifier ne s'exécute pas | Le job passe au rouge ; les rapports sont conservés grâce à if: always() |
| Type de tâche adapté | Traitements récurrents, réentraînement et suivi des exécutions | Vérification automatique des modifications du projet |
| Ce qui est versionné dans Git | flow_mlops.py, planifier.py et prefect.yaml | ci.yml, verifier_qualite.py et requirements-ci.txt |

## Conclusion

Prefect permet de planifier et de surveiller le pipeline de réentraînement.
Le worker exécute les traitements demandés par le serveur.
GitHub Actions vérifie automatiquement le pipeline à chaque push.
Les deux outils refusent le modèle lorsque son F1 est inférieur à 0.82.
Ils sont complémentaires : la CI vérifie les modifications et l'orchestrateur gère les traitements récurrents.