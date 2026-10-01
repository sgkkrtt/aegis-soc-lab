# Catalogue — tous les scénarios sont planifiés

| ID | Scénario contrôlé | Télémétrie à vérifier | Hypothèse |
|---|---|---|---|
| ASL-01 | Échecs SSH limités sur compte lab | sshd + agent Linux | Répétition dans une fenêtre |
| ASL-02 | Connexion Windows hors baseline | Security 4624/4625, audit vérifié | Type/horaire/source inhabituel selon baseline |
| ASL-03 | Ajout puis retrait d'un compte lab à un groupe privilégié | Audit groupes Windows ou Linux/auditd | Changement de privilège |
| ASL-04 | Processus bénin avec marqueur lab | Sysmon Event ID 1 | Processus/ligne de commande ciblés |
| ASL-05 | Requêtes HTTP limitées sur chemins de test | Nginx access/error | Reconnaissance possible, sans exploiter |
| ASL-06 | Modification puis restauration d'un fichier lab surveillé | Wazuh FIM | Intégrité modifiée |
| ASL-07 | Échecs SSH puis succès légitime | sshd : IP, compte, temps | Corrélation ; succès seul ≠ compromission |
| ASL-08 | Arrêt contrôlé puis reprise d'un agent | État agents + logs locaux | Perte de visibilité |
| ASL-09 | Tâche planifiée bénigne puis suppression | Audit Windows + Sysmon selon événement | Persistance simulée |

Pour ASL-06 commencer par un fichier dédié, pas une configuration essentielle. Pour chaque scénario : bornes de volume, cible lab explicite, préconditions, snapshot/retour arrière, contrôle négatif et collecte de preuves avant remédiation.
Les IDs de règles, seuils et champs seront décidés après observation des événements et du décodage Wazuh. La baseline précède les notions « inhabituel ». ATT&CK décrit une technique simulée, sans démontrer à lui seul une attaque.
