
# Rapport d’activité pratique : Signature d’images Docker avec Cosign et GPG

---

## Objectif  
L'objectif de cette activité est d'assurer l'intégrité et l'authenticité des images Docker en les signant numériquement avec **Cosign** et une **clé GPG** personnelle, puis de vérifier la détection d'une image altérée.

---

##  1. Créer un projet GitLab  
Un projet GitLab a été créé avec le nom suivant : **cosign-test**, à l'adresse :  
👉 https://gitlab.com/seddik2/cosign-test

---

##  2. Générer une paire de clés GPG  
Commande :
```bash
gpg --full-generate-key
```

**Paramètres choisis :**
- Type : RSA (sign only)
- Taille : 4096 bits
- Expiration : aucune
- Identité : `SEDDIK <seddik.berrim@edu.ece.fr>`

**Résultat :**
Clé générée avec ID :
```
4C463DC6913629CA506F5BAA145E8A1C43BD00F6B
```

![Génération de la clé GPG]
![image](https://github.com/user-attachments/assets/161c529a-f390-4ffd-8d8a-70965df7d659)

---

##  3. Exporter la clé privée GPG  
Commande :
```bash
gpg --export-secret-keys --armor 4C463DC6913629CA506F5BAA145E8A1C43BD00F6B > private-gpg.key
```

---

##  4. Création et signature d'une image Docker

### Build et tag :
```bash
docker build -t registry.gitlab.com/seddik2/cosign-test:v1 .
```

### Login :
```bash
docker login registry.gitlab.com
```

### Push :
```bash
docker push registry.gitlab.com/seddik2/cosign-test:v1
```

### Signature :
```bash
cosign sign --key cosign.key registry.gitlab.com/seddik2/cosign-test:v1
```

![Signature Cosign]
![image](https://github.com/user-attachments/assets/9159eae3-edb7-4d7a-9fd0-4ac6b28b67d6)


---

##  5. Modification de l'image et push d’une version altérée

### Étapes :
```bash
docker run -it registry.gitlab.com/seddik2/cosign-test:v1 sh
touch /tampered
exit
```

### Commit + push :
```bash
docker commit $(docker ps -lq) registry.gitlab.com/seddik2/cosign-test:v2
docker push registry.gitlab.com/seddik2/cosign-test:v2
```

---

##  6. Vérification des signatures

###  Image originale :
```bash
cosign verify --key cosign.pub registry.gitlab.com/seddik2/cosign-test:v1
```
Résultat : **Succès**

###  Image altérée :
```bash
cosign verify --key cosign.pub registry.gitlab.com/seddik2/cosign-test:v2
```
Résultat : **Erreur - no signatures found**

![Erreur signature v2]
![image](https://github.com/user-attachments/assets/ae2026fb-69b6-4b7a-a8d5-c52ee419b9e6)

---

##  Conclusion

La signature de l'image Docker avec Cosign et GPG a permis de :
- Valider l’authenticité de l’image d’origine
- Détecter une altération sur une image modifiée

**Cosign est donc un outil puissant et simple à intégrer dans une chaîne CI/CD pour garantir l'intégrité des conteneurs.**

---


**Projet GitLab :** https://gitlab.com/seddik2/cosign-test
