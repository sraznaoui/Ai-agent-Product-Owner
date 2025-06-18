# 🤖 AI-Agent Product Owner

## 🧭 Présentation Générale
Ce projet a été conçu comme un agent intelligent au service des Product Owners d’une plateforme SaaS de gestion de projet. L’objectif : soulager le PO de la surcharge opérationnelle.

🛠 Il orchestre trois missions fondamentales :

- ✍️ Générer des **User Stories** enrichies (titre, description, critères, complexité)
- 🚦 Prioriser les éléments du backlog via les frameworks **MoSCoW** & **RICE** 
- 📬 Classifier automatiquement les mails entrants en **Bug**, **Feature Request** ou **Feedback**.

L’ensemble est propulsé par **n8n** et **OpenAI**, avec une interface pilotée via **Airtable**.

---

## 🛠️ Architecture

### 🧩 Stack Technique
- `n8n` – Moteur d’orchestration no-code
- `Airtable` – Front-end léger, base de données collaborative et formulaire de feedbakcs clients. voici l'accès à la base donné https://airtable.com/appdbdWixyLMElhAH/shrX1YU7wWhg9DkuJ
- `OpenAI API` – Intelligence de génération et d’analyse
- `Gmail` – Source de données pour les feedbacks clients

### 🔗 Interfaces clés dans Airtable
- **Brief** : déclenche la génération de stories à partir du brief client
- **Projet** : lance la priorisation des features associées
- **Feedback** : centralise les retours analysés automatiquement
- **MoSCoW Prioritization** : Visualise les priorisations des features

En vu des limitation sur Airtable un accès complet avec la possibilité de modifier ne peut être données qu'aux collaborateurs du workspace ( payant ), si vous voulez y accéder n'hésitez pas à me le demander.

---

## ⚙️ Workflows IA

### 1. ✍️ Génération assistée de User Stories
**Déclencheur :** script depuis l’onglet **Brief**

Fonctions :
- Génération structurée de stories (titre, description, critères)
- Estimation automatisée de la complexité (XS → XL)
- Association automatique au projet parent
- Synthèse d’une **vision produit mobilisatrice**

📌 `https://airtable.com/appdbdWixyLMElhAH/shr61nuyOpT0LW8ZC?Bm7FO=recC7u336r20vEihL  ( Lecture seule ).`

Chaque projet peut avoir plusieuers brief et sur la base de chaque brief client nous pouvons générer les User Stories.

Ici on lance le process de "Assisted Writing"


![image](https://github.com/user-attachments/assets/fd6a2fe1-d05b-4008-bf6e-9d75818330ce)

L'automation via Script sur Airtable :

![image](https://github.com/user-attachments/assets/4f085b61-994a-4968-804e-c2c53bdc1340)


Le Script Airtable pour déclencher le workflow de n8n : 

![image](https://github.com/user-attachments/assets/f83792c2-fa73-4314-b237-d55c233fd6a2)




Ici le workflow : 

![image](https://github.com/user-attachments/assets/75fa5f9f-c864-49ff-ad5c-37e658506ac0)



Dès que le workflow est terminé le PO en charge du projet reçoit un mail de confirmation : 

![image](https://github.com/user-attachments/assets/6522dc03-4008-4202-b76b-cb618d3aef0d)




Ici le résultat : 

![image](https://github.com/user-attachments/assets/c3ab484f-f372-4e3b-9554-4d5027464b3e)


![image](https://github.com/user-attachments/assets/7b9f9659-1aa6-4ec5-93f0-fbb9bbcf85ad)


* Note importante : pour ne pas mettre en erreur le PO j'ai mis deux cases pour prévenir comme quoi la user story a été créée par l'IA et une case pour confirmer que cela a été vérifié par le PO

---

### 2. 🚦 Priorisation intelligente du backlog
**Déclencheur :** clic depuis l’onglet **Projet**

Fonctions :
- Lecture du backlog lié
- Application stricte de la méthode **MoSCoW** (via LLM)
- Estimation de **Reach** & **Impact** (RICE)
- Explication contextuelle de la priorité attribuée

  * Note important : le C & le E de RICE ne peut pas être délégué à l'IA car il s'agit d'une estimation subjective du PO et de son équipe de développement donc je laisse le remplissage de cette donné au PO

📌 `(https://airtable.com/appdbdWixyLMElhAH/shrruPyt9kQdQP9rm)`

![image](https://github.com/user-attachments/assets/801aa64f-9906-46e0-a507-6f3d3106b8a0)



Ici le résultat : 

![image](https://github.com/user-attachments/assets/080f0798-dfbc-498f-8e78-9909e3c77027)


---

### 3. 📬 Analyse des Feedbacks
**Déclencheur :** emails entrants ou formulaire externe

Fonctions :
- Scraping intelligent du contenu de mail toutes les heures
- Classification sémantique stricte : `Bug`, `Feature Request`, `Feedback`, ou `Hors Sujet`
- Extraction des données clés (contact, projet, contenu)
- Intégration dans la table **Feedbacks**
- Intégration des Feedbacks via Formulaire donné aux clients 

📌 `[Lien Airtable à insérer – Feedback]`



---

## 🧪 Guide de test

1. 🧾 Saisir un **brief** client dans Airtable
2. 📊 Ouvrir le projet et lancer la **priorisation automatique**
3. 📩 Envoyer un email à la boîte configurée pour test
4. 🌍 (Optionnel) Soumettre une demande via le **formulaire public**

---

## 📚 Détails Techniques
- RICE : seuls **R** et **I** sont calculés par l’IA ; **C** et **E** sont à compléter manuellement
- La Vision Produit suit un format actionnable :
  > "Notre produit [type de solution] aide [utilisateur] à [transformation], en leur fournissant [valeurs clés]. Contrairement à [alternative], notre produit permet [bénéfice différenciant]."
- Lien entre projet et backlog géré par `recordId` sécurisé dans chaque scénario

---

## 🧠 Pistes d'Amélioration
- [ ] Ajouter une **vidéo de démonstration** ou animation GIF
- [ ] Améliorer l’expérience sur le **formulaire utilisateur**
- [ ] Intégrer une **réponse automatique personnalisée** par email

---

## 👤 Auteur
Projet conçu par **Saad**, ingénieur efficacité énergétique & Product Builder IA / No-Code 🚀

💡 N’hésitez pas à fork, tester ou collaborer !

---

> "Build once. Scale endlessly."
