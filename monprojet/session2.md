![Capture d'écran 2025-04-30 202107](https://github.com/user-attachments/assets/d881b567-ab7b-4f5b-a267-4b0bfc5bbbcf)

Exposition du Port 8080 

docker run -d -p 8080:80 nginx

Le port 8080 est exposé sur toutes les interfaces, comme visible dans netstat.

Problème : Exposition inutile augmentant la surface d'attaque.

Bonnes pratiques :

Restreindre à une IP spécifique. 

Utiliser un réseau Docker isolé.


![Capture d'écran 2025-04-30 202947](https://github.com/user-attachments/assets/98e8d698-80f1-4e9b-ac45-9613e9d58326)

![Capture d'écran 2025-04-30 203008](https://github.com/user-attachments/assets/6d44233f-609b-43e3-b273-f8508196e234)

Observations :

Lecture réussie (cat /mnt/passwd) : Accès au fichier système critique.

Échec d'écriture (Read-only file system) : Montage en ro efficace.

Risque : Même en lecture seule, exposer /etc/passwd révèle des infos sensibles.

Solution : Éviter de monter des fichiers systèmes. Préférer les secrets Docker.


![Capture d'écran 2025-04-30 203737](https://github.com/user-attachments/assets/81563665-e469-4f3d-829c-26ba5a4e3952)

Résultat Docker Bench Security
Score : 6/117
Configuration très faible en sécurité.
Absence de profils AppArmor/Seccomp.
Conteneurs privilégiés.
Secrets en clair.


![Capture d'écran 2025-04-30 230344](https://github.com/user-attachments/assets/83f2a452-68b1-4683-8ccc-af86f9c09f86)

Démarrage de Vault
Stockage local
Interface web activée 
Bonnes pratiques :
* --cap-add=IPC_LOCK pour sécuriser la mémoire.
* Utilisation de politiques ACL pour limiter l'accès.
