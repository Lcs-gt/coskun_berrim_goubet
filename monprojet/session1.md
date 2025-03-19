Activités Pratiques

1 - Lancer un Container Simple

<img width="562" alt="image-1" src="https://github.com/user-attachments/assets/d10f7bd2-a232-4e09-b6dc-d3fb0e9949fb" />


2 - Explorer un Container en Interactif

<img width="435" alt="image" src="https://github.com/user-attachments/assets/4b3835f6-6b2b-4f0e-b791-535305200b8f" />


3 - Analyser les ressources système d’un container

<img width="632" alt="image" src="https://github.com/user-attachments/assets/d9db078f-5128-4949-a773-4f3116538d87" />


4 - Lister les capacités d’un container

<img width="508" alt="image" src="https://github.com/user-attachments/assets/6f49e3fe-35ca-4d72-8b93-79fea13180ec" />





Activités Pratiques 

1/ Tester un Container avec des Permissions Élevées

<img width="524" alt="image" src="https://github.com/user-attachments/assets/822dff70-4f31-4282-ab36-615d37cd8c14" />

Cette pratique est dangereuse, car elle donne au conteneur un accès total au système hôte. Cela permet à un attaquant de modifier des fichiers système, d’accéder aux périphériques et même de prendre le contrôle de la machine.


2/ Simuler une Évasion de Container

<img width="281" alt="image" src="https://github.com/user-attachments/assets/e14ce33d-a11d-4a7e-aebc-20e41986cae9" />

Cette faille permet au conteneur d'accéder et de modifier tous les fichiers du système hôte. Un attaquant pourrait alors voler des données, modifier des fichiers critiques ou même prendre le contrôle total de la machine.


3/ Créer une Image Sécurisée

Écrire un Dockerfile minimaliste :

<img width="265" alt="image" src="https://github.com/user-attachments/assets/a4bd46e1-b81a-4835-9f3c-66190dce056a" />

Construire et exécuter l’image

<img width="617" alt="image" src="https://github.com/user-attachments/assets/e41ec57d-f0c6-4ffa-8486-a41f79dd2551" />

Afficher l'id et l'uid de cet utilisateur

<img width="266" alt="image" src="https://github.com/user-attachments/assets/b485012f-ec4a-4f41-8d22-1c37399d7cf7" />



4/ Restreindre l’accès réseau d’un container

<img width="600" alt="image" src="https://github.com/user-attachments/assets/aa356b44-a46e-459e-9a3a-f3ce71568fa5" />

7/ Télécharger et Scanner une Image

Télécharger une image vulnérable et l’analyser avec Trivy :

<img width="605" alt="image" src="https://github.com/user-attachments/assets/12abf913-769c-4845-bdc5-7d654e504cd2" />


<img width="628" alt="image" src="https://github.com/user-attachments/assets/1febb6db-8aeb-401a-a7d7-53cd1b609532" />


<img width="624" alt="image" src="https://github.com/user-attachments/assets/712d410b-7e2e-42bb-bc87-9ec7e90e5a23" />

Résumé des vulnérabilités :


L'image vulnerables/web-dvwa utilise Debian 9.5, une version obsolète qui ne reçoit plus de mises à jour de sécurité. Le scan Trivy a détecté plusieurs vulnérabilités, dont certaines critiques. L'absence de mises à jour de sécurité augmente les risques d'exploitation.



8/ Scanner une Image pour Détecter les Vulnérabilités

Analyser une image avec Grype :

<img width="631" alt="image" src="https://github.com/user-attachments/assets/647716e0-6ab2-42fa-8406-5244c0044205" />


