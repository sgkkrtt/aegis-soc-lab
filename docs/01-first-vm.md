# Première VM : aegis-wazuh

**Procédure préparée, pas encore exécutée sur le PC.** Objectif de cette étape : obtenir Ubuntu Server et un relevé d'état avant d'installer le SIEM.

## 1. Vérifier l'hôte
Gestionnaire des tâches → Performances → CPU : relever « Virtualisation ». Si désactivée, activer AMD SVM dans l'UEFI en suivant la documentation de la carte mère.
Relever mémoire disponible, espace SSD libre, hyperviseur déjà installé et sa version. Ne pas désactiver Hyper-V/VBS ou des protections Windows sans diagnostic d'un problème précis.

## 2. Médias officiels
- VirtualBox pour Windows : https://www.virtualbox.org/wiki/Downloads ; ne pas installer l'Extension Pack.
- Ubuntu Server **24.04 LTS amd64**, image live-server, pas Desktop ni cloud image : https://releases.ubuntu.com/24.04/
- Télécharger SHA256SUMS depuis la même page ; comparer le nom et SHA256 exacts avec PowerShell :
```powershell
Get-FileHash -Algorithm SHA256 "C:\chemin\vers\ubuntu-24.04.x-live-server-amd64.iso"
```
Remplacer le chemin et x par le vrai fichier. Une comparaison de somme détecte la corruption ; vérifier la signature de SHA256SUMS permet une validation d'authenticité plus forte.

## 3. Créer
Dans VirtualBox : Nouvelle VM, nom aegis-wazuh, Linux/Ubuntu 64-bit ; sélectionner ISO et cocher « ignorer l'installation automatique ».
8192 Mo RAM, 4 CPU, disque VDI dynamique 80 Go. Pas d'accélération 3D.
Carte 1 NAT ; carte 2 host-only sera ajoutée après confirmation du réseau local. Presse-papiers, glisser-déposer et dossiers partagés désactivés.
Si un hyperviseur existe déjà, adapter la procédure avant d'en installer un second.

## 4. Installer Ubuntu
Langue au choix, clavier approprié ; Ubuntu Server standard, réseau NAT DHCP, proxy vide, miroir par défaut.
Disque entier **du disque virtuel de 80 Go uniquement**, partitionnement guidé, sans chiffrement pour ce lab et sans LVM pour simplifier. Vérifier taille/nom du disque dans le résumé avant validation.
Nom serveur aegis-wazuh ; utilisateur socadmin ; mot de passe unique conservé localement.
Ignorer Ubuntu Pro ; installer OpenSSH Server sans import de clé GitHub ; aucun snap supplémentaire.
Redémarrer et retirer l'ISO si demandé.

## 5. Relever l'état et s'arrêter à ce point
Se connecter puis :
```bash
hostnamectl
ip -br address
ip route
free -h
df -h /
timedatectl
```
Transmettre ces sorties après revue des données personnelles. Ne pas transmettre de mot de passe.
La prochaine étape dépend des noms d'interfaces, du réseau host-only et de l'état réel : configuration IP statique, mises à jour et installation Wazuh depuis l'assistant officiel relu. Ne pas installer Wazuh avant cette vérification.
