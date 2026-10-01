# Preuves et publication

États : planifié → exécuté → détecté → investigué → remédié → retesté. Un scénario n'est « réalisé » que si ses preuves sont disponibles et relues.

Conserver les données brutes hors Git, dans un espace privé local. Pour chaque exécution, noter un identifiant, heure UTC de début/fin, hôtes, commande exacte, versions, règle/configuration et hash SHA256 des exports. Distinguer heure de l'événement, de collecte et d'alerte. Garder les originaux ; une copie expurgée ne les remplace pas.

Avant publication : relire chaque extrait et screenshot ; retirer mots de passe, tokens, clés d'agent, clés privées, cookies et informations personnelles. Documenter les expurgations. Le .gitignore aide mais ne détecte pas les secrets dans un fichier Markdown ou une image.

Publier seulement les extraits minimaux nécessaires, associés au rapport et à leur provenance. Aucun événement synthétique présenté comme réel ; aucune alerte attendue présentée comme obtenue. Aucune métrique de taux de détection sans jeu de test, dénominateur et protocole explicites.
