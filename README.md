# Aegis SOC Lab

Laboratoire personnel de cybersécurité défensive : collecte Windows/Linux, SIEM Wazuh, détections personnalisées et investigations documentées.

**État : conception et préparation. Aucune VM ni détection n'a encore été validée dans le laboratoire. Aucun incident réalisé n'est revendiqué.**

## Objectif
Apprendre à exploiter une chaîne complète : endpoints → télémétrie → collecte → détection → alerte → investigation → remédiation → vérification. Le laboratoire est local, sans service payant. Les évaluations Windows ont une durée limitée.

## Architecture
Trois VM prévues sur un hôte Windows avec Ryzen 7 5700X et 16 Go de RAM : Ubuntu Server 24.04 LTS pour Wazuh tout-en-un, Windows 11 avec Sysmon et agent Wazuh, Ubuntu Server 24.04 LTS avec SSH/Nginx et agent Wazuh. Active Directory est une extension future.
Voir [le réseau et le budget](architecture/network.md).

## Démarrer
1. Lire [les phases et critères de validation](docs/roadmap.md).
2. Suivre [la création de la première VM](docs/01-first-vm.md).
3. Conserver les preuves brutes hors du dépôt et suivre [la politique de preuves](docs/evidence.md).

## Scénarios et résultats
Les neuf scénarios du [catalogue](detections/catalog.md) sont **planifiés, non exécutés**. Les règles seront écrites à partir des événements réellement collectés, puis testées dans Wazuh. Aucun screenshot, log ou rapport d'incident terminé n'est fourni.

## Compétences visées
Virtualisation et réseau, administration, audit Windows/Sysmon, logs SSH/web, SIEM, corrélation, réglage des faux positifs, timelines UTC, réponse à incident et hardening. Ces compétences seront illustrées par les cas effectivement validés.

## Différence avec mes autres projets
[Security Log Analyzer](https://github.com/sgkkrtt/security-log-analyzer) analyse des fichiers localement avec des heuristiques Python et une démonstration synthétique. Aegis ajoute les machines sources, les agents, un SIEM et des preuves issues d'exécutions réelles. Une comparaison sur les mêmes logs SSH pourra être étudiée.
[Linux Sysadmin Toolkit](https://github.com/sgkkrtt/linux-sysadmin-toolkit) fournit inventaire, contrôle disque et sauvegarde. Il pourra servir au diagnostic de l'endpoint Linux, sans recopier ses fonctionnalités ici.

## Organisation
- architecture/ : topologie et décisions de dimensionnement.
- docs/ : procédures reproductibles et suivi de validation.
- detections/ : catalogue ; règles et tests ajoutés avec la télémétrie.
- incident-reports/ : modèle, puis rapports réels validés.
- wazuh/, sysmon/, scripts/, screenshots/ : ajoutés lorsqu'ils contiennent des éléments utiles et vérifiés.

## Cadre
Uniquement les machines du laboratoire autorisé. Pas de VM, ISO, secrets ou journaux bruts dans Git. Une alerte est un indice à investiguer, pas une preuve automatique de compromission.
