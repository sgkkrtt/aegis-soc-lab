# Phases et critères

| Phase | Travail | Critère de sortie | État |
|---|---|---|---|
| 0 | Architecture, dimensionnement, dépôt | Documents préparés ; matériel local à confirmer | Préparée |
| 1 | VM Wazuh : OS, réseau, installation | Services actifs, dashboard accessible, versions et mémoire relevées | À exécuter |
| 2 | Endpoint Linux, SSH, Nginx, agent | Événement réel visible avec source et heure cohérentes | À exécuter |
| 3 | Windows 11, audit, Sysmon, agent | Événement de processus visible et audit vérifié | À exécuter |
| 4 | Baseline et premières détections | Activité normale observée ; règles testées sur événements réels | À exécuter |
| 5 | Scénarios et investigations | Alerte, timeline, cas positif et contrôle négatif documentés | À exécuter |
| 6 | Réponse et hardening | Remédiation appliquée, retest et retour arrière documentés | À exécuter |
| 7 | Présentation | README mis à jour avec résultats prouvés, revue des données | À exécuter |

Chaque étape dépend des résultats de la précédente. Pas de règle présentée comme opérationnelle avant wazuh-logtest et test de bout en bout. Pas de réponse automatique initiale : investigation et actions manuelles réversibles d'abord.
Noter versions OS/hyperviseur/Wazuh/Sysmon, configuration, date, commandes et critères. Faire des commits par résultat cohérent ; conserver les échecs utiles et les limites.

Pour un entretien : expliquer pourquoi une donnée est collectée, quelle hypothèse une règle teste, comment on vérifie une alerte et quelles conclusions les preuves ne permettent pas.
